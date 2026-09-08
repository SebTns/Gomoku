## AC-07-01: Spelaren anger ett giltigt namn
Relaterade krav: FR-02.1, FR-02.2, FR-02.5, UC-07 (Steg 1-7)

Given att spelaren har öppnat spelet (UC-06)
And inget parti är pågående
And systemet visar ett fält med det senast använda namnet ifyllt, eller standardnamnet "Spelare 1"

When spelaren skriver in ett namn som består av 2–20 tecken (bokstäver, siffror, bindestreck eller understreck) och bekräftar

Then ska systemet validera namnet som giltigt
And spara namnet lokalt
And visa namnet i gränssnittet (t.ex. i turindikatorn och resultatvyn)

---

## AC-07-02: Namnet uppfyller inte reglerna
Relaterade krav: FR-02.3, UC-07 (AF-01)

Given att spelaren har öppnat spelet (UC-06)
And inget parti är pågående

When spelaren skriver in ett namn som bryter mot reglerna (t.ex. för kort, för långt, eller innehåller otillåtna tecken som ! eller @) och bekräftar

Then ska systemet avvisa namnet
And visa ett tydligt felmeddelande som anger vilken regel som inte uppfylls
And inte spara namnet
And låta spelaren skriva om namnet och försöka igen

---

## AC-07-03: Spelaren anger inget namn
Relaterade krav: FR-02.4, UC-07 (AF-02)

Given att spelaren har öppnat spelet (UC-06)
And inget parti är pågående

When spelaren lämnar namnfältet tomt och bekräftar

Then ska systemet automatiskt tilldela standardnamnet "Spelare 1"
And spara standardnamnet lokalt
And visa standardnamnet i gränssnittet

---

## AC-07-04: Spelaren avbryter namnändringen
Relaterade krav: FR-02.7, UC-07 (AF-03)

Given att spelaren har öppnet spelet (UC-06)
And inget parti är pågående
And spelaren redan har ett befintligt namn

When spelaren väljer att avbryta namnändringen innan den bekräftas

Then ska systemet behålla det tidigare namnet
And ingen ändring ska sparas
And spelarens namn ska förbli oförändrat

---

## AC-07-05: Namnet saneras och skyddas (NFR-krav)
Relaterade krav: FR-02.2, NFR-07.3, NFR-07.4, UC-07 (Särskilda krav)

Given att spelaren har öppnat spelet (UC-06)
And inget parti är pågående

When spelaren skriver in ett namn som innehåller skadlig kod eller skript (t.ex. `<script>` eller onmouseover)

Then ska systemet sanera namnet så att skriptet inte kan köras hos andra spelare
And endast samla in det synliga namnet som personuppgift i gästläge
And inte samla in några andra personuppgifter (t.ex. e-post eller IP-adress)
