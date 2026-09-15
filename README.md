<img src="assets/header.svg" width="100%" alt="Sofiya · Mathematical Foundation of Data Science · University of Vienna — why models work, how systems break, and how to prove it" />

## 🕵️ paranoid

<a href="https://github.com/kulchankas/paranoid"><img src="https://img.shields.io/badge/repo-kulchankas%2Fparanoid-3fb950?style=flat-square&labelColor=161b22&logo=github" alt="kulchankas/paranoid on GitHub" /></a>
<img src="https://img.shields.io/badge/runs%20in-Claude%20Code%20·%20Codex%20·%20Cursor-8957e5?style=flat-square&labelColor=161b22" alt="Runs in Claude Code, Codex and Cursor" />
<img src="https://img.shields.io/badge/proofs-localhost%20only-58a6ff?style=flat-square&labelColor=161b22" alt="Localhost-only proofs" />
<img src="https://img.shields.io/badge/license-MIT-8b949e?style=flat-square&labelColor=161b22" alt="MIT license" />

**Your app is guilty until proven secure.** `paranoid` is an agent skill for Claude Code, Codex and Cursor. Its core, **`/hack-me`**, breaks into your *own* running app on localhost the way an attacker would: it finds a hole, proves it with a real request, patches the root cause, and re-verifies the exploit now fails.

<a href="https://github.com/kulchankas/paranoid"><img src="assets/paranoid.svg" width="100%" alt="/hack-me against a running app on localhost: it finds four real vulnerabilities — IDOR, missing admin auth, SQL injection, mass assignment — proves each with a live request, patches it, and re-verifies that the exploit now fails" /></a>

Pointed at a small invoicing API it was told nothing about, `/hack-me` found four real bugs by probing, proved each with a live request, fixed them, and confirmed legitimate traffic still works:

| # | Found by probing the API | Class | After patch |
|---|---|---|:--:|
| 1 | Any user reads any invoice | IDOR / broken object auth | `404` |
| 2 | `/admin/users` open to anyone logged in | broken function auth | `403` |
| 3 | `/search?email=` dumps password hashes | SQL injection | `[]` |
| 4 | `/profile` accepts `is_admin` | mass assignment → priv-esc | `400` |

I built it benchmark-first: a reproducible harness showed that *advising* a capable model to "write secure code" adds nothing on isolated functions, because real bugs live in the wiring of a whole running app. So paranoid stops advising and starts attacking. Authorized, defensive, localhost-only.

```bash
npx skills add kulchankas/paranoid/skills/paranoid
```

<br>

## Interests

<img src="assets/interests.svg" width="100%" alt="Interests: mathematics (analysis, linear algebra, probability and statistics), security (offensive security, network security, Active Directory), machine learning (interpretability, adversarial ML, probabilistic ML)" />

<img src="https://skillicons.dev/icons?i=python,r,julia,linux,kali" alt="Python, R, Julia, Linux, Kali Linux" />

<sub>English · Russian · Belarusian · Polish &nbsp;·&nbsp; <a href="mailto:kulchankas@gmail.com">kulchankas@gmail.com</a></sub>
