# Ansible Role: Raspberry Pi PoE fan control 

An Ansible role that configures Raspberry Pi PoE Fan speeds.  The Fans are controlled by the 
Rasperry Pi via I2C.  They turn on and off depending on the temperature of the processor. One 
can manipulate when the fan turns on/off and at which temperature the fan speed will ramp up.
This is extremely useful when using Rpi's in a cluster.

## Requirements
Must be running an up-to-date version of RaspberryPi OS. A reboot is required after running 
the role, the role **will not** perform a reboot.

## Role Variables
Default settings are set by default (see `defaults/main.yml`)

```
# Default fan temperature and temperature deltas
# temperatures are in millicelcius, 40000 == 40C

# Temperature at which fan turns on | Temp delta which fan turns off.
poe_temp0: poe_fan_temp0=40000,poe_fan_temp0_hyst=2000

# Temperature at which fan speeds up | Temp delta which fan slows down.
poe_temp1: poe_fan_temp1=45000,poe_fan_temp1_hyst=2000

# Temperature at which fan speeds up | Temp delta which fan slows down.
poe_temp2: poe_fan_temp2=50000,poe_fan_temp2_hyst=2000

# Temperature at which fan speeds up | Temp delta which fan slows down.
poe_temp3: poe_fan_temp3=55000,poe_fan_temp3_hyst=5000
```


## Dependencies

None.

## Example Playbook

```yaml
- hosts: pis
   
  vars:
    poe_temp0: poe_fan_temp0=48000,poe_fan_temp0_hyst=2000
    poe_temp1: poe_fan_temp0=55000,poe_fan_temp0_hyst=2000
    poe_temp2: poe_fan_temp0=60000,poe_fan_temp0_hyst=2000
    poe_temp3: poe_fan_temp0=65000,poe_fan_temp0_hyst=5000
      
  roles:
    - 34fathombelow.rpi_poe_fancontrol 
```

## License

MIT

                                                                                     
