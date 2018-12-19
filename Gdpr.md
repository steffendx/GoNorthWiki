GoNorth has GDPR support implemented. This includes displaying a privacy policy page, showing a cookie consent banner and allowing users to download and delete their personal data.  
If you want to activate the GDPR support feature you will have to change the **UseGdpr** appsettings key in the misc section to true. Below you can read about the different features that are activated if you change this value to true.

**Important Note:** I am no lawyer and I do not provide any warranty of any kind that this feature fulfilles all GDPR requirements. See the [GoNorth MIT license](/steffendx/GoNorth/blob/master/LICENSE) for more details.

## Privacy Policy Page
A link to the privacy policy page will be shown at the bottom of each page. This page lists all the personal data stored by GoNorth and the cookies that are saved.

## Cookie Consent Banner
Unless the user has given consent to the usage of cookies a banner will be shown at the top. This banner will notify the user that cookies are used on this page and ask for consent. A link to the privacy policy page is included.

## Download/Delete personal data
By clicking on the name of the user in the top navigation bar and selecting **Personal Data** in the navigation bar on the left the user can reach the personal data page. Here the user can select one of the following buttons:
 * **Download**: A JSON file will be created with all the different personal data saved for the current user and offered as a download to the user.
 * **Delete**: A dialog will be shown to the user, asking to confirm that their personal data should be deleted. If the user confirms, the account, the timeline entries, the date and time at which the user modified data and all other personal data will be deleted.