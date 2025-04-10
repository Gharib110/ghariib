---
title: "Revocation Reason Codes for TLS Server Certificates"
date: 2025-01-19
categories: 
  - "ca-program"
  - "cybersecurity"
  - "cybersecurity-awareness"
  - "privacy"
  - "security"
  - "vulnerabilities"
tags: 
  - "certificate-authority"
---

In our continued efforts to improve the security of the web PKI, we are taking a multi-pronged approach to tackling some long-existing problems with revocation of TLS server certificates. In addition to our ongoing CRLite work, we added new requirements to version 2.8 of Mozilla’s Root Store Policy that will enable Firefox to depend on revocation reason codes being used consistently, so they can be relied on when verifying the validity of certificates during TLS connections. We also added a new requirement that CA operators provide their full CRL URLs in the CCADB. This will enable Firefox to pre-load more complete certificate revocation data, eliminating dependency on the infrastructure of CAs during the certificate verification part of establishing TLS connections. The combination of these two new sets of requirements will further enable Firefox to enforce revocation checking of TLS server certificates, which makes TLS connections even more secure.

## Previous Policy Updates

Significant improvements have already been made in the web PKI, including the following changes to Mozilla’s Root Store Policy and the CA/Browser Forum Baseline Requirements (BRs), which reduced risks associated with exposure of the private keys of TLS certificates by reducing the amount of time that the exposure can exist.

- TLS server certificates issued on or after 1 September 2020 MUST NOT have a Validity Period greater than 398 days.
- For TLS server certificates issued on or after October 1, 2021, each dNSName or IPAddress in the certificate MUST have been validated within the prior 398 days.

Under those provisions, the maximum validity period and maximum re-use of domain validation for TLS certificates roughly corresponds to the typical period of time for owning a domain name; i.e. one year. This reduces the risk of potential exposure of the private key of each TLS certificate that is revoked, replaced, or no longer needed by the original certificate subscriber.

## New Requirements

In version 2.8 of Mozilla’s Root Store Policy we added requirements stating that:

1. Specific RFC 5280 Revocation Reason Codes must be used under certain circumstances; and
2. CA operators must provide their full CRL URLs in the Common CA Database (CCADB).

These new requirements will provide a complete accounting of all revoked TLS server certificates. This will enable Firefox to pre-load more complete certificate revocation data, eliminating the need for it to query CAs for revocation information when establishing TLS connections.

The new requirements about revocation reason codes account for the situations that can happen at any time during the certificate’s validity period, and address the following problems:

- There were no policies specifying which revocation reason codes should be used and under which circumstances.
- Some CAs were not using revocation reason codes at all for TLS server certificates.
- Some CAs were using the same revocation reason code for every revocation.
- There were no policies specifying the information that CAs should provide to their certificate subscribers about revocation reason codes.

### Revocation Reason Codes

Section 6.1.1 of version 2.8 of Mozilla’s Root Store Policy states that when a TLS server certificate is revoked for one of the following reasons the corresponding entry in the CRL must include the revocation reason code:

- keyCompromise (RFC 5280 Reason Code #1)
    - The certificate subscriber must choose the “keyCompromise” revocation reason code when they have reason to believe that the private key of their certificate has been compromised, e.g., an unauthorized person has had access to the private key of their certificate.
- affiliationChanged (RFC 5280 Reason Code #3)
    - The certificate subscriber should choose the “affiliationChanged” revocation reason code when their organization’s name or other organizational information in the certificate has changed.
- superseded (RFC 5280 Reason Code #4)
    - The certificate subscriber should choose the “superseded” revocation reason code when they request a new certificate to replace their existing certificate.
- cessationOfOperation (RFC 5280 Reason Code #5)
    - The certificate subscriber should choose the “cessationOfOperation” revocation reason code when they no longer own all of the domain names in the certificate or when they will no longer be using the certificate because they are discontinuing their website.
- privilegeWithdrawn (RFC 5280 Reason Code #9)
    - The CA will specify the “privilegeWithdrawn” revocation reason code when they obtain evidence that the certificate was misused or the certificate subscriber has violated one or more material obligations under the subscriber agreement or terms of use.

RFC 5280 Reason Codes that are not listed above shall not be specified in the CRL for TLS server certificates, for reasons explained in the wiki page.

## Conclusion

These new requirements are important steps towards improving the security of the web PKI, and are part of our effort to resolve long-existing problems with revocation of TLS server certificates. The requirements about revocation reason codes will enable Firefox to depend on revocation reason codes being used consistently, so they can be relied on when verifying the validity of certificates during TLS connections. The requirement that CA operators provide their full CRL URLs in the CCADB will enable Firefox to pre-load more complete certificate revocation data, eliminating dependency on the infrastructure of CAs during the certificate verification part of establishing TLS connections. The combination of these two new sets of requirements will further enable Firefox to enforce revocation checking of TLS server certificates, which makes TLS connections even more secure.

The post Revocation Reason Codes for TLS Server Certificates appeared first on Mozilla Security Blog.

Go to Source
