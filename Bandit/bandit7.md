# Bandit Level 7 → Level 8

## Goal | Amaç

**EN:** Find the password for Bandit Level 8.

**TR:** Bandit Level 8 için gerekli şifreyi bulmak.

---

## Looking Around | Dosyaları Kontrol Etme

```bash
ls -la
```

The output showed a file named:

```text
data.txt
```

Komutun çıktısında `data.txt` adlı bir dosya bulundu.

---

## Searching for the Password | Şifreyi Arama

The challenge stated that the password is stored **next to the word `millionth`**.

Challenge'da şifrenin **`millionth`** kelimesinin yanında bulunduğu belirtilmişti.

```bash
grep "millionth" data.txt
```

### Explanation (EN)

The `grep` command searches a file for lines containing a specific word or pattern.

- `grep` → Search for matching text.
- `"millionth"` → The keyword provided by the challenge.
- `data.txt` → The file to search.

Since `data.txt` contained a large amount of text, using `grep` was much faster than searching manually.

### Açıklama (TR)

`grep` komutu, bir dosya içerisinde belirli bir kelimeyi veya deseni aramak için kullanılır.

- `grep` → Belirtilen metni arar.
- `"millionth"` → Challenge tarafından verilen anahtar kelime.
- `data.txt` → Arama yapılacak dosya.

`data.txt` çok fazla satır içerdiği için dosyayı tek tek incelemek yerine `grep` kullanmak çok daha hızlı ve verimli bir çözümdü.

The command returned the line containing **`millionth`**, along with the password for **Bandit Level 8**.

Komut, **`millionth`** kelimesini içeren satırı ve **Bandit Level 8** için gerekli şifreyi ekrana yazdırdı.

---

## Commands Used

| Command | Description |
|---------|-------------|
| `ls -la` | List all files, including hidden ones. |
| `grep "millionth" data.txt` | Search for the line containing the word `millionth`. |

---

## What I Learned

- How to search for specific text using the `grep` command.
- Why `grep` is useful when working with large text files.
- How to quickly locate information without reading an entire file.
