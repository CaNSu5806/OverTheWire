# Bandit Level 8 → Level 9

## Goal | Amaç

**EN:** Find the password for Bandit Level 9.

**TR:** Bandit Level 9 için gerekli şifreyi bulmak.

---

## Challenge Hint | Verilen İpucu

The challenge stated that the password is the **only line of text that occurs once** in the file.

Challenge'da şifrenin, dosya içerisinde **yalnızca bir kez geçen satır** olduğu belirtilmişti.

---

## Finding the Unique Line | Tekrar Etmeyen Satırı Bulma

```bash
sort data.txt | uniq -u
```

### Explanation (EN)

This solution uses two commands connected with a pipe (`|`).

#### `sort`

The `sort` command arranges all lines in alphabetical order.

This step is necessary because the `uniq` command only compares **adjacent** lines. If identical lines are scattered throughout the file, `uniq` cannot detect them unless they are grouped together by `sort`.

#### `|` (Pipe)

The pipe (`|`) takes the output of `sort` and passes it directly as the input to `uniq`, so there is no need to create an intermediate file.

#### `uniq -u`

The `uniq` command removes or filters duplicate lines.

The `-u` option displays **only the lines that appear exactly once**, which matches the challenge requirement.

### Açıklama (TR)

Bu çözümde iki komut **pipe (`|`)** kullanılarak birlikte çalıştırıldı.

#### `sort`

`sort` komutu dosyadaki tüm satırları alfabetik olarak sıralar.

Bu adım gereklidir çünkü `uniq` komutu yalnızca **yan yana bulunan aynı satırları** karşılaştırabilir. Aynı satırlar dosyanın farklı yerlerinde bulunuyorsa `uniq` bunların tekrar ettiğini anlayamaz. `sort` sayesinde aynı satırlar bir araya getirilir ve `uniq` bunları doğru şekilde analiz edebilir.

#### `|` (Pipe)

Pipe (`|`) operatörü, `sort` komutunun çıktısını doğrudan `uniq` komutuna gönderir. Böylece geçici bir dosya oluşturmaya gerek kalmaz.

#### `uniq -u`

`uniq` komutu tekrar eden satırları filtrelemek için kullanılır.

`-u` parametresi ise **yalnızca bir kez geçen satırları** ekrana yazdırır. Challenge'da aranan bilgi de yalnızca bir kez geçen satır olduğu için bu seçenek kullanılmıştır.

The output contained the password for **Bandit Level 9**.

Komutun çıktısında **Bandit Level 9** için gerekli şifre görüntülendi.

---

## Commands Used

| Command | Description |
|---------|-------------|
| `sort` | Sort all lines alphabetically. |
| `uniq -u` | Display only lines that appear exactly once. |
| `|` | Pass the output of one command directly to another. |

---

## What I Learned

- How to sort text using the `sort` command.
- Why `uniq` requires sorted input to detect duplicate lines correctly.
- How the `-u` option prints only unique lines.
- How to combine commands using the pipe (`|`) operator.
