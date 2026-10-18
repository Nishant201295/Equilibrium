# Equilibrium on Vercel

Files
- public/        the website (index.html is the live app, replay.html is the day replay)
- api/upstox.js  the Upstox proxy (a Vercel serverless function)
- vercel.json    settings: serves public/, gives the function 30 seconds, no caching of the app files

Deploy, way 1: GitHub (no command line)
1. Create a new PRIVATE repository on github.com.
2. Upload everything in this folder (keep the folders), commit.
3. On vercel.com choose Add New > Project, import that repository, leave every setting as it is, press Deploy.
4. Project > Settings > Environment Variables: add UPSTOX_TOKEN (your analytics token). Optional: APP_CODE (any code you choose).
5. Deployments > the latest one > Redeploy, so the variables take effect.

Deploy, way 2: command line
1. Install Node.js, open a terminal in this folder.
2. npx vercel login
3. npx vercel --prod
4. npx vercel env add UPSTOX_TOKEN production   (paste the token when asked)
5. npx vercel --prod   (again, so the variable takes effect)

After it is live
- Open the site, then Setup > Test connection. Every line should be a green tick, including "Day log works".
- If Vercel shows a login page, open Settings > Deployment Protection and turn Vercel Authentication off for production.
- Never put the token in the files or the repository. Keep it in Environment Variables only.
