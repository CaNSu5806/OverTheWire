# Bandit Level 15 → Level 16

## 🇬🇧 English

### Goal

Retrieve the password for **Bandit Level 16** by sending the current level's password to a service running on **localhost** at **port 30001** using **SSL/TLS encryption**.

---

### Challenge Hint

The challenge states that a service is listening on **TCP port 30001** on the local machine. Unlike the previous level, this service accepts **SSL/TLS encrypted connections** instead of plain TCP.

---

### Retrieving the Current Password

First, I displayed the password for **Bandit15**.

```bash
cat /etc/bandit_pass/bandit15
```

I copied the password because it would be required in the next step.

---

### Connecting with SSL/TLS

Since the service requires an encrypted connection, using **Netcat (`nc`)** is no longer sufficient.

Instead, I connected using OpenSSL.

```bash
openssl s_client -connect localhost:30001
```

---

### Understanding the Command

```bash
openssl s_client -connect localhost:30001
```

#### Explanation

- **openssl** → A command-line toolkit that provides cryptographic functions and supports SSL/TLS communication.
- **s_client** → Creates an SSL/TLS client connection to a remote server.
- **-connect** → Specifies the host and port to connect to.
- **localhost** → Refers to the current machine (`127.0.0.1`).
- **30001** → The TCP port where the challenge service is listening.

Unlike `nc`, which only creates a normal TCP connection, `openssl s_client` first performs an **SSL/TLS handshake** and then establishes an encrypted communication channel.

---

### SSL/TLS Handshake

When the command is executed, OpenSSL performs the SSL/TLS handshake automatically.

During this process:

1. The client connects to the server.
2. The server sends its certificate.
3. Both sides negotiate the encryption algorithm.
4. A secure encrypted channel is established.

After the handshake completes, the terminal waits for input.

This indicates that the server is ready to receive data over the secure connection.

---

### Sending the Password

The challenge description instructs us to **submit the password of the current level**.

After the encrypted connection was established, I pasted the password obtained from the previous step and pressed **Enter**.

If the password was correct, the server responded with:

```text
Correct!
<Bandit16 Password>
```

The second line is the password required to access **Bandit Level 16**.

---

### Why Doesn't Netcat Work?

In the previous level, the following command was sufficient:

```bash
nc localhost 30000
```

This worked because the service accepted **plain TCP** connections.

However, Level 15 requires **SSL/TLS encryption**.

Since Netcat does not perform an SSL/TLS handshake, the server rejects the connection.

OpenSSL handles the handshake automatically before any data is sent.

---

### Commands Used

| Command | Description |
|---------|-------------|
| `cat` | Display the contents of a file. |
| `openssl` | Perform cryptographic operations and establish SSL/TLS connections. |
| `s_client` | Act as an SSL/TLS client. |
| `-connect` | Specify the target host and port. |

---

### What I Learned

- The difference between **TCP** and **SSL/TLS**.
- How to establish an encrypted connection using `openssl s_client`.
- How the SSL/TLS handshake works.
- Why some services require encrypted communication instead of plain TCP.
- How to communicate securely with a service using SSL/TLS.

---

# 🇹🇷 Türkçe

## Amaç

**Bandit15** şifresini, **localhost** üzerindeki **30001** numaralı portta çalışan **SSL/TLS** destekli servise göndererek **Bandit Level 16** şifresini elde etmek.

---

## Verilen İpucu

Challenge'da, yerel makinede (**localhost**) **30001** numaralı TCP portunda çalışan bir servis olduğu belirtilmektedir.

Bu servis, bir önceki seviyeden farklı olarak **normal TCP bağlantısı değil, SSL/TLS ile şifrelenmiş bağlantı** kabul etmektedir.

---

## Mevcut Seviyenin Şifresini Alma

Öncelikle **Bandit15** kullanıcısının şifresini görüntüledim.

```bash
cat /etc/bandit_pass/bandit15
```

Elde ettiğim şifreyi bir sonraki adımda kullanmak üzere kopyaladım.

---

## SSL/TLS ile Bağlantı Kurma

Bu seviyede normal TCP bağlantısı yeterli değildir.

Bu nedenle Netcat (`nc`) yerine OpenSSL kullandım.

```bash
openssl s_client -connect localhost:30001
```

---

## Komutun Açıklaması

```bash
openssl s_client -connect localhost:30001
```

### Açıklama

- **openssl** → Kriptografik işlemler ve SSL/TLS bağlantıları kurmak için kullanılan bir araçtır.
- **s_client** → OpenSSL'in SSL/TLS istemcisi olarak çalışmasını sağlar.
- **-connect** → Bağlanılacak sunucu ve portu belirtir.
- **localhost** → Bulunulan makineyi ifade eder (`127.0.0.1`).
- **30001** → Challenge servisinin dinlediği TCP portudur.

Bir önceki seviyede kullandığımız `nc` komutu yalnızca normal TCP bağlantısı kurarken, `openssl s_client` önce **SSL/TLS Handshake** gerçekleştirir ve ardından güvenli iletişim başlatır.

---

## SSL/TLS Handshake Nedir?

Komut çalıştırıldığında OpenSSL arka planda otomatik olarak **SSL/TLS Handshake** işlemini gerçekleştirir.

Bu süreçte:

1. İstemci sunucuya bağlanır.
2. Sunucu sertifikasını gönderir.
3. İki taraf kullanılacak şifreleme algoritması üzerinde anlaşır.
4. Şifrelenmiş güvenli iletişim kanalı oluşturulur.

Handshake tamamlandıktan sonra terminal herhangi bir mesaj vermeden kullanıcıdan giriş bekler.

Bu durum, güvenli bağlantının başarıyla kurulduğunu ve sunucunun veri almaya hazır olduğunu gösterir.

---

## Şifreyi Gönderme

Challenge açıklamasında mevcut seviyenin şifresini göndermemiz gerektiği belirtilmektedir.

Bu nedenle güvenli bağlantı kurulduktan sonra bir önceki adımda elde ettiğim **Bandit15** şifresini yapıştırıp **Enter** tuşuna bastım.

Doğru parola gönderildiğinde sunucu şu cevabı verdi:

```text
Correct!
<Bandit16 Şifresi>
```

İkinci satırda görünen değer, **Bandit Level 16** için kullanılacak şifredir.

---

## Neden `nc` Kullanmadık?

Bir önceki seviyede aşağıdaki komut yeterliydi.

```bash
nc localhost 30000
```

Çünkü servis **normal TCP bağlantısı** kabul ediyordu.

Bu seviyede ise servis yalnızca **SSL/TLS ile şifrelenmiş bağlantıları** kabul etmektedir.

Netcat SSL/TLS Handshake gerçekleştiremediği için bağlantı başarılı olmaz.

`openssl s_client` ise önce güvenli bağlantıyı kurar, ardından veri gönderilmesini sağlar.

---

## Kullanılan Komutlar

| Komut | Açıklama |
|--------|----------|
| `cat` | Dosyanın içeriğini görüntüler. |
| `openssl` | SSL/TLS işlemleri gerçekleştiren araçtır. |
| `s_client` | SSL/TLS istemcisi olarak bağlantı kurar. |
| `-connect` | Bağlanılacak sunucu ve portu belirtir. |

---

## Ne Öğrendim

- TCP ile SSL/TLS arasındaki farkı.
- `openssl s_client` komutunun nasıl kullanıldığını.
- SSL/TLS Handshake sürecinin temel mantığını.
- Bazı servislerin neden yalnızca şifrelenmiş bağlantıları kabul ettiğini.
- SSL/TLS kullanarak güvenli şekilde veri göndermeyi.
