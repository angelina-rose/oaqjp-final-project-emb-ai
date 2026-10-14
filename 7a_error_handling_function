import requests  # Import the requests library to handle HTTP requests
import json

def emotion_detector(text_to_analyze):
    url = 'https://sn-watson-emotion.labs.skills.network/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict'
    myobj = { "raw_document": { "text": text_to_analyze } }  # Create a dictionary with the text to be analyzed
    header = {"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"}
    response = requests.post(url, json = myobj, headers=header)  # Send a POST request to the API with the text and headers
    # If the response status code is 200, extract response
    if response.status_code == 200:
        # Parse the response from the API
        formatted_response = json.loads(response.text)
        # Saving each of the emotion scores
        anger_score = formatted_response['emotionPredictions'][0]['emotion']['anger']
        disgust_score = formatted_response['emotionPredictions'][0]['emotion']['disgust']
        fear_score = formatted_response['emotionPredictions'][0]['emotion']['fear']
        joy_score = formatted_response['emotionPredictions'][0]['emotion']['joy']
        sadness_score = formatted_response['emotionPredictions'][0]['emotion']['sadness']
        
        # Returning a dictionary containing analysis results
        emotion_scores={'anger': anger_score,
        'disgust': disgust_score,
        'fear': fear_score,
        'joy': joy_score,
        'sadness': sadness_score}

        dominant_emotion=max(emotion_scores,key=emotion_scores.get)
        emotion_scores['dominant_emotion']=dominant_emotion
   # If the response status code is 400, set label and score to None
    elif response.status_code == 400:
        emotion_scores={'anger': None,
        'disgust': None,
        'fear': None,
        'joy': None,
        'sadness': None,
        'dominant_emotion':None}
    return emotion_scores
        
	

	