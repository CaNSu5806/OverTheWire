# Bandit Level 16 → Level 17

## 🇬🇧 English

### Goal

Retrieve the credentials for **Bandit Level 17** by finding the correct service running on **localhost** within the port range **31000–32000**.

The correct server must:

- Be listening on one of the ports in the given range.
- Communicate using **SSL/TLS**.
- Return the credentials for the next level instead of simply echoing the submitted password.

---

### Challenge Hint

The challenge states that multiple services are listening on ports between `31000` and `32000`.

To retrieve the next credentials, the following steps are required:

1. Scan the given port range to identify listening services.
2. Determine which of the open ports use **SSL/TLS**.
3. Connect to the SSL/TLS services and submit the current **Bandit16 password**.
4. Identify the server that returns the next credentials instead of echoing the input.
5. Save the returned **SSH private key**.
6. Use the private key to log in as **Bandit17**.

---

### Port Scanning and Service Detection

First, I scanned the specified port range using `nmap`.

I also used the `-sV` option to detect the services running on the open ports.

```bash
nmap -p 31000-32000 -sV localhost
```

The scan revealed which ports were open and provided information about the services running on them.

The important part was identifying which services supported **SSL/TLS**, since the challenge specifically states that only one of the SSL/TLS-enabled servers returns the correct credentials.

---

### Connecting to the SSL/TLS Service

After identifying the SSL/TLS-enabled ports, I connected to the appropriate service using `openssl s_client`.

```bash
openssl s_client -connect localhost:31790 -quiet
```

Here:

- `openssl` provides cryptographic and SSL/TLS-related tools.
- `s_client` acts as an SSL/TLS client and allows us to connect to encrypted services.
- `-connect localhost:31790` specifies the target host and port.
- `-quiet` reduces unnecessary connection output.

After the connection was established, I submitted the current **Bandit16 password** and pressed **Enter**.

Instead of echoing the password back, the correct server returned an **RSA Private Key**.

```text
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAz...
...
-----END RSA PRIVATE KEY-----
```

This private key is the credential required to authenticate as **Bandit17**.

---

### Saving the Private Key

The returned private key needs to be stored in a file before it can be used with SSH.

I created a temporary working directory:

```bash
mkdir -p /tmp/bandit17_key
cd /tmp/bandit17_key
```

Then I created a file for the private key:

```bash
nano key.private
```

I pasted the **entire private key**, including the beginning and ending lines:

```text
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```

Then I saved the file.

---

### Setting the Private Key Permissions

SSH requires private key files to have strict permissions.

I changed the permissions using:

```bash
chmod 600 key.private
```

The permission `600` means:

```text
-rw-------
```

This gives:

- **Owner:** Read + Write
- **Group:** No permissions
- **Others:** No permissions

SSH rejects private keys that are accessible by other users because private keys are supposed to remain secret.

---

### Logging into Bandit Level 17

After saving the key and configuring its permissions, I used it as the SSH identity file.

From inside the Bandit server:

```bash
ssh -i key.private bandit17@localhost -p 2220
```

Alternatively, if the key is stored on a local machine such as Kali Linux:

```bash
ssh -i key.private bandit17@bandit.labs.overthewire.org -p 2220
```

The `-i` option tells SSH which private key should be used for authentication.

---

### Understanding the Commands

#### Nmap Port and Service Scan

```bash
nmap -p 31000-32000 -sV localhost
```

- **`nmap`** → Network exploration and port scanning tool.
- **`-p 31000-32000`** → Specifies the exact port range to scan.
- **`-sV`** → Attempts to identify the services and their versions running on open ports.
- **`localhost`** → Refers to the local machine, usually `127.0.0.1`.

---

#### OpenSSL Connection

```bash
openssl s_client -connect localhost:31790 -quiet
```

- **`openssl`** → Toolkit for SSL/TLS and cryptographic operations.
- **`s_client`** → Creates an SSL/TLS client connection.
- **`-connect`** → Specifies the destination server and port.
- **`localhost:31790`** → Connects to port `31790` on the local machine.
- **`-quiet`** → Reduces unnecessary connection information.

---

#### Private Key Permissions

```bash
chmod 600 key.private
```

- **`chmod`** → Changes file permissions.
- **`600`** → Gives read and write permissions only to the file owner.
- **`key.private`** → The SSH private key file.

---

#### SSH with a Private Key

```bash
ssh -i key.private bandit17@localhost -p 2220
```

- **`ssh`** → Secure Shell client.
- **`-i key.private`** → Specifies the private key used for authentication.
- **`bandit17@localhost`** → Connects as the `bandit17` user.
- **`-p 2220`** → Specifies OverTheWire's SSH port.

---

### Commands Used

| **Command** | **Description** |
|---|---|
| `nmap -p 31000-32000 -sV localhost` | Scans the specified port range and identifies running services. |
| `openssl s_client` | Connects to an SSL/TLS-enabled service. |
| `mkdir` | Creates a temporary directory for storing the key. |
| `nano` | Creates and edits the private key file. |
| `chmod 600` | Restricts private key permissions to the owner. |
| `ssh -i` | Authenticates to SSH using a private key. |

---

### What I Learned

- How to scan a specific port range using `nmap`.
- How to perform service detection with `nmap -sV`.
- How to identify services using **SSL/TLS**.
- How to connect to an SSL/TLS service using `openssl s_client`.
- How SSH private key authentication works.
- Why SSH private keys require strict file permissions.
- How the `-i` option is used to specify an SSH identity file.

---

# 🇹🇷 Türkçe

## Amaç

**localhost** üzerindeki **31000–32000** port aralığını tarayarak doğru servisi bulmak ve **Bandit Level 17** için gerekli kimlik bilgilerini elde etmek.

Doğru sunucunun:

- Verilen port aralığında dinliyor olması,
- **SSL/TLS** kullanması,
- Gönderilen parolayı yalnızca geri döndürmek (echo) yerine bir sonraki seviyenin kimlik bilgilerini vermesi

gerekmektedir.

Bu seviyede elde edilen kimlik bilgisi normal bir parola değil, **SSH Private Key**'dir.

---

## Verilen İpucu

Challenge açıklamasına göre `31000-32000` port aralığında birden fazla servis çalışmaktadır.

İzlenmesi gereken temel adımlar:

1. Verilen port aralığını tarayarak açık portları tespit etmek.
2. Açık portlardan hangilerinin **SSL/TLS** kullandığını belirlemek.
3. SSL/TLS kullanan servislere bağlanarak mevcut **Bandit16 şifresini** göndermek.
4. Gönderilen veriyi yalnızca geri döndüren (echo) servisleri elemek.
5. Kimlik bilgilerini döndüren doğru servisi bulmak.
6. Elde edilen **SSH Private Key**'i kaydetmek.
7. Private Key kullanarak **Bandit17** hesabına bağlanmak.

---

## Port Taraması ve Servis Tespiti

İlk olarak belirtilen port aralığını `nmap` ile taradım.

Aynı zamanda açık portlarda çalışan servisleri belirlemek için `-sV` parametresini kullandım:

```bash
nmap -p 31000-32000 -sV localhost
```

Bu tarama sonucunda hangi portların açık olduğu ve bu portlarda hangi servislerin çalıştığı hakkında bilgi elde ettim.

Challenge açısından özellikle **SSL/TLS kullanan servisleri** tespit etmek önemliydi.

---

## SSL/TLS Servisine Bağlanma

SSL/TLS kullanan portları belirledikten sonra ilgili servise `openssl s_client` kullanarak bağlandım:

```bash
openssl s_client -connect localhost:31790 -quiet
```

Burada:

- `openssl` → SSL/TLS ve kriptografik işlemler için kullanılan araçtır.
- `s_client` → SSL/TLS destekleyen bir servise istemci olarak bağlanmayı sağlar.
- `-connect localhost:31790` → Bağlanılacak adresi ve portu belirtir.
- `-quiet` → Gereksiz bağlantı çıktılarını azaltır.

Bağlantı kurulduktan sonra mevcut **Bandit16 şifresini** yapıştırıp **Enter** tuşuna bastım.

Doğru sunucu, gönderdiğim parolayı echo etmek yerine bir **RSA Private Key** döndürdü:

```text
-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAz...
...
-----END RSA PRIVATE KEY-----
```

Bu anahtar, **Bandit17** kullanıcısına bağlanmak için kullanılacak SSH kimlik bilgisidir.

---

## Private Key'i Kaydetme

SSH bağlantısında kullanabilmek için elde ettiğim Private Key'i bir dosyaya kaydetmem gerekiyordu.

Öncelikle `/tmp` altında geçici bir çalışma klasörü oluşturdum:

```bash
mkdir -p /tmp/bandit17_key
cd /tmp/bandit17_key
```

Daha sonra anahtarı kaydetmek için bir dosya oluşturdum:

```bash
nano key.private
```

Sunucudan aldığım Private Key'in tamamını dosyaya yapıştırdım.

Anahtarın başlangıç ve bitiş satırlarının da dosyada bulunması gerekir:

```text
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```

Ardından dosyayı kaydettim.

---

## Private Key İzinlerini Ayarlama

SSH, özel anahtarların başka kullanıcılar tarafından erişilebilir olmasını güvenlik riski olarak kabul eder.

Bu nedenle dosya izinlerini şu şekilde değiştirdim:

```bash
chmod 600 key.private
```

`600` izni şu şekilde görünür:

```text
-rw-------
```

Bu izinler:

- **Dosya sahibi:** Okuma + Yazma
- **Grup:** Yetki yok
- **Diğer kullanıcılar:** Yetki yok

anlamına gelir.

Böylece Private Key yalnızca dosyanın sahibi tarafından okunabilir ve değiştirilebilir.

---

## Bandit Level 17'ye Giriş Yapma

Private Key'i kaydedip izinlerini ayarladıktan sonra SSH bağlantısında bu anahtarı kullandım.

Bandit sunucusunun içerisinden:

```bash
ssh -i key.private bandit17@localhost -p 2220
```

Anahtar kendi bilgisayarımda bulunuyorsa:

```bash
ssh -i key.private bandit17@bandit.labs.overthewire.org -p 2220
```

Buradaki `-i` parametresi, SSH'a kimlik doğrulaması sırasında hangi **Private Key** dosyasını kullanacağını söyler.

---

## Komutların Açıklaması

### Nmap ile Port ve Servis Taraması

```bash
nmap -p 31000-32000 -sV localhost
```

- **`nmap`** → Ağ keşfi ve port taraması yapmak için kullanılan araçtır.
- **`-p 31000-32000`** → Taranacak port aralığını belirtir.
- **`-sV`** → Açık portlarda çalışan servisleri ve mümkünse versiyonlarını tespit etmeye çalışır.
- **`localhost`** → Bulunulan yerel makineyi temsil eder. Genellikle `127.0.0.1` adresine karşılık gelir.

---

### OpenSSL ile SSL/TLS Bağlantısı

```bash
openssl s_client -connect localhost:31790 -quiet
```

- **`openssl`** → SSL/TLS ve kriptografik işlemler için kullanılan araç setidir.
- **`s_client`** → SSL/TLS destekleyen bir servise istemci olarak bağlanır.
- **`-connect`** → Bağlanılacak hedefi belirtir.
- **`localhost:31790`** → Yerel makinenin `31790` portuna bağlanır.
- **`-quiet`** → Gereksiz bağlantı çıktılarını azaltır.

---

### Private Key Dosya İzinleri

```bash
chmod 600 key.private
```

- **`chmod`** → Dosya veya dizinlerin erişim izinlerini değiştirir.
- **`600`** → Yalnızca dosya sahibine okuma ve yazma izni verir.
- **`key.private`** → Kaydettiğimiz SSH Private Key dosyasıdır.

---

### Private Key ile SSH Bağlantısı

```bash
ssh -i key.private bandit17@localhost -p 2220
```

- **`ssh`** → Secure Shell istemcisidir.
- **`-i key.private`** → Kimlik doğrulamasında kullanılacak Private Key dosyasını belirtir.
- **`bandit17@localhost`** → `bandit17` kullanıcısı olarak yerel makineye bağlanır.
- **`-p 2220`** → OverTheWire'ın SSH için kullandığı portu belirtir.

---

## Kullanılan Komutlar

| **Komut** | **Açıklama** |
|---|---|
| `nmap -p 31000-32000 -sV localhost` | Belirtilen port aralığını tarar ve servisleri tespit eder. |
| `openssl s_client` | SSL/TLS kullanan bir servise istemci olarak bağlanır. |
| `mkdir` | Private Key'i saklamak için geçici dizin oluşturur. |
| `nano` | Private Key dosyasını oluşturmak ve düzenlemek için kullanılır. |
| `chmod 600` | Private Key dosyasının erişim izinlerini sınırlar. |
| `ssh -i` | Private Key kullanarak SSH kimlik doğrulaması gerçekleştirir. |

---

## Ne Öğrendim?

- `nmap` ile belirli bir **port aralığını taramayı**.
- `-sV` parametresiyle açık portlardaki **servisleri tespit etmeyi**.
- **SSL/TLS kullanan servisleri** normal TCP servislerinden ayırt etmeyi.
- `openssl s_client` kullanarak **SSL/TLS servisine bağlanmayı**.
- SSH bağlantılarında parola yerine **Private Key ile kimlik doğrulaması** yapılabileceğini.
- SSH Private Key dosyalarında `chmod 600` izninin neden önemli olduğunu.
- SSH'daki `-i` parametresinin **identity file (kimlik dosyası)** belirtmek için kullanıldığını.
