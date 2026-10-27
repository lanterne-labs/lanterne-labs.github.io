# tartuffe.me — the vote app

The static build of the vote pages of tartuffe.me (tartuffe-vote/2), served
from this repository's pages at https://tartuffeme.github.io/.

The vote page talks to no server of the site: it reads the public data
mirror (https://github.com/tartuffeme/vote-data) and posts registrations and
ballots through public Nostr relays, so that no one, the site included, sees
a voter's address with their ballot. Serving the app from here, rather than
from the site, is what lets anyone check that the code a voter runs is the
code that was published.

The build is produced from the site's source; its hash is named in the
vote's setup entry so that auditors can rebuild and compare it.
