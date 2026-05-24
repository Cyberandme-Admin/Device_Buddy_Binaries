# DeviceBuddy Public Release Binaries

This folder contains the first set of DeviceBuddy binaries to be released publicly for Cyber and Me.

DeviceBuddy is a small endpoint companion application that runs on a user's device, collects device information, and sends that information to the user's Cyber and Me account. It is intended to support Cyber and Me workflows where the portal needs current device details for visibility, onboarding, assessment, support, or account-linked device records.

These files are intended for public distribution to users who have access to the Cyber and Me portal and need to connect their device information to their Cyber and Me account.

## Important Portal Requirement

DeviceBuddy requires the Cyber and Me portal to function correctly.

The application is not a standalone device management product. Its primary purpose is to collect information from the local device and submit it to a Cyber and Me account through the Cyber and Me portal. Without a working portal account, portal-side configuration, and network access to the portal services, DeviceBuddy may launch but cannot complete its intended workflow.

At minimum, successful use requires:

- An active Cyber and Me portal environment.
- A valid Cyber and Me user account or organization-linked account.
- Any required portal-side setup for DeviceBuddy enrollment or reporting.
- Internet access from the user's device.
- Permission for the application to communicate with Cyber and Me services.
- A supported operating system build for the selected public release binary.

## Folder Contents

```text
.
├── linux/
│   ├── DeviceBuddy.desktop
│   └── devicebuddy.png
├── macos/
│   └── DeviceBuddy.app/
│       └── Contents/
│           ├── Info.plist
│           ├── MacOS/devicebuddy
│           └── Resources/AppIcon.icns
└── windows/
    └── DeviceBuddy.exe
```

## Platform Builds

### Windows

The Windows public release binary is located at:

```text
windows/DeviceBuddy.exe
```

Run this executable on a supported Windows device to start DeviceBuddy. Depending on Windows security policy, SmartScreen, antivirus, or endpoint protection tooling may warn about newly released or unsigned binaries. Validate signing, reputation, and distribution requirements before broad rollout.

### macOS

The macOS public release app is located at:

```text
macos/DeviceBuddy.app
```

The bundle metadata identifies the app as:

- Display name: `DeviceBuddy`
- Bundle identifier: `com.cyberandme.devicebuddy`
- Version: `1.0.0`
- Minimum macOS version: `10.13`
- Executable: `devicebuddy`

The app is configured with `LSUIElement`, which means it is intended to run as a background/menu-bar style utility rather than as a standard dock application. macOS Gatekeeper, notarization, quarantine, and privacy permission behavior should be tested before release.

### Linux

The Linux public release folder currently contains:

```text
linux/DeviceBuddy.desktop
linux/devicebuddy.png
```

The desktop entry describes DeviceBuddy as a background dashboard utility and launches:

```text
./devicebuddy tray
```

If distributing the Linux build, ensure the executable file referenced by the desktop entry is present in the same folder, has executable permissions, and is packaged with the desktop file and icon.

## What DeviceBuddy Does

DeviceBuddy is designed to collect information from a user's device and associate that information with the user's Cyber and Me account.

Typical information collected by an endpoint companion app may include device identity, operating system details, hardware details, application/runtime environment, security posture signals, or other diagnostics required by Cyber and Me workflows. The exact fields collected should be confirmed against the current DeviceBuddy implementation and Cyber and Me portal configuration before release.

The expected flow is:

1. The user launches DeviceBuddy on their device.
2. DeviceBuddy gathers supported local device information.
3. The application connects to Cyber and Me services.
4. The collected device information is sent to the user's Cyber and Me account.
5. The Cyber and Me portal displays or uses the device information according to the portal's configured workflows.

## Intended Use

These public release binaries are intended for:

- Public distribution to Cyber and Me users.
- Device information collection for linked Cyber and Me accounts.
- Portal-backed onboarding, visibility, assessment, support, or device record workflows.
- Cross-platform use on supported Windows, macOS, and Linux devices.
- Support and troubleshooting by Cyber and Me teams.

They require a working Cyber and Me portal environment. Users without portal access, a valid Cyber and Me account, or the required portal configuration will not be able to complete the intended DeviceBuddy workflow.

## Portal Dependency Details

DeviceBuddy depends on Cyber and Me portal services for account association, data submission, and useful output. The app should be tested against the target portal environment before being shared with end users.

Confirm the following before release:

- The correct Cyber and Me portal endpoint is configured.
- The target portal environment is online and reachable.
- User authentication or account-linking works as expected.
- Device records appear in the correct user or organization account.
- Failed submissions are handled clearly.
- Offline or poor-network behavior is acceptable.
- Duplicate device records are handled appropriately.
- Portal-side permissions restrict access to device information correctly.

## Privacy And User Consent

Because DeviceBuddy collects information from a user's device and sends it to a Cyber and Me account, the release process should include privacy and consent review.

Before deployment, make sure users or administrators understand:

- What device information is collected.
- Why the information is collected.
- Where the information is sent.
- Which Cyber and Me account or organization can view it.
- How long the information is retained.
- How users can request support or removal if required.

Any required privacy notices, consent screens, terms, or administrator communications should be reviewed before production release.

## Security Considerations

Before distributing these binaries, verify:

- The binaries are built from the intended source revision.
- Release artifacts are signed where required.
- macOS builds are notarized if they will be distributed outside controlled test environments.
- Windows builds are code signed if required for production trust and SmartScreen reputation.
- Linux artifacts include the correct executable permissions and packaging metadata.
- The app communicates with Cyber and Me services over secure transport.
- Portal API credentials, tokens, or secrets are not embedded insecurely.
- Logs do not expose sensitive user, account, device, or credential information.
- Error handling does not leak sensitive portal or environment details.

## Public Release Checklist

Use this checklist before distributing or supporting these binaries:

- Confirm the app launches on each supported operating system.
- Confirm the app can connect to the Cyber and Me portal.
- Confirm device information is submitted successfully.
- Confirm the portal associates the submission with the correct account.
- Confirm the app behaves correctly when the user is offline.
- Confirm the app behaves correctly when portal authentication fails.
- Confirm duplicate runs do not create incorrect records.
- Confirm application logs are useful but do not expose sensitive data.
- Confirm uninstall, removal, or cleanup expectations for each platform.
- Confirm signing, notarization, packaging, and distribution requirements.
- Confirm end-user instructions are accurate.
- Confirm privacy and consent requirements are satisfied.

## Distribution Notes

When distributing these public release binaries:

- Clearly identify them as the first public DeviceBuddy binaries.
- Share them with users who have a Cyber and Me account and access to the required portal workflow.
- Include the target portal environment to use for testing.
- Include known limitations and expected setup steps.
- Track which binary was published or distributed for each platform.
- Collect platform, operating system version, portal account, and timestamp when investigating issues.

## Troubleshooting

If DeviceBuddy does not appear to work:

1. Confirm the Cyber and Me portal is available.
2. Confirm the user's Cyber and Me account is valid and has access to the required portal workflow.
3. Confirm the device has internet access.
4. Confirm local firewall, proxy, VPN, endpoint protection, or DNS settings are not blocking portal access.
5. Confirm the correct platform binary is being used.
6. Confirm the app has the permissions required by the operating system.
7. Check application or system logs for connection, authentication, or submission errors.
8. Validate that the device record appears in the expected Cyber and Me account.

## Support Information To Capture

When reporting an issue, capture:

- Operating system and version.
- DeviceBuddy platform build used.
- Cyber and Me portal environment.
- User or test account involved.
- Approximate time of the test.
- Whether the app launched successfully.
- Whether authentication or account linking completed.
- Whether the portal received the device information.
- Any visible error messages.
- Relevant logs, with sensitive values removed.

## Release Status

Current status: first public release binaries.

These binaries are intended for public release, but they still depend on the Cyber and Me portal to provide account linking, device record storage, and the user-facing portal experience.
