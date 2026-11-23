# Proxy Email Assistant (Cloudflare Worker)

Tiene la chiave API Anthropic di AlpStay fuori dal browser: la pagina chiama questo Worker, il Worker chiama Anthropic.

## Messa online (una volta, ~5 minuti)

```bash
cd proxy
npm install
npx wrangler login                       # account Cloudflare AlpStay
npx wrangler secret put ANTHROPIC_API_KEY  # incolla la chiave sk-ant-...
npx wrangler deploy
```

`deploy` stampa l'indirizzo, es. `https://alpstay-emailassistant.<sottodominio>.workers.dev`.
Copialo in `index.html` nella costante `PROXY_URL`, poi unisci il ramo `accesso-pubblico` in `main`.

Nessun limite di utilizzo: ogni risposta generata da chiunque è a carico della chiave AlpStay.
Per il consumo: console.anthropic.com → Usage.
