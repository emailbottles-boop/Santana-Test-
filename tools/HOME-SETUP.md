# Setting up the home computer, in one command

Paste this into **Git Bash** on the caretaker's computer (the one with the
scheduled task and wrangler already signed in). It clones this repository,
then hands Claude Code a precise list of what to do: deploy, re-point the
scheduled task, run it once, and check the live site. Claude stops and says so
if any step fails.

```
cd ~ && git clone https://github.com/emailbottles-boop/Santana-Test-.git santana-site && cd santana-site && (git checkout main >/dev/null 2>&1; [ -d site ] || git checkout claude/santana-site-domain-outage-4hpsib) && claude "This folder is the memorial website for Santana Turner (mahoganyjr.com and santanaturner.com), just moved here from a side branch of the WizardShit repository. Do these steps in order and stop and tell me if any step fails. 1) Read README.md, the section called 'This repository, and where it came from'. 2) Run 'npx wrangler whoami' from the api folder; if it is not signed in, run 'npx wrangler login' and wait for me. 3) From the api folder run 'bash deploy.sh'. If it fails only because the zone for santanaturner.com cannot be found, comment out the two santanaturner.com lines in api/wrangler.toml, run deploy.sh again, and tell me that santanaturner.com still has to be added to Cloudflare; change nothing else in that file. 4) Find the scheduled task on this computer that runs an autodeploy.sh from the old WizardShit clone (use: schtasks /query /v /fo LIST | findstr /i autodeploy) and change that task so it runs tools/autodeploy.sh from THIS folder instead, keeping the same schedule and the same way of launching bash. Show me the before and after. 5) Run 'bash tools/autodeploy.sh' once by hand from this folder and show me autodeploy.log. 6) Check that https://mahoganyjr.com loads with his photographs, that no 'added by' names appear anywhere on the page, and that http://mahoganyjr.com redirects to https. 7) Rules: do not run seed.sh by hand, do not run any .sql file except through deploy.sh, do not delete anything in Cloudflare or GitHub, do not touch the old WizardShit folder, do not change the admin password. When done, summarise exactly what changed."
```

Once it has run, the old branch in WizardShit can be deleted; everything is here.
