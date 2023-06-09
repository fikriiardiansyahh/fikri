# ☁️ASAH: Cloud Computing
## 📑About Our Project

## 🖥️Related Project Repositories

Here are some of the related repositories which are part of the same project:

| Repository | Link |
| --- | --- |
| 📱 Mobile Development | [MD Repository](https://github.com/ASAH-Bangkit-2023/MD.git) |
| 🤖 Machine Learning | [ML Repository](https://github.com/ASAH-Bangkit-2023/ML) |

# 📋Deployment Steps

## 1. Cloud SQL 💾
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/6010b58c-e52f-4133-81fb-aca8c21fae08" width="500px">
</p>

- Sudah mengisi bagian instance ID dan password setelah itu, scroll kebawah to create instance

<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/4ab97880-be57-4c62-b293-04513834fb51" width="500px">
</p>

- Mengubah network menjadi public agar dapat di akses oleh client

<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/669ed3c4-939d-4504-9adc-e31f3f7ccdf1" width="500px">
</p>

- Jika sudah lakukan save

## 2. Cloud Storage 🛒
- Klik create Bucket
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/6cdf462d-6053-4243-9dfe-9759d6a45d7a" width="500px">
</p>

- Sesudah klik create isi pada bagian name bucket sesuai dengan yang dibutuhkan
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/1fcdba61-5040-4d11-ab48-55ba0502e9b0" width="500px">
</p>

- Pada bagian “Choose how to control access to object” unchecklist pada bagian “enforce public access prevention on this bucket”.
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/63a5e42f-3594-4aca-b818-8e4eef748e5e" width="500px">
</p>

- Setelah itu klik continue dan klik create.
- Setelah terbuat bucket, klik permissions karena masih dalam “not public”
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/cbae7f2a-9619-4b6a-898b-71715845d1b9" width="500px">
</p>

- Selanjutnya scrol to “+ grand access”
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/51acfee8-6610-4b09-99d2-471de912f4cc" width="500px">
</p>
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/162a15fc-3d99-4d9c-8ab4-7f593450d5f8" width="500px">
</p>

- Tambahkan pada new principals yaitu “ allUsers dan allAuthenticatedUsers” dan role sebagai storage viewer.

- Klik save dan selesai.

## 3. Create Maps API Key 🔑
- Search “Google Maps ” pada bagian search di GCP
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/f8b83bf7-0f55-4fc6-a2f4-6fe229243fca" width="500px">
</p>

- Klik pada bagian APIs, scrol hingga ada pada bagian additional APIs 
- Pilih yang di inginkan
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/51e194fd-6ab3-4662-91b5-b90691b4f612" width="500px">
</p>

-  Jika sudah memilih klik, lalu klik enable
-  Lalu pindah pada bagian credentials, lalu pilih Google maps Platform APIs yang ingin dibuat key nya
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/179df1de-eca4-470b-a090-6ec2113dd43b" width="500px">
</p>

-  Jika sudah klik pada bagian “ +CREATE CREDENTIALS”
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/f6ba0599-6f52-4316-a4bc-14250fc88110" width="500px">
</p>

-  Setelah klik “ +CREATE CREDENTIALS”
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/2f6e1d3d-72a7-4f8d-82e5-e9d14a11d280" width="500px">
</p>

-  Pilih API key, lalu memulai creating API key
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/94b7c6f1-e631-4f52-92ff-9b0926fe6a46" width="300px">
</p>

-  Setelah itu muncul API key
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/71427553-5f45-47f5-b19c-4ab4ffd2a672" width="500px">
</p>

## 4. Prepare FastAPI (Using this exist repository) 🔥
- Clone the repository from the existing repo:
  ```bash
  git clone https://github.com/your-repo.git
  ```
## 5. Prepare Dockerfile 📄
- Setting image Dockerfile untuk dideploy.

```dockerfile
FROM python:3.11-slim

ENV PYTHONUNBUFFERED True

ENV APP_HOME /app
WORKDIR $APP_HOME
COPY . ./

ENV PORT 1234
ENV MYSQL_URL "mysql+pymysql://root:PASSWORD@SERVER-IP:PORT/NAME DATABASE"
ENV JWT_SECRET_KEY "SECRET KEY"  
ENV JWT_REFRESH_SECRET_KEY "REFRESH SECRET KEY" 

RUN pip install --no-cache-dir -r requirements.txt

CMD exec uvicorn main:app --host 0.0.0.0 --port ${PORT}
```

## 6. Cloud Run 🏃‍♂️☁️
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/e5e4812a-2159-4ee9-8e36-6cbd2ba0e6f8" width="500px">
</p>

- Klik create service
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/87fe8769-e3b5-4b89-9cff-dfb9d79494ba" width="500px">
</p>

- memilih Continuously deploy new revisions from a source repository untuk membuat CI/CD
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/aa23cea5-3923-4f88-b090-a70583d8c6a1" width="500px">
</p>

- Sambungkan dengan github dan pilih repository yang anda inginkan.
- Selanjutnya pilih Build Configuration dengan Dockerfile.
- Selanjut biarkan semua sesuai dengan default, dan pada bagian authentication pilih “allow unauthenticated invoactions” agar dapat diakses oleh public
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/78dad855-09d1-4a82-b0cd-93b7ea2047d4" width="500px">
</p>

- Jika sudah memilih pada bagian “allow unauthenticated invoactions”, lalu klik create
- Setelah itu website berhasil di deploy.
<p align="center">
  <img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/1c5c729a-7078-42c6-9c4a-700c2c46f9a7" width="500px">
</p>

## 7. Testing the Application 📱📟
To test the deployed application, you can use tools like `curl` or API testing tools like Postman. Here is an example of how to test the API using `curl`:

```bash
curl -X GET https://your-app-url.com/api/endpoint
```

Replace `your-app-url.com` with the actual URL of your deployed application and `/api/endpoint` with the desired endpoint to test.

You can also use Postman to send requests to the API and verify the responses.
