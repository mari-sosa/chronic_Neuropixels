# chronic_Neuropixels
Setup documentation for syncing chronic Neuropixels recordings with video

## Specifications

The included wiring diagrams and photo apply to the following hardware/software:

Camera: [Basler acA780-75gc (CS-mount)](https://www.edmundoptics.com/p/basler-ace-aca780-75gc-color-gige-camera/29513/)  \
I/O cable: [Basler gray Power-I/O Hirose cable (HRS 6P/OPEN)](https://docs.baslerweb.com/basler-power-io-cable-hrs-6p-open-twisted-p)  \
NIDAQ (National Instruments) breakout box: BNC-2110  \
PXIe card: PXIe-6341 card  \
PXIe chassis: 1071  \
Neural, I/O acquisition software: [SpikeGLX](https://billkarsh.github.io/SpikeGLX/#what-is-spikeglx)

This setup is used for acquisition of neural, behavioral, and video data from freely moving animals with chronic Neuropixels implants in Lisa Giocomo's lab at Stanford University.

The TTL signal from the camera is supplied with a 5V DC power supply that is separate from the 12V power applied to operate the camera (camera power can also be supplied via gigE, i.e. via the ethernet cable used to acquire video frames). The TTL signal line and ground are connected to an alligator-to-BNC cable plugged into an analog input on the NIDAQ. 

NOTE: The analog TTL voltage received by the NIDAQ is slightly variable from day to day -- this is a property of the Basler camera that cannot be circumvented, to our knowledge. We set a threshold around 2.5V to detect the TTLs using [CatGT](https://billkarsh.github.io/SpikeGLX/help/dmx_vs_gbl/dmx_vs_gbl/).

### Wiring information for the Hirose cable

| Pin Number	| Wire Color | Function |
| --- | --- | --- |
| 1	| Brown	| Camera Power |
| 2	| Pink | Opto-isolated IN (Line1) |
| 3	 | Green |	Not connected	|
| 4	 | Yellow |	Opto-isolated OUT (Out1) |
| 5 |	Gray |	Opto-isolated I/O Ground |
| 6	| White |	Camera Power Ground |


