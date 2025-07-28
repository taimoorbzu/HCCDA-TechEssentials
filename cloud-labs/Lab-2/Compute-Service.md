# HUAWEI CLOUD Compute Service

## Overview
This guide demonstrates how to deploy and manage Elastic Cloud Servers (ECS) using HUAWEI CLOUD's infrastructure services, with a focus on creating and utilizing custom images through the Image Management Service (IMS).

---

## 1. Initial Setup and ECS Deployment

### Network Foundation
1. **Create a Virtual Private Cloud (VPC)**:
   - Provides isolated network environment
   - Configure IP ranges and subnets
   - Set up route tables and gateways

### Server Provisioning
Deploy two server types with distinct configurations:

#### Windows ECS
- **Image**: Windows Server 2012 R2 (public image)
- **Configuration**:
  - Billing: Pay-per-use
  - Region: AP-Singapore
  - No Elastic IP (EIP) assigned initially
  - Set administrator password during creation

#### Linux ECS
- **Image**: CentOS 7.6 (public image)
- **Configuration**:
  - Auto-assign Elastic IP
  - Same region and billing model
  - Set root password during creation

### Server Management
- **Access Methods**:
  - Windows: Remote Desktop via VNC client
  - Linux: Command line via VNC terminal (user: root)
  
- **Resource Modification**:
  1. Stop the ECS instance
  2. Select "Modify Specifications"
  3. Choose new hardware configuration
  4. Restart to apply changes

---

## 2. Image Management Service (IMS)

### Creating Private Images
Transform configured ECS instances into reusable templates:

#### Windows Image Preparation
1. **Network Configuration**:
   - Set NIC to DHCP (automatic IP/DNS)
2. **Remote Access**:
   - Enable Remote Desktop
   - Configure firewall rules
3. **Initialization**:
   - Verify Cloudbase-Init installation

#### Linux Image Preparation
1. **Network Configuration**:
   - Ensure DHCP in network config files
2. **Initialization**:
   - Confirm Cloud-Init and password reset plugin
3. **Cleanup**:
   - Remove persistent network rules (`/etc/udev/rules.d`)

#### Image Creation Process
1. Navigate to IMS console
2. Select "Create System Disk Image"
3. Choose prepared ECS as source
4. Configure image metadata (name, description)

---

## 3. Advanced Image Operations

### Image Management
- **Metadata Editing**: Update names/descriptions
- **Regional Replication**: Create copies within same region
- **Version Control**: Maintain multiple image versions

### Image Sharing
1. Obtain recipient's Project ID
2. Select "Share" on private image
3. Add recipient's Project ID
4. Recipient accepts shared image in their account

### Deployment from Custom Images
1. Launch new ECS instance
2. Select your private image as source
3. Configure instance parameters
4. Deploy identical environment in minutes

---

## Best Practices
- **Security**: Always remove sensitive data before imaging
- **Documentation**: Maintain change logs for custom images
- **Testing**: Validate new images in staging before production
- **Tagging**: Use consistent naming conventions for images

