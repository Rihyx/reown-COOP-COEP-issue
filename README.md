# Reown AppKit Example with COOP and COEP headers which breaks the social login

This is a Next.js project  with Reown AppKit generate by running `npx @reown/appkit-cli`. The only change is the `next.config.ts` file.

## How reproduce headers issue

1. Run `npm install` to install dependencies
2. Run the app by `npm run dev`
3. Try to login with social media, everything works fine.
4. Stop the app by `Ctrl + C`
5. Go to `next.config.ts` and uncomment the `Cross-Origin-Embedder-Policy` header.
6. Run `npm run dev` to start the development server
7. Try to login with social media
8. You will see that social login is not working. It just hangs until the timeout. If you open the console in the popup, you will see the error because there is no `projectid`. E.g. `https://secure.walletconnect.org/get-dapp-data?projectId=&referer=http%3A%2F%2Flocalhost%3A3001%2F`

### Important to mention

There is NO CSP at all. So, it is not related to the CSP.

## Docs

- [Cross-Origin-Opener-Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cross-Origin-Opener-Policy)
- [Cross-Origin-Embedder-Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cross-Origin-Embedder-Policy)
- [Cross-Origin-Resource-Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cross-Origin-Resource-Policy)
- [Load cross-origin resources without CORP headers using COEP: credentialless](https://developer.chrome.com/blog/coep-credentialless-origin-trial#why_we_need_cross-origin_isolation)
- [Secure popup interactions with restrict-properties](https://developer.chrome.com/blog/coop-restrict-properties)
