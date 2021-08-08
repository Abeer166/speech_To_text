# speech_To_text
I have to method to do it 
first : The following is  using Watson to real time transcribe from Speech to Text using the websockets streaming API.
git clone https://github.com/nicknochnack/RealTimeSpeechToText/tree/main/watson-streaming-stt
virtualenv -p python3 .venv
source .venv/bin/activate
cd watson-streaming-stt
pip install pyaudio
pip install websocket-client
Getting Started by :
python3.9 transcribe.py -t 2


<img width="564" alt="Screen Shot 1442-12-29 at 6 11 02 AM" src="https://user-images.githubusercontent.com/56722657/128619473-f8167aaa-b712-4c2a-904f-6e8afe660f59.png">




the second method by audio file ..........

from ibm_watson import SpeechToTextV1

from ibm_watson.websocket import RecognizeCallback, AudioSource

from ibm_cloud_sdk_core.authenticators import IAMAuthenticator

apikey = 'JXbLacbFdspDyhWxsqBTU77nhSFg-VbPORSV0vTmZQ5M'

url = 'https://api.us-east.speech-to-text.watson.cloud.ibm.com/instances/e7c29f37-a63e-4254-9bf8-2e250d02b340'

authenticator = IAMAuthenticator(apikey)

stt = SpeechToTextV1(authenticator=authenticator)

stt.set_service_url(url)

with open('/Users/abeerabdullah/Desktop/winston.mp3', 'rb') as f:

    res = stt.recognize(audio=f, content_type='audio/mp3', model='en-US_NarrowbandModel', continuous=True).get_result()
		
    res
	
    text = res['results'][0]['alternatives'][0]['transcript']
		
    text
    confidence = res['results'][0]['alternatives'][0]['confidence']
		
    confidence
    with open('output.txt', 'w') as out:
		
        out.writelines(text)
				
       <img width="1407" alt="Screen Shot 1442-12-29 at 6 03 24 AM" src="https://user-images.githubusercontent.com/56722657/128619536-32c6f0a3-9310-46b6-b3e1-c9bcd19ccb2b.png">



