GoNorth has legal notice support implemented. This includes displaying contact data for the domain and some disclaimers
If you want to activate the legal notice feature you will have to change the **UseLegalNotice** appsettings key in the misc section to true.  
You will also have to enter your contact data in the **legal notice section** of the appsetting file.  
Afterwards a link will be shown at the bottom of each page, linking to the legal notice page. You might want to not only adjust your contact data in the appsetting file, but also the disclaimer texts shown on this page by adjusting the texts in the **/Resources/Views/LegalNotice** JSON files.

**Important Note:** I am no lawyer and I do not provide any warranty of any kind that this feature fulfilles all legal notice requirements. See the [GoNorth MIT license](/steffendx/GoNorth/blob/master/LICENSE) for more details.