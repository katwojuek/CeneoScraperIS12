# CeneoScraperIS12

## Kod produktu, o którym będą pobierane opinie
84514582

## Algorytm pobiernia opini o pojedynczym produkcie z serwisu Ceneo.pl
1. Wysłanie żądania dostępu do strony z opiniami o produkcie
2. Jeżeli operacja zakończy się sukcesem, wyodrębnienie z kodu strony fragmentów odpowiadających poszczególnym opiniom
3. Dla każdej z opinii wydobycie z kodu HTML poszczególnych składowych i zapisanie ich w postaci złożonych struktur danych
4. Jeżeli istnieje kolejna strona z opiniami, przejście na tą stronę i powtórzenie dla niej kroków 1-4
5. zapisanie wszystkich opinii w bazie danych

## Struktura opini w serwwsie Ceneo.pl
|składowa|zmienna|selektor|
|--------|-------|--------|
|opinia|review|div.js_product-review:not(.user-post--highlight)|
|identyfikator opinii|review_id|['data-entry-id']|
|autor|author|span.user-post__author-name|
|rekomendacja|recomendation|span.user-post__author-recomendation > em|
|liczba gwiazdek|stars|span.user-post__score-count|
|treść opinii|content|div.user-post__text|
|lista zalet|pros|div.review-feature__item--positive|
|lista wad|cons|div.review-feature__item--negative|
|ile osób uznało opinię za przydatną|likes|button.vote-yes > span|
|ile osób uznało opinię za nieprzydatną|dislikes|button.vote-no > span|
|data wystawienia opinii|publish_date|span.user-post__published > time:nth-child(1)['datetime']|
|data zakupu produktu|purchase_date|span.user-post__published > time:nth-child(2)['datetime']|
