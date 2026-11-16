# LocalDir – Android app (APK) project

This is a ready-to-build Android app that wraps the LocalDir website (`app/src/main/assets/index.html`).

## Get the APK (no Android Studio needed)
1. Create a new repository on github.com and upload everything in this folder (keep the hidden `.github` folder).
2. Open the **Actions** tab, choose **Build APK**, and wait for it to finish (about 3–5 minutes). It also runs automatically on every push.
3. Open the finished run, download the **LocalDir-APK** artifact, unzip it, and install `app-debug.apk` on your phone (allow "install unknown apps" when asked).

## Or build with Android Studio
Open this folder in Android Studio, let it sync, then **Build > Build APK(s)**.

## Updating the app
Replace `index.html` / `privacy.html` in `app/src/main/assets/` with newer versions and push again.

## Email verification setup (EmailJS, free plan)
New provider accounts must confirm their email with a 6-digit code. The site sends it through EmailJS, so you need to add your keys once:
1. Sign up at emailjs.com. Under **Email Services**, add a service (for example Gmail) and copy its **Service ID**.
2. Under **Email Templates**, create a template. Subject: `Your {{app_name}} verification code`. Body: `Hi {{to_name}}, your verification code is {{code}}. It expires in 10 minutes.` Set the **To Email** field to `{{to_email}}`. Copy the **Template ID**.
3. Under **Account > General**, copy your **Public Key**.
4. In `app/src/main/assets/index.html`, find `EMAILJS:{SERVICE_ID:"",TEMPLATE_ID:"",PUBLIC_KEY:""}` near the top of the script and paste the three values in.
Until this is filled in, sign-up shows "Email verification is not set up yet".
Note: because the site runs entirely in the browser, this confirms the email works but is not tamper-proof. Fully secure verification needs a server.
