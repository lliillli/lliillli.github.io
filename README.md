
# 1. Final project Video

You can find our project video by clicking this [link](https://drive.google.com/file/d/1OxCNUOv104NPlGW3K9_btHVaHvuEmDWO/view?usp=drive_link) or watching the video below:

<div style="display:flex; justify-content:center; margin:20px 0;">
  <video style="max-width:960px; width:100%;" controls>
    <source src="./video/team18glove.mp4" type="video/mp4">
  </video>
</div>


# 2. Final projects Images

<div style="display:flex; gap:40px; justify-content:center; margin:20px 0;">
  <img src="./image/PALM.jpg" style="max-height:250px; border-radius:6px;">
  <img src="./image/Final_glove1.jpg" style="max-height:250px; border-radius:6px;">
  <img src="./image/Final_glove2.jpg" style="max-height:250px; border-radius:6px;">
  <img src="./image/FINAL_glove3.png" style="max-height:250px; border-radius:6px;">
</div>


# 3. SRS


| ID     |                                                                                                                                                                                          Description                                                                                                                                                                                          | Validation Outcome                                                                                                                                                                                       |
| ------ | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SRS-01 |                                                                                                               The ATmega328PB shall measure heart-rate using ADC sampling driven by Timer1 ISR, compute IBI, and output BPM within the valid physiological range (40–170 bpm).                                                                                                               | **Confirmed.** The BPM values are compared with the measure results from Apple Watch. However it sometimes gives unexpected results due to hardware reasons.                                       |
| SRS-02 |                                                                                                                   The system shall classify hand gestures using three flex sensors, converting ADC readings into a 3-bit gesture code (0–7) based on threshold comparison.                                                                                                                   | **Confirmed.** Repeated fist/palm/other finger motions were recorded. LED and LCD changes match the 3-bit output.                                                                                 |
| SRS-03 |                                                                                                                                             The ATmega328PB shall transmit the current BPM and gesture state to the ESP32 using the UART protocol                                                                                                                                             | **Confirmed.** UART output are shown on the HTTP webpage.                                                                                                                                          |
| SRS-04 |                                                                                                                                        The LCD UI shall display the current BPM, the current gesture name, and a continuously beating heart animation.                                                                                                                                        | **Confirmed.** LCD output recorded in video demonstrates correct BPM text updates, real-time gesture rendering, and smooth heart-size toggling every ~200 ms.                                      |
| SRS-05 |                                                                                                                                         The WS2812 LED strip and LED ring shall change color according to the gesture code using predefined patterns.                                                                                                                                         | **Confirmed.** Visual inspection during testing shows gesture transitions immediately update LED colors.                                                                                           |
| SRS-06 |                                                                                                            The ESP32 shall correctly record microphone audio through I2S,  execute keyword-spotting inference (“Jarvis” vs. “Other”) using the deployed TFLite Micro model.                                                                                                            | **Partially Confirmed.** The full audio pipeline is verified functional: I2S recording works, ring buffer is stable. However, the model that are deployed does not maintain satisfactory accuracy. |
| SRS-07 | The ESP32 shall host a Wi-Fi provisioning AP with an embedded webpage for scanning available networks and entering credentials. After provisioning, the ESP32 shall switch to STA mode, auto-connect to the saved Wi-Fi credentials, and store IP information. Once STA is connected, the ESP32 shall run a simple HTTP status server displaying mode, detected voice, and gesture values. | **Confirmed.** AP mode launches successfully; The web dashboard loads at the assigned IP, updates via  JSON polling, and reflects changes from both KWS and ATmega UART data.                     |

#### 3.2 Hardware Requirements Specification (HRS) Results
