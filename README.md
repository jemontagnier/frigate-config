# Frigate NVR configuration

## Host Configuration
- CPU: `Intel(R) Core(TM) i7-8700T CPU @ 2.40GHz`
- GPU: `Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630]`

## Guest Configuration
- Frigate Guest Type: `LXC (on Proxmox)`
- CPU: `2 `
- Memory: `4Go`
- Swap: `512Mo`
- OS: `15Go NVMe`
- Media: `130 Go SSD`

## TPU
- Google Coral USB-C

## Cameras
- Annke C800
- Hikvision HWI-T240H
- Wanswiew W4
- Foscam C1

## Frigate Customization 

### Annke C800 
#### Main stream configuration:

    Resolution: 3840x2160
    Bit rate type: Variable
    Video quality: Superior 
    Max. bit rate: 4096
    Avegrage bit rate: 2048 
    Frame rate: 15
    Video encoding: H.265
    H.265+: On
    SVC: OFF

Because Annke C800 maximum substream resolution is low (640x480), I use go2rtc to create a custom substream (1280x720) instead of using main stream to detect role.
This is consuming few cpu than using main stream on detect & record and detection is very better on small object.

### Hikvision HWI-T240H 
#### Main stream configuration:

    Resolution: 2560x1440
    Bit rate type: Variable
    Video quality: Superior 
    Max. bit rate: 4096
    Avegrage bit rate: 2048 
    Frame rate: 15
    Video encoding: H.264
    H.264+: On
    WDR: On

#### Sub stream configuration:

    Resolution: 640x330
    Bit rate type: Variable
    Video quality: Superior 
    Max. bit rate: 512
    Frame rate: 6
    Frame interval: 20
    Profil: High
    Video encoding: H.264

## Statistics 

- Avergage load: `0.66 (CPU: 4%, GPU: 15%)`
- Avergage Inference speed: `8,84ms`
- Average Memory Usage: `58%`