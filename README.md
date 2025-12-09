1. PODSTAWY – NAWIGACJA I INFORMACJE

pwd
Print Working Directory – pokazuje pełną ścieżkę bieżącego katalogu (np. /home/me).
cd katalog
Change Directory – przechodzi do podanego katalogu.
cd ..
Przechodzi do katalogu nadrzędnego (poziom wyżej).
cd ~ lub cd
Przechodzi do katalogu domowego użytkownika.
cd -
Przechodzi z powrotem do ostatnio używanego katalogu.
ls
List – wyświetla nazwy plików i katalogów w bieżącym katalogu.
ls -l
Długi format: uprawnienia, liczba linków, właściciel, grupa, rozmiar, data, nazwa.
ls -a
Pokazuje ukryte pliki (zaczynające się od kropki, np. .bashrc).
ls -la
Łączy -l i -a – wyświetla wszystkie pliki z pełnymi informacjami.
ls -li
Pokazuje numery i-węzłów (inode) – kluczowe przy pracy z dowiązaniami.
ls -R
Rekurencyjnie wyświetla zawartość wszystkich podkatalogów.



2. TWORZENIE I ZARZĄDZANIE KATALOGAMI

mkdir nazwa
Tworzy nowy katalog o podanej nazwie.
mkdir -p a/b/c
Tworzy całą hierarchię katalogów (nawet jeśli a lub b nie istnieją).


3. KOPIOWANIE PLIKÓW I KATALOGÓW

cp źródło cel
Kopiuje plik do nowej lokalizacji lub pod nową nazwą.
cp -r źródło cel
Kopiuje katalog rekurencyjnie (razem z podkatalogami i plikami).
cp -i źródło cel
Kopiuje z potwierdzeniem – pyta, czy nadpisać istniejący plik.
cp -v źródło cel
Kopiuje w trybie verbose – pokazuje, co zostało skopiowane (np. 'a' -> 'b').


4. PRZENOSZENIE I ZMIANA NAZW

mv stary nowy
Zmienia nazwę pliku/katalogu (jeśli oba są w tym samym katalogu).
mv plik katalog
Przenosi plik do podanego katalogu.
mv katalogA katalogB
– Jeśli katalogB istnieje → przenosi katalogA do wnętrza katalogB. <br> – Jeśli katalogB nie istnieje → zmienia nazwę katalogA na katalogB.
mv -i źródło cel
Przenosi z potwierdzeniem przed nadpisaniem.
mv -f źródło cel
Wymusza przeniesienie – nadpisuje bez pytania.


5. USUWANIE PLIKÓW I KATALOGÓW

rm plik
Usuwa plik trwale (nie da się cofnąć!).
rm -i plik
Usuwa z potwierdzeniem – bezpieczna wersja.
rm -f plik
Wymusza usunięcie – nie pyta, ignoruje błędy (np. jeśli plik nie istnieje).
rm -r katalog
Usuwa cały katalog wraz z zawartością (rekurencyjnie).
rm -R katalog
To samo co -r (alias).


6. TWORZENIE I MODYFIKACJA PLIKÓW

touch plik
Tworzy pusty plik lub aktualizuje datę jego modyfikacji.
touch -d "2025-01-01" plik
Ustawia dowolną datę modyfikacji.
touch -t 202501011200.00 plik
Ustawia datę w formacie YYYYMMDDhhmm.ss.
cat plik
Wyświetla całą zawartość pliku.
less plik
Przegląda plik strona po stronie (q = wyjście).
head plik
Pokazuje pierwsze 10 linii pliku.
tail plik
Pokazuje ostatnie 10 linii pliku.


7. DOWIĄZANIA (LINKI)

ln źródło cel
Tworzy dowiązanie twarde – nową nazwę dla tego samego pliku (ten sam numer i-węzła).
ls -l
Pokazuje liczbę dowiązań twardych (druga kolumna).
ls -li
Potwierdza, że wszystkie mają ten sam inode.



8. WILDCARDS (SZABLONY DO WYBIERANIA PLIKÓW)

*
Dowolna liczba znaków (np. *.txt = wszystkie pliki z rozszerzeniem .txt).
?
Dokładnie jeden znak (np. file?.log → file1.log, fileA.log).
[abc]
Jeden znak z podanego zestawu.
[a-z]
Jedna mała litera.
.*
Wszystkie ukryte pliki (zaczynające się od kropki).
[!.]*
Wszystkie nieukryte pliki.
s*
Wszystkie nazwy zaczynające się od litery s.


9. DIAGNOSTYKA I INFORMACJE O PLIKACH

file nazwa
Określa typ pliku (np. „regular file”, „symbolic link”, „broken symbolic link”).
readlink nazwa
Pokazuje, do czego prowadzi dowiązanie symboliczne.
stat plik
Pokazuje dokładne daty: dostępu (Access), modyfikacji (Modify), zmiany metadanych (Change).
whoami
Pokazuje nazwę bieżącego użytkownika.
man komenda
Wyświetla pełny podręcznik systemowy dla danej komendy.
komenda --help
Pokazuje szybką pomoc z najważniejszymi opcjami.


10. PRZYDATNE SYMBOLY

.
Bieżący katalog
..
Katalog nadrzędny
~
Katalog domowy użytkownika
Tab
Autouzupełnianie nazw (oszczędza czas i błędy!)
2>/dev/null
Ukrywa komunikaty o błędach (np. ls *.xyz 2>/dev/null)
