# Bandit Level 10 → Level 11

## 🇬🇧 English

### Goal

Find the password for **Bandit Level 11**.

---

### Challenge Hint

The challenge states that the password is stored in `data.txt`, where **all human-readable strings are preceded by several '=' characters**.

---

### Extracting Readable Text

```bash
strings data.txt | grep "="
```

The file contained a large amount of binary and unreadable data. Instead of inspecting the entire file manually, I extracted only the human-readable strings and searched for the lines containing `=` characters, as suggested by the challenge.

---

### Explanation

This solution combines two commands using a pipe (`|`).

#### `strings`

The `strings` command extracts **printable (human-readable)** text from a file.

It is commonly used to inspect binary files and identify embedded text without displaying unreadable binary data.

#### `|` (Pipe)

The pipe passes the output of the `strings` command directly to `grep`.

#### `grep "="`

The challenge hint mentioned that the password is preceded by several `=` characters.

The `grep` command filters the output and displays only the lines containing `=`, making it easy to locate the password.

Running the command revealed the password for **Bandit Level 11**.

---

### Commands Used

| Command | Description |
|---------|-------------|
| `strings data.txt` | Extract printable strings from the file. |
| `grep "="` | Search for lines containing `=`. |
| `|` | Pass the output of one command to another. |

---

### What I Learned

- How to extract readable text from binary files using `strings`.
- How to filter command output using `grep`.
- How to combine commands with pipes (`|`).
- When `strings` is useful during Linux and CTF challenges.

---

# 🇹🇷 Türkçe

## Amaç

**Bandit Level 11** için gerekli şifreyi bulmak.

---

## Verilen İpucu

Challenge'da şifrenin `data.txt` dosyasında bulunduğu, **önünde birkaç adet `=` karakteri olduğu** ve **okunabilir (human-readable)** bir metin olduğu belirtiliyordu.

---

## Okunabilir Metinleri Bulma

```bash
strings data.txt | grep "="
```

`data.txt` dosyası büyük ölçüde okunamayan (binary) veriler içeriyordu. Dosyanın tamamını incelemek yerine önce yalnızca okunabilir metinler çıkarıldı, ardından challenge'ın verdiği ipucuna uygun olarak `=` karakteri bulunan satırlar filtrelendi.

---

### Açıklama

Bu çözümde iki komut **pipe (`|`)** kullanılarak birlikte çalıştırıldı.

#### `strings`

`strings` komutu, bir dosya içerisindeki **okunabilir (printable)** metinleri ekrana yazdırır.

Özellikle binary dosyaların içinde gömülü bulunan metinleri görüntülemek için oldukça kullanışlıdır.

#### `|` (Pipe)

Pipe (`|`) operatörü, `strings` komutunun çıktısını doğrudan `grep` komutuna aktarır.

#### `grep "="`

Challenge'da şifrenin önünde birkaç adet `=` karakteri bulunduğu belirtildiği için `grep` komutu kullanılarak yalnızca bu karakteri içeren satırlar görüntülendi.

Komut çalıştırıldığında **Bandit Level 11** için gerekli şifre ekrana yazdırıldı.

---

## Kullanılan Komutlar

| Komut | Açıklama |
|--------|----------|
| `strings data.txt` | Dosya içerisindeki okunabilir metinleri çıkarır. |
| `grep "="` | İçerisinde `=` bulunan satırları arar. |
| `|` | Bir komutun çıktısını diğer komuta aktarır. |

---

## Ne Öğrendim

- `strings` komutuyla binary dosyalardaki okunabilir metinleri çıkarmayı.
- `grep` komutuyla belirli desenleri filtrelemeyi.
- Pipe (`|`) operatörü ile komutları birleştirmeyi.
- `strings` komutunun CTF ve Linux analizlerinde ne kadar kullanışlı olduğunu.
