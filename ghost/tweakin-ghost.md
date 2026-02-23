# Notes on tweaking ghost: #

## To remove the social media links: ##
1. Depends on Theme, but on Edge-master, go to `/var/www/ghost/content/themes/Edge-master/partials/header.hbs`
2. Delete the social media links at `<div> `to `</div>`
3. `Restart ghost`
