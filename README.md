# FILUM ANDROID EXAMPLE APP

## Example App

Example app is under `example` directory, use Android Studio to build and run the app.

Make sure to update `serverUrl` and `token` in `FILUM.initialize()` before running.

## Installation

**Step 1: Clone `filum-android-sdk` repository**

```sh
git clone https://github.com/Filum-AI/filum-android-sdk
```

**Step 2: Import filum-android-sdk as a module**

- In Android Studio, select `File` -> `New` -> `Import Module...`
- Specify the path to `filum-android-sdk`

**Step 3: Add `filum-android-sdk` in build.gradle**

- Open `example/build.gradle` of your app
- Add this line

```text
...
dependencies {
    ...
    implementation project(':filum-android-sdk')
    ...
}
```

## Usage

### Initialize

```java
final FILUM filum = FILUM.initialize(
    "http://server-url.example",
    "your_project_token",
    MainActivity.this
);
```

### Identify

Use this method right after user has just logged in/signed up or update any of his/her profile info.

```java
filum.identify(userId);
```

### Track event

Use a string to represent the event name and a JSONObject to contain all custom properties.

```java
// With custom props
try {
    JSONObject props = new JSONObject();
    props.put("price", 100);
    props.put("package_sku", "package_1_free");
    filum.track("Purchase", props);
} catch (JSONException e) {
    e.printStackTrace();
}

// Without custom props
filum.track("End session");
```

### Reset

Use this method right after user has just logged out. It will clear the current `user_id` and 
generate new anonymous ID for the new user.

```java
filum.reset();
```
