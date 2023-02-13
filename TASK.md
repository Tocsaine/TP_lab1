Выполнение работы.

1. При помощи wget скачиваем саму библиотеку:
wget + url
2. Разархивируем объект: tar xvzf boost_1_69_0.tar.gz
3. cd ~/boost_1_69_0
4. Посчитаем файлы не считая вложенные директории: tree -a -L 1
5. ПОсчитаем все файлы: tree -a
6. find -name "*.cpp" -not -type d|wc -l (Все файлы .срр)
7. find -name "*.hpp" -o -name "*.h" -not -type d|wc -l (Все заголовочные файлы)
8. find -not -name "*.cpp" -not -name "*.hpp" -not -name "*.h" -not -type d|wc -l (остальные файлы)
9. realpath "any.cpp" (узнаем истинный путь до файла any.cpp)
10. grep -r "boost::asio"|wc -l (17424) - Находим все файлы с упоминание этой последовательности
11. cd ~/boost_1_69_0/tools/build
12. ./bootstrap.sh
13. ./b2 install --prefix=/home/tocsaine/boost_1_69_0/tools/build/test (В папку тест)
14. ... updated 436 targets...
15. mv -i test ~/boost-libs/ (Переносим результаты компиляции в заданную папку)
16. cd ~/boost-libs/
17. find . -xdev -type f -not -type d  -print | xargs ls -lh | sort -k5,5 -h -r (Отсортированный список файлов и их вес)
18. find . -xdev -type f -not -type d  -print | xargs ls -lh | sort -k5,5 -h -r | head (Топ 10 тяжелых)

В ходе работы использовались g++ и gcc