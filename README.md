# Connecting two virtual machines and networks using the Microsoft Azure Portal
![VirtualNetworkLogo](img/virtual-network-icon.png)


---------------------------------------------------------


## Requirements
- Microsoft Azure Account ( with funds or credits    )
- Microsoft Azure Suscription
- A web browser
- Access to internet

---------------------------------------------------------

## Instructions
#### 1. Login to the [Azure Portal](https://portal.azure.com/).
#### 2. Once you're on the portal's home page, you will see something like this:
![PortalImage](img/portal-main.png)
#### 3. Inside the search bar (located at the top), look for *resource groups* and click on it.
![Searchbar](img/searchbar.png)
#### 4. Click on *Create*.
![CreateButton](img/create-resource-group-button.png)
#### 5. Select your subscription, the resource where you will locate the resource group and give it a name.
![ResourceGroupConfig](img/resource-group-config.png)
#### 6. Click *Review + create*.
![ReviewAndCreate](img/review-and-create.png)
#### 7. If validation passed, click *Create*.
![Create](img/create.png)
#### 8. Click on the searchbar and look for *virtual networks*, then click on it.
![Searchbar](img/searchbar1.png)
#### 9. Click on *Create*.
![CreateButton](img/create-vn-button.png)
#### 10. Configure the *Project Details* for your Virtual Network.
![VNProjectDetails](img/vn-project-details.png)
#### 11. Go to the *IP Addresses* tab and make sure to have the same IPv4 address space is *10.0.0.0/16 *.
![IPAddressesTab](img/ip-addresses-tab.png)
#### 12. Select the default subnetwork and remove it.
![RemoveDefaultSubnetwork](img/remove-default-subnetwork.png)
#### 13. Click on *Add subnet*.
![AddSubnetButton](img/add-subnet.png)
#### 14. Configure your subnet's details.
![SubnetConfig](img/subnet-config.png)
#### 15. Click *Add*.
![Add](img/add.png)
#### 16. Click *Review + create*.
![ReviewAndCreate](img/review-and-create.png)
#### 17. If validation passed, click *Create*.
![Create](img/create.png)
#### 18. Deployment will begin, please wait a couple of seconds.
![DeploymentInProgress](img/vn-deployment-in-progress.png)
#### 19. Once deployment is complete, repeat steps 8-13 to create another virtual network(using a different name for the new virtual network of course). When you're on step 11, you will notice a difference in the IPv4 address space, don't worry, it's ok.
![OtherVirtualNetworkIPv4](img/other-vn-ipv4.png)
#### 20. Configure the subnetwork for the new virtual network. Notice how the subnet address range belongs to the IPv4 address space (which is different from the first network we created).
![OtherSubnet](img/other-subnet-config.png)
#### 21. Click *Add*.
![Add](img/add.png)
#### 22. Click *Review + create*.
![ReviewAndCreate](img/review-and-create.png)
#### 23. If validation passed, click *Create*.
![Create](img/create.png)
#### 24. Implementation will begin,please wait a couple of seconds until it's complete.
#### 25. Go back to *Virtual networks* (step 8) and click on the first network you created.
![VirtualNetworksSelection](img/virtual-networks-selection.png)
#### 26. Open another tab inside the [Azure Portal](https://portal.azure.com/).
#### 27. Click on the searchbar and look for *virtual machines*, then click on it.
![Searchbar](img/searchbar2.png)
#### 28. Click on *Create* and then on *Azure Virtual Machine*.
![CreateButton](img/create-vm-button.png)
#### 29.Configure an Ubuntu VM inside the same resource group you have been working in.
![VM1Config](img/vm-1-config.png)
#### 30. Make sure your VMs and your Virtual Networks are all in the same region you can check the region where you created your VN inside the resource itself and move it if you need to (in my case, I needed to move my VNs from South Central US to the France Central because of directives in my subscription, [here is the documentation for that](https://docs.microsoft.com/en-us/azure/resource-mover/about-move-process#move-region-process)).
![VNDetails](img/vn-details.png)
#### 31. In the administrator section, choose *Password* and set the login credentials.
![VM1AdminConfig](img/vm-1-admin-config.png)
#### 32. Scroll all the way up and click on *Networking*.
![VMTabs](img/vm-tabs.png)
#### 33. Select one of your virtual networks, its respective subnet will be automatically selected.
![VM1Network](img/vm1-network.png)
#### 34. Click *Review + create*.
![ReviewAndCreate](img/review-and-create.png)
#### 35. If validation passed, click *Create*.
![Create](img/create.png)
#### 36. Create another VM repeating steps 27-31.
#### 37. Go to the *Networking* tab and select your other virtual networking, its subnetwork will be selected automatically.
#### 38. Click *Review + create* and then *Create*.
#### 39. Go to your virtual machines (step 27) and click on your first vm.
![SelectVM](img/select-virtual-machine.png)
#### 40. Click on *Connect* and then on *SSH*.
![ConnectSSH](img/connect-ssh.png)
#### 41. Click on the *Cloud Shell* icon at the top of the page.
![CloudShellIcon](img/cloud-shell-icon.png)
#### 42. You will neet to create a *Storage Account* to use Cloud Shell; just click *Create storage* to do so and wait a couple of seconds.
![CreateStorage](img/create-storage.png)
#### 43. Copy the key at the end of the 4th step on how to connect to your first VM.
![CopyKeyVM1](img/copy-ssh-vm1.png)
#### 44. Paste it inside the command line writing *ssh* and a space before it.
![ConnectToVM1Command](img/connecting-to-vm1-command.png)
#### 45. Type *yes* and press enter.
![Yes](img/yes.png)
#### 46. Repeat step 46, enter your password and press enter.
![VM1Login](img/vm1-login.png)
#### 47. You will now be connected to your first VM.
![ConnectedToVM1](img/connected-to-vm1.png)
###### Extra: Insert *sudo apt-get moo* to see a cow
![Moo](img/moo.png)
#### 48. Go back to your virtual networks and select your other virtual network.
![OtherVirtualNetworkPanel](img/other-vn-panel.png)
#### 49. Type on connected devices and copy the IP address of your other virtual machine.
![OtherVMIP](img/connected-devices.png)
#### 50. If you try to ping your second VM from your first VM, you will see no response. Let's fix that.
![PingFail](img/ping-fail.png)
#### 51. Go to your first VM and click on *Peerings*.
![Peerings](img/peerings.png)
#### 52. Click on *Add*.
![AddPeering](img/add-peering.png)
#### 53. Give names to your peerings.
![PeeringNames](img/peering-names.png)
#### 54. Select the virtual network to peer to (the other one).
![PeeringNetwork](img/select-peering-network.png)
#### 55. Click *Add*.
![Add](img/add.png)
#### 56. Wait a bit until the peering is ready. Once you refresh the page and the *Peering status* is set to *Connected*, you're ready.
![Connected](img/peering-status-connected.png)
#### 57. Open cloud shell again, connect to your first VM and copy your other VM's IP address (steps 39 to 49).
#### 58. If you try to ping your other VM, you will now see that there are responses, which means they are now connected.
![PingSuccesful](img/ping-succesful.png)

---------------------------------------------------------


## Congratulations ! You've just made your connected 2 virtual machines and networks using the Azure Portal !
Don't forget to delete or turn off your resources once you're done!