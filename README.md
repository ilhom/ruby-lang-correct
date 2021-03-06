ruby-lang-correct
=================

Automatic correction of the language for words in the text because of the wrong keyboard layout

Автоматическое исправление языка для слов в тексте из-за неправильной раскладки клавиатуры

> За основу взята библиотека http://code.google.com/p/php-lang-correct/ , данный код является портом кода с PHP.<br>
> http://code.google.com/p/php-lang-correct/<br> 
> http://creativecommons.org/licenses/by-nc-sa/3.0/<br>
> @Nasibullin Rinat


## Purpose ##
  * Корректировка поисковых запросов
  * Корректировка существующих и новых текстов, публикуемых посетителями на веб-сайтах.

## Features ##
- Режим SIMILAR\_CHARS. Исправление ошибочно набранных букв в словах, которые выглядят одинаково в разных раскладках клавиатуры. Незаметные латинские буквы среди русских исправляются в русские и наоборот. Алгоритм работает достаточно надёжно и быстро.
- Режим KEYBOARD\_LAYOUT. Исправление ошибочно набранных слов в другой раскладке клавиатуры. Для определения языка используются N-граммы. Алгоритм может иногда ошибаться, работает в разы медленнее, чем SIMILAR\_CHARS. Алгоритм постоянно совершенствуется. Для поддержания качества существует тестовый набор слов, который в поставку не входит.
- Двухстороннее исправление слов для русского и английского языка.
- Исправление слов на смешанном языке.
- Кодировка символов — UTF-8.

## Examples ##
- "сщsmщ" => 'cosmo' (2 первых и последняя буква — ошибочные)
- "[htн" => 'хрен'  (первые 3 буквы — ошибочные)
- "вебvfcnth" => 'вебмастер'
- "webьфыеук" => 'webmaster'
- "цццюмуыеш.ru" => 'www.vesti.ru'
- "T.C.Yfвка" => 'Т.С.Навка'

## Hints ##
Типичный пример алгоритма работы для поля ввода с автодополнением:

1. Сделать выборку по исходному запросу;
2. Если есть результат, возвратить его и исходный запрос;
3. Иначе скорректировать исходный запрос через Text\_LangCorrect;
4. Если исходный и скорректированный запрос совпадает, возвратить пустой результат и исходный запрос;
5. Иначе сделать выборку по скорректированному запросу;
6. Возвратить результат. Если результат не пустой, возвратить скорректированный запрос, иначе исходный.


