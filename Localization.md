GoNorth uses JSON files for localization. If you want to support a new language you will have to follow these steps:
 * Add a new localized version of the different json files in the Resources folder. So lets say you want to translate the portal to spanish you will have to add versions that end with ".es.json". So copy the file "/Resources/Authentication/GoNorthIdentityErrorDescriber.en.json" rename it to "GoNorthIdentityErrorDescriber.es.json" and translate it. And do this for the rest of the files as well.  
 In some files you will find values like *"DropzoneLocale": "en"*. These values are used to load the JavaScript localization files (see next step). You will have to provide your locale name here (so in case of spanish "es").
 * Some localization is done through JavaScript files since the localized strings are used in JavaScript. You will have to copy these and adjust them in the same way. The postfix must match the locale name you used for "DropzoneLocale" etc.. You will also have to adjust the bundle files to create a new bundled language file for the new locale. These are the files you will have to consider:
   * /wwwroot/js/Aika/chapterDetail/chapterDetailLang.en.js (bundle target: /wwwroot/js/Aika/aikaLang.en.js)
   * /wwwroot/js/Aika/chapterOverview/chapterOverviewLang.en.js (bundle target: /wwwroot/js/Aika/aikaLang.en.js)
   * /wwwroot/js/Aika/quest/questLang.en.js (bundle target: /wwwroot/js/Aika/aikaLang.en.js)
   * /wwwroot/js/Aika/shared/sharedLang.en.js (bundle target: /wwwroot/js/Aika/aikaLang.en.js)
   * /wwwroot/js/Localization/dropzone.locales.en.js
   * /wwwroot/js/Shared/nodeGraph/nodeLang.en.js (just minified in bundleconfig.json)
   * /wwwroot/js/Tale/dialogForm/taleLang.en.js (bundle target: /wwwroot/js/Tale/taleLang.en.js)
   * /wwwroot/lib/jquery-validation-locales/messages_en.js
   * /wwwroot/lib/bootstrap-wysiwyg/locale/bootstrap-wysiwyg.en.js (just minified in bundleconfig.json)
 * You will have to add the new language as a supported culture in the Startup.cs:

    List<CultureInfo> supportedCultures = new List<CultureInfo>  
    {  
        new CultureInfo("de"),  
        new CultureInfo("en")  
    };