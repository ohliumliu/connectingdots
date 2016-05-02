* Processes
  * Get all the relevant strings and filter out specific words that are irrelevant. Split it into a list of words
  * Stem each word using a stemmer (for example, nltk.stem.snowball). It converts a word to its "stem" which is shared a group of similar words. This reduces the feature space. Convert the word list back to a string.
  * Vectorize all the strings. It essentially counts the word frequency. The result is a sparse matrix (n_sample, n_feature). sklearn.feature_extraction.text This is actually comprised of two step: fit -- get the feature vectors, transform -- do the counting.
  * Tfidf transformation. Tf (term frequency) is the result of vectorization. Idf (inverse document frequency) is a normalization procedure applied on the result of vectorization that puts more weight on the rare words.
  * Vectorization and Ifidf transformation is available in a single class TfidfVectorizer.
  * Remove the stopwords (high frequency, low information words). Use nltk to find stopwords. TfidfVectorizer has a built-in stop word list.
