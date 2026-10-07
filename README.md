# DLORG Jens Dossel DBAD26

DLORG är ett Bash-script som sorterar hämtade filer i Linux-katalogen `~/Hämtningar` genom att använda funktionen `id_n_sort` och programmet `inotifywait`.

Scriptet identifierar filer som "landar", döps om eller skapas i Hämtningar baserat på filändelse och lägger dem i fördefinierade kategorier enligt en hårdkodad associativ array.

## Filtyper och kategorier

| Filändelser                   | Kategori |
| 
| jpeg, jpg, gif, heic, png     | image |
| txt, rtf, md                  | text |
| pdf                           | pdf |
| doc, docx, pages              | docs |
| ppt, pptx, key                | presentation |
| xls, xlsx, numbers, csv       | tabell |
| mp3, wav                      | musik |
| logicx                        | musikprojekt |
| mp4, mov                      | video |
| zip                           | paket |
| övriga eller inga             | other |

Vill en framtida användare utöka listan över filändelser och/eller kategorier kan detta enkelt göras genom att redigera scriptet:

`vim ~/dlorg_jensdossel/dlorg`

Funktionen skapar målkatalogen om den saknas genom `mkdir -p` och döper den enligt kategorinamnet.

Scriptet ligger i repot `~/dlorg_jensdossel`, har en symbolisk länk i `~/.local/bin/dlorg` och körs via systemd-filen `~/.config/systemd/user/dlorg.service`.

Bevakningen av `~/Hämtningar` sköts av `inotifywait`.
Identifiering och sortering sköts av Bash-funktionen `id_n_sort`

![Systemd service](Image.png)
