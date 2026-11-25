# SAPIO MASK v0.2 — pakiet do niezaleznego testu enwik9

**Status: LAB VERIFIED / CONTEST NOT VERIFIED.** To skompilowany kandydat badawczy, NIE zatwierdzony rekord Hutter Prize.

## Zrodlo programu

- GitHub Actions run: https://github.com/kosza123/hutter-prize-filip-majchrzak/actions/runs/44617030588
- Kompilacja kodu: `experimental/mask-early-v0.2`, commit `90cc1a7da40381a94fbfea732fc25420746ef23c`
- `comp9`: 4 042 713 bajtow, Linux x86-64 (instrukcje x86-64-v3, w tym AVX2).
- SHA-256 `comp9`: `88c7fd65064a725567fd36d3fdfc28bb0c5a9d7c4d985ce2972f9a8c13300995`

## Co zrobic

1. Linux x86-64 z odpowiednim CPU, co najmniej 16 GB fizycznej RAM na probe i duzo wolnego miejsca. GPU nie uzywac. Limit konkursowy RAM jest osobny: 10 GB.
2. Pobierz kanoniczny `enwik9.zip` ze strony https://www.mattmahoney.net/dc/enwik9.zip i rozpakuj `enwik9` w katalogu z `comp9`. Oczekiwany rozmiar: dokladnie 1 000 000 000 B; SHA-256: `159b85351e5f76e60cbe32e04c677847a9ecba3adc79addab6f4c6c7aa3744bc`.
3. Sprawdz `sha256sum -c SHA256_COMP9.txt`, nadaj prawa `chmod +x comp9`. Uruchom pod kontrola czasu i pamieci: `/usr/bin/time -v -o czas_kompresji.txt ./comp9`.
4. Zapisz wygenerowany NOWY plik `archive9`. Nie lacz tego `comp9` z `archive9` ze starego `v0.1.0-experimental`: tamten uzywa innego modelu.
5. W czystym katalogu, bez pliku `enwik9`, uruchom nowy `archive9` (po `chmod +x archive9`). Zmierz czas, szczytowe RAM i disk usage; sprawdz SHA-256, rozmiar odtworzonego pliku i dokladna zgodnosc bajtowa z oryginalem.
6. Podaj rozmiar `archive9`, sume `S = 4 042 713 + len(archive9)`, SHA obu plikow, pelne logi, CPU, OS, czas kompresji i dekompresji, zuzycie RAM i dysku.

## Istotne progi

- Oficjalny rekord opisywany w dokumentacji (stan 25.11.2026): `100 424 672 B`. Sprawdz oficjalna strone przed zgloszeniem, czy sie nie zmienil.
- Przynajmniej 1% lepiej: `S <= 99 420 425 B`, tj. `archive9 <= 95 377 712 B` dla tego `comp9`.
- Osobny, nieoficjalny benchmark: `93 388 956 B`; przebicie: `archive9 <= 89 346 242 B`, poprawa o 1%: `archive9 <= 88 412 353 B`.

Zasady: https://hutter1.net/prize/hrules.htm
Wyniki: https://prize.hutter1.net/
Kod: https://github.com/kosza123/hutter-prize-filip-majchrzak/tree/experimental/mask-early-v0.2

Silnik bazowy: CMIX / cmix-neif-2.0 Marcusa Wolka i autorow upstream, GPL-3.0. Projekt SAPIO MASK: Filip Majchrzak. Zachowac atrybucje, licencje i informacje o zaleznosciach.
