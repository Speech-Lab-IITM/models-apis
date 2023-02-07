# Speech Lab IITM Models and APIs
## ASR v2 API Documentation

Our ASR API accepts the following three inputs in the request:

-   **file** - the audio or video file to be transcribed
    
-   **language** - the language of the source audio/video in all lowercase (eg: tamil, english)
    
-   **vtt** (optional) - whether a webVTT caption file has to be generated. This is an optional value. It accepts two string values either true or false. By default, this is false. This can be used for captioning purposes.
    

  

On success, the API returns a JSON response with the following fields:

-   **status**: success
    
-   **time_taken**: time taken to transcribe the given audio/video in seconds
    
-   **transcript**: the transcription of the given input
    
-   **vtt**: WebVTT caption if it was requested
    

  

On failure, the API returns a JSON response with the following fields:

-   **status**: failure
    
-   **reason**: The reason for failure of the request
    

  

Sample audio files to test API: [English](https://drive.google.com/file/d/1ucJCfKfKr00_09H8_FmW57xFYHYPzC2h/view?usp=share_link), [Tamil](https://drive.google.com/file/d/19tgIL2YeZ-vU9eABePeBL_O1f1jWp2Sv/view?usp=share_link)

  

Our ASR API accepts files of most common formats such as mp3, mp4, wav, ogg etc.,

Currently supported languages:

1.  English
    
2.  Tamil
    
3.  Hindi
    
4.  Gujarati
    
5.  Kannada
    
6.  Marathi
    
7.  Telugu
    

### CURL Example:

Request: ```curl -v -X POST -F 'file=@voice.mp3' -F 'language=english' -F 'vtt=true' https://asr.iitm.ac.in/asr/v2/decode```

Response: {"status":"success","time_taken":"4.61","transcript":"welcome to madras program thank you","vtt":"WEBVTT\n\n00:00:00.800 --> 00:00:04.600\nwelcome to madras\n\n00:00:04.900 --> 00:00:10.000\nprogram thank you"}

  

### Python Example:
```
import requests


files = {

'file': open('tamil.mp3', 'rb'),

'language': (None, 'tamil'),

'vtt': (None, 'true'),

}

response = requests.post('https://asr.iitm.ac.in/asr/v2/decode', files=files)

print(response.json())
```
  

### Web Demo:

[https://asr.iitm.ac.in/asr/v2](https://asr.iitm.ac.in/asr/v2)
