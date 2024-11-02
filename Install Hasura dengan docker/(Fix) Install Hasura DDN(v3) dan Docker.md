# 📜 Getting Started
## 1. Download Hasura DDN
Install terlebih dahulu Hasura DDN CLI, Berikut link unduh: 
🚴[Download](https://graphql-engine-cdn.hasura.io/ddn/cli/v4/latest/DDN_CLI_Setup.exe)

## 2. Download Docker Desktop
lalu install Docker dengan versi terbaru, Berikut link unduh:🚴[Download](https://docs.docker.com/engine/install)

Aplikasi docker harus keadaan open, jika sudah diinstall maka bisa dilihat lokasi DDN CLI dan kriteria Docker
- Input: 
```bash
ddn doctor 
```
- Output: 
![image](https://github.com/user-attachments/assets/dacbb8ed-6a46-483d-b855-ef2ab8737df8)

### Masuk ke file DDN CLI
```
cd C:\Users\USER\AppData\Local\Programs\DDN_CLI
```
![image](https://github.com/user-attachments/assets/41ee56f7-0301-4810-b8ef-25bd5b67637b)

### Masuk/Login melalui CLI
Perintah di bawah ini akan mengautentikasi sesi CLI dan memberi akses ke sumber daya Hasura Cloud.
```
 ddn auth login
 ```
![image](https://github.com/user-attachments/assets/4e0646e1-4cba-42e8-a50e-a4910a1f10a8)

### Membuat nama file directory
- Input:
```
 mkdir hasura_ddn_cli
 ```
- Output: ![image](https://github.com/user-attachments/assets/7d00b80d-d8e2-4c4b-a051-1bc7cf6aa160)
### Masuk ke file directory
- Input:
```
 cd hasura_ddn_cli
 ```
#### lalu 
Perintah ini {ddn supergraph init} menginisialisasi supergraf yang merupakan API gabungan — dengan menyiapkan semua file dan direktori yang diperlukan untuk pengembangan di mysupergraphdirektori baru.
- Input:
```
ddn supergraph init .
 ```
- Output ![image](https://github.com/user-attachments/assets/c0df23b8-3db7-4c28-bd9b-11b661eaad86)
- Output !![image](https://github.com/user-attachments/assets/f306cd79-fe02-43c6-b6af-b71a0e15366d)


![image](https://github.com/user-attachments/assets/9a8ebbe4-1e6a-4dde-8726-8cb0aba3bbbd)
![image](https://github.com/user-attachments/assets/64a3463b-ff6b-4950-9512-a9aa09d6be8b)



![image](https://github.com/user-attachments/assets/bc35f141-2470-41a7-bc6c-e6f5b8ff6e1c)

![image](https://github.com/user-attachments/assets/51fc5504-9d38-4579-9397-17e72e63328e)

![image](https://github.com/user-attachments/assets/e8f8bf85-ff28-4dbb-ac7a-5c866894d0f7)

![image](https://github.com/user-attachments/assets/3c607999-22de-4d71-92c1-56dcd7a91345)


Build Version | e92cf66dce 
API URL       | https://viable-fawn-2440-e92cf66dce.ddn.hasura.app/graphql 
Console URL   | https://console.hasura.io/project/viable-fawn-2440/build/e92cf66dce 
Project Name  | viable-fawn-2440                                                    

![image](https://github.com/user-attachments/assets/fef4e30b-aa23-429b-afd6-0378852f3cd7)

