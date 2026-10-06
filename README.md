# LeaveFlow — Firebase + Vercel

## 1. Firebase

Create a Firebase Web App and paste its config into `index.html`.

Firebase Console:
Project settings → Your apps → Web app → SDK setup/config

Enable:
- Authentication → Sign-in method → Email/Password
- Firestore Database

Use the default Firestore database.

Deploy `firestore.rules` from Firebase Console → Firestore Database → Rules.

## 2. First manager

New registrations are always `employee`.

After registering the first manager, open:
Firestore → users → USER_UID

Change:
role = "manager"

Do not allow public users to choose the manager role.

## 3. Vercel

Upload this folder to GitHub and import the repository into Vercel.

Framework preset: Other
Build command: leave empty
Output directory: leave empty
Install command: leave empty

Because this is a static HTML app, Vercel can serve it directly.

## 4. Firebase Authorized Domains

Firebase Console → Authentication → Settings → Authorized domains

Add your Vercel domain, for example:
your-project.vercel.app

## 5. Important

The Firebase Web config is not a password. Firestore Security Rules are what protect your data.

For a production HR system, move manager approval + balance deduction into a trusted Cloud Function/Admin backend. The included client transaction is suitable for an MVP but should not be treated as the final HR-grade authorization boundary.
