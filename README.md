# Sample Web Agent - Reset User Password

![Sample Web Agent - Reset User Password](docs/assets/images/png/screenshot.png)
## Info
Property | Value   
---|---
Filename | PwdResetSample.nsf
Templatename | -
Template version | 8.5.1 (18.11.2008)
Signed by | Notes Template Development/Domino
Optimized for | Web

## What does this database do?

This database provides authenticated web users the ability to reset the password of their NotesID when it is stored in the IDVault. The application runs an agent to call the IDVault reset password function. For this to work, the agent needs to be signed with an identity that is a PasswordReset authority.

## Setting up the sample self-service application to allow ID vault users to reset their Notes® passwords

From: 
https://help.hcltechsw.com/domino/12.0.2/admin/conf_settingupthesampleselfserviceapplicationtoallowi_t.html

A Domino® server comes with the Sample Web Agent - Reset User Password application (PwdResetSample.nsf). The application contains a sample LotusScript® agent called UserPasswordReset that enables users with IDs stored in an ID vault to reset their Notes® passwords from a browser. A user who has forgotten his or her Notes® password might do this to specify a new one.

### About this task

This application is intended as an example for you to customize to suit your needs. By default, users use their HTTP passwords to log into a Domino® Web server in the domain that is authorized to run the agent. The agent code also provides examples of setting up the agent not to require HTTP authentication or to allow users to specify the number of ID downloads they are allowed for ID recovery.
Procedure

1. Open the PwdResetSample.nsf database located in the data directory of a Domino® server and modify the database ACL as follows: 
    -Give at least Editor access to the vaulted users who will use the application to reset their passwords. One way to do this is to ensure that the -Default- entry has Editor access.
    - Give Manager access to the name of the Notes® ID that will be used to sign the agent in the next step.
2. From Domino® Designer, open PwdResetSample.nsf and perform the following steps to sign the UserPasswordReset agent using a Notes® ID that you will trust to reset passwords. Using an ID created specifically for this purpose is recommended.
    - From the Applications view, click Code > Agents and then double-click.
    - With the UserPasswordReset agent selected, click Sign.
3. Decide which server or servers in the Domino® domain to allow to run the agent on behalf of the agent signer specified in Step 2. Then in the Server document of each in the Domino® Directory, give the name of the agent signer Sign or run restricted LotusScript/Java agents access. A server does not have to be a vault server to run the agent.
4. Copy the signed PwdResetSample.nsf to the data directory of each server that will run it.
5. Assign password reset authority to the following names:
    - The name that signed the agent in Step 2. Be sure to select the Self-service password reset authority field.
    - The names of each server you allowed to run the agent in Step 3.
6. Specify instructions to display for users who forget their passwords.
7. Consider disabling the default requirement that users change passwords after they are reset, so that users who reset their passwords do not have to change passwords again afterwards.
8. Run the HTTP task on each server that is allowed to run the agent. 

### What to do next

Users whose IDs have been uploaded to the vault can now perform the following steps to reset their Notes® passwords:

1. Launch a Web browser and open the sample application by specifying a URL such as the following one:

    http://<server>/PwdResetSample.nsf

2. Log in to the HTTP server.
3. In the Reset User Password window, type and confirm a new password, then click Reset My Password.

## Related information
- [Assigning password reset authority](https://help.hcltechsw.com/domino/12.0.2/admin/conf_assigningpasswordresetauthority_t.html)
- [Creating and configuring an ID vault](https://help.hcltechsw.com/domino/12.0.2/admin/conf_creatingandconfiguringanidvault_t.html)

## Related Open Source projects
- OpenNTF: [IDVault Password Reset / Xpages](https://www.openntf.org/internal/home.nsf/project.xsp?name=IDVault%20Password%20Reset)
- OpenNTF: [Password Reset Tool](https://openntf.org/main.nsf/project.xsp?r=project/Password%20Reset%20Tool)