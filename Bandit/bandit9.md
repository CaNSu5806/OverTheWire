# Bandit Level 9 → Level 10

## Goal | Amaç

**EN:** Find the password for **Bandit Level 10**.

**TR:** **Bandit Level 10** için gerekli şifreyi bulmak.

---

## Challenge Hint | Verilen İpucu

The challenge stated that the password is stored in `data.txt`, which contains **Base64 encoded data**.

Challenge'da şifrenin **Base64 ile kodlanmış** `data.txt` dosyasında bulunduğu belirtiliyordu.

---

## Viewing the File | Dosyayı İnceleme

```bash
cat data.txt
```

The output was a long string containing uppercase and lowercase letters, numbers, and characters such as `+`, `/`, and `=`.

Since the challenge explicitly stated that the file was Base64 encoded, the next step was to decode it. The character set (`A-Z`, `a-z`, `0-9`, `+`, `/`, `=`) is also typical of Base64 encoding.

Dosyanın içeriği büyük-küçük harfler, sayılar ve `+`, `/`, `=` gibi karakterlerden oluşan uzun bir metindi.

Challenge açıklamasında verinin Base64 ile kodlandığı belirtildiği için bir sonraki adım bu veriyi çözmek oldu. Ayrıca kullanılan karakter kümesi (`A-Z`, `a-z`, `0-9`, `+`, `/`, `=`) Base64 kodlamasının tipik özelliklerinden biridir.

---

## Decoding the File | Veriyi Çözme

```bash
base64 -d data.txt
```

### Explanation (EN)

#### `base64`

The `base64` utility is used to encode and decode Base64 data.

#### `-d`

The `-d` option tells the command to **decode** the Base64-encoded data back to its original form.

#### `data.txt`

The file containing the encoded data.

Running the command revealed the password for **Bandit Level 10**.

---

### Açıklama (TR)

#### `base64`

`base64` komutu, Base64 ile kodlanmış verileri kodlamak ve çözmek için kullanılır.

#### `-d`

`-d` parametresi, Base64 ile kodlanmış veriyi **decode ederek** orijinal haline dönüştürür.

#### `data.txt`

Kodlanmış veriyi içeren dosyadır.

Komut çalıştırıldığında **Bandit Level 10** için gerekli şifre ekrana yazdırıldı.

---

## Commands Used

| Command | Description |
|---------|-------------|
| `cat data.txt` | Display the contents of the file. |
| `base64 -d data.txt` | Decode the Base64-encoded data. |

---

## What I Learned

- What Base64 encoding is.
- How to recognize Base64-encoded text.
- How to decode Base64 data using the `base64` command.
- The difference between **encoding** and **encryption**.
