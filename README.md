
# ToolVerse Auto Deploy Bundle

Prepared for GitHub user: naveedqadri73-lab
Primary domain: toolverse.pk
API subdomain: api.toolverse.pk

## What is inside
- `toolverse-frontend/` - Static frontend (index.html, CNAME, sitemap, robots).
- `toolverse-backend/` - Node.js Express backend (server.js) + package.json + render.yaml.
- `.github/workflows/deploy_frontend.yml` - GitHub Actions workflow for deploying frontend to Pages.
- `README.md` - This instructions file.

## Quick start - Frontend (GitHub Pages)

1. Create repository `toolverse-frontend` at GitHub under your account `naveedqadri73-lab`.
2. Copy the contents of `toolverse-frontend/` into the repo root and push to `main`.
3. Add the workflow file `.github/workflows/deploy_frontend.yml` (already included at repo root in this bundle).
4. GitHub Actions will publish the `toolverse-frontend` directory to Pages when you push to `main`.
5. Ensure `CNAME` contains `toolverse.pk`. In your DNS provider, add A records for GitHub Pages:
   A 185.199.108.153
   A 185.199.109.153
   A 185.199.110.153
   A 185.199.111.153
   And optionally CNAME for www -> your GitHub pages domain.

## Quick start - Backend (Render + api.toolverse.pk)

1. Create repository `toolverse-backend` at GitHub and push the `toolverse-backend` folder contents.
2. Log in to Render and create a new Web Service connected to the `toolverse-backend` repo. Use the provided `render.yaml` or manual configuration:
   - Environment: Node
   - Build command: npm install
   - Start command: node server.js
3. After service is deployed, you'll have a Render domain like `toolverse-backend.onrender.com`.
4. In your DNS, add CNAME record:
   - Host: api
   - Value: toolverse-backend.onrender.com
5. In Render, add custom domain `api.toolverse.pk` to the service and follow verification steps. Render will provision TLS automatically once verified.

## Notes
- The frontend can call `https://api.toolverse.pk/api/convert` for cached currency conversion. Update client code if you switch from public API.
- Replace GA ID `G-XXXXXXX` in index.html with your GA4 ID.
- For automatic backend deploy via GitHub Actions/Render, Render can deploy from repo on push by default.

If you'd like, I can also create the two GitHub repositories with the files pre-filled (I'll provide exact git commands and files); you'll only need to run them locally and push. Or I can generate a one-click Render deploy button for the backend.
