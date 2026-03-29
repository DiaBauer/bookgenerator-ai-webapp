# BookGenerator.ai – Deployment auf Vercel

## Schritt 1: Anthropic API Key besorgen
Gehe zu https://console.anthropic.com → API Keys → neuen Key erstellen → kopieren

## Schritt 2: Terminal öffnen
Öffne ein Terminal (oder PowerShell) und navigiere in diesen Ordner:
```
cd pfad/zu/bookgenerator-ai_webapp_bau1
```

## Schritt 3: Abhängigkeiten installieren
```bash
npm install
```

## Schritt 4: Lokal testen (optional)
```bash
cp .env.example .env.local
# .env.local öffnen und ANTHROPIC_API_KEY eintragen
npm run dev
# → http://localhost:3000
```

## Schritt 5: Auf Vercel deployen
```bash
npx vercel login     # einmalig, öffnet Browser-Login
npx vercel --prod    # deployt auf Produktion
```

**Beim ersten Mal fragt Vercel:**
- Set up and deploy? → Y
- Which scope? → dein Team / Konto wählen
- Link to existing project? → N (neues Projekt)
- Project name? → `bookgenerator-ai` (Enter)
- Directory? → `.` (Enter)
- Override settings? → N (Enter)

## Schritt 6: Umgebungsvariable setzen
Nach dem Deployment:
```bash
npx vercel env add ANTHROPIC_API_KEY production
# → deinen API Key eingeben
npx vercel --prod   # nochmal deployen (damit der Key aktiv ist)
```

Oder über das Vercel Dashboard:
1. Öffne vercel.com → dein Projekt → Settings → Environment Variables
2. Füge hinzu: `ANTHROPIC_API_KEY` = dein Key (Environment: Production)
3. Redeploy

## Schritt 7: Domain verbinden
Im Vercel Dashboard → dein Projekt → Settings → Domains:
- `bookgenerator.ai` hinzufügen
- `www.bookgenerator.ai` hinzufügen
- DNS-Einträge bei deinem Domain-Registrar setzen (Vercel zeigt dir genau was)

## Fertig! 🎉
Dein App läuft auf https://bookgenerator.ai
