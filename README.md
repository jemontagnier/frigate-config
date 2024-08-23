# Frigate NVR configuration

## Host Configuration
- CPU: `Intel i7-8700T (1) @ 2.399GHz`
- GPU: `Intel Corporation CoffeeLake-S GT2 [UHD Graphics 630]`

## Guest Configuration
- Frigate Guest Type: `LXC (on Proxmox)`
- CPU: `2 `
- Memory: `4Go`
- Swap: `512Mo`

## TPU
- Google Coral USB-C

## Cameras
- Annke C800
- Wanswiew W4
- Foscam C1

## Frigate Customization 

Annke C800 main stream configuration:

    Resolution: 3840x2160
    Bit rate type: Constant 
    Frame rate: 15
    Max. bit rate: 2048 
    Video encoding: H.265
    H.265+: OFF
    Frame interval: 30
    SVC: OFF

Because Annke C800 maximum substream resolution is low (640x480), I use go2rtc to create a custom substream (1280x720) instead of using main stream to detect role.
This is consuming few cpu than using main stream on detect & record and detection is very better on small object.

Average load without custom config (main stream for both record and detect exterieur1 camera): `1,2`.

## Statistics 
Exported to Grafana with [frigate-exporter](https://github.com/bairhys/prometheus-frigate-exporter)

- Avergage load: `0.66 (CPU: 4%, GPU: 10%)`
- Avergage Inference speed: `8,84ms`
- Average Memory Usage: `58%`