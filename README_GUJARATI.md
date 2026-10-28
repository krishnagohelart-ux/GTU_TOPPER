# GTU Topper OS — Gujarati Setup Guide

## App માં શું છે?
- બધા 6 Diploma IT subjects માટે dashboard અને syllabus progress
- Topic ઉમેરવા, edit કરવા, delete/mark status કરવા
- Daily study planner અને checklist
- Focus timer (25/45/60 minutes), saved study sessions
- 1, 3, 7 અને 14 દિવસના spaced-revision reminders
- Mock test marks, mistake notebook, analytics
- JSON backup/restore અને CSV export
- Installable PWA + service worker offline cache

> નોંધ: શરૂઆતના topic names માત્ર editable starter examples છે. Official GTU syllabus પ્રમાણે જાતે edit/replace કરજો.

## Windows + VS Code માં ચલાવવાની રીત
1. ZIP extract કરો. `GTU_Topper_OS_PWA` folder ખોલો.
2. VS Code ખોલો → **File → Open Folder** → આ folder પસંદ કરો.
3. VS Code માં Extensions ખોલીને **Live Server** (Ritwick Dey) install કરો.
4. `index.html` પર right-click → **Open with Live Server**.
5. Browser માં app ખૂલે. પહેલા online હોય ત્યારે એક વાર app ખોલો જેથી service worker files cache કરી શકે.
6. Install માટે Chrome/Edge address bar પાસે install icon દેખાય તો દબાવો; નહીં તો browser menu → **Install app** / **Add to Home screen**.

## Android phone પર ખોલવાની રીત
PWA install અને offline માટે HTTPS અથવા localhost જરૂરી છે. Laptop પર Live Server ખોલવાથી phone પર સીધું `localhost` નહીં ચાલે.
- સરળ રીત: folder ને GitHub Pages જેવા HTTPS static host પર publish કરો, પછી phone ના Chrome માં URL ખોલો → menu → **Add to Home screen**.
- Local Wi-Fi method માં Live Server host/IP વાપરી શકાય, પણ browser અને service-worker security restrictions ને કારણે offline install દરેક setup માં કામ કરે જ એવું નથી.
- આ app localStorage વાપરે છે: phone અને laptop નો data આપમેળે sync થતો નથી. બંને પર અલગ data રહેશે. JSON backup/restore થી manually transfer કરી શકો.

## Data safety
- Data એ જ browser/device માં રહે છે. Browser site data clear કરશો તો data ખોવાઈ શકે.
- Settings & backup માંથી નિયમિત **Export backup (JSON)** કરો.
- Import backup હાલના app data ને replace કરે છે.
- કોઈ login/cloud sync નથી; આ personal local study app છે.

## જો install/offline ન ચાલે
- `file://` થી સીધું `index.html` ખોલશો નહીં; local web server અથવા HTTPS વાપરો.
- Browser DevTools → Application → Service Workers માં service worker status જુઓ.
- App online હોય ત્યારે એક વાર load થયા પછી refresh કરો; પછી airplane mode માં ફરી ખોલીને ચકાસો.
- CSS/JS બદલ્યા પછી `service-worker.js` માં `CACHE_NAME` version `gtu-topper-os-v2` જેવી નવી value કરો, પછી reload કરો.
