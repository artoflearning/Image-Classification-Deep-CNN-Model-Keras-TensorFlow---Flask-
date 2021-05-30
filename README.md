# Image Classification Deep Learning CNN REST API (Keras TensorFlow + Flask)
This repository contains the code for [*Building a simple Keras + deep learning REST API*](https://blog.keras.io/building-a-simple-keras-deep-learning-rest-api.html), published on the Keras.io blog.

The method covered here is intended to be instructional. It is _not_ meant to be production-level and capable of scaling under heavy load.

## Getting started

I assume you already have Keras (and a supported backend) and TensorFlow installed on your system. From there you need to install [Flask](http://flask.pocoo.org/) and [requests](http://docs.python-requests.org/en/master/):

```sh
$ pip install flask gevent requests
```
*NOTES
- the original code has had all import statements of from keras updated to tensorFlow.keras
- ignore cudart64_110.dll GPU error
- may need to:
```sh
$ pip uninstall tf-nightly
```
and 
```sh
$ pip install tensorflow --upgrade --force-reinstall
```
if receiving keras.utils.generic_utils module AttributeError.

Next, clone the repo:

```sh
$ git clone https://github.com/jrosebr1/simple-keras-rest-api.git
```

## Starting the Keras server

Below you can see the image we wish to classify, a _dog_, but more specifically a _Shih-Tzu_:

![dog](dog.jpg)

The Flask + Keras server can be started by running:

```sh
$ python run_keras_server.py 
Using TensorFlow backend.
 * Loading Keras model and Flask starting server...please wait until server has fully started
...
 * Running on http://127.0.0.1:5000
```

You can now access the REST API via `http://127.0.0.1:5000`.

## Submitting requests to the Keras server

Requests can be submitted via cURL:

```sh
$ curl -X POST -F image=@dog.jpg 'http://localhost:5000/predict'
{
  "predictions": [
    {
      "label": "Shih-Tzu", 
      "probability": 0.7272
    }, 
    {
      "label": "Pekinese", 
      "probability": 
  "success": true
}
```

Or programmatically:

```sh
$ python simple_request.py 
1. Shih-Tzu: 0.7272
2. Pekinese: 0.1508
3. Lhasa: 0.0415
4. Japanese_spaniel: 0.0225
5. Sussex_spaniel: 0.0165
```
