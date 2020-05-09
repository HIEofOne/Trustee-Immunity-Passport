# Trustee Deploy

Trustee Deploy is actually Dockerized along with the Trustee Directory!

## Admin:

-   SSH login via PGP key

-   "cd /opt/docker"

-   "./deploy_admin_user_add.sh" to add Admin users to Deploy (use trustee.ai e-mail address instead of Gmail address) so you can test out being a subscriber when you use OIDC with Google, for instance.

-   "./deploy_create_droplet.sh" to create first Trustee Droplet and domain records/CNames (already done).  You can check that the droplet is online at [https://traefik.d*.trustee.ai](about:blank) and you'll see the dashboard (username is admin, password is chenngropper).

-   "./deploy_update_droplets.sh"to update all Droplets with the latest Docker images

-   Go to "<https://deploy.trustee.ai>" to enter the Deploy app, click on Admin Login on upper right

-   Login as admin allows you to view all current subscribers and logs for any update/deploy failures if needed.

-   Logout

-   <https://dir.trustee.ai> is where the Directory resides and is also functioning as the Oauth2 proxy (still awaiting updates from BlueButton 2.0 to update the redirect URL so Medicare functions are not working yet).

## Subscriber:

-   Go to "<https://deploy.trustee.ai>" to enter the Deploy app, click on "Get Started"

-   Login via Google, Twitter, or GitHub

-   If no previous subscriptions will go to Start Subscription page; chose between Individual or Group subscriptions

-   Click on "Checkout .." to confirm; will forward to Stripe checkout

-   Use "4242 4242 4242 4242" as credit card number, MM/YY as any future date, and CVC as any 3 digits for the Stripe sandbox

-   Click on "Subscribe" and Trustee will begin deployment - wait...

-   Once complete, will go to home page where URL of Trustee will be found.

-   Install the AS as before...