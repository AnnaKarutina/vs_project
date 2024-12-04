# Juhend: Kuidas luua GitHub Issue ja siduda see commitiga

GitHub Issues on võimas vahend probleemide jälgimiseks ja projektide haldamiseks. Selle juhendi abil saate luua uue issue ja siduda selle vastava commitiga.

---

## 1. Kuidas luua GitHub Issue

### Samm 1: Ava repositoorium
1. Logi sisse oma GitHubi kontole.
2. Mine projekti juurde, mille jaoks soovid issue luua.

### Samm 2: Ava "Issues" sektsioon
1. Klõpsa menüüribal "Issues" vahekaardil.

### Samm 3: Loo uus issue
1. Klõpsa nupul **New issue**.
2. Täida järgmised väljad:
   - **Title**: Kirjuta probleemi või ülesande pealkiri.
   - **Description**: Selgita üksikasjalikult, mis probleem on või milline ülesanne tuleb täita. Kasuta markdown-süntaksit (nt loetelud, paks tekst) vajadusel.
3. Vajadusel lisa märgised (labels), assigneeri isik ja lisa milestone.
4. Klõpsa **Submit new issue**, et salvestada.

---

## 2. Kuidas siduda issue commitiga

Commiti ja issue sidumine aitab hoida tööd organiseeritud ja jäljgitav.

### Samm 1: Kasuta commit message’it issue viitamiseks
Git-süsteemi commit’ide sõnumites saate viidata GitHub issue’dele, kasutades viitenumbrit. Näiteks:

```bash
Fixes #123
```

Siin **#123** on issue number, mida soovite lahendada. See:
- Sulgeb issue automaatselt, kui commit lükatakse GitHubi peaharusse (main).
- Märgistab commit’i vastava issue’ga seotud ajaloos.

#### Näited:
- **Sulge issue automaatselt:**
  ```bash
  git commit -m "Fix typo in documentation. Fixes #45"
  ```
- **Viita issue’le ilma sulgemata:**
  ```bash
  git commit -m "Update README with additional examples. See #67"
  ```

### Samm 2: Pushi commit GitHubi
1. Salvesta muudatused lokaalses repositooriumis:
   ```bash
   git add .
   git commit -m "Fix login bug. Fixes #101"
   ```
2. Lükka muudatused GitHubi:
   ```bash
   git push origin branch-name
   ```

### Samm 3: Kontrolli issue olekut
1. Mine GitHubis vastava issue juurde.
2. Veendu, et commit’id on seotud ja issue’d kas suleti automaatselt või on neile lisatud kommentaar vastavalt commit message’ile.

---

## 3. Töö erinevate harudega

### Samm 1: Loo eraldi haru iga issue jaoks
1. Kontrolli, et oled repositooriumi põhiharus (nt `main` või `dev`):
   ```bash
   git checkout dev
   ```
2. Loo uus haru:
   ```bash
   git checkout -b issue-123
   ```
   Siin `issue-123` on haru nimi, mis viitab konkreetsele issue’le.

### Samm 2: Tee muudatused ja commit’id
1. Tee vajalikud muudatused koodis.
2. Salvesta muudatused commit’iga, viidates issue’le:
   ```bash
   git add .
   git commit -m "Add feature X. Fixes #123"
   ```

### Samm 3: Pushi haru GitHubi
1. Lükka loodud haru GitHubi:
   ```bash
   git push origin issue-123
   ```

### Samm 4: Tee pull request
1. Ava GitHubi repositoorium.
2. Mine "Pull requests" sektsiooni ja klõpsa **New pull request**.
3. Vali võrdluseks:
   - Base: `dev`
   - Compare: `issue-123`
4. Lisa kirjeldus ja viide issue’le ning klõpsa **Create pull request**.

### Samm 5: Liida muudatused põhiharudesse
1. Kui pull request on heaks kiidetud ja testitud, liida see `dev` harusse.
   ```bash
   git checkout dev
   git merge issue-123
   ```
2. Testi, kas kood toimib pärast liitmist.
3. Kui valmis, liida `dev` haru `main` harusse:
   ```bash
   git checkout main
   git merge dev
   ```
4. Pushi põhiharu muudatused GitHubi:
   ```bash
   git push origin main
   ```

---

## Lisamärkused
- Kui töötate meeskonnas, veenduge, et kõik liikmed järgivad sama töövoogu.
- Kasutage GitHubi projekte ja issue’sid töö paremaks korraldamiseks.

---

Selle juhendi järgimine aitab hoida teie projektid korrastatud ja muudatused hästi hallatavad. Kui tekib lisaküsimusi, andke teada!

