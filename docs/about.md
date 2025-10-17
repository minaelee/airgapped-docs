---
myst:
  html_meta:
    "description": "Learn key concepts about airgapped environments, including the types of airgaps and deployment considerations."
---

(about-top)=
# About airgapped environments

An airgapped environment is a type of environment in which systems are isolated from the public internet and, in some cases, from all external networks. This isolation prevents direct access to external services, which requires special considerations for installing, updating, and operating software. Many organizations use airgapped environments to meet security, compliance, or operational requirements.

(about-types)=
## Types of airgapped environments

There are two main types of airgapped environments: restricted network airgaps and fully disconnected airgaps.

### Restricted network airgap (controlled endpoint)

In this model, the systems inside the airgaped environment don’t have direct access to the public internet. Instead, they can communicate with a designated external system by connecting through a controlled endpoint, such as a proxy server, gateway host, or firewall with allow-listed rules.

This setup allows updates and data to flow in securely without exposing systems inside the environment to the internet. Since data can be synchronized through the controlled connection, this approach reduces the need for physical data transfers while still maintaining a strong security boundary.

This type of airgapped environment is used when full isolation isn’t required, but tight control over external communication is still necessary.

### Fully disconnected airgap (manual data transfer)

In this model, the systems inside the environment have no network connectivity to external systems and the public internet. All updates and data must be brought in manually, typically using removable storage or other physical media.

This lack of any external connectivity provides the strongest network separation, but requires more careful planning to keep systems up to date. Administrators must regularly prepare and manually transfer updates into the environment.

This type of airgapped environment is used when the highest level of network isolation is required. They’re also common in physically isolated or remote environments where connectivity is impractical.

(about-considerations)=
## Considerations

When planning to deploy Canonical products in an airgapped environment, keep in mind:

- **Software updates**
  
  Updates (security patches, bug fixes, and new features) must be periodically mirrored or exported and imported into the environment. Depending on your deployment, this may involve tools such as [Landscape](https://ubuntu.com/landscape), [Enterprise Store](https://snapcraft.io/enterprise-store), repository mirrors, and container registries.

- **Repository mirrors**
  
  Many products rely on external package repositories (e.g., APT, snaps, charm stores). You may need to set up internal mirrors or bring snapshots of these repositories into the environment.

- **Internal networking**
  
  Even without access to the public internet, internal systems still need reliable network access to each other. Administrators should consult specific product documentation for any special networking requirements.