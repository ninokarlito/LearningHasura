## Setting VPN 
Koneksikan VPN yang sudah di dapatkan dengan VPN Pritunl.
[Dokumentasi penggunaan Pritunl](https://docs.google.com/document/d/12waQ-Z15AeJ61NZ48Avke8BO27v_Oc5e/edit?usp=drive_link&ouid=106095707560747597119&rtpof=true&sd=true)

## Koneksi atau Menyambungkan ke Rancher
Setelah VPN terhubung, gunakan informasi di bawah ini untuk login ke Rancher :
- **URL:** `https://10.100.13.175/`
- **User:** `devteams`
- **Password:** `K4wah1j3n2024`
- **Cluster Kubernetes:** `cluster-k8s-alldataint`

## Deploy Hasura 
Setelah login, silahkan melakukan deploy hasura, dengan namespace yang telah dibuat.

Untuk list server dan juga namespace dapat dilihat pada file berikut [List Server.xlsx](https://github.com/user-attachments/files/17197355/List.Server.xlsx)


Berikut adalah kode yang saya gunakan :

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  labels:
    app: hasura
    hasuraService: custom
  name: hasura-nino
  namespace: nino
spec:
  replicas: 1
  selector:
    matchLabels:
      app: hasura-nino
  template:
    metadata:
      labels:
        app: hasura-nino
    spec:
      containers:
      - image: hasura/graphql-engine:v2.42.0
        imagePullPolicy: IfNotPresent
        name: hasura
        env:
        - name: HASURA_GRAPHQL_DATABASE_URL
          value: postgres://nino:nino@10.100.13.205:/nino
        - name: HASURA_GRAPHQL_ENABLE_CONSOLE
          value: "true"
        - name: HASURA_GRAPHQL_DEV_MODE
          value: "true"
        ports:
        - name: http
          containerPort: 8080
          protocol: TCP
        livenessProbe:
          httpGet:
            path: /healthz
            port: http
        readinessProbe:
          httpGet:
            path: /healthz
            port: http
        resources: {}
```



## Menambahkan Service untuk Hasura pada Rancher
Setelah melakukan Deployment untuk Hasura selanjutnya, kita harus menambahkan service untuk hasura tersebut.

Berikut contoh file untuk Service pada hasura yang saya gunakan :

```yaml
apiVersion: v1
kind: Service
metadata:
  labels:
    app: hasura-nino
  name: hasura-nino
  namespace: nino
spec:
  ports:
  - protocol: TCP
    port: 8886
    targetPort: 8080
  selector:
    app: hasura
  type: LoadBalancer
```


## Membuat Hasura Enterprise
By Default untuk hasura akan terpasang bukan dengan versi enterprise, oleh karena itu harus ditambahkan file agar hasura bisa menjadi enterprise.

Pada bagian Deployment, bisa ditambahkan untuk code seperti dibawah: 

```yaml
- name: HASURA_GRAPHQL_EE_LICENSE_KEY
  valueFrom:
    secretKeyRef:
      key: HASURA_GRAPHQL_EE_LICENSE_KEY
      name: hasura-code-inject
```


Dan juga menambahkan admin key dibagian deployment dan melakukan inject key menggunakan key dibawah pada bagian services

```yaml
- name: HASURA_GRAPHQL_ADMIN_SECRET
  valueFrom:
    secretKeyRef:
      key: admin-secret
      name: hasura-secret
```

Untuk key inject yang digunakan pada bagian services adalah sebagai berikut :

```yaml
eyJhbGciOiJSUzI1NiIsImtpZCI6IjEiLCJ0eXAiOiJKV1QifQ.eyJpc3MiOiJIYXN1cmEiLCJzdWIiOiJpbmRyYUBhbGxkYXRhaW50LmNvbSIsImV4cCI6MTc0MzQ2NTYwMCwiaWF0IjoxNzExOTk3Mzg5LCJqdGkiOiIwNjdmNzJlNC1hOGIwLTQwZWQtOTE3Zi1jYzQ2NzVhNWYwOGIiLCJsaWNlbnNlX2V4cF9hdCI6MTc0MzQ2NTYwMCwiZ3JhY2VfZXhwX2F0IjoxNzQzNDY1NjAwLCJsaWNlbnNlX3R5cGUiOiJ0cmlhbCJ9.JYICPbZKpFrcpjMhN_2I-SPDUPRI39riScUq1GfBWWOuTPrDyx-2nw18drTH-vgxjbekrFGDf0BqywZT66f2ucq3um57e_1BTDAgTQs6uZ-Z6cAjs0AQmd7iuCQzworealzuNuxreh1vR_QJljupZZmdpn4Gw6vmIhh6nYzTgC-QMsxlnBpxLXkBywWLKaMGIuKBIV0QDFIvc8NCjWeM5Aff8NB6cj4Q8uXEhq4mcBLblBihUuIaVXB8kTYQmHlQjx7jxzTLWa1tc1fsofKqZgvJlLHFgRi_ErHkM3KLsGE61Ntw9j8IaKhLOXengSuLn47DXjuXxmqmqIvRFpS_XPUG3pOQ-Cw86UrQ4KBGvt5EOlg842rfvVFjpT1uZ3njXzXn7CsY0AwT77LnWrCjeLyldtl-wPyDf1wChGDAHYscqgmeqx4FqbbrEjhdbBrRN84B9-cJ0eIHtiGp6_ayyl2aF3jQbVzwbd6FJci8Y9e1UH776mOoJqFfTLLx5fPu
```
