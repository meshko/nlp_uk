Скрипти в цій теці дозволяють опрацьовувати українські тексти в пакетному режимі:

* `ExtractText.groovy [<src_dir> [<txt_dir>]]` (типово: `pdf/` та `txt/`)

    Витягує тексти з різних форматів у теці <src_dir> і складає в теку <txt_dir>. Підтримувані формати:

    * .pdf (вимагає pdftotext)
    * .djvu (вимагає djvutxt)
    * .fb2 (вимагає unoconv)
    * .epub (вимагає ebook-convert)
    * .doc, .docx, .rtf (вимагає unoconv)

    Також відсіює файли, в яких визначено два ствопчики в теку `<txt_dir>/multicol/` (в майбутньому плануємо об'єднувати стовпчики в один)

* `CleanText.groovy [<txt_dir>]` (типово: `txt/`)

    Читає всі файли .txt в теці й намагається знайти ті, що відповідають крітеріям українського тексту (>2 тис. українських слів), вивід йде в `<txt_dir>/good/`

    Перед застосуванням критерію намагається почистити і випарвити типові проблеми:

    * поломані/мішані кодування
    * мішанину латиниці та кирилиці
    * нетипові апострофи (міняє на прямий — ')
    * вилучає м'який дефіс (00AD)
    * об'єднує перенесення слів на новий рядок (використовуючи орфографічний словник)

* `EvaluateText [<txt_dir>]` (типово: ./)

    Читає всі файли .txt в теці й генерує файли `*.err.txt` для кожного з описом помилок знайдених перевіркою граматики LanguageTool (деякі правила вимкнені)

    Також генерує файл `<txt_dir>/err/ratings.txt` зі статистикою для кожного файлу
