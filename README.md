# Traductor - English to Spanish on Base

> AI-powered English to Spanish translator.
> Every translation triggers a permanent Base transaction.
> Includes community phrase book and Mini App Builder.
> Owner: `0xdBF45AF1cD37deBEDD059BEe0525289d2b5E5CF4`

---

## Files

| File | Purpose |
|------|---------|
| `Traductor.sol` | Smart contract - deploy on Base via Remix |
| `index.html` | Full DApp frontend |
| `vercel.json` | Vercel static deployment config |
| `icon.png` | 1024x1024 Base app icon |
| `splash.png` | 200x200 splash screen |
| `og.png` | 1200x630 social preview |
| `.well-known/farcaster.json` | Base Mini App manifest |

---

## Step 1 - Deploy on Base via Remix

1. Go to **https://remix.ethereum.org**
2. New file -> paste `Traductor.sol`
3. Compile: Solidity `^0.8.20`
4. Deploy:
   - Environment: **Injected Provider - MetaMask**
   - Network: **Base Mainnet** (Chain ID 8453)
5. Copy deployed address -> send to Claude to update files

---

## Step 2 - Verify on Basescan

1. **https://basescan.org/verifyContract**
2. Paste address, Compiler `0.8.20`, paste source, Submit

---

## Step 3 - Update Files (send to Claude)

Send Claude:
- Contract address
- GitHub repo URL
- Vercel app URL

Claude will update all files automatically.

---

## Step 4 - Push to GitHub + Deploy on Vercel

Repo structure:
```
/
|-- index.html
|-- vercel.json
|-- icon.png
|-- splash.png
|-- og.png
|-- README.md
|-- Traductor.sol
`-- .well-known/
    `-- farcaster.json
```

**https://vercel.com/new** -> Import repo -> Framework: Other -> Deploy

---

## Step 5 - Register on Base.dev

1. **https://base.dev** -> Connect wallet
2. Create project -> enter Vercel URL
3. Copy the meta tag -> send to Claude -> redeploy -> Verify

---

## Contract Features

```
Traductor.sol
|-- logTranslation(sourceText, translatedText, category)
|   -> Stores full text on-chain (use for <500 chars)
|-- logTranslationLite(sourceHash, translatedText, charCount, category)
|   -> Stores hash + translation (gas efficient for long texts)
|-- addPhrase(english, spanish)
|   -> Community phrase book contributions
|-- upvotePhrase(phraseId)
|-- verifyPhrase(phraseId, verified)  [owner only]
|-- deployMiniApp(name, config)
`-- getStats() -> (totalTranslations, totalChars, totalWords, totalPhrases)
```

## DApp Features

- **Translate tab** - Type English, get Spanish via Claude AI API
- **History tab** - Full on-chain translation log
- **Phrase Book tab** - Community EN/ES phrase contributions with upvoting
- **Mini Apps tab** - 4 templates: Spanish Greeter, Phrasebook, Vocab Quiz, Numbers

---

*Built for `0xdBF45AF1cD37deBEDD059BEe0525289d2b5E5CF4`*
