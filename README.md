
ibrahemhassan55/ibrahemhassan55 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
from flask import Flask, jsonify, request
import numpy as np
import tensorflow as tf
# Create a Flask app
app = Flask(__name__)
# Load the generative model
model = tf.keras.models.load_model('my_model.h5')
# Define the API endpoints
@app.route('/generate_word', methods=['GET'])
def generate_word():
  # Generate a word
  word = model.generate_word()
  # Return the word
  return jsonify({'word': word})
@app.route('/generate_words', methods=['POST'])
def generate_words():
  # Get the number of words to generate
  num_words = request.args.get('num_words', 10)
  # Generate words
  words = model.generate_words(num_words)
  # Return the words
  return jsonify({'words': words})
# Run the app
if __name__ == '__main__':
  app.run()
