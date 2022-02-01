# Next.js for Drupal on Lando

Create this based on https://next-drupal.org/ to see how this works and how to configure in Lando.

## Setup

### Install Drupal

1. git clone git@github.com:hkirsman/nextjs_drupal_demo.git
2. cd nextjs_drupal_demo
3. lando start
4. lando composer install
5. lando drush si --existing-config  -y

### Generate keys

1. Visit https://next-drupal-backend.lndo.site/admin/config/people/simple_oauth
2. Click Generate keys to generate encryption keys for tokens
3. Fill in Directory for the keys - ../keys
4. Click Generate.

### Create User

Add a new user at `https://next-drupal-backend.lndo.site/admin/people/create` and assign it the "Next.js Site".

### Create Consumer

1. Visit https://next-drupal-backend.lndo.site/admin/config/services/consumer/add
2. Fill in the following values:
Label: `Next.js site`
User: `Select the user we created`
Secret: `Your secret`
Scopes: `Select the "Next.js Site" role`
3. Click Save

### Connect Drupal

1. Open `nextjs_drupal_basic_starter/.env.local`
2. Retrieve DRUPAL_CLIENT_ID and DRUPAL_CLIENT_SECRET from
https://next-drupal-backend.lndo.site/admin/config/services/consumer
DRUPAL_CLIENT_ID is the consumer UUID created in the last section.
DRUPAL_CLIENT_SECRET is the "New Secret" field of the consumer created.

### Start Development Server

To start the Next.js development server, run `lando npm run dev`.
This starts the development server on `http://next-drupal-frontend.lndo.site/`.

Visit http://next-drupal-frontend.lndo.site/ to view the site.
