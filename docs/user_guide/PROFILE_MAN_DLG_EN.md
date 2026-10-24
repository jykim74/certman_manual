# Profile Manager Dialog Guide

This guide explains the **Profile Man** dialog, titled **Profile Management**. Open it from **Tools > Profile Manager** (`Shift+F11`). It lists certificate, CSR, and CRL profiles saved in the connected database. Other workflows can open it in selection mode to choose a profile.

![Profile Manager dialog](../images/profile_man_dlg.png)

## Management mode

Use the **Certificate Profile** and **CRL Profile** tabs to browse profiles. The Certificate Profile tab includes a type filter for **Certificate** or **CSR** profiles.

| Tab / column | Description |
|---|---|
| **Certificate Profile** | Lists certificate or CSR profiles according to the type filter. |
| **Type filter** | Select **Certificate** or **CSR** to filter the list. |
| **Num** | Profile database record number. |
| **NotBefore / NotAfter** | Profile validity start/end or relative validity period. |
| **Name** | Profile name. |
| **CRL Profile** | Lists CRL profiles. |
| **ThisUpdate / NextUpdate** | CRL update start/end or relative update period. |

Select a row and click **View** to inspect the profile or **Delete** to remove it after confirmation. These actions are also available from each table's right-click menu. Double-clicking a row opens its details. The lists are read-only; create and edit profiles through **Tools > Make Cert Profile** or **Tools > Make CRL Profile** and the related profile workflows.

## Selection mode

Other dialogs can open Profile Manager as a picker. The caller limits the available choice to a certificate profile, CSR profile, or CRL profile. Only the relevant tab is enabled, management buttons are hidden, and **OK** appears. Select a row and click **OK**, or double-click it, to return its profile record number. Click **Close** to cancel selection.

## Important implementation note

In the current source, **CRL Profile > Delete** calls the certificate-profile deletion function (`delCertProfile`) instead of the CRL-profile deletion function (`delCRLProfile`). As a result, this action does not delete the selected CRL profile and may delete a certificate profile with the same record number. Avoid using **Delete** on the CRL Profile tab until this implementation is corrected.

## Notes

- The dialog requires an open database.
- Delete actions are confirmed before execution. Certificate-profile deletion uses the certificate-profile database table; CRL-profile deletion is affected by the implementation issue described above.
- The Certificate Profile type filter switches between ordinary certificate profiles and CSR extension profiles.

## Related implementation

This guide is based on `images/profile_man_dlg.png`, `src/CertMan/profile_man_dlg.ui`, `src/CertMan/profile_man_dlg.h`, and `src/CertMan/profile_man_dlg.cpp`.
