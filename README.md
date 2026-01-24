# brainbit-headphone-eeg-recorder
Python script to connect to BrainBit headphones and collect raw EEG to CSV via NeuroSDK

## Features
- Scans for BrainBit EEG headphones (10 seconds) {time adjustable}
- Connects automatically to the first detected device
- Records EEG for the specified duration
- Exports data into a new CSV file each run (e.g., 'brainbit_eeg_2026-01-24_15-30-12.csv')

## Requirement
- Python 3.12
- NeuroSDK (Brainbit SDK)
- BrainBit EEG headphone device (Bluetooth)

## Installation
### 1. Install Python 3.12
To check your version:

```bash
python --version
```

You should see:
```bash
Python 3.12.x
```
### 2. Install NeuroSDK
Install NeuroSDK using BrainBit's official instructions: https://sdk.brainbit.com/sdk2_python_install/

## How to run
### Run the script
```bash
py -3.12 brainbit_EEG_recorder.py
```

### Output
Each run generates a new CSV file like this: 
```
brainbit_eeg_YYYY-MM-DD_HH-MM-SS.csv
```

### CSV columns
The output file contains the following columns:
1. t_sec --- time in seconds since recording started
2. pack_num --- Packet number
3. marker --- Marker value (if available)
4. ch1, ch2, ch3, ch4 --- EEG channels (the one I am using has 4 channels)

## Configuration
You can change how long it records by changing:
```python
RECORD_SECONDS = 10
```

You can also change the scanning time by changing:
```python
sleep(10)
```

## Notes
* Make sure your BrainBit headset is powered on and is ready for pairing, of course.
* The script currently scans using:
* ```python
  Scanner([SensorFamily.LEHeadPhones2])
  ```
  If you have a different Brainbit model, you may need to change the SensorFamily part
* The program connects to the first device found. If multiple devices are nearby, it may connect to a different one.

## License
MIT License
