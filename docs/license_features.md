# CertMan Features by License Status

CertMan can run with a valid license or as an unlicensed version. This page summarizes the feature differences enforced by the application. Availability can also depend on the product edition, build options, and runtime configuration.

## Feature comparison

| Feature | Valid license | Unlicensed version |
| --- | --- | --- |
| Key algorithms | RSA and the other algorithms enabled by the build, including ECDSA, DSA, EdDSA, SM2, ML-DSA, and SLH-DSA where supported | RSA only for key generation, CSR creation, and applicable key/certificate import or export operations |
| Key pairs, CSRs, certificates, and CRLs | Normal creation workflows, subject to edition and build | Creation is subject to unlicensed-version count limits. The application reports the applicable limit when it is reached; limits may vary by artifact type or build |
| LDAP publishing | Available when the relevant configuration is present | Disabled |
| Private-key password operations | Set and change private-key passwords | Disabled |
| Certificate renewal | Available where the relevant workflow is supported | Disabled |
| PKI services | TSP, OCSP, CA, and ACME service controls can be used when included and configured | Service controls are disabled |
| Application log tab | Available | Disabled |
| Viewing, exporting, and deleting existing records | Available, with algorithm restrictions applying to relevant exports | General record viewing, deletion, and export remain available; key and certificate operations are limited to RSA where applicable |

## Notes

- “Valid license” means a license accepted by the running CertMan installation. An expired, invalid, or mismatched license is treated as unlicensed.
- Other edition and build differences still apply. For example, some service integrations and algorithms depend on product edition, compiled features, and available cryptographic providers.
- Unlicensed count limits are enforced by the application. This document does not state fixed numbers because limits can vary between builds and artifact categories.
- The application title identifies the unlicensed version. The **Help > License Information** dialog displays license status and provides available license actions.

## Getting a license

A free trial license may be requested through the [CertMan license registration page](https://jykim7.mycafe24.com/user_reg.php). See **Help > License Information** in the application to request, import, or review a license.
