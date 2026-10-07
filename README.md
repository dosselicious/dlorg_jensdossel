DLORG Jens Dossel DBAD26  DLORG är ett Bash-script som sorterar hämtade filer i linux Hämtningar-katalog genom att använda funktionen id_n_sort och programmet inotifywait.
Scriptet identifierar filer som ”landar”, döps om eller skapas i Hämtningar baserat på filändelse och lägger dem i fördefinierade mappar enligt en hårdkodad lista, en associativ array:

Filändelser                  	Kategori
jpeg, jpg, gif, heic, png      	image  
txt, rtf, md    		text 
pdf                     	pdf
doc, docx, pages         	docs
ppt, pptx, key             	presentation
xls,xlsx,numbers, csv      	tabell
mp3, wav                    	musik
logicx                   	musikprojekt
mp4, mov                     	video
zip                          	paket
övriga eller inga          	other

Vill framtida användare utöka listan över filändelser och/eller kategorier kan hen enkelt göra det via terminalkommandot ”vim ~/jdossel/dlorg_jensdossel/dlorg”.
 
Funktionen skapar målkatalog om den saknas genom ”mkdir -p”, och döper den enligt kategorinamnet.
Scriptet ligger i repot och foldern ”~/jdossel/dlorg_jensdossel”, och har en symbolisk länk i ”~/.local/bin/dlorg”
Det aktiveras vid start av användarmiljön via service-filen ”~/.config/systemd/user/dlorg.service”. 
Bevakningen av Hämtningar/ sköts via scriptet med hjälp av inotifywait.
Identifiering och sortering sköts av funktionen id_n_sort.

![Systemd service](Image.png)
