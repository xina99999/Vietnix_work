

## 🔐 SSL

### 🔸 SSL là gì?

**SSL** (Secure Sockets Layer) là một tiêu chuẩn công nghệ bảo mật, giúp mã hóa thông tin trong quá trình truyền tải giữa trình duyệt và máy chủ web. Mục tiêu chính là đảm bảo rằng:

- Dữ liệu truyền đi luôn **toàn vẹn**.
- Thông tin được giữ **riêng tư**.
- Mọi giao tiếp đều **bảo mật**.

📌 SSL lần đầu được phát triển bởi Netscape vào năm 1995, là tiền thân của giao thức **TLS** (Transport Layer Security) hiện đại.  
SSL cung cấp:

- **Mã hóa** dữ liệu: Giúp người ngoài không thể đọc được thông tin.
- **Xác thực**: Đảm bảo danh tính máy chủ.
- **Tính toàn vẹn dữ liệu**: Dữ liệu không bị thay đổi trong quá trình truyền.

### 🔸 Các loại chứng chỉ SSL

#### ✅ 1. **DV SSL (Domain Validation)**

- Xác thực quyền sở hữu tên miền.
- Mức mã hóa cơ bản.
- Phù hợp cho **website cá nhân**.
- **Chi phí rẻ**, cài đặt **nhanh**.

#### ✅ 2. **OV SSL (Organization Validation)**

- Xác thực tên miền + doanh nghiệp đăng ký.
- Hiển thị tên công ty trong chứng chỉ.
- Dành cho **doanh nghiệp** muốn tăng độ tin cậy.

#### ✅ 3. **EV SSL (Extended Validation)**

- Cấp độ xác thực **cao nhất**.
- Trình duyệt hiển thị **thanh địa chỉ màu xanh** + tên doanh nghiệp.
- Rất phù hợp với **tổ chức tài chính**, ngân hàng, thương mại điện tử.

#### ✅ 4. **Wildcard SSL**

- Bảo vệ **nhiều subdomain** chỉ với một chứng chỉ.
- Không giới hạn số lượng subdomain.
- Phù hợp với các tổ chức có nhiều dịch vụ dưới cùng một miền chính.

#### ✅ 5. **SANs SSL (Subject Alternative Names)**

- Cho phép một chứng chỉ SSL bảo vệ **nhiều tên miền hoặc subdomain** khác nhau.
- Phù hợp với **Microsoft Exchange, Office Communication Server, Lync**...
- Giúp **tiết kiệm chi phí và dễ quản lý** hơn Wildcard SSL.
- Hỗ trợ nhiều cấp độ như: **DV, OV, EV**.

---

### 📄 CSR là gì? Dùng để làm gì trong SSL?

**CSR (Certificate Signing Request)** là một đoạn văn bản mã hóa, chứa các thông tin định danh của tổ chức/doanh nghiệp, bao gồm:

- Tên miền
- Quốc gia
- Tên công ty
- Địa chỉ email liên hệ kỹ thuật

🌐 CSR được gửi đến nhà cung cấp SSL để họ cấp phát chứng chỉ chính thức. Nó là bước đầu tiên trong quá trình đăng ký SSL.

### Sử dụng OpenSSL để gen file CSR sau đó request SSL cho domain tech.training.vietnix.tech
## 🌐 **Quy trình tạo CSR và Private Key bằng OpenSSL**

## 📦 Bước 1: Kiểm tra phiên bản OpenSSL
```bash
openssl version
```

## 📁 Bước 2: Tạo thư mục lưu trữ
```bash
mkdir vietnix.trainning
cd vietnix.trainning/
```

## 🔐 Bước 3: Tạo **Private Key**
```bash
openssl genrsa -out tech.training.vietnix.tech.key 2048
```

## 📝 Bước 4: Tạo **CSR (Certificate Signing Request)**
```bash
openssl req -new -key tech.training.vietnix.tech.key -out tech.training.vietnix.tech.csr
```

---

## 📂 **Kết quả** trong thư mục `vietnix.trainning/`:

| Tên tập tin                             | Mô tả                          |
|----------------------------------------|--------------------------------|
| `tech.training.vietnix.tech.key`       | Private Key                    |
| `tech.training.vietnix.tech.csr`       | Certificate Signing Request    |

---

## Nội dung file tech.training.vietnix.tech.csr

-----BEGIN CERTIFICATE REQUEST-----

MIIDQjCCAioCAQAwgc8xCzAJBgNVBAYTAlZOMRQwEgYDVQQIDAtIbyBDaGkgTWlu
aDEUMBIGA1UEBwwLSG8gQ2hpIE1pbmgxOTA3BgNVBAoMMFZpZXRuaXggU29sdXQg
YW5kIHRlY2hub2xvZ3kgam9pbnQgc3RhY2sgY29tcGFueTELMAkGA1UECwwCSVQx
IzAhBgNVBAMMGnRlY2gudHJhaW5pbmcudmlldG5peC50ZWNoMScwJQYJKoZIhvcN
AQkBFhh0ZWNoLnRlYW1AdmlldG5peC5jb20udm4wggEiMA0GCSqGSIb3DQEBAQUA
A4IBDwAwggEKAoIBAQCo6IpXtSHFZRqHbqN1FMgKlew89xzh+lCusg5OROQ/YEhh
OAO0DHHD9tA2v1ZSA3A6jNBUPSGHCeLX4PA6S607o6YIdk1/nE8TX5WdjQqh0bOz
pNGPiEQum3obFB2jdty5+qiacQrvMLOHCHJrY+24q7igRrw89sXvbXIcHeYp/ULH
/FNvjreDRAdvo5nJwgK/wLNXHdKyLY9/r1Z73R9Ijhd/o66b6Tc8D5nuGMnVQ7M+
KpTlE8oeRE4BE4CX/lkUn6jEiqEfSoEbRT8EGSV6yRjAHicnfZu3feH+F0I+1Qn1
dT+Cq/kG3Jr0o64tBk5QdgzgzOPkzWklFb62z807AgMBAAGgLTATBgkqhkiG9w0B
CQcxBgwEMTIzNDAWBgkqhkiG9w0BCQIxCQwHVmlldG5peDANBgkqhkiG9w0BAQsF
AAOCAQEATYRDDiNdne+cM28Kn0QpEZXGZdj0LLLcMJMoPBCp57rCxcTPOh+qXlg/
OYUFdYC5b/r1gCVGgTM0to3TGHHRw3wY5pp5rz+ry46ZpkACD7DJdo0K26C3JxxA
s1OjTsmlYVIHmmVTiBTsLafKKoxKFnCjgtUF3Ud3nnkvTvetGYvl26A2fY9BYdyA
vuJF25K4Kn0AeVj/LC7Z18RlXD/NUQXI7CIwVMXbwGAw9YaSIEfM7b33xot/DONE
6maNNLmFCigq03+iKvKa0yeDEYOQ8Ei0hELoNAD87sqHP274i3/vq1dDfQVEZ07C
iywIg1KJs4m0vehXg+W+Db5xe+pREQ==

-----END CERTIFICATE REQUEST-----

## Nội dung file tech.training.vietnix.tech.key

-----BEGIN PRIVATE KEY-----

MIIEvgIBADANBgkqhkiG9w0BAQEFAASCBKgwggSkAgEAAoIBAQCo6IpXtSHFZRqH
bqN1FMgKlew89xzh+lCusg5OROQ/YEhhOAO0DHHD9tA2v1ZSA3A6jNBUPSGHCeLX
4PA6S607o6YIdk1/nE8TX5WdjQqh0bOzpNGPiEQum3obFB2jdty5+qiacQrvMLOH
CHJrY+24q7igRrw89sXvbXIcHeYp/ULH/FNvjreDRAdvo5nJwgK/wLNXHdKyLY9/
r1Z73R9Ijhd/o66b6Tc8D5nuGMnVQ7M+KpTlE8oeRE4BE4CX/lkUn6jEiqEfSoEb
RT8EGSV6yRjAHicnfZu3feH+F0I+1Qn1dT+Cq/kG3Jr0o64tBk5QdgzgzOPkzWkl
Fb62z807AgMBAAECggEAB1K3BFRaeWwOzOR/DE0RTMgxIFtQ1heNlrucGJ3ZPtgt
UIMRQglMwLyQoeGveFgImOPtP6/0Xx4Ojf6FP11XXK35Lz7ZX25jabsdkP4QSRxU
PdK2XFlzmDO1WmX5ezYBHf0ZD0JypL9koTa8fB1ZLVRZhecwiKdy/c1mrWbXHrwU
AxeI3HfdPKqEG2LhCV+aUJYQEH+9IPEXgizSaqdDokMr2DptZomxwq/bNrkqn/+/
kuqliKmefxwgLq1yCBeD4femPtbpQw6XuVZYaUVsGEF1W+j/6bckOxOPgVbtVLbM
Y7pBsLuwAyvVMeRYCNv4pKU+XuYUmZifnvPTpFGGNQKBgQDeox3P+0w+AgpBnfWF
HTLXrDGLulLaAT6e0yHU2+AHQVdVp4HBq8N7NA+UC6wuRSyLCWsHU13WuqdAMtq7
xCgehD/ib/bLts1PKCnDwmICVgm0r66KDab+iOPBTSkrftnIknSIVwPKVire6jJ/
ZLpH+ek3rFBe1YFc8nD03gRKXQKBgQDCOELFOXsydKtexGRZNwfLwILRY6jA0eOP
+JwWuOtNzG2kO0O4Yn8nWOLviIYA6/2WiOOH9yA8T9TMKanZ/KLuUtmi8Dh3YpDV
/0YwotRmmZkt8/FvHf92dLDuCmwZUKKdqdxalP244FlyXc2dF7Y1ZzQFXnNs0+xU
jcBUXhpsdwKBgDmcnjdWwSj+oCbQuFsE8kYvMfcFdTEix1CUNBn/994Iw4/Ps90p
FIHKPAnEZ37luZwVCNQxd4P8cxFC16VlIjibYmi3LncSy9gi/YPBxljyaLqQB6uD
0uXlCILZ88Bkp/imJW+ujLWMTLW4hu6+YxIDEp2sgnO37izeM+q5lQSlAoGBAKyd
okJ1txf9931voRxlu4kMnXgKUialpNIFjHzpd0CbC2tmvOZ4rDhFWNS5ixfwpl6P
ZWIncsAH18Jo2SwDzK9ydTnKtPTuZnm7ux9o6MwTgcAEyrUOfUlDpyi5nJ/XOeBU
4qKjPul8hCMQWblgJLJL+kE3U/EKXUY9Ag454NQ7AoGBAJAP1fF9KrHWCAI37o78
ICJRIjRJ5s57lAR/a5trlTPgFxlMfDj3RnWfnJOs0grrouF99H+xejqA+GCPdOBI
yF5KJL7oN9Xbl6uRKJRm6EZxujuRcEyDwqPgi1AxM4gKbjA5zXT5WCavEhLOKDLF
22zGAJPNOKBC2+zw7YhK/Ryx

-----END PRIVATE KEY-----

# Pem file là gì ?
Tệp PEM (Privacy Enhanced Mail) là một định dạng lưu trữ dữ liệu mật mã như chứng chỉ SSL/TLS, khóa riêng, khóa công khai hoặc chứng chỉ của cơ quan cấp chứng chỉ (CA). Tệp PEM thường được sử dụng trong SSL/TLS, máy chủ web, OpenSSL và cả trong SSH để bảo mật thông tin liên lạc. Các phần mở rộng phổ biến bao gồm .pem, .crt, .cer và .key và được mã hóa Base64.

# Private key ssl là gì ?
Là file mã hoá được sinh ra cùng lúc khi tạo CSR. Để đơn giản, hãy hình dung CRT là phần mã hoá công khai được trình duyệt sử dụng để truy cập đến website của bạn. Vậy khi dữ liệu đến được website sẽ cần chìa khoá để mở khoá thông tin được mã hoá ở CRT.

# PFX file là gì ? Cách chuyển từ file crt file sang PFX file.
File PFX (Personal Exchange Format), còn được gọi là PKCS #12, là một định dạng tệp chứa các chứng chỉ bảo mật và các khóa mã hóa liên quan.

Đây là một tệp tin nhị phân được sử dụng để lưu trữ cả chứng chỉ công khai (public certificate) và khóa riêng (private key) trong một tệp duy nhất, thường được bảo vệ bằng mật khẩu để đảm bảo an toàn.

### cách chuyển từ file crt file sang PFX file
# Hướng dẫn chuyển file `.crt` sang `.pfx`

Để chuyển từ file `.crt` sang file `.pfx`, bạn cần các thành phần sau:

## 🧾 Yêu cầu
- File chứng chỉ: `.crt` (certificate)
- File khóa riêng: `.key` (private key)
- (Tuỳ chọn) Chuỗi chứng chỉ trung gian: `.ca-bundle` hoặc `.crt` của intermediate CA

---

## 🔧 Câu lệnh OpenSSL

```bash
openssl pkcs12 -export \
  -out tenfile.pfx \
  -inkey tenfile.key \
  -in tenfile.crt \
  -certfile ca-bundle.crt

~                                    

