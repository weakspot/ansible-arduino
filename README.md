# ansible-arduino
### Ansible playbook for installing inotool, picocom and dependencies on a Raspberry Pi to enable serial communications with Arduino.
---
This playbook has been tested
April 2nd 2016:
Raspberry Pi 2 Model B Raspbian kernel release 4.1.19-v7+

Instructions:<br />
1. Update the *hosts* file to use the IP's of your raspberry pi below the [pis] group.<br />
2. In the same file, update your username under the [pis:vars] section.<br />
3. You should be using SSH keys, but if you have not setup them, you may uncomment the line "#ansible_ssh_pass=raspberry" by removing the '#' sign, and replacing 'raspberry' with your own password.<br />
4. Save the changes.

Once you've done that simply run:
```bash
ansible-playbook -i hosts inotool.yml
```

After installation is complete, test the serial communications:
Install some test code to the Arduino which outputs text, e.g. "Serial.println("test output");". <br />
Make sure you use 9600 bps: "Serial.begin(9600);" in void setup().
Connect the Arduino to Raspberry Pi USB port.
Log in to Raspberry Pi and run:
```bash
ino serial -b 9600
```
You should see your test output printed on the screen. If not, reboot helps.<br />
To exit inotool (picocom) use Ctrl+A Ctrl+X.
