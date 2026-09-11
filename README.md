# Muhaidib Connect — iOS Wrapper (Unsigned Build)

This wraps your live site (`https://muhaidib-connect-flow.base44.app`) in a
native iOS shell using Capacitor, and builds an **unsigned** `.ipa` for free
using GitHub Actions — no Mac, no Apple Developer account needed for this step.

The unsigned `.ipa` this produces is meant to be signed afterwards by a
sideloading/signing tool on your iPhone (the app you referred to as
"متجر بلس"). It is NOT ready to submit to the App Store as-is.

## Step-by-step

1. **Create a free GitHub account** at https://github.com if you don't have one.

2. **Create a new repository** (e.g. `muhaidib-ios-app`), set it to **Private**.

3. **Upload these files** to that repo, keeping the folder structure:
   - `package.json`
   - `capacitor.config.json`
   - `www/index.html`
   - `.github/workflows/build-ios.yml`

   Easiest way: on the repo page, click "Add file" → "Upload files", drag
   the whole folder in, and commit.

4. **Run the build**:
   - Go to the **Actions** tab of your repo.
   - Click **"Build Unsigned iOS IPA"** in the left sidebar.
   - Click **"Run workflow"** → **"Run workflow"** (green button).
   - Wait 5–10 minutes for it to finish (green checkmark = success).

5. **Download the .ipa**:
   - Click into the finished run.
   - Scroll down to **"Artifacts"**.
   - Download `MuhaidibConnect-unsigned-ipa` — it's a zip containing your
     `.ipa` file.

6. **Sign it on your iPhone**:
   - Get the `.ipa` onto your phone (AirDrop, iCloud Drive, a file host —
     anything that gives you a link or lets you open it on-device).
   - Open it with your signing app and let it sign + install using your
     Apple ID.

## Notes

- GitHub Actions gives you free macOS build minutes each month (limited but
  enough for occasional builds like this).
- If the build fails, the most common cause is a Capacitor/Xcode version
  mismatch — paste the error log and it can be diagnosed.
- Any changes you make on the live Base44 site show up automatically next
  time you open the app, since it just loads the live URL — you only need
  to rebuild if you change the native wrapper itself (icon, name, etc).
