# How (not) to do bad things with AutoPkg

Slides, links, and resources from my MacAD UK 2016 conference session. This is a simple outline for now, but I plan to develop it into a full article soon.

## The Bad Things

1. Deleting things
2. Overwriting things
3. Fun with processors
4. Naming curiosities
5. Surprise variables
6. Surreptitious scripts
7. Trust without verification
8. Plain boring typos
9. Technical confusion
10. Find/replace flubs
11. Loose licensing
12. Software regression
13. Side-loading and hijacking
14. Administrative fatigue
15. Over-automation

## Tips For Avoiding the Bad Things

- __Don't run AutoPkg as root__
    - Permissions errors are often an indication of a deeper issue
    - Troubleshoot the deeper issue, rather than working around it
- __Read and write recipes__
    - Start small: Make overrides, copy existing recipes
    - Recipe Robot can be a good learning tool
    - Use a text editor with syntax highlighting and autofill
    - Run recipes locally before pushing your changes to GitHub
    - Use trusted sources only to download the software
    - Reach out to community for help
- __Isolate your AutoPkg Mac__
    - Run in a VM
    - Or run on a dedicated Mac
    - Don't run on the same box as your Munki repo or Casper distribution point
- __Verify code signatures__
    - Use trusted sources to download software
    - Investigate code signature verification errors
    - Contact developers who code sign improperly
- __Pay attention to changes__
    - The point of automation is not to eliminate time spent, but rather to reduce both time and errors
    - Read Git commit history
    - Don't have AutoPkgr automatically update repos
    - Use AutoPkgr as a daily reminder to check commits, review/apply manually
    - Put your AutoPkg repos in Git (They probably already are)
    - Put your Munki repo in Git
    - Put your AutoPkg recipe runner script in Git
    - Don't check the "Update repos" box in AutoPkgr
    - Trust recipe authors, but verify the changes they make
    - Take time to understand processors
    - Test changes in a VM
- __Use overrides liberally__
    - Rarely, if ever, run Munki/JSS recipes directly.
    - Instead, create an override and customize the variables for your organization.
    - Use AppStoreApp overrides, but only backed by VPP purchases.
- __Mass edit with caution__
    - Don't change identifiers after recipe publication unless the changes are significant enough to warrant a "new" recipe.
    - When making bulk changes to recipes, test before committing.
    - Use GitHub app or another diff tool to see the changes visually.
    - When using Find/Replace, consider the context…
- __Inspect packages before deploying__
    - Suspicious Package Quick Look plugin, or Pacifist.
    - Check the payload. Check the scripts.
    - Test in a VM.
- __Don't deploy directly to production__
    - Think of yourself as the QA inspector. What do you need in order to certify that your deployment will be problem-free?
    - Test locally first, then in small batches.
    - Use shards, trusted tester groups.
    - Use Self Service, Managed Software Center.
    - Standardize collection of feedback from testers.
- __Documentation, of course__
    - Write it all down.
    - Have somebody else read it. (Maybe Kitzy.)
    - Keep it up to date.
- __The principle of least privilege__
    - "...giving a user account only those privileges which are essential to that user's work."
    - When setting up JSS accounts.
    - When setting up Munki repos.
    - When configuring SSH/VNC access to admin Macs.
    - When configuring Amazon Web Services.
    - When configuring email service accounts.

## Links Mentioned During My Session

- [Linde Group](http://lindegroup.com/)
- [AutoPkg](http://autopkg.github.io/autopkg)
- [PathDeleter processor](https://github.com/autopkg/autopkg/wiki/Processor-PathDeleter)
- [Copier processor](https://github.com/autopkg/autopkg/wiki/Processor-Copier)
- [MozillaURLProvider processor](https://github.com/autopkg/recipes/blob/master/Mozilla/MozillaURLProvider.py)
- [CasperCheck](https://github.com/rtrouton/CasperCheck)
- [AutoPkgr](http://lindegroup.com/autopkgr)
- [JSSImporter](https://github.com/sheagcraig/jssimporter)
- [jss-recipes](https://github.com/autopkg/jss-recipes)
- [AppStoreApp recipe overrides](https://github.com/autopkg/nmcspadden-recipes#appstoreapp-recipe)
- [Radek at VulnSec: "There's a lot of vulnerable OS X applications out there"](https://vulnsec.com/2016/osx-apps-vulnerabilities/)
- [Simone Margaritelli: "OSX Mass Pwning using BetterCap and the Sparkle Updater Vulnerability"](https://www.evilsocket.net/2016/01/30/osx-mass-pwning-using-bettercap-and-the-sparkle-updater-vulnerability/)
- [Thomas Reed: "Java now installing adware"](http://www.thesafemac.com/java-now-installing-adware/)
- [Thomas Reed: "Has MacUpdate fallen to the adware plague?"](http://www.thesafemac.com/has-macupdate-fallen-to-the-adware-plague/)
- [The Register: "SourceForge sorry for adware, promises only opt-in in future"](http://www.theregister.co.uk/2015/06/03/sourceforge_to_offer_only_optin_adware_after_gimp_grump/)
- [Auto Update Magic](https://github.com/homebysix/auto-update-magic)
- [Recipe Robot](https://github.com/homebysix/recipe-robot)
- [Munki With Git](https://github.com/munki/munki/wiki/Munki-With-Git)
- [Allister Banks: "Introduction to Git-Fat for Munki"](https://www.afp548.com/2014/11/24/introduction-to-git-fat-for-munki/) ([and part 2](https://www.afp548.com/2014/12/01/git-fat-intro-part-two-setup-and-migration/))
- [Recipe Runner](https://github.com/homebysix/recipe-runner)
- [Kaleidoscope](http://www.kaleidoscopeapp.com/)
- [Suspicious Package](http://www.mothersruin.com/software/SuspiciousPackage/)
- [Rich Trouton and Vanessa White: "Take Vacations using this One Weird Trick – DOCUMENTATION!"](https://youtu.be/jgsNxvlfWW8?list=PLRUboZUQxbyVydhdMcxGGfEaZc2sFdQk8) ([PDF slides](http://macadmins.psu.edu/wp-content/uploads/sites/24696/2015/07/psumac2015-60-vwhite_rtrouton_documentation_talk.pdf))
