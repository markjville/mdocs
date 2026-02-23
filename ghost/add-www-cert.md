# Add “www” cert to site with an existing non-www cert

## Determine your secondary URL
ghost config url https://my-second-domain.com

## Get Ghost-CLI to generate an SSL setup for you:
ghost setup nginx ssl

## Change your config back to your canonical domain
ghost config url https://my-canonical-domain.com

## Edit the nginx config files for your second domain to redirect to your canonical domain. In both files replace the content of the first location block with:
return 301 https://my-canonical-domain.com$request_uri;

## Get nginx to verify your config
sudo nginx -t

## Reload nginx with your new config
sudo nginx -s reload
