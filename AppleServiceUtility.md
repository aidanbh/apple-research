# Apple Service Utility

# Download

This customer version is available at [https://support.apple.com/en-hk/104052](https://support.apple.com/en-hk/104052).

This was published September 16, 2024, but should update to the latest version upon first launch. 

Internal versions are distributed to Apple Authorized Service Providers and Independent Repair Providers, as well as Apple Stores and AppleCare. Notably, the ASU app itself has no login functionality (neither GSX or AppleConnect), and internal .pkgs have appeared on the internet from time to time. The application bundles no help, and contains links to GSX KBs that require login.

# Modifying Customer to Full Version

The installer scripts in the `Apple Service Utility Customer.pkg` reveal that the "customer mode" is not the default behavior of the app or updater. As such, we can simply reverse the defaults it sets:

```
% sudo defaults write com.apple.fielddiagnostics.appleserviceutility.updaterdTwo customerMode -bool NO
% defaults write com.apple.fielddiagnostics.appleserviceutility.uiapp  customerMode -bool YES
```

The customer mode is also stored at `/Users/Shared/AppleServiceUtility/SoftwareASU.plist`, but changing it manually appears to be unnecessary.

Once you've relaunched, you should see additional modules in the updater (customer version only supports Studio Display and iPhone TrueDepth Camera repair, plus an undocumented updated for the Heated Display Fixture which, oddly enough, is signed by an individual-name Developer ID cert.) You'll also see that the connection instructions dropdown shows all devices, not just those two, as pictured below.


# History

The customer variant of ASU seems to have previously called "System Configuration" when the Self-Service Repair Program launched. However, as this was apparently distributed manually via the SSR contractor website, no copy
is readily available now to compare.

Cleanup scripts in the installer suggest that ASU is a replacement/evolution of "Mac Configuration Utility".

For unknown reasons, updates appear to have been unavailable for several months preceding the September 2026 product launch. This affected both the customer and full versions. Early reports about the iPhone Duo apparently gleaned some information from ASU modules, which might had had something to do with that, although it's not clear how official repair partners were able to access it during that time if it was indeed intentional.

(Note that if updates are unavailable, the error message is also different--customers are pointed to the Self-Service Repair contractor, while internal users are pointed to Apple's Channel Service Support.)
