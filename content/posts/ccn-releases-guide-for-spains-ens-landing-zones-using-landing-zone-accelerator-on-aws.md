---
title: "CCN releases guide for Spain’s ENS landing zones using Landing Zone Accelerator on AWS"
date: 2025-01-23
---

Spanish version »

The Spanish National Cryptologic Center (CCN) has published a new STIC guide (CCN-STIC-887 Anexo A) that provides a comprehensive template and supporting artifacts for implementing landing zones that comply with Spain’s National Security Framework (ENS) Royal Decree 311/2022 using the Landing Zone Accelerator on AWS. Spain’s ENS establishes a common framework of basic principles and requirements of security for Spanish public sector organizations and their service providers, including supply chain providers. Over the years, the collaboration between Amazon Web Services (AWS) and the CCN has resulted in the publication of eight secure configuration guides (Series STIC 887) that provide comprehensive advice on the configuration of AWS services to align with the ENS. The guide CCN-STIC-887 Anexo A is the last addition to this series.

The centerpiece of this new guide is the ENS template for the Landing Zone Accelerator on AWS (LZA ENS). A landing zone serves as the initial setup of an organization’s cloud account or environment, including the implementation of security controls, access management, and compliance frameworks. The Landing Zone Accelerator on AWS is a powerful open source tool created by AWS for organizations that want to quickly customize and automate implementation of landing zones that align with AWS best practices and with regulatory compliance frameworks. This tool provides a comprehensive solution that, managed entirely by code, automatically configures over 35 AWS services using a simplified set of configuration files to manage and govern a multi-account environment, helping customers with highly regulated workloads and complex compliance requirements.

The CCN-STIC-887 Anexo A guide focuses on helping organizations implement landing zones that meet ENS security requirements from the ground up. It offers detailed instructions and templates for establishing a landing zone—the foundational infrastructure required for a secure, well-managed cloud environment—and a control matrix to demonstrate compliance with ENS controls.

Key components covered in the STIC 887H guide include:

- **Logging and monitoring**: LZA ENS performs a default and scaled activation of the necessary logging and monitoring services required to meet ENS monitoring requirements in AWS services (such as AWS CloudTrail, Amazon CloudWatch, AWS Security Hub, and Amazon GuardDuty).
- **Access control**: LZA ENS implements the management of identity and access management methods and policies at scale, which are aligned with the access control requirements of the ENS in a centralized manner using AWS IAM Identity Center.
- **Asset management**: By default, LZA ENS activates inventory functions and resource and inventory tagging policies (for example, AWS Config) that support ENS asset management controls in the services.
- **Network topology**: LZA ENS can be used to deploy a centralized network topology in accordance with ENS network security controls.
- **Cryptography**: The encryption service activation capabilities built into LZA ENS can help organizations align with ENS data protection standards through mandatory encryption at rest, enforcement mechanisms with AWS Key Management Service (AWS KMS), and monitoring mechanisms to detect unencrypted data and communications with AWS Config rules.
- **Compliance and data residency**: LZA ENS includes control policies to promote the use of AWS services with the ENS High certification and to provide processing on AWS in accordance with customers’ data residency requirements.

Organizations that require specific customizations to fully meet the requirements of the ENS can use LZA ENS to quickly modify and add customized security controls and then execute the scaled deployment of these controls to their accounts in the landing zone. One of the customizations included in LZA ENS is the integration of the open source security tool Prowler with Security Hub as an automated auditing tool with the objective of providing an up-to-date view of compliance with ENS controls. In addition, by providing a base designed for security and the flexibility to add custom controls, LZA ENS can support the process of achieving and maintaining compliance with the ENS in the AWS Cloud environment.

The CCN-STIC-887 Anexo A guide represents an important step forward in standardizing secure cloud deployments for Spanish public sector organizations and those working with government entities. This publication demonstrates the AWS commitment to support organizations in their secure cloud adoption journey while maintaining compliance with national security standards.  
 

* * *

#### Spanish version

## CCN publica la guía para las Zonas de Aterrizaje del ENS con AWS Landing Zone Accelerator

El Centro Criptológico Nacional de España (CCN) ha publicado una nueva guía STIC (CCN-STIC-887 Anexo A) que proporciona una plantilla de código y material de soporte para implementar zonas de aterrizaje (o landing zones) que cumplan con el Esquema Nacional de Seguridad del Real Decreto 311/2022 (ENS) mediante el Landing Zone Accelerator on AWS. El ENS establece un marco común de principios básicos, requisitos y medidas de seguridad para las organizaciones del sector público español y sus prestadores de servicios, incluyendo la cadena de suministro. A lo largo de los años, la colaboración entre Amazon Web Services (AWS) y el CCN se ha traducido en la publicación de ocho guías de configuración segura (serie STIC 887) que proporcionan consejo sobre la configuración de los servicios de AWS para alinearse con el ENS. La guía CCN-STIC-887 Anexo A es la última incorporación a esta serie.

La pieza central de la nueva guía es la plantilla ENS para el AWS Landing Zone Accelerator (LZA ENS). Una zona de aterrizaje (landing zone) sirve como la configuración inicial del entorno en la nube de una organización, e incluye la implementación inicial de controles de seguridad, la administración del acceso y los marcos de cumplimiento. El AWS Landing Zone Accelerator es una potente herramienta de código abierto creada por AWS para las organizaciones que desean implementar de forma rápida, segura, personalizada y automatizada zonas de aterrizaje alineadas con las prácticas recomendadas de AWS, así como con marcos de conformidad. Esta herramienta proporciona una solución integral que, mediante código, configura automáticamente más de 35 servicios de AWS con un conjunto simplificado de archivos de configuración para administrar y gobernar un entorno multicuenta, lo que ayuda a los clientes con cargas de trabajo altamente reguladas y requisitos de cumplimiento normativo.

La guía CCN-STIC-887 Anexo A se centra específicamente en ayudar a las organizaciones a implementar desde cero zonas de aterrizaje que cumplan con los requisitos de seguridad del ENS. Ofrece instrucciones y plantillas detalladas para establecer una zona de aterrizaje – la infraestructura básica necesaria para un entorno de nube seguro y bien administrado – así como una matriz de control para demostrar el cumplimiento de los controles del ENS.

Los componentes clave incluidos en la guía STIC 887H incluyen:

- **Registro y monitoreo:** LZA ENS realiza una activación por defecto y a escala de los servicios de registro y monitoreo necesarios en AWS (como AWS CloudTrail, Amazon CloudWatch, AWS Security Hub, y AWS GuardDuty) para cumplir con los requisitos de monitoreo del ENS.
- **Control de acceso:** LZA ENS implementa los métodos y políticas de administración de identidades y accesos a escala, que se alinean con los requisitos de control de acceso del ENS de manera centralizada mediante AWS IAM Identity Center..
- **Administración de activos:** De forma predeterminada, el LZA ENS activa las funciones de inventario y las políticas de etiquetado de recursos e inventario (por ejemplo AWS Config) que soportan los controles de administración de activos del ENS.
- **Topología de red:** LZA ENS se puede utilizar para implementar una topología de red centralizada de acuerdo con los controles de seguridad de red ENS.
- **Criptografía:** las capacidades de activación de cifrado integradas en la LZA ayudan a organizaciones a alinearse con los estándares de protección de datos del ENS mediante el cifrado obligatorio en reposo, los mecanismos de aplicación con AWS Key Management Service (AWS KMS) y los mecanismos de supervisión para detectar datos y comunicaciones no cifrados con las reglas de AWS Config.
- **Cumplimiento y residencia de datos:** LZA ENS incluye políticas de control para promover el uso de los servicios de AWS con la certificación del ENS Alto y realizar el procesamiento en AWS de acuerdo con los requisitos de residencia de datos del cliente.

Las organizaciones que requieren personalizaciones específicas para cumplir plenamente los requisitos del ENS pueden usar el LZA ENS para modificar rápidamente y añadir fácilmente controles de seguridad personalizados y ejecutar la implementación a escala de estos controles en sus cuentas de la zona de aterrizaje. Una de las personalizaciones que hemos incluido en el LZA ENS es la integración de Prowler con AWS Security Hub como una herramienta de auditoría automatizada, con el objetivo de proporcionar una visión actualizada del cumplimiento de los controles ENS de una manera fácil y eficaz. Además, al proporcionar una base diseñada para la seguridad y la flexibilidad de agregar controles personalizados, LZA ENS puede ayudar durante el proceso de obtener la conformidad con el ENS en el entorno de nube de AWS.

La guía CCN-STIC-887 Anexo A representa un importante paso adelante en la estandarización de las implementaciones seguras en la nube para las organizaciones del sector público español. Esta publicación demuestra el compromiso de AWS de apoyar a las organizaciones en su proceso de adopción segura de la nube, manteniendo al mismo tiempo el cumplimiento de las normas de seguridad nacionales.

   
If you have feedback about this post, submit comments in the **Comments** section below. If you have questions about this post, contact AWS Support.

![Tomás Clemente Sánchez](https://d2908q01vomqb2.cloudfront.net/22d200f8670dbdb3e253a90eee5098477c95c23d/2025/01/21/tomascle.jpg) Tomás Clemente Sánchez  
Tomás Clemente Sánchez is a Principal Security Solutions Architect at AWS, based in Madrid, Spain. He works advising highly regulated customers in public sector and national security organizations on the implementation of cloud security technologies and data protection frameworks. Outside of work, he is addicted to cinema and sci-fi novels, a rugby fan, and a scuba diver.

Go to Source
