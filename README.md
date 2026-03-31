# Vaksin Untuk Kita

Aplikasi informasi vaksin berbasis Nuxt.

## Setup

Make sure to install dependencies:

```bash
# npm
npm install

# pnpm
pnpm install

# yarn
yarn install

# bun
bun install
```

## Development Server

Start the development server on `http://localhost:3000`:

```bash
# npm
npm run dev

# pnpm
pnpm dev

# yarn
yarn dev

# bun
bun run dev
```

## Production

Build the application for production:

```bash
# npm
npm run build

# pnpm
pnpm build

# yarn
yarn build

# bun
bun run build
```

Locally preview production build:

```bash
# npm
npm run preview

# pnpm
pnpm preview

# yarn
yarn preview

# bun
bun run preview
```

## Deploy ke Vercel

Project ini sudah disiapkan dengan `nitro.preset = 'vercel'` di `nuxt.config.ts`.

Langkah deploy:

1. Push project ke repository GitHub.
2. Import repository di Vercel.
3. Gunakan pengaturan build berikut (biasanya otomatis terdeteksi):
	- Build Command: `npm run build`
	- Output Directory: `.vercel/output`
4. Deploy.

Untuk local preview hasil production, tetap bisa pakai:

```bash
npm run preview
```
