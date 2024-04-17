import nltk
from nltk.chat.util import Chat, reflections

# Define some patterns and responses
patterns = [
    (r'hi|hello|hey', ['Hello!', 'Hi there!', 'Hey!']),
    (r'how are you?', ['I\'m doing well, thank you!', 'I\'m great, thanks for asking.']),
    (r'(.*) travel plans (.*)', ['I can help you with your travel plans. Where do you want to go?', 
                                  'Sure, tell me where you want to travel.']),
    (r'I want to travel to (.*)', ['That sounds exciting! When are you planning to go to {}?', 
                                   'Great choice! When are you thinking of going to {}?']),
    (r'I want to go on a (.*)', ['That sounds like fun! Where would you like to go?', 
                                 'Awesome! Where do you want to go for your {}?']),
    (r'I am planning to go to (.*)', ['When are you planning to go to {}?', 
                                      'Nice! When are you thinking of going to {}?']),
    (r'(.*) thanks', ['You\'re welcome!', 'No problem.']),
    (r'(.*)', ['Could you please provide more details?', 'I\'m not sure I understand.']),
]

# Create a Chat object
chatbot = Chat(patterns, reflections)

def travel_bot():
    print("Welcome to the Travel Chatbot! How can I assist you today?")
    while True:
        user_input = input("You: ")
        if user_input.lower() == 'quit':
            print("Goodbye!")
            break
        else:
            print("Bot:", chatbot.respond(user_input))

# Run the chatbot
if __name__ == "__main__":
    nltk.download('punkt')
    travel_bot()
