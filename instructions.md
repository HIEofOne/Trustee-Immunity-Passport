Install Ubuntu Server 18.04 on DigitalOcean

-   Install Docker <https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04>

-   Install Docker Compose <https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04>

-   Run 10 Trustee containers on  4GB RAM/80GB SSD droplet ($20/month)

-   Install traefik load balancer to direct subdomain to each patient container.

With registration - a unique subdomain (as0*) is created

-   Add wildcard (*) subdomain to CName

-   Create directory (as*)  named subdomain

-   Inside directory (as*)  create docker-compose.yml template that defines Patient container

Trustee container consists of

-   Nginx proxy-pass to allow subdomain to have a root (/) pointing to AS container and /nosh pointing to pNOSH container

-   AS container is: a mariadb container + nginx container + php/laravel container with hieofone-as code

-   pNOSH container is: a mariadb container + nginx container + php/laravel container with nosh2 code

-   Docker secrets prevents HIE of One from being able to access each mariadb container instance

-   Backup container

-   SyncThing container to connect to other devices outside of network for off-site backup

pNOSH mariadb database will have data-at-rest encryption enabled

<https://mariadb.com/kb/en/library/data-at-rest-encryption/>

Docker secrets will protect database user and password, file key management for database encryption as well as MailGun domain and secret.

A DigtialOcean droplet snapshot of "trustee-docker-snapshot" named "trustee-docker-snapshot-base" is used to deploy multiple droplets once 10 containers

Trustee Deploy

Trustee Deploy is actually Dockerized along with the Trustee Directory!

Admin:

-   SSH login via PGP key

-   "cd /opt/docker"

-   "./deploy_admin_user_add.sh" to add Admin users to Deploy (use trustee.ai e-mail address instead of Gmail address) so you can test out being a subscriber when you use OIDC with Google, for instance.

-   "./deploy_create_droplet.sh" to create first Trustee Droplet and domain records/CNames (already done).  You can check that the droplet is online at [https://traefik.d*.trustee.ai](about:blank) and you'll see the dashboard (username is admin, password is chenngropper).

-   "./deploy_update_droplets.sh"to update all Droplets with the latest Docker images

-   Go to "<https://deploy.trustee.ai>" to enter the Deploy app, click on Admin Login on upper right

-   Login as admin allows you to view all current subscribers and logs for any update/deploy failures if needed.

-   Logout

-   <https://dir.trustee.ai> is where the Directory resides and is also functioning as the Oauth2 proxy (still awaiting updates from BlueButton 2.0 to update the redirect URL so Medicare functions are not working yet).

Subscriber:

-   Go to "<https://deploy.trustee.ai>" to enter the Deploy app, click on "Get Started"

-   Login via Google, Twitter, or GitHub

-   If no previous subscriptions will go to Start Subscription page; chose between Individual or Group subscriptions

-   Click on "Checkout .." to confirm; will forward to Stripe checkout

-   Use "4242 4242 4242 4242" as credit card number, MM/YY as any future date, and CVC as any 3 digits for the Stripe sandbox

-   Click on "Subscribe" and Trustee will begin deployment - wait...

-   Once complete, will go to home page where URL of Trustee will be found.

-   Install the AS as before...

* * * * *

Testing Notes - Jan 29

-   Sign-in with GitHub did not work: "Tunnel d40f0dc3.ngrok.io not found"

-   Can you reduce the scope of data accessible from Twitter? - the list looks scary

-   Set up

-   An email address was shown on the Stripe form. That's good. Why am I being  asked for an email on the Set up form? If these can be different, then we need to explain. Otherwise, people will get confused.

-   Why am I being asked to set a password? I just signed-in with Twitter? I also identified myself by my CC number. Is this a third identity? We need to discuss.

-   Photo

-   On the mac, take a picture buttons under the live camera view are confusing. Should be only Snap and Cancel. Once there's a snap, then maybe Save, Retake, and Cancel

-   Also, the Upload choice is below the "fold" and I did not know it was there.

-   We need to discuss the new landing page. Maybe we can skip it somehow.

-   The My Resource Servers page is confusing. There should be two very prominent links or buttons: NOSH for Adrian Gropper and Directory: Trustee All the other info is secondary.

-   "You are looged for the first time into Trustee via Twitter. If you believe this is an error, please contact Twitter." should be changed. Do not suggest to contact Twitter. Use a link  to the Directory or somewhere. Also, fix "logged".

-   The Deploy page should tell people you can close this page after the email goes out.

Discussion

You opened up a nice Pandora's Box by rethinking the Deploy experience. I'm thinking we need to double-down on what you started, including the jargon, like resources.

1.  Pick a Directory for hosting and support (Trustee? HIE of One? [dir.hieofone.com](http://dir.hieofone.com/)) and review their Privacy Policy. I suggest we start with trustee.health to start. This protects our trademark and belongs to the responsible corporate entity that's taking your money. The other reason to do this is because we want to appeal to future directory operators from the start.

2.  Deploy -  sign-in and Stripe are nice. The email link should take people to the Directory with a random six-digit pseudonym. People can later change the pseudonym to a nickname or disappear from the Directory altogether. The random six-digit pseudonym should be their subdomain. We'll worry about other directories later.

3.  Subscribe with Credit Card

4.  Fill out the absolute minimum of information:

1.  verify your email as your identity

2.  change the random pseudonym to a nickname

3.  uncheck the box that makes you appear in the named Directory (with logo for marketing reasons :-)

4.  add a SMS number for alternate notice and account recovery

5.  perform a verification loop for either the email and/or SMS (not strict, not  urgent)

6.  No password. Send users a magic link. Anyone without access to their email or SMS should use uPort via QR code.

7.  Send out a monthly email with the Directory and NOSH links and link to stop the credit card and service with a (binary) export of their database.

6.  Do the optional photo

7.  Take user _directly_ to their NOSH. No jargon. No AS.

1.  We should discuss adding to NOSH (and to the various emails) a very prominent link that can be used to either add a resource, or, with a bit more effort, a credential, directory, etc...

2.  We might display connected resources (Weil-Cornell,  Medicare, Trustee Directory) very prominent on the NOSH timeline page.

My goals are:

-   Eliminate all passwords

-   Promote our directory marketing partners

-   Avoid discussing the AS as such as long as possible.