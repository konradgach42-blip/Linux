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
------------------------------------------------------------------



1. Tworzenie struktury katalogów i plików

mkdir ~/lab_archiwizacja                  # Tworzy główny katalog ćwiczeń w domu
cd ~/lab_archiwizacja                     # Przechodzi do tego katalogu
mkdir dane1 dane2                         # Tworzy dwa katalogi naraz
echo "Tekst" > dane1/plik1.txt           # Tworzy plik z tekstem (nadpisuje, jeśli istnieje)
cp /etc/passwd ./dane1/                  # Kopiuje systemowy plik passwd do dane1/


2. Archiwizacja z tar (bez kompresji)

tar -cvf archiwum.tar dane1 dane2        # Tworzy archiwum .tar z katalogów
tar -tf archiwum.tar                     # Pokazuje zawartość archiwum (bez szczegółów)
tar -tvf archiwum.tar                    # Pokazuje zawartość z datami, uprawnieniami, rozmiarami
tar -xvf archiwum.tar -C ./rozpakowane   # Rozpakowuje archiwum do katalogu ./rozpakowane

c = create (utwórz archiwum)
x = extract (rozpakuj)
t = list (pokaż zawartość)
v = verbose (pokaż, co się dzieje)
f = file (podać nazwę pliku archiwum)
-C = change directory (rozpakuj do innego katalogu)


3. Archiwizacja z kompresją

tar -czvf archiwum.tar.gz dane1 dane2    # Tworzy skompresowane archiwum gzip
tar -xzvf archiwum.tar.gz                # Rozpakowuje archiwum gzip


tar -cjvf archiwum.tar.bz2 dane1 dane2   # Tworzy archiwum skompresowane bzip2
tar -xjvf archiwum.tar.bz2               # Rozpakowuje


tar -cJvf archiwum.tar.xz dane1 dane2    # Tworzy archiwum xz
tar -xJvf archiwum.tar.xz                # Rozpakowuje


4. Porównanie rozmiarów i czasu

ls -lh archiwum.*                        # Pokazuje rozmiary wszystkich archiwów w czytelnej formie
du -h archiwum.*                         # Inna forma – pokazuje użycie dysku
time tar -czvf test.tar.gz dane1 dane2   # Mierzy czas wykonania komendy


5. Kompresja pojedynczych plików (bez tar)


gzip plik.txt                            # Kompresuje → plik.txt.gz (usuwając oryginał)
gunzip plik.txt.gz                       # Dekompresuje → plik.txt

bzip2 plik.txt                           # → plik.txt.bz2
bunzip2 plik.txt.bz2                     # → plik.txt

xz plik.txt                              # → plik.txt.xz
unxz plik.txt.xz                         # → plik.txt


gzip -k plik.txt      # -k = keep original
bzip2 -k plik.txt
xz -k plik.txt


6. Praca z archiwem ZIP

zip -r dane.zip dane1 dane2              # Tworzy archiwum .zip (rekurencyjnie!)
unzip dane.zip -d ./rozpakuj_zip         # Rozpakowuje do katalogu rozpakuj_zip
unzip -l dane.zip                        # Pokazuje zawartość ZIP bez rozpakowywania


7. Sprawdzanie i porównywanie


ls -R                                    # Pokazuje rekurencyjnie całą strukturę katalogów
diff -r katalog1 katalog2                # Rekurencyjnie porównuje dwa katalogi
file archiwum.tar.gz                     # Określa typ pliku (np. "gzip compressed data")


~ = Twój katalog domowy (/home/twój_użytkownik)
. = bieżący katalog
.. = katalog nadrzędny
> = nadpisz plik
>> = dopisz do pliku
| = przekieruj wynik jednej komendy do drugiej


----------------------------------------------------------------------------


1. Podstawowe informacje o komendach

type -a ls
Sprawdza, czy komenda jest wbudowana, aliasem czy zewnętrznym programem
type -a ls → pokazuje /bin/ls
which nano
Znajduje ścieżkę do pliku wykonywalnego
which nano → /usr/bin/nano
command -v python
Bezpieczniejszy sposób na znalezienie ścieżki (działa w każdej powłoce)
command -v python
python --version
Pokazuje wersję Pythona uruchamianą domyślnie
python3 --version
man chmod
Otwiera podręcznik (manual) dla polecenia
man ls
/ -l w manie
Szukaj opcji -l w manie (nacisnij /, wpisz -l, Enter)
—
apropos user
Szuka wszystkich komend związanych ze słowem „user” w opisach manów
apropos compress
whatis cat
Krótki opis działania polecenia
whatis grep → „print lines matching a pattern”
info ls
Alternatywna dokumentacja (bardziej szczegółowa niż man)
info chmod


2. Aliasy i konfiguracja

alias ll='ls -alF'
Tworzy tymczasowy alias
ll → zamiast ls -alF
echo "alias ll='ls -alF'" >> ~/.bashrc
Dodaje alias do pliku konfiguracyjnego (trwały)
—
source ~/.bashrc
Przeładowuje konfigurację bez wylogowania
—

3. Przekierowania i strumienie

>
Przekierowuje stdout do pliku (nadpisuje)
>>
Przekierowuje stdout do pliku (dopisuje)
2>
Przekierowuje stderr (błędy) do pliku
2>/dev/null
Ukrywa błędy (wyrzuca je do „kosza”)
&> lub > file 2>&1
Przekierowuje stdout i stderr do pliku
2>&1 >/dev/null
Pokazuje tylko błędy, ukrywa normalne wyjście
`
`
tee file
Przekazuje dane na ekran i do pliku jednocześnie


 4. Przeglądanie i filtrowanie plików

cat file
Wyświetla cały plik
cat notes.txt

less file
Interaktywny przegląd (strzałki, q = wyjście)
less /var/log/syslog

head -n 10 file
Pierwsze 10 linii
head -n 5 list.txt

tail -n 5 file
Ostatnie 5 linii
tail -f /var/log/syslog (monitorowanie w czasie rzeczywistym)

grep "wzorzec" file
Szukaj linii zawierających wzorzec
grep "error" syslog

grep -i "error" file
Szukaj bez uwzględniania wielkości liter
—
grep -n "user" file
Pokaż linie z numerami
—
tac file
Wyświetla plik od końca
tac c.txt


5. Sortowanie, unikalność, liczenie

sort file
Sortuje alfabetycznie
`ls /bin /usr/bin
sort -r
Sortuje odwrotnie (Z → A)
—
uniq
Usuwa sąsiednie duplikaty (musi być po sort)
`sort file
uniq -c
Liczy wystąpienia każdej linii
—
wc -l
Liczy linie
`find / -type f 2>/dev/null
comm -12 file1 file2
Linie wspólne w dwóch posortowanych plikach
comm -12 <(ls /bin) <(ls /usr/bin)


6. Praca z plikami i katalogami

mkdir test
Tworzy katalog
mkdir ~/test
touch file.txt
Tworzy pusty plik
touch ~/test/file.txt
cat > file
Tworzy lub nadpisuje plik przez wpisanie tekstu
cat > notes.txt → Ctrl+D
cat file1 file2 > file3
Łączy pliki
cat a.txt b.txt > combined.txt
cat -n file
Wyświetla z numerami linii
cat -n script.sh

7. Uprawnienia i właściciele

chmod 600 file
Ustawia uprawnienia (właściciel: rw, inni: ---)
chmod 644 notes.txt
chown root file
Zmienia właściciela pliku
sudo chown root config.conf
chgrp users file
Zmienia grupę pliku
sudo chgrp mygroup file.txt
ls -l file
Pokazuje uprawnienia, właściciela i grupę
ls -l /etc/passwd

8. Zarządzanie użytkownikami i grupami


sudo groupadd mygroup
Tworzy nową grupę
—
sudo usermod -a -G mygroup $USER
Dodaje użytkownika do grupy
—
id
Pokazuje aktualnego użytkownika i jego grupy
id → uid=1000(user) gid=1000(user) groups=1000(user),4(adm),24(cdrom)...

10. Analiza systemu

grep "cpu MHz" /proc/cpuinfo
Częstotliwość procesorów
`find / -type f 2>/dev/null
wc -l`
mimetype plik
Określa typ MIME pliku
find ~ -type f -not -path "*/\\.*"
Znajduje pliki, pomijając ukryte




