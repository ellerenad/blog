# Deployment status

[![Netlify Status](https://api.netlify.com/api/v1/badges/f592ae9d-eb02-458a-8a80-9d04be23acee/deploy-status)](https://app.netlify.com/sites/modest-darwin-f6086e/deploys)

# Description
This is the repository for my blog, [ienjoysoftware.dev](https://ienjoysoftware.dev)

## Run

### Prerequisites
- Docker

### Instructions

- Clone the repository
- Run the below:

```bash
export JEKYLL_VERSION=3.8
sudo docker run --rm \
-p 4000:4000 \
--volume="$(pwd):/srv/jekyll" \
-it jekyll/jekyll:$JEKYLL_VERSION \
jekyll serve --livereload --draft
```

## Credits

This blog was created with the Jekyll theme [Centrarim](https://github.com/bencentra/centrarium) by [Ben Centra](https://github.com/bencentra)
