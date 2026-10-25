# CertMan: Basic Usage

CertMan is a desktop application for creating and managing X.509 certificates, certificate signing requests (CSRs), certificate revocation lists (CRLs), and key pairs. Certificate and CRL profiles let you create test data with different settings and exercise common PKI workflows. It is especially useful for PKI development and testing.

For the original overview and examples, see the [CertMan introduction](https://jykim74.tistory.com/100) and the [CertMan manual articles](https://jykim74.tistory.com/category/Manual/CertMan).

## 1. Getting started

1. Install and launch the package for your operating system. Package links and version details are listed in the [CertMan update history](https://jykim74.github.io/software/2024/03/08/CertManUpdate.html).
2. Select **File > New** to create a database, or **File > Open** to open an existing database.
3. When creating a database, choose a location and set its password. Store the password safely; losing it may prevent you from accessing the database.
4. Check **Help > License Information** to see the current license and available features. Some functions and algorithms depend on the license.

## 2. Main records and workflow

The tree on the left side of the main window organizes the records. A typical workflow is:

**Key pair → certificate profile → CSR or certificate → issue, review, and export**

- **KeyPair**: a public and private key managed as a pair.
- **CSR**: a signed request containing a subject name and public key.
- **Certificate**: a CA-signed record that binds a public key to subject information.
- **CA / Signer**: CA information and keys used to issue or sign certificates.
- **Cert Profile / CRL Profile**: settings for certificate or CRL fields and extensions.
- **CRL**: a list of revoked certificates.

Use the **Tools** menu or right-click the relevant tree item to create, view, or export records.

## 3. Create a key pair

1. Select **Tools > NewKey**, or right-click **KeyPair** in the tree and select **New Key**.
2. Enter a name and select an algorithm. For RSA, set the exponent and key length; for an elliptic-curve algorithm, choose a curve.
3. Generate the pair and confirm that it appears in the key list.
4. If needed, select the pair and export its public or private key. Export private keys in an encrypted format and store them in a restricted location.

Available algorithms vary by CertMan version and license. For RSA, ECDSA, and SM2 examples, see [Creating asymmetric key pairs](https://jykim74.tistory.com/180).

## 4. Create a CSR

1. Prepare the key pair that will be used by the request.
2. Open the certificate request (CSR) creation function from the **Tools** menu.
3. Enter the subject DN (for example, country, organization, and common name) and select the key pair.
4. Configure any required request extensions, then generate the CSR.
5. Review the subject and public key, then export the CSR if needed.

A CSR is a request, not a certificate. Send it to the issuing CA and then import or register the certificate returned by that CA.

## 5. Issue a certificate with a CA and profile

To issue a test certificate, prepare an issuing CA and a certificate profile first.

1. Prepare a key pair and CA certificate for a root or intermediate CA. In a test environment, you can start with a self-signed test root.
2. Use **Tools** to create a **Cert Profile**. Set the certificate type, validity period, default subject information, and required extensions.
3. Select the subject CSR or open the certificate creation function.
4. Choose the issuing CA, certificate profile, serial number, and validity period, then issue the certificate.
5. Inspect the issuer, subject, validity, extensions, and signature.
6. Export the certificate in the required format, such as PEM or DER.

A self-signed test certificate is not trusted by operating systems or browsers by default. Use it only in a test environment, and check the chain and intended purpose before adding it to any trust configuration.

## 6. Revoke a certificate and create a CRL

1. Select the certificate and run **Revoke** or the certificate revocation function.
2. Choose a revocation reason and confirm the record.
3. Select the issuing CA and a CRL profile, then generate a CRL.
4. Review the CRL issuer, update times, and revoked-certificate list before exporting it.

Changing a certificate's revocation status does not automatically update CRLs that were already created or distributed. Generate and distribute a new CRL after changing the revocation list.

## 7. Import, export, and data handling

- Use the **Data** menu to review supported import, URI retrieval, and publishing functions.
- Select a record and use its context menu to view details or export it.
- Before exporting, check the format (such as PEM or DER) and which data will be included. Encrypt exported private keys and restrict file access.
- Back up the database and private keys separately, and protect the backups as carefully as the originals.

Menus and supported formats may vary by version and edition.

## 8. Suggested first exercise

Use a separate test database and test keys rather than production keys while learning the workflow.

1. Create a test database.
2. Create a CA key pair and prepare a test root certificate.
3. Create a user key pair and a certificate profile.
4. Generate a user CSR and issue a certificate with the test CA.
5. Inspect the certificate and export it as PEM or DER.
6. Revoke the user certificate and create a CRL to confirm that it appears in the revoked list.

## References

- [CertMan introduction](https://jykim74.tistory.com/100)
- [CertMan key-pair example](https://jykim74.tistory.com/180)
- [CertMan downloads and update history](https://jykim74.github.io/software/2024/03/08/CertManUpdate.html)
- [CertMan questions and bug reports](https://github.com/jykim74/CertMan/discussions)
