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

## se quiser synergy para trabalhar ##

sudo apt-get install synergy

synergyc (ip do servidor)

## end synergy##

##nstalling PIP:##

# download de scripts de instalação
    curl -O https://bootstrap.pypa.io/get-pip.py

#executar os scripts para insalação (instalado em ~/.local/bin)
    python get-pip.py --user

## end pip##

## install aws cli ##

## install in user and check for upgrades and connect 
    pip3 install awscli --upgrade --user

    export PATH=~/.local/bin:$PATH

    #Create credentials to acess te tools you want
    #https://www.youtube.com/watch?time_continue=225&v=_f0d2pLJjiA

    aws configure
    #put credentials and other things

## end aws cli 

## create thing in aws

# create a thing with a name and atribute required
    
    #gerar id aleatório no futuro
    aws iot create-thing --thing-name "clitest1" --attribute-payload "{}"

# create Cer priv and pub keys

    aws iot create-keys-and-certificate --set-as-active --certificate-pem-outfile "Cer-PEM" --public-key-outfile "Pub-KEY" --private-key-outfile "Priv-KEY"

    #usar nome gerado e principal(gerado no comando anterior)
    aws iot attach-thing-principal --thing-name "clitest1" --principal "arn:aws:iot:us-east-1:603656461584:cert/09628a3525b7796c6d7c5cb5bda5aa58f9d0f35ccc9fdabb345e000ff86a351e"

    #baixa e criar politica de uso IoT (colocar política no git)
    aws iot create-policy --policy-name IoTGate --policy-document file://IoTPolicy.json

    #anexar a política na coisa precisa do ARN !DO CERTIFICADO! criado na hora de gerar a coisa
    aws iot attach-policy --policy-name "IoTGate" --target "arn:aws:iot:us-east-1:603656461584:cert/09628a3525b7796c6d7c5cb5bda5aa58f9d0f35ccc9fdabb345e000ff86a351e"

    #criar thing shadow 
    aws iot-data (ver comandos mais pra frente)


## 




