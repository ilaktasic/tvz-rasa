#Treniranje modela
1. Instalacija rase lokalno -> https://rasa.com/docs/rasa/user-guide/installation/2. 
2  kreirati folder za projekt i inicijalizirati rasu pomoću `rasa init` 
3. U data/nlu.md dodati primjere
4. U domain.yml dodati korištene intentove
5. config.yml izkopirati iz ovog projekta
5. Istrenirati model `rasa train nlu`
6. Najbolje pushati sve na neki git repo


#Deploy
1. kreirati docker volume pod imenom rasa `docker volume create rasa`
2. pozicionirati se u docker volume (lokcaija: `docker volume inspect rasa` mountpoint property) 
3. `git clone` prije kriranog git repozitorija
4. prebaciti datoteke iz foldera od git repozitorija razinu gore, znaci u _data folder
5. pokrenuti rasu pomocu docker compose fajle iz ovog projekta `docker-compose up -d rasa ` 
6. rasa docker ima exposan api na portu 8080, to se može konfigurirati u docker-compose fajli
7. testirati `curl -XPOST -d '{
"text":"kad je ispit iz jave"
}' 'localhost:8080/model/parse'` 