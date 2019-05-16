IoTGate

based in raspbian lite:

Create distro with SSH:

 1. Format SD Card 
 2. Write Raspbian To SD Card 
 3. After the Image as been written to the SD Card. 
 4. Now to get SSH enabled before turning on the Pi 
 5. Open Command Prompt, 
 6. Confirm drive letter of Boot Mine is E: 
 7. Type in "dir E:" 
 8. After the files load you are safe to type the following command to create a SSH file that enables SSH as default to finish installation over terminal.
 Type "echo(RightBracket)E:\SSH" - Unable to place a right bracket here due to youtube text box. 
 9. You will now be able to see a SSH file on the boot partition, Eject the SD Card and place it in the Raspberry Pi 
 10. Plug the network cable into the Pi and power the device 
 11. Confirm IP Address of the Pi, By typing in ping raspberrypi in Command Prompt -192.168.1.251- 
 12. Load Putty and type in the IP address of the Pi you got in the step above - Click yes 
 13. When asked username is "pi", and password is raspberry 
 14. When you have logged in type in the following command "sudo raspi-config" this will load the last part of the installation 
 15. Now you are free to make the final changes to your Pi, 
    -Expand FileSystem, 
    -Change User Password 
    -Overclocking (Your Choice)
    -Advanced Hostname if you want, SSH and i would enable even tho you are using it to make sure when its finished installation it will still be enabled

sudo apt-get update

sudo apt-get upgrade

- se quiser synergy para trabalhar

sudo apt-get install synergy

synergyc (ip do servidor)

Requisitos CLI AWS:

#download de scripts de instalação
    curl -O https://bootstrap.pypa.io/get-pip.py

#executar os scripts para insalação (instalado em ~/.local/bin)
    python get-pip.py --user