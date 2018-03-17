*************
Twitton
*************

.. image:: https://img.shields.io/pypi/v/twitton.svg?style=flat-square
    :target: https://pypi.python.org/pypi/twitton/
    :alt: PyPi version

.. image:: https://readthedocs.org/projects/twitton/badge/?version=latest
     :target: https://twitton.readthedocs.org/en/latest/
     :alt: Documentation


.. image:: https://img.shields.io/github/last-commit/marcosvbras/twitton.svg
     :alt: GitHub last commit


.. image:: https://img.shields.io/github/issues-raw/marcosvbras/twitton.svg
     :alt: GitHub issues


.. image:: https://img.shields.io/github/license/marcosvbras/twitton.svg
     :alt: license


.. image:: https://img.shields.io/github/forks/marcosvbras/twitton.svg?style=social&logo=github&label=Fork
     :alt: GitHub fork


.. image:: https://img.shields.io/github/stars/marcosvbras/twitton.svg?style=social&logo=github&label=Stars
     :alt: GitHub stars

**Twitton** is a Python library that provides easy Twitter Search API use.

With this library you can:

* Create powerful searches
* Get all available tweet information
* Use your own Twitter search URL's

Installation
############
Run the command:

.. code-block:: python

  pip install twitton

Basic use
############
Import the **TweetSearch** class and create an object. Pass **consumer_key**, **consumer_key_secret**, **access_token** and **access_token_secret** arguments to constructor.

.. code-block:: python

  from twitton import TweetSearch

  tweet_search = TweetSearch(
      consumer_key,
      consumer_secret,
      access_token,
      access_token_secret
    )

**NOTE**: These arguments are required. Twitter API calls always requires authentication.

Then, specify some search arguments

.. code-block:: python

  tweet_search.set_keyword_list(['Star Wars', 'movie'])
  tweet_search.set_result_type("recent")
  tweet_search.set_language("en")
  tweet_search.set_max_tweet_response(100)
  result = tweet_search.search_tweets()

This settings will look up for tweets that contains "Star Wars" and "movie", published recently, written in english and will return 100 results.

You can iterate the object to get all available tweet dict:

.. code-block:: python

  for tweet in result:
    print(tweet)

Do you need more results? Search for the next tweets in sequence

.. code-block:: python

  result = tweet_search.search_older_tweets()

... or search for the new ones published after your last search

.. code-block:: python

  result = tweet_search.search_newer_tweets()
