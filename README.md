# Классификация токсичных комментариев

Условный интернет-магазин запускает новый сервис - теперь пользователи могут редактировать и дополнять описания товаров, то есть клиенты предлагают свои правки и комментируют изменения других. Магазину нужен инструмент, который будет искать токсичные комментарии и отправлять их на модерацию. 

Необходимо обучить модель классифицировать комментарии на позитивные и негативные. В распоряжении набор данных с разметкой о токсичности правок.


## Stack
- Pandas
- Numpy
- Seaborn
- WordCloud
- NLTK
- TfidfVectorizer
- MultinomialNB
- SGDClassifier
- RandomForestClassifier
- LogisticRegression


## Вывод

- выборка содержит 5537156 уникальных слов;
![WordCloud ALL](https://user-images.githubusercontent.com/94479037/173242146-fb57e5e1-1668-485a-9ac8-f6812e6c4de0.png)
- позитивные комментарии содержат 5071297 уникальных слова, среди которых выражаются - talk, page, people, article, one, even;
![WordCloud Possitive](https://user-images.githubusercontent.com/94479037/173242157-9792ebd9-769f-43b9-84dc-f3fe874ac677.png)
- негативные комментарии содержат 465859 уникальных слова, среди которых выражаются - fuck, moron, hate, people, nigger, pig.
![WordCloud Negative](https://user-images.githubusercontent.com/94479037/173242164-b147b8ac-08ff-487e-9dbf-cbcb7aea15ba.png)


Для обучения использовались сл. алгоритмы:

- `Naive Bayes Classifier`;
- `Linear Support Vector Machine`;
- `Random Forest Classifier`;
- `Logistic Regression`.

- выборка была разделена на обучающую и тестовую в соотношении 75:25;
- векторизация выполнена при помощи `Tfidfvectorizer`;
- для модели `Naive Bayes Classifier` обучение произведено на выборке с балансированными классами техникой `downsampling`;
- для моделей `Linear Support Vector Machine`, `Random Forest Classifier` и `Logistic Regression` использован параметр `class_weight='balanced'`;
- качество моделей оценено кросс-валидацией с пятью блоками.


Все четыре модели показали хороший результат на тренировочной выборке. На тестовой же выборке порог качества в не менее 0.75 показали модели - Linear Support Vector Machine и Logistic Regression.

Score for Linear Support Vector Machine on the test set: `0.754`

![error_matrix SGD](https://user-images.githubusercontent.com/94479037/173242301-061798cb-afcc-45ea-bec8-1bc6ae23c045.png)

Score for Logistic Regression on the test set: `0.752`

![error_matrix LR](https://user-images.githubusercontent.com/94479037/173242316-8394e1d8-b2d9-41fe-af7c-5a53af7ce83e.png)




