## Deploying to Github pages with Hugo
1. Create a repository with the name <username>.github.io to deploy to
1a) inside the hugo project, add a public folder and initialize a submodule to
point to the new github repository
```git submodule add -b main git@github.com:kalinkochnev/kalinkochnev.github.io.git public```

2. Make sure you already have a repo with the site
3. Change the custom domain what you wish in Settings > Pages

Go to your DNS provider
4. Add an A record for the Apex domain <domain name>.com
    Hostname: kalinkochnev.com
    Type: A
    TTL: 1 hour
    Data: (find the github pages domains here https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153


5. Add a CNAME record for the www.<domain name>.com
    Hostname: www.kalinkochnev.com
    Type: CNAME
    TTL: 1 hour
    Data: https://kalinkochnev.github.io

6. Build the hugo site with `hugo`

7. cd into thepublic folder and commit all files to the deployment repo
