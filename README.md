## NativeWind React Native Expo Template (Arch Linux Friendly)

This repo is a minimal starter for building React Native apps with **Expo**, **NativeWind** (TailwindCSS for React Native), and **Expo Router**.  
It is known to work on **Arch Linux** with a recent Node and npm.

### Tech stack

- **Expo** (`expo`, `expo-router`) for app runtime and file‑based routing
- **React Native** (`react-native`, `react-native-web`) for cross‑platform UI
- **NativeWind + TailwindCSS** (`nativewind`, `tailwindcss`, `prettier-plugin-tailwindcss`) for utility‑first styling
- **React Navigation** (`@react-navigation/*`) for navigation primitives
- **TypeScript + ESLint** for type‑safe development and linting

### Prerequisites (Arch Linux)

- **Node.js** (use the LTS or the version recommended by Expo)
- **npm** or **pnpm/yarn** (examples below use npm)
- Android SDK / emulator (optional, for running on Android)

On Arch, you can typically install Node with:

```bash
sudo pacman -S nodejs npm
```

Then install the Expo CLI if you want the global command:

```bash
npm install -g expo
```

### Install dependencies

From the project root:

```bash
npm install
```

### Run the app

- **Start Metro bundler (default Expo dev tools):**

```bash
npm start
```

- **Run on Android emulator/device:**

```bash
npm run android
```

- **Run on web (React Native Web):**

```bash
npm run web
```

When the dev server is up, follow the terminal or browser instructions to open the app on:

- A development build
- Android emulator / device
- Expo Go (if supported for your features)

### Using NativeWind & Tailwind

- Tailwind is configured in `tailwind.config.js` with `nativewind/preset`.
- You can use Tailwind classes directly via the `className` prop:

```tsx
<View className="flex-1 items-center justify-center bg-slate-900">
  <Text className="text-white text-xl font-bold">Hello NativeWind</Text>
</View>
```

- All screens/components under `app/` and `components/` are already included in the Tailwind content paths.

### Project structure

- `app/` – Expo Router routes and screens
- `app/_layout.tsx` – navigation layout
- `app/global.css` – global styles for web
- `tailwind.config.js` – Tailwind / NativeWind configuration
- `nativewind-env.d.ts` – NativeWind TypeScript helpers

### Linting

Run ESLint via Expo:

```bash
npm run lint
```

### Resetting to a blank Expo project

This template still includes the helper script from `create-expo-app`:

```bash
npm run reset-project
```

This moves the starter code into `app-example/` and creates a fresh `app/` directory.

### Notes for Arch Linux users

- If you have issues with Android emulators, ensure `android-tools`, `android-sdk`, and required images are installed and that `ANDROID_HOME`/`ANDROID_SDK_ROOT` are set.
- If Metro fails to start due to watch limits, increase inotify watches:

```bash
echo "fs.inotify.max_user_watches=524288" | sudo tee /etc/sysctl.d/40-max-user-watches.conf
sudo sysctl --system
```

After that, restart the dev server:

```bash
npm start
```

