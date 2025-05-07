Dalam Kubernetes, **Ingress**, **LoadBalancer**, dan **Service Account** adalah komponen penting yang masing-masing punya fungsi berbeda. Berikut penjelasan singkat dan jelas untuk ketiganya:

---

### 1. **Ingress**

**Ingress** adalah objek Kubernetes yang mengatur **akses HTTP dan HTTPS** dari luar ke dalam klaster (biasanya ke pod).
Fungsinya seperti **gateway atau router web**.

* Digunakan untuk mengatur **routing berdasarkan domain atau path** (misalnya `/api`, `/admin`, dll).
* Dapat mengatur **TLS/SSL (HTTPS)**.
* Biasanya digunakan bersama **Ingress Controller** (seperti NGINX, Traefik, dll).

**Contoh Ingress:**

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
spec:
  rules:
    - host: myapp.example.com
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: myapp-service
                port:
                  number: 80
```

---

### 2. **LoadBalancer**

**LoadBalancer** adalah tipe dari **Service** di Kubernetes yang membuat aplikasi dapat diakses dari luar klaster **melalui IP publik**.

* Biasanya digunakan pada cloud provider (AWS, GCP, Azure).
* Secara otomatis membuat **external load balancer** yang mengarah ke pod-pod di dalam klaster.
* Alternatif sederhana dari Ingress jika hanya butuh satu service yang diekspose.

**Contoh Service LoadBalancer:**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  type: LoadBalancer
  selector:
    app: myapp
  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080
```

---

### 3. **Service Account**

**Service Account** adalah identitas untuk pod (aplikasi) agar bisa **mengakses API Kubernetes** secara aman.

* Biasanya digunakan oleh aplikasi yang perlu **berinteraksi dengan cluster**, misalnya untuk autoscaling, monitoring, atau konfigurasi dinamis.
* Setiap pod menggunakan satu service account.
* Bisa dikombinasikan dengan **RBAC (Role-Based Access Control)** untuk membatasi hak akses.

**Contoh Service Account:**

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: myapp-sa
```

**Lalu digunakan di pod:**

```yaml
spec:
  serviceAccountName: myapp-sa
```

---

### Kesimpulan Sederhana:

| Komponen            | Fungsi Utama                                          |
| ------------------- | ----------------------------------------------------- |
| **Ingress**         | Atur trafik HTTP(S) dari luar ke dalam klaster.       |
| **LoadBalancer**    | Buka akses IP publik langsung ke Service (via cloud). |
| **Service Account** | Identitas pod untuk akses ke API Kubernetes.          |

---

