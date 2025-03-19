# CeneoScraper

## Kod produktu, w którym będa obierane opinie

## Algorytm pobierania opinii o pojedyńczym punkcie z serwisu Ceneo.pl
1. Wysłanie zapytania dostępu do strony z opiniami o produkcie
2. Jesli operacja zakończy się sukcesem, wyodrębnienie z kodu strony fragmentów opinii 
3. Dla każdej z opinii wydobycie z kodu HTML poszczególnych składowych i zapisanie ich w postaci złożonych struktur danych 
4. jeżeli istnieje kolejna strona z opiniami to przechodzimy na kolejna stronę i powtarzamy kroki od 1-4
5. zapisanie opinii w bazie danych

## struktura opinii w serwisie Ceneo.pl
|składowa|zmienna|selektor|
|--------|-------|--------|
|opinia|review|js_product-review|
|identyfikator opinii|review_id|['data-entry-id']|
|autor|author|span.user-post__author-name|
|rekomendację|recomendation|span.user-post__author-recomendation > em|
|liczbę gwiazdek|stars|span.user-post__score-count|
|treść opinii|content|div.user-post__text|
|listę zalet|pros|div.review-feature__item--positive|
|listę wad|cons|div.review-feature__item--negative|
|ile osób uznało opinię za przydatną|likes|button.vote-yes > span|
|ile osób uznało opinię za nieprzydatną|dislikes|button.vote-no > span|
|data wystawienia opinii|publish_date|span.user-post__published > time:nth-child(1)['datetime']|
|data zakupu produktu|buy_date|user-post__published > time:nth-child(2)['datetime']|
|czy opinia jest potwierdzona zakupem||.review-pz|

