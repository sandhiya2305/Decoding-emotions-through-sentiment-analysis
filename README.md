import pandas as pd
from textblob import TextBlob

# Sample dataset of sentences
data = {
    'Text': [
        'I love this product!',
        'This is the worst movie I have ever seen.',
        'I feel amazing today!',
        'I am not happy with the service.',
        'The food was okay, nothing special.',
        'Absolutely fantastic experience!',
        'It was a total disaster.'
    ]
}

# Create DataFrame
df = pd.DataFrame(data)

# Function to analyze sentiment
def get_sentiment(text):
    analysis = TextBlob(text)
    polarity = analysis.sentiment.polarity
    if polarity > 0:
        return 'Positive'
    elif polarity < 0:
        return 'Negative'
    else:
        return 'Neutral'

# Apply sentiment analysis
df['Sentiment'] = df['Text'].apply(get_sentiment)

# Display results
print(df)
