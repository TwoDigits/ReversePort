# ReversePort
Create a ssh tunnel to a public server and reverse forward a defined port.

# Why
we have a PiCluster which is sitting in our office in Cologne. To be able to remotely access it via internet we needed a way to forward the ssh port.

# How
First of all you need a publicly accessible server (for example a AWS Lightsail starting at 3,5$ a Month).
Make sure you can login via public key method. (checkout https://kb.iu.edu/d/aews)

Modify /etc/ssh/sshd_config and add/modify the following line
GatewayPorts clientspecified

Make sure your firewall allows incoming traffic for your desired port.

On the local device on which you want to expose the port you have to run the following command:
ssh -N -R :<desired public port>:localhost:<desired local port> <user on server>@<server hostname/ip>

This establishes a ssh tunnel and creates a new port on the server side where all communication to this port will be forwared through the tunnel to the local maschine.

the provided script is a sample implementation for a SystemV init script. (original template from : https://github.com/fhd/init-script-template/blob/master/template )
