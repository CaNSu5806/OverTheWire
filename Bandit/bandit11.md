# Bandit Level 10 → Level 11

## 🇬🇧 English

### Goal

Find the password for **Bandit Level 11**.

---

### Challenge Hint

The challenge states that the password is stored in `data.txt`, where **all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions (ROT13).**

---

### Viewing the File

```bash
cat data.txt
```

The output was not readable because it had been encoded using **ROT13**.

---

### Decoding the Text

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

#### Explanation

- **cat data.txt** → Displays the contents of the file.
- **|** → Passes the output of `cat` directly to the next command.
- **tr** → Translates characters from one set to another.
- **'A-Za-z'** → Specifies all uppercase and lowercase letters.
- **'N-ZA-Mn-za-m'** → Maps each letter to the one **13 positions away**, implementing the ROT13 cipher.

Unlike Base64, ROT13 is a simple letter substitution cipher. Each letter is replaced with the letter located 13 positions later in the alphabet.

Running the command decoded the text and revealed the password for **Bandit Level 11**.

---

### Commands Used

| Command | Description |
|---------|-------------|
| `cat data.txt` | Display the contents of the file. |
| `tr 'A-Za-z' 'N-ZA-Mn-za-m'` | Decode the ROT13-encoded text. |

---

### What I Learned

- What the ROT13 cipher is.
- How to translate characters using the `tr` command.
- How pipes (`|`) connect multiple commands together.

---

# 🇹🇷 Türkçe

## Amaç

**Bandit Level 11** için gerekli şifreyi bulmak.

---

## Verilen İpucu

Challenge'da `data.txt` dosyasındaki tüm **küçük (a-z) ve büyük (A-Z) harflerin 13 karakter döndürüldüğü (ROT13)** belirtiliyordu.

---

## Dosyayı İnceleme

```bash
cat data.txt
```

Dosyanın içeriği okunabilir görünmüyordu çünkü metin **ROT13** yöntemi ile dönüştürülmüştü.

---

## Veriyi Çözme

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

### Açıklama

- **cat data.txt** → Dosyanın içeriğini ekrana yazdırır.
- **|** → İlk komutun çıktısını doğrudan ikinci komuta aktarır.
- **tr** → Karakterleri başka karakterlerle değiştirir.
- **'A-Za-z'** → Tüm büyük ve küçük harfleri seçer.
- **'N-ZA-Mn-za-m'** → Her harfi alfabede **13 karakter sonraki harfle** eşleştirerek ROT13 dönüşümünü uygular.

ROT13, Base64 gibi bir kodlama yöntemi değil; her harfi alfabede 13 karakter kaydıran basit bir harf değiştirme yöntemidir.

Komut çalıştırıldığında metin çözüldü ve **Bandit Level 11** için gerekli şifre ekrana yazdırıldı.

---

## Kullanılan Komutlar

| Komut | Açıklama |
|--------|----------|
| `cat data.txt` | Dosyanın içeriğini görüntüler. |
| `tr 'A-Za-z' 'N-ZA-Mn-za-m'` | ROT13 ile dönüştürülmüş metni çözer. |

---

## Ne Öğrendim

- ROT13 yönteminin nasıl çalıştığını.
- `tr` komutuyla karakter dönüşümü yapmayı.
- Pipe (`|`) operatörü ile komutları birleştirmeyi.
