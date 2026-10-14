# Sailing Rosbag Upload — pagine informative

Sito statico del Polimi Sailing Team per presentare l'uploader delle rosbag e la sua informativa privacy nella schermata di consenso Google OAuth.

## File

- `index.html`: descrizione dell'applicazione e collegamento all'informativa.
- `privacy.html`: dati utilizzati, permessi Google Drive, conservazione, condivisione e revoca.
- `styles.css`: stile condiviso, senza dipendenze esterne.
- `.nojekyll`: pubblicazione dei file statici senza elaborazione Jekyll.

Non servono Node.js, compilazione, un server applicativo o un container. Il sito non gestisce il login Google e non carica rosbag.

Prima della pubblicazione, il referente del team deve rileggere i testi e confermare che contatto, utilizzi dei dati e modalità di conservazione descrivano la gestione effettiva. I testi descrivono la configurazione dell'uploader esaminata il 14 ottobre 2026; vanno aggiornati se il programma o la gestione del team cambiano.

Non aggiungere credenziali OAuth, `rclone.conf`, token, file di registrazione o dati della barca a questa repository pubblica.

## Pubblicazione su GitHub Pages

Dopo aver controllato i file, da CMD nella cartella clonata:

```cmd
git add index.html privacy.html styles.css .nojekyll .gitignore README.md
git commit -m "Aggiungi presentazione e informativa privacy dell'uploader"
git push origin main
```

Su GitHub apri la repository e vai in **Settings → Pages**:

1. In **Build and deployment → Source**, seleziona **Deploy from a branch**.
2. Seleziona il branch **main** e la cartella **/(root)**.
3. Premi **Save** e attendi la pubblicazione. Usa l'indirizzo effettivo mostrato da GitHub Pages.

Non occorre aggiungere un workflow personalizzato: GitHub gestisce la pubblicazione dal branch. [Istruzioni ufficiali](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

Con il nome attuale dell'organizzazione e della repository, gli indirizzi predefiniti attesi sono:

- Home: <https://sailing-team-polimi.github.io/rosbag-upload-info/>
- Privacy: <https://sailing-team-polimi.github.io/rosbag-upload-info/privacy.html>

Questi indirizzi diventano disponibili soltanto dopo il push e l'attivazione di Pages. Apri entrambi senza login per verificare che siano raggiungibili.

## Collegamento con Google OAuth

Nella pagina **Google Auth Platform → Branding** inserisci l'indirizzo pubblicato della home in **Home page applicazione** e quello di `privacy.html` nel campo dell'informativa privacy. Il nome dell'app su Google deve restare **Sailing Rosbag Upload**, come nelle pagine.

Se Google richiede un dominio autorizzato, usa il dominio del sito del team (`sailing-team-polimi.github.io` per gli URL predefiniti), senza `https://` né il percorso della repository. Non inserire il dominio generale `github.com`. Se viene richiesta una verifica della proprietà, completa quella procedura con l'account Google che gestisce il progetto; non inventare un dominio alternativo per superare il controllo.

Torna su **Pubblico** e controlla se **Pubblica app** è disponibile. La pubblicazione delle pagine non garantisce da sola l'approvazione di Google: eventuali altre richieste della console vanno valutate in base alla configurazione dell'app.

Dopo il passaggio fuori dalla modalità Test, ripeti l'autorizzazione di rclone per ottenere un nuovo token. Una credenziale condivisa accidentalmente va sostituita nella console e aggiornata nella configurazione privata. Il file da trasferire successivamente al Raspberry è `rclone.conf`, che resta esterno a questa repository.

Riferimenti: [requisiti di presentazione dell'app](https://developers.google.com/identity/protocols/oauth2/production-readiness/brand-verification), [Google API Services User Data Policy](https://developers.google.com/terms/api-services-user-data-policy), [scadenza dei token](https://developers.google.com/identity/protocols/oauth2#expiration).
