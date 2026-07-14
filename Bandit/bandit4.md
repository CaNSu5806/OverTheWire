# Bandit Level 3 → Level 4

## Goal | Amaç

**EN:** Find the password for Bandit Level 4.

**TR:** Bandit Level 4 için gerekli şifreyi bulmak.

---

## Listing the Files | Dosyaları Listeleme

```bash
ls -la
```

### Explanation (EN)

The `-a` option displays all files, including hidden ones. This level contains a hidden file, so using `ls` or `ls -l` alone would not show it.

### Açıklama (TR)

`-a` parametresi gizli dosyalar da dahil olmak üzere tüm dosyaları gösterir. Bu levelde şifre gizli bir dosyada bulunduğu için `ls` veya `ls -l` komutu tek başına yeterli değildir.

The output showed a hidden file named:

```text
...Hiding-From-You
```

---

## Reading the File | Dosyayı Okuma

```bash
cat ./...Hiding-From-You
```

### Explanation (EN)

The `cat` command displays the contents of the hidden file.

### Açıklama (TR)

`cat` komutu gizli dosyanın içeriğini terminal ekranında görüntüler.

The file contained the password for **Bandit Level 4**.

Dosyanın içinde **Bandit Level 4** için gerekli şifre bulunuyordu.

---

## Commands Used

| Command | Description |
|---------|-------------|
| `ls -la` | List all files, including hidden ones, with detailed information. |
| `cat` | Display the contents of a file. |

---

## What I Learned

- How to display hidden files using `ls -a`.
- Hidden files in Linux usually start with a `.` (dot).
- How to read the contents of a hidden file using `cat`.
