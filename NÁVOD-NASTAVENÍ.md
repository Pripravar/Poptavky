# Nastavení webu „Poptávky a objednávky"

Cíl: veřejná adresa (GitHub Pages) chráněná přihlášením, data ve Firebase, plní se samo.
Vše je **zdarma** — žádný placený plán, žádná platební karta.

Kroky, které musíš udělat TY (účty a přihlášení za tebe dělat nemůžu). U každého kroku
mi pak řekni, ať pokračuju.

---

## A) Firebase (databáze + přihlášení)

1. Jdi na **console.firebase.google.com**, přihlas se účtem `popobjmsilniceozjih@gmail.com`.
2. **Add project** → název třeba `poptavky-objednavky` → Google Analytics můžeš vypnout → Create.
3. Vlevo **Build → Realtime Database** → *Create Database* →
   - lokace **europe-west1** (Belgium),
   - **Start in locked mode** → Enable.
4. Záložka **Rules** → přepiš obsah na tohle a dej **Publish**:
   ```json
   { "rules": { ".read": "auth != null", ".write": "auth != null" } }
   ```
5. Vlevo **Build → Authentication** → *Get started* →
   - **Sign-in method** → zapnout **Email/Password** → Save.
   - Záložka **Users** → **Add user** → zadej společný e‑mail a heslo pro tým
     (např. `tym@poptavky` + heslo) → Add user. *(Toto heslo budeš dávat kolegům.)*
6. **Project settings** (⚙️ vlevo nahoře) → dole **Your apps** → **</>** (Web) →
   přezdívka `web` → Register app → ukáže se blok `firebaseConfig = { … }`.
   **Tenhle blok mi pošli** (apiKey, authDomain, databaseURL, projectId, appId).

## B) GitHub (hosting stránky)

7. Na **github.com** (účet `Pripravar`) → **New repository** →
   název třeba `poptavky` → Public → Create.
8. Repo vyžaduje nahrát soubory z této složky `web-poptavky` (index.html …).
   Uděláš to přes **GitHub Mac app** (jako u staveb) — nebo mi řekni a navedu tě.
9. V repu **Settings → Pages** → Source: **main** / složka `/root` → Save.
   Za 1–2 min vznikne adresa `https://pripravar.github.io/poptavky/`.
10. Tu adresu (resp. doménu `pripravar.github.io`) ještě přidej ve Firebase:
    **Authentication → Settings → Authorized domains → Add domain** → `pripravar.github.io`.

---

## Co udělám JÁ, jakmile mi pošleš `firebaseConfig`

- Doplním config do `index.html` (vypne se ukázkový režim, zapne přihlášení + živá data).
- Nahraju aktuální data (4 stavby) do Firebase.
- Upravím ranní úlohu (7/10/13/16), aby zapisovala nové poptávky/objednávky rovnou do
  Firebase → web se bude aktualizovat sám.

Heslo k týmovému účtu i jakékoliv klíče nikam nezveřejňuju.
