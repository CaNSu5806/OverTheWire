# Bandit Level 2 → Level 3

## Goal | Amaç

**EN:** Find the password for Bandit Level 3.

**TR:** Bandit Level 3 için gerekli şifreyi bulmak.

---

## Listing the Files | Dosyaları Listeleme

```bash
ls
```

The output contained a file named:

```text
--spaces in this filename--
```

---

## Reading the File | Dosyayı Okuma

```bash
cat "./--spaces in this filename--"
```

### Explanation (EN)

The filename contains spaces, so it must be enclosed in quotes. Adding `./` also ensures the shell treats it as a file in the current directory rather than interpreting the leading `--` as an option.

### Açıklama (TR)

Dosya adında boşluk bulunduğu için tırnak içine alınmalıdır. Ayrıca dosya adı `--` ile başladığından, komutun bunu bir seçenek olarak algılamaması için başına `./` eklenir.

The file contained the password for **Bandit Level 3**.

Dosyanın içinde **Bandit Level 3** için gerekli şifre bulunuyordu.

---

## Commands Used

| Command | Description |
|---------|-------------|
| `ls` | List files in the current directory. |
| `cat` | Display the contents of a file. |

---

## What I Learned

- How to access files whose names contain spaces.
- Why filenames beginning with `-` or `--` should be prefixed with `./`.
