# Bandit Level 9 → Level 10

## 🇬🇧 English

### Goal

Find the password for **Bandit Level 10**.

---

### Challenge Hint

The challenge states that the password is stored in `data.txt`, which contains **Base64 encoded data**.

---

### Viewing the File

```bash
cat data.txt
```

The output was a long string consisting of uppercase and lowercase letters, numbers, and characters such as `+`, `/`, and `=`.

Since the challenge explicitly mentions that the file contains **Base64 encoded data**, the next step is to decode it. These characters are also typical of Base64-encoded text, making it easy to recognize.

---

### Decoding the File

```bash
base64 -d data.txt
```

#### Explanation

- **base64** → A utility used to encode and decode Base64 data.
- **-d** → Decodes the Base64-encoded text back to its original form.
- **data.txt** → The file containing the encoded data.

Running the command revealed the password for **Bandit Level 10**.

---

### Commands Used

| Command | Description |
|---------|-------------|
| `cat data.txt` | Display the contents of the file. |
| `base64 -d data.txt` | Decode the Base64-encoded data. |

---

### What I Learned

- What Base64 encoding is.
- How to recognize Base64-encoded text.
- How to decode Base64 data using the `base64` command.
- The difference between **encoding** and **encryption**.

---

# 🇹🇷 Türkçe

## Amaç

**Bandit Level 10** için gerekli şifreyi bulmak.

---

## Verilen İpucu

Challenge'da şifrenin **Base64 ile kodlanmış** `data.txt` dosyasında bulunduğu belirtiliyordu.

---

## Dosyayı İnceleme

```bash
cat data.txt
```

Dosyanın içeriği; büyük-küçük harfler, sayılar ve `+`, `/`, `=` gibi karakterlerden oluşan uzun bir metindi.

Challenge açıklamasında verinin **Base64 ile kodlandığı** belirtildiği için bir sonraki adım bu veriyi çözmek oldu. Ayrıca bu karakter yapısı da Base64 kodlamasının tipik özelliklerinden biridir.

---

## Veriyi Çözme

```bash
base64 -d data.txt
```

### Açıklama

- **base64** → Base64 ile kodlanmış verileri kodlamak ve çözmek için kullanılan araçtır.
- **-d** → Veriyi decode ederek orijinal haline dönüştürür.
- **data.txt** → Kodlanmış veriyi içeren dosyadır.

Komut çalıştırıldıktan sonra **Bandit Level 10** için gerekli şifre ekrana yazdırıldı.

---

## Kullanılan Komutlar

| Komut | Açıklama |
|--------|----------|
| `cat data.txt` | Dosyanın içeriğini görüntüler. |
| `base64 -d data.txt` | Base64 ile kodlanmış veriyi çözer. |

---

## Ne Öğrendim

- Base64 kodlamasının ne olduğunu.
- Base64 ile kodlanmış metinlerin nasıl tanınacağını.
- `base64 -d` komutu ile Base64 verisinin nasıl çözüleceğini.
- **Encoding** ile **encryption** arasındaki farkı.
