# Speech-Recognition
import speech_recognition as sr   #text to audio
import pyttsx3    # audio to text


r=sr.Recognizer() #it recognize the voice
  


def speakText(command):
     # Initialize the engine
     engine = pyttsx3.init()
     engine.say(command)
     engine.runAndWait()

while(1):
    try: #manage the error
        with sr.Microphone() as source:  #input source 
            print("wait for the calibaration")
            r.adjust_for_ambient_noise(source,0) #it ignoer the background noises
            print("start speaking")# 1 refers to the male voice
            audio=r.listen(source) #input is getting from the sources r
            speech=r.recognize_google(audio) # this  will convert audio to the text
            speech=speech.lower() #  the letter will be displayed lower
            

            print("did you say"+ speech)#the text will be printed
            speakText(speech) # here we are calling the speechText calling the text here
    except sr.UnknownValueError:
        print("Unknown error occured")    
