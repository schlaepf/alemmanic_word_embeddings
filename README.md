# alemmanic_word_embeddings

This repository consists of two IPython notebooks which can be used to train alemannic word embeddings using word2vec. \
The first one (`alemmanic_wiki_articles_preprocessing`) is only used for preprocessing of the alemannic wikipedia. The output of that notebook is the processed wikipedia dump (`wiki_articles_preprocessed.pkl`). This is a list of sentences, which itselves are list of tokenized words.\
The second notebook (`word2vec_alemmanic_wiki`) reads the preprocessed wikipedia dump and trains a word2vec model using the gensim library.

As the alemannic Wikipedia doesn't consist of that much articles, some of the word vectors are not so good. I didn't do a quantitative analysis, but I tried some examples by myself. For that I wrote a method which returns the `n` most similar words for a given word. You can find the method in the second notebook.

Here are some (good as well as bad) examples:

## Good examples

### Holz

('holz', 1.0),\
('metall', 0.77798355),\
('sand', 0.77707565),\
('staal', 0.77436936),\
('silber', 0.7699583),\
('glas', 0.7697315),\
('chalch', 0.74511236),\
('iise', 0.740827),\
('iis', 0.7318938),\
('bronze', 0.73029613)

### Frankriich

('frankriich', 1.0),\
('italie', 0.8466697),\
('östriich', 0.81186247),\
('spanie', 0.78971946),\
('groossbritannie', 0.771404),\
('russland', 0.75582993),\
('israel', 0.7433873),\
('preusse', 0.7382926),\
('ägypte', 0.73614293),\
('grossbritannie', 0.73122436)

## bad examples

### bild

('bild', 0.99999994),\
('gsicht', 0.73320806),\
('härz', 0.7099498),\
('drama', 0.70758563),\
('satz', 0.7059978),\
('konzept', 0.70439506),\
('fest', 0.70284754),\
('aug', 0.69814765),\
('universum', 0.6963069),\
('liecht', 0.6859163)

### wandere

('wandere', 0.99999976),
 ('starte', 0.7334156),
 ('zälldood', 0.73183024),
 ('monetsbricht', 0.73058367),
 ('heukatz', 0.72671133),
 ('vilzäller', 0.7247832),
 ('trinke', 0.7241421),
 ('häize', 0.7203049),
 ("d'noochberorte", 0.7110232),
 ('süferli', 0.7080671)

I suppose there are at least two factors, why it doesn't work good for some of the embeddings:

1) The corpus is not that big. The larger the corpus, the better.
2) As there doesn't exist an official ortography for Alemmanic, some of the words are spelled in multiple ways. I guess that hurts the performance of word2vec. (An example can be seen in the 'Frankriich' example, where Great Britain is spelled in two different ways.)

These are just assumptions though. \
Also, I didn't use a lot of different hyperparameters for the word2vec model. So maybe there's some better parameters which can be used to train the model.

## References

- Gensim (<https://radimrehurek.com/gensim/>)
- SoMaJo (<https://github.com/tsproisl/SoMaJo>). Used for sentence tokenization. It works reasonably well, even though it's intended use is for German tokenization.
