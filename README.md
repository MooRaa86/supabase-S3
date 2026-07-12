# Supabase S3 File Upload

A simple Spring Boot project that demonstrates how to upload files to Supabase Storage using the AWS S3 SDK.

## Tech Stack

- Java 21
- Spring Boot 4.1.0
- AWS SDK for Java v2 (S3)

---

## Environment Variables

You need to set 5 environment variables, either in a `.env` file or as system environment variables:

| Variable | Description |
|---|---|
| `SUPABASE_URL` | Your Supabase project URL |
| `SUPABASE_S3_ENDPOINT` | S3-compatible endpoint for Supabase Storage |
| `SUPABASE_S3_REGION` | Your project's region |
| `SUPABASE_S3_ACCESS_KEY` | Access Key ID |
| `SUPABASE_S3_SECRET_KEY` | Secret Access Key |

---

## How to Get These Values from Supabase

### `SUPABASE_URL`
- Go to [supabase.com](https://supabase.com) → open your project
- Click **Project Overview** → **Connect** → **Session pooler**
- Copy the value next to `SUPABASE_URL`

### `SUPABASE_S3_ENDPOINT` and `SUPABASE_S3_REGION`
- Go to **Project Settings** → **Storage** → **S3 Configuration**
- You'll find both the **Endpoint** and the **Region** there

### `SUPABASE_S3_ACCESS_KEY` and `SUPABASE_S3_SECRET_KEY`
- Go to **Project Settings** → **Storage** → **S3 Connection**
- You'll find the **Access Key ID** and **Secret Access Key** there

---

## Run the Project

### 1. Clone the repo
```bash
git clone <repo-url>
cd supabaseS3
```

### 2. Set the environment variables

Either in your terminal:
```bash
set SUPABASE_URL=https://<project-ref>.supabase.co
set SUPABASE_S3_ENDPOINT=https://<project-ref>.supabase.co/storage/v1/s3
set SUPABASE_S3_REGION=<your-region>
set SUPABASE_S3_ACCESS_KEY=<your-access-key>
set SUPABASE_S3_SECRET_KEY=<your-secret-key>
```

Or create a `.env` file in the project root:
```env
SUPABASE_URL=https://<project-ref>.supabase.co
SUPABASE_S3_ENDPOINT=https://<project-ref>.supabase.co/storage/v1/s3
SUPABASE_S3_REGION=<your-region>
SUPABASE_S3_ACCESS_KEY=<your-access-key>
SUPABASE_S3_SECRET_KEY=<your-secret-key>
```

### 3. Run the project
```bash
./mvnw spring-boot:run
```

---

## Testing the Endpoint

Once the app is running, you can test the upload endpoint using **curl** or **Postman**.

### curl
```bash
curl -X POST http://localhost:8080/api/storage/upload \
  -F "file=@/path/to/your/file.jpg"
```

### Postman
1. Set method to **POST** and URL to `http://localhost:8080/api/storage/upload`
2. Go to **Body** → select **form-data**
3. Add a key named `file`, change its type to **File**, then select your file
4. Hit **Send**

A successful upload returns the public URL of the uploaded file.
