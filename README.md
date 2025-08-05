# Reown AppKit Example with COOP and COEP headers which breaks the social login

This is a Next.js project.

## How reproduce headers issue

1. Go to `next.config.ts` and uncomment the `Cross-Origin-Embedder-Policy` header.
2. Run `pnpm run dev` to start the development server
3. Try to login with social media
4. You will see that social login is not working. It just hangs until the timeout. If you open the console in the popup, you will see the error because there is no `projectid`. E.g. `https://secure.walletconnect.org/get-dapp-data?projectId=&referer=http%3A%2F%2Flocalhost%3A3001%2F`

### Important to mention

There is NO CSP at all. So, it is not related to the CSP.
