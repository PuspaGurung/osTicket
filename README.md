# Mat-Norge Helpdesk use osTicket

**osTicket** is a widely-used open source support ticket system. It seamlessly
integrates inquiries created via email, phone and web-based forms into a
simple easy-to-use multi-user web interface. Manage, organize and archive
all your support requests and responses in one place while providing your
customers with accountability and responsiveness they deserve.

## How osTicket works for you

1. Users create tickets via your website, email, or phone
1. Incoming tickets are saved and assigned to agents
1. Agents help your users resolve their issues

osTicket is an attractive alternative to higher-cost and complex customer
support systems; simple, lightweight, reliable, open source, web-based and
easy to setup and use. The best part is, it's completely free.

## Requirements

- HTTP server running Microsoft® IIS or Apache
- PHP version 8.0
- mysqli extension for PHP
- MySQL database version 5.5

### Recommendations

- gd, gettext, imap, json, mbstring, and xml extensions for PHP
- APC module enabled and configured for PHP

## Deployment

osTicket now supports bleeding-edge installations. The easiest way to
install the software and track updates is to clone the public repository.
Create a folder on you web server (using whatever method makes sense for
you) and cd into it. Then clone the repository (the folder must be empty!):

    git clone https://github.com/osTicket/osTicket

And deploy the code into somewhere in your server's www root folder, for
instance

    cd osTicket
    php manage.php deploy --setup /var/www/htdocs/osticket/

Then you can configure your server if necessary to serve that folder, and
visit the page and install osTicket as usual. Go ahead and even delete
setup/ folder out of the deployment location when you’re finished. Then,
later, you can fetch updates and deploy them (from the folder where you
cloned the git repo into)

    git pull
    php manage.php deploy -v /var/www/htdocs/osticket/

## Upgrading

osTicket supports upgrading from 1.6-rc1 and later versions. As with any
upgrade, strongly consider a backup of your attachment files, database, and
osTicket codebase before embarking on an upgrade.

To trigger the update process, fetch the osTicket tarball from either
the osTicket [github](http://github.com/osTicket/osTicket/releases) page
or from the [osTicket website](https://osticket.com). Extract the tarball
into the folder of your osTicket codebase. This can also be accomplished
with the zip file, and a FTP client can of course be used to upload the new
source code to your server.

Any way you choose your adventure, when you have your codebase upgraded to
osTicket-1.7, visit the /scp page of you ticketing system. The upgrader will
be presented and will walk you through the rest of the process. (The couple
clicks needed to go through the process are pretty boring to describe).

### Upgrading from v1.6

**WARNING**: If you are upgrading from osTicket 1.6, please ensure that all
your files in your upload folder are both readable and writable to your
http server software. Unreadable files will not be migrated to the
database during the upgrade and will be effectively lost.

After upgrading, we recommend migrating your attachments to the database or
to the new filesystem plugin. Use the `file` command-line applet to perform
the migration.

    php manage.php file migrate --backend=6 --to=D

View the UPGRADING.txt file for other todo items to complete your upgrade.

## Help

Visit the [Documentation](https://docs.osticket.com/) or the
[forum](https://forum.osticket.com/). And if you'd like professional help
managing your osTicket installation,
[commercial support](https://osticket.com/support/) is available.

## Contributing

Create your own fork of the project and use
[git-flow](https://github.com/nvie/gitflow) to create a new feature. Once
the feature is published in your fork, send a pull request to begin the
conversation of integrating your new feature into osTicket.

### Localization

[![Crowdin](https://d322cqt584bo4o.cloudfront.net/osticket-official/localized.png)](http://i18n.osticket.com/project/osticket-official)

The interface for osTicket is now completely translatable. Language packs
are available on the [download page](https://osticket.com/download). If you
do not see your language there, join the [Crowdin](https://crowdin.com/project/osticket-official)
project and request to have your language added. Languages which reach 100%
translated are are significantly reviewed will be made available on the
osTicket download page.

The software can also be translated in place in our [JIPT site](http://jipt.i18n.osticket.com).
Once you have a Crowdin account, login and translate the software in your browser!

Localizing strings in new code requires usage of a [few rules](setup/doc/i18n.md).

## License

osTicket is released under the GPL2 license. See the included LICENSE.txt
file for the gory details of the General Public License.

osTicket is supported by several magical open source projects including:

- [Font-Awesome](http://fortawesome.github.com/Font-Awesome/)
- [HTMLawed](http://www.bioinformatics.org/phplabware/internal_utilities/htmLawed)
- [jQuery dropdown](http://labs.abeautifulsite.net/jquery-dropdown/)
- [jsTimezoneDetect](http://pellepim.bitbucket.org/jstz/)
- [mPDF](http://www.mpdf1.com/)
- [PasswordHash](http://www.openwall.com/phpass/)
- [PEAR](http://pear.php.net/package/PEAR)
- [PEAR/Auth_SASL](http://pear.php.net/package/Auth_SASL)
- [PEAR/Mail](http://pear.php.net/package/mail)
- [PEAR/Net_SMTP](http://pear.php.net/package/Net_SMTP)
- [PEAR/Net_Socket](http://pear.php.net/package/Net_Socket)
- [PEAR/Serivces_JSON](http://pear.php.net/package/Services_JSON)
- [php-gettext](https://launchpad.net/php-gettext/)
- [phpseclib](http://phpseclib.sourceforge.net/)
- [Spyc](http://github.com/mustangostang/spyc)

## Customization osTicket for Mat-Norge Helpdesk

In this project customization applies only on the user interface (UI) part of the osTicket.
We follows the latest trends and technology in order to develope user interface looks modern and responsive.
In addition we adopts the Mat-Norge color scheme that used as for key visual element of company identity.

## Recommended developer setup for customizaiton osTicket UI

- Install node
- Install yarn to handle package.json scripts
- After installed node and yarn, run the command: yarn (this install all packages that exists in package.json file, the command shoud be run in the root file directory)
- In order to compile sass, run the command: yarn compile:sass (in root file directory)

## Custom scss file directory

All the custom scss files are located in the customizationUI folder (on root directory).
Compiled css file are located in the css folder (root directory).
Please see the package.json scripts to know about how we configure scripts to compile scss file.

## How to use custom css file

There are three custom css file (compiled scss files) located in css folder (in root directory).

1. customClientPanel.css : this style works for client panel UI and it is imported in the directory:: includes > client > header.inc.php in the header section.
2. customStaffLoginPage.css : this style works for staff login pages UI and it is imported in the directory:: includes > staff > login.header.php in the header section.
3. customStaffPanel.css : this style works for staff panel (after logged in) UI and it is imported in the directory:: includes > staff > header.inc.php in the header section.

## How to upgrade osTicket in this project

- if you are on "develop" branch then checkout to "matnorge-helpdesk-v1.17.x" branch
- create new branch (you can give branch name like "matnorge-helpdesk-v[write-latest-version-number-of-osTicket]" )
- checkout to newly created branch
- write the following git commmands:
  1. sudo git remote add upstream https://github.com/osTicket/osTicket.git (here upstream is the new remote branch, you can give the name as you like)
  2. sudo git fetch upstream
  3. git merge upstream/latest-branch-of-osTicket (basically latest version)

Please watch the osTicket youtube video tutorial regarding How to Install/Upgrade osTicket Using Github
https://www.youtube.com/watch?v=0R4xu118LzM&ab_channel=osTicket
