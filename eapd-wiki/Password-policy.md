Passwords used in eAPD are checked for a minimum strength using [zxcvbn](https://github.com/dropbox/zxcvbn).  zxcvbn uses algorithmic complexity checks along with comparisons to common or widely-compromised passwords to compute a strength score.  eAPD requires a score of 3 or higher, which zxcvbn describes as "safely unguessable: moderate protection from offline slow-hash scenario. (guesses < 10^10)".

In addition, eAPD adopts the following policies:

- Passwords must be case sensitive
- Passwords may contain any combination of any characters, provided it satisfies the complexity requirement.  The [NIST 800-63 FAQ](https://pages.nist.gov/800-63-FAQ/#q-b6) explains why we should not impose character composition requirements on passwords.
- The eAPD app will allow users to view their password to confirm they've typed what they intended.
- CMS will require users to change their passwords if there is evidence that their accounts or the eAPD database have been compromised.  CMS will not otherwise require periodic password changes.