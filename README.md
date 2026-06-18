# Welcome to your Lovable project

## Project info

**URL**: https://lovable.dev/projects/1b632ea3-53b8-45b4-a7e6-fb29d8481149

## How can I edit this code?

There are several ways of editing your application.

**Use Lovable**

Simply visit the [Lovable Project](https://lovable.dev/projects/1b632ea3-53b8-45b4-a7e6-fb29d8481149) and start prompting.

Changes made via Lovable will be committed automatically to this repo.

**Use your preferred IDE**

If you want to work locally using your own IDE, you can clone this repo and push changes. Pushed changes will also be reflected in Lovable.

The only requirement is having Node.js & npm installed - [install with nvm](https://github.com/nvm-sh/nvm#installing-and-updating)

Follow these steps:

```sh
# Step 1: Clone the repository using the project's Git URL.
git clone <YOUR_GIT_URL>

# Step 2: Navigate to the project directory.
cd <YOUR_PROJECT_NAME>

# Step 3: Install the necessary dependencies.
npm i

# Step 4: Start the development server with auto-reloading and an instant preview.
npm run dev
```

**Edit a file directly in GitHub**

- Navigate to the desired file(s).
- Click the "Edit" button (pencil icon) at the top right of the file view.
- Make your changes and commit the changes.

**Use GitHub Codespaces**

- Navigate to the main page of your repository.
- Click on the "Code" button (green button) near the top right.
- Select the "Codespaces" tab.
- Click on "New codespace" to launch a new Codespace environment.
- Edit files directly within the Codespace and commit and push your changes once you're done.

## What technologies are used for this project?

This project is built with .

- Vite
- TypeScript
- React
- shadcn-ui
- Tailwind CSS

## How can I deploy this project?

Simply open [Lovable](https://lovable.dev/projects/1b632ea3-53b8-45b4-a7e6-fb29d8481149) and click on Share -> Publish.

## I want to use a custom domain - is that possible?

We don't support custom domains (yet). If you want to deploy your project under your own domain then we recommend using Netlify. Visit our docs for more details: [Custom domains](https://docs.lovable.dev/tips-tricks/custom-domain/)




# Ready Player Me Avatar Integration Guide

## Avatar Setup Instructions

1. Download your Ready Player Me avatar with Oculus VSEMS morph targets by using this URL:
   ```
   https://readyplayer.me/avatar?morphTargets=OculusVSEMS
   ```

2. Download the GLB file and rename it to `avatar_with_morphs.glb`

3. Place the GLB file in this directory (`public/assets/avatars/`)

4. The application will automatically load the avatar and enable lip-sync functionality

## Morph Target Requirements

Your Ready Player Me avatar GLB file should contain the following morph targets for proper lip-sync:

- Oculus VSEMS morph targets (viseme_A, viseme_B, etc.)
- Head and teeth morph targets
- Mouth-related morph targets (mouthOpen, jawOpen, etc.)

## Troubleshooting

If the avatar is not speaking properly, check the following:

1. Verify that your GLB file contains the required morph targets
2. Check the browser console for any errors related to loading the model
3. Ensure that audio playback is working correctly
4. Try a different Ready Player Me avatar if the current one doesn't have the required morph targets

## Advanced Customization

To customize the lip-sync behavior, you can modify the `MOUTH_SHAPE_MAPPING` in the `Avatar3D.tsx` component.