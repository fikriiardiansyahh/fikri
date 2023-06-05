# ASAH: Cloud Computing
## About Our Project

## Related Project Repositories

Here are some of the related repositories which are part of the same project:

| Repository | Link |
| --- | --- |
| 📱 Mobile Development | [MD Repository](https://github.com/ASAH-Bangkit-2023/MD.git) |
| 🤖 Machine Learning | [ML Repository](https://github.com/ASAH-Bangkit-2023/ML) |


# 
Setting image Dockerfile untuk dideploy.
```text
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

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/16f63ae3-093d-4cc8-9df4-4a56d92b9283" width="700px">


Sudah mengisi bagian instance ID dan password setelah itu, scroll kebawah
to create instance

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/a81c2e96-53cd-4df8-8c3e-53ba5da49848" width="300px">

Mengubah network menjadi public agar dapat di akses oleh client

<img width="500" alt="image" src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/fae32be0-3377-4019-8b1a-c0911b7cf535">


Jika sudah lakukan save.


Selanjutnya membuat data base, klik create data base

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/3ea503fa-649a-4b1c-8897-ef0b5f368893" width="500px">

Selanjut mengisi nama untuk data base

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/66f4360f-36b5-4ca8-b274-7fc80bf10a5e" width="500px">

Lalu klik create
 
Membuat table dengan sricpt sql

```text
CREATE TABLE `news` (
  `news_id` int NOT NULL,
  `title` varchar(255) DEFAULT NULL,
  `content` text,
  `author` varchar(100) DEFAULT NULL,
  `date_news` date DEFAULT NULL,
  `thumbnail` varchar(255) DEFAULT NULL,
  `url` varchar(255) DEFAULT NULL
);

CREATE TABLE `point_system` (
  `point_id` int NOT NULL,
  `username` varchar(50) DEFAULT NULL,
  `total_points` int DEFAULT NULL,
  `date_point` date DEFAULT NULL
);

CREATE TABLE `scan_history` (
  `waste_id` int NOT NULL,
  `username` varchar(50) DEFAULT NULL,
  `date_scan` date DEFAULT NULL,
  `recycle_recommendation` varchar(255) DEFAULT NULL,
  `gcs_image_path` varchar(255) DEFAULT NULL,
  `prediction_waste` varchar(255) DEFAULT NULL,
  `action` varchar(255) DEFAULT NULL,
  `accuracy_percentage` varchar(255) DEFAULT NULL,
  `message` varchar(5000) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL
);

CREATE TABLE `user` (
  `username` varchar(50) NOT NULL,
  `full_name` varchar(100) DEFAULT NULL,
  `email` varchar(100) DEFAULT NULL,
  `password` varchar(100) DEFAULT NULL,
  `date_user` date DEFAULT NULL
);

ALTER TABLE `news`
  ADD PRIMARY KEY (`news_id`);

ALTER TABLE `point_system`
  ADD PRIMARY KEY (`point_id`),
  ADD UNIQUE KEY `username` (`username`);
  
ALTER TABLE `scan_history`
  ADD PRIMARY KEY (`waste_id`),
  ADD KEY `username` (`username`);

ALTER TABLE `user`
  ADD PRIMARY KEY (`username`),
  ADD UNIQUE KEY `email` (`email`);

ALTER TABLE `news`
  MODIFY `news_id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=11;

ALTER TABLE `point_system`
  MODIFY `point_id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=6;

ALTER TABLE `scan_history`
  MODIFY `waste_id` int NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=45;

ALTER TABLE `point_system`
  ADD CONSTRAINT `fk_point_system_user` FOREIGN KEY (`username`) REFERENCES `user` (`username`),
  ADD CONSTRAINT `point_system_ibfk_1` FOREIGN KEY (`username`) REFERENCES `user` (`username`);

ALTER TABLE `scan_history`
  ADD CONSTRAINT `scan_history_ibfk_1` FOREIGN KEY (`username`) REFERENCES `user` (`username`);
```
 
Membuat table dengan sricpt sql

Sesudah membuat tabel dan berhasil, selanjutnya pindah pada cloud run

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/9d4e4903-f9d0-4783-9558-ca832a8708ee"  width="500px">

Klik create service

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/da236cde-1536-4f12-825a-72ed64d538b0"  width="500px">

memilih Continuously deploy new revisions from a source repository untuk membuat CI/CD

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/7bb3a6c4-bf49-45d4-a17b-9f1acf14232f"  width="500px">

Sambungkan dengan github dan pilih repository yang anda inginkan.

Selanjutnya pilih Build Configuration dengan Dockerfile.

Selanjut biarkan semua sesuai dengan default, dan pada bagian authentication pilih “allow unauthenticated invoactions” agar dapat diakses oleh public.

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/abc06721-16c6-45d2-91af-7920c1f065b8"  width="500px">

Jika sudah memilih pada bagian “allow unauthenticated invoactions”, lalu klik create
Setelah itu website berhasil di deploy.

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/96ebd29f-b3d1-4503-a9c3-c6442c8ac7a0"  width="500px">

Membuat bucket

Klik create 

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/e7d1c010-90db-4c44-97ff-37d5aa9fd2e9"  width="500px">

Sesudah klik create isi pada bagian name bucket sesuai dengan yang dibutuhkan

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/ee521dad-bb75-42b4-b0fc-5e7cc434a294"  width="350px">

Pada bagian “Choose how to control access to object” unchecklist pada bagian “enforce public access prevention on this bucket”.

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/0dea0450-de31-419d-816a-d4335524de81"  width="350px">

Setelah itu klik continue dan klik create.

Setelah terbuat bucket, klik permissions karena masih dalam “not public”

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/1f028a37-a731-4540-8564-eb2b8e16ba1e"  width="700px">


Selanjutnya scrol to “+ grand access”

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/265bc86c-4258-4444-b777-dc6d6ce8b707"  width="500px">




<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/7b84e843-6785-4672-bb09-5e57723d8bb6"  width="500px">

Tambahkan pada new principals yaitu “ allUsers dan allAuthenticatedUsers” dan role sebagai storage viewer.

Klik save dan selesai.

Pindah pada IAM & ADMIN.

Buat pada service account.

Pada bagian “Grant this service account access to project” tambahkan role yaitu “storage admin”.

Jika sudah klik done .

Klik create service account untuk mendapatkan key access untuk google cloud storage .

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/3929c46f-47d9-4f88-9362-701e32e3d8a8"  width="450px">


Klik add key 

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/1f181ed4-d046-46cd-b1e0-1b690125f7c9"  width="200px">


Klik create new key

<img src="https://github.com/fikriiardiansyahh/fikri/assets/72667607/e10f3b41-1a56-471b-a28a-25fb9bb9387d"  width="450px">

Pilih JSON dan klik create
Hasil dari JSON tersebut, ubah dan sesuaikan dengan JSON key yang didapat pada service account.
```text
{
  "type": "service_account",
  "project_id": "Project ID",
  "private_key_id": "Private key",
  "private_key": "----BEGIN PRIVATE KEY-----\"private key"==\n-----END PRIVATE KEY-----\n",
  "client_email": "Serviceaccountname@projectID",
  "client_id": "Client ID",
  "auth_uri": "https://accounts.google.com/o/oauth2/auth",
  "token_uri": "https://oauth2.googleapis.com/token",
  "auth_provider_x509_cert_url": "https://www.googleapis.com/oauth2/v1/certs",
  "client_x509_cert_url": "https://www.googleapis.com/robot/v1/metadata/x509/asah-baru%40vibrant-catbird-385607.iam.gserviceaccount.com",
  "universe_domain": "googleapis.com"
}
```
