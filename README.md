# The tartuffe.me vote app

**An anonymous online pre-poll for the 2027 French presidential election, open to every French adult with a valid passport.**

This repository is the published build of the vote pages of [tartuffe.me](https://tartuffe.me). GitHub Pages serves it at **https://lanterne-labs.github.io**. The site's own vote pages send voters here.

> Vote: [tartuffe.me/election/presidentielle-2027](https://tartuffe.me/election/presidentielle-2027)

---

## Why the app lives here, and not on the site

The vote page talks to no server of tartuffe.me:

- **Eligibility** is proved on the voter's phone with [ZKPassport](https://zkpassport.id). The phone proves in zero knowledge "French, 18 or older" from the passport's chip. No name, number or photo leaves the phone.
- **Ballots** are encrypted and proved in the browser, then posted through public Nostr relays. Nobody, the site included, can link a voter's address to their ballot.
- **Results** are read from the public data mirror, [lanterne-labs/vote-data](https://github.com/lanterne-labs/vote-data). Every file there is signed and anchored in Bitcoin.

Serving the app from a public repository lets anyone check that the code a voter runs is the code that was published. Each commit here is one build, named after the commit of the site's source it came from (`build <commit>`). The vote's setup entry names the build's hash, so an auditor can rebuild it and compare.

## What is in here

| Path | What |
|---|---|
| `_app/` | the compiled app (SvelteKit, static) |
| `srs/` | the public parameters the browser proves with (Barretenberg's SRS) |
| `vote/candidates/` | the candidates' cards (name, photo, honesty score), fetched at build time |
| `coi-sw.js` | the service worker that enables the cross-origin isolation the prover needs |

Every file is overwritten at each build. Do not edit this repository by hand. The `README.md` is the only file kept.

## Technical documentation

- **The protocol, the cryptography and the audit**: [lanterne-labs/isoloir](https://github.com/lanterne-labs/isoloir), with the normative spec in [SPEC.md](https://github.com/lanterne-labs/isoloir/blob/main/SPEC.md) and how a vote works, in French, in [docs/comment-ca-marche.md](https://github.com/lanterne-labs/isoloir/blob/main/docs/comment-ca-marche.md).
- **The browser library** the app runs: [`js/`](https://github.com/lanterne-labs/isoloir/tree/main/js) in isoloir.
- **The data a vote produces**: [lanterne-labs/vote-data](https://github.com/lanterne-labs/vote-data).
- **For voters**: [how it works](https://tartuffe.me/election/presidentielle-2027/fonctionnement) and the [privacy page](https://tartuffe.me/about/privacy) on tartuffe.me.

## Contact

lanternelabs@proton.me · [tartuffe.me/contact](https://tartuffe.me/contact)
