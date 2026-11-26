# Math Lab 3D

Interactive 3D tools that make functions and trigonometry something you can **see and rotate**, instead of only read about.

🔗 **Live site:** https://math-lab-3d.fadytamerfofo123.workers.dev

## Features

- **Function graphers** – constant, linear, cubic, sine, cosine, tangent and absolute value functions, drawn in a 3D scene.
- **Quadratic lab** – roots, vertex and complex roots visualised in 3D.
- **Trig ratios** – explore sine, cosine and tangent on the unit circle.
- **Equation solver** – solve equations step by step.
- **User accounts** – sign up, log in, and edit your profile (powered by Supabase Auth).
- **Light / paper theme** support.

## Tech stack

| Part | Technology |
|------|------------|
| Frontend | Plain HTML, CSS and JavaScript (no build step) |
| 3D graphics | [three.js](https://threejs.org/) r128 |
| Authentication | [Supabase](https://supabase.com/) (`supabase-js` 2.45.4) |
| Hosting | Cloudflare Workers |

## Project structure

```
math-lab-site/
├── index.html            # Home page
├── about.html            # About page
├── login.html            # Log in / create account
├── account.html          # Profile page
├── constant.html  linear.html  cubic.html
├── sine.html  cosine.html  tangent.html  absolute.html
├── quadratic.html  quadratic.js
├── trig.html  trig.js
├── solver.html  solver.js
├── fn-engine.js          # Shared function-graphing engine
├── functions-data.js     # Function definitions/data
├── theme.js              # Theme + user-session helper
├── supabase-config.js    # Supabase URL + publishable key
├── style.css  style-paper.css
```

## Run locally

No installation needed. Just serve the folder with any static server:

```bash
cd math-lab-site

# Option 1: Python
python3 -m http.server 8000

# Option 2: Node
npx serve .
```

Then open http://localhost:8000.

## Supabase setup

1. Create a project at [supabase.com](https://supabase.com).
2. Go to **Project Settings → API** and copy your **Project URL** and **publishable (anon) key**.
3. Put them in `supabase-config.js`:

   ```js
   window.MATHLAB_SUPABASE = {
     url: 'https://YOUR-PROJECT.supabase.co',
     anonKey: 'sb_publishable_...'
   };
   ```

4. In **Authentication → Providers → Email**, make sure Email is enabled.
5. In **Authentication → URL Configuration**, set the **Site URL** to your live site URL.

> ⚠️ The publishable key is safe to be public. **Never** commit the `service_role` or `secret` key. If you add database tables, enable **Row Level Security** on them.

## Deploy

The site is a static site and is deployed on Cloudflare Workers. Any static host (Cloudflare Pages, GitHub Pages, Netlify, Vercel) will also work: just upload the contents of `math-lab-site/`.

## Contributing

Issues and pull requests are welcome. Please open an issue first to discuss big changes.

## License

Add a license of your choice (for example [MIT](https://choosealicense.com/licenses/mit/)
