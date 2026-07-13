```markdown
# Bandit Level 2 → Level 3

## Goal | Amaç

**EN:** Find the password for Level 3, which is stored in a file called `-- spaces in this filename--` located in the home directory.

**TR:** Home dizininde bulunan ve ismi `-- spaces in this filename--` olan dosyanın içindeki Level 3 şifresini bulmak.

---

## Solving the Problem | Çözüm

```bash
cat "./-- spaces in this filename--"
