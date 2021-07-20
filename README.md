# review-report-system
try:
    text = r.recognize_google(audio, language='en-GB')
    print("You said " + text)
   
except sr.UnknownValueError:
    print("Google Speech Recognition could not understand audio")
except sr.RequestError as e:
         print("Could not request results from Google Speech Recognition Service; {0}".format(e))
###########################################################################################         
##Step 3. Using TextBlob perform Sentiment Analysis, POS tagging etc.,        
# sentiment analysis using TextBlob.
print(text)
text = TextBlob(text)    

#1. Parts of Speech tagging POS
pos= text.tags
print(pos)

#2. Sentiment Analysis
    # setiments result will be tuple (polarity, subjectivity)
    # polarity ranges from -1 to 1 
        # -1 -> Negative sentiments 
        # 1  -> Positive sentiments
    # Subjectivity ranges from 0 to 1
        # 0 -> very objective
        # 1 -> very subjective
senti = text.sentiment
print(senti)

# appropriately print the review status.
if(senti.polarity<0):
    review = "Sorry to say it was Negative review, I appreciate your feedback"
    print("Negative review")
else:
    review = "Thanks for the positive review, I appreciate your feedback"
    print("Positive review")

#using Googles text to speech
import pyttsx3
engine = pyttsx3.init()
engine.say("Hello this is vara talking")
engine.say("echoing your words")
engine.say(text)
engine.say(review)
engine.setProperty('rate',125)
engine.setProperty('volume',1.0)
engine.runAndWait()

									
