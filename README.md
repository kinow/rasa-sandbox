# Rasa Sandbox

A sanbox for [Rasa NLU](https://github.com/RasaHQ/rasa_nlu).

How to run the sample (or what I did):

1. - On a simple Linux (in my case, Ubuntu LTS)...
2. - Install latest Python Anaconda 3
3. `pip install rasa_nlu`
4. `pip install python-crfsuite`
5. - Following instructions from [spaCy quickstart page](https://spacy.io/docs/usage/)...
6. `conda config --add channels conda-forge`
7. `conda install spacy` (this takes a bit...)
8. `python -m spacy download en` (this one takes a while...)
9. - Train the Chat model...
10. `python -m rasa_nlu.train -c config_spacy.json`
11. - Start the Chat server
12. `python -m rasa_nlu.server -c config_spacy.json --server_model_dirs=model_20170628-151706/` (the date here will, very likely, be different in your computer)
13. - That will start a server on your current terminal window, open another window and test it:
14. `curl -XPOST localhost:5000/parse -d '{"q":"I am looking for Chinese food"}' | python -mjson.tool`

If everything is OK, you should get something as:

```
curl -XPOST localhost:5000/parse -d '{"q":"I am looking for Chinese food"}' | python -mjson.tool
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   545  100   508  100    37   102k   7619 --:--:-- --:--:-- --:--:--  124k
{
    "entities": [],
    "intent": {
        "confidence": 0.7767037924370481,
        "name": "restaurant_search"
    },
    "intent_ranking": [
        {
            "confidence": 0.7767037924370481,
            "name": "restaurant_search"
        },
        {
            "confidence": 0.0956471273154457,
            "name": "greet"
        },
        {
            "confidence": 0.09080398877697965,
            "name": "goodbye"
        },
        {
            "confidence": 0.036845091470526566,
            "name": "affirm"
        }
    ],
    "text": "I am looking for Chinese food"
}
```

Tutorial link: [https://rasa-nlu.readthedocs.io/en/latest/tutorial.html](https://rasa-nlu.readthedocs.io/en/latest/tutorial.html)
