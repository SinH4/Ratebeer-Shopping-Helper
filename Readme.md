<h2 id="Content">Content</h2>

1. [Ratebeer Shopping Helper](#RSH)<br>
1.1 [Pupose](#RSHPurpose)<br>
1.2 [Usage](#RSHUsage)<br>
1.3 [License](#RSHLicense)<br>
1.4 [Disclaimer](#RSHDisclaimer)<br>
1.5 [Error](#RSHError)<br>
1.5.1 [File not found](#RSHfnf)<br>
1.5.2 [no module named termcolor](#RSHnmnt)<br><br>
2. [Low Hanging Fruits](#LHF)<br>
2.1 [Pupose](#LHFPurpose)<br>
2.2 [Usage](#LHFUsage)<br>
2.2.1 [gen_Bier.save.py](#LHFgBs)<br>
2.2.2 [local_fruits.py](#LHFlf)<br>
2.4 [Disclaimer](#LHFDisclaimer)<br>

<h1 id="RSH">Ratebeer Shopping Helper</h1>

This little script will help you buy beers for you and other <b>Ratebeerians</b>.

<h3 id="RSHPupose">Purpose</h3>
This script will allow you to search the ratings of you and your friends, and will show you who already rated the wanted beer.

<h3 id="RSHUsage">Usage</h3>
1. Download all your ratings (click on <i>My Account → My Beer Ratings → Compile My Ratings</i> ; leave the standard delimiter "|")<br>
2. Get your friend(s) to send you  their ratings<br>
3. Put the `*.csv` files in the <i>Ratings</i> folder<br>
4. Run `prepare_data.py` once for each user (prepare_data.py is only tested on a Linuxmachine)<br>
5. Install <i>QPython3</i> or a similar app on your mobile device<br>
6. Copy the `compare.py` and all needed <b>\*.ratings</b> files to the mobile device<br>
7. Start `compare.py` and have fun<br><br>

If you run the program only on a computer item <b>6)</b> and <b>7)</b> are unnecessary.

<h3 id="RSHLicense">License</h3>
This and all versions is/will be licensed under the [GPLv3](./neur0nic/Ratebeer-Shopping-Helper/LICENSE).

<h3 id="RSHDisclaimer">Disclaimer</h3>
This is just a little fun project I do, so I can buy some beers for <i>jfb</i> 's next visit. There will be most likely
no maintaining. If you find a bug in this project, you can contact me on [github](https://github.com/neur0nic) or on
[ratebeer](https://www.ratebeer.com/user/133619/).
<br>This script is only tested on an Linux machine with Python 3.6 and an Android 4.2 with QPython3.

<h3 id="RSHError">Error</h3>
<h4 id="RSHFnf">File not found</h4>
If the program on your mobile device returns something like <i>file *.ratings not found</i> , you probably need to change
`compare.py` line <b>53</b> to your actual working directory.
<h4 id="RSHnmnt">no module named termcolor</h4>
I had to manually install the <i>termcolor</i> package to my Android app


<h1 id="LHF">Low Hanging Fruits</h1>

<h3 id="LHFPurpose">Purpose</h3>
After shopping with the `compare.py` script, I realised I was missing some pretty common ratings. This little
program is looking for beers in Germany, Austria or Switzerland that have e.g. 100 and more ratings and hence are
common beers and easy to get in that country.

<h3 id="LHFUsage">Usage</h3>
The program is split into two parts. Part one (`gen_Bier.save.py`) generates a list of "all" beers available in
a country. Part two (`local_fruits.py`) generates a text-file that list the names of the missing ratings.

<h4 id="LHFgBs">gen_Bier.save.py</h4>
A list of all the breweies in the country is need and stored as `breweries.lst` in the same folder as `gen_Bier.save.py`.
Only one brewery per line and no special character (less is more).
```sh
python gen_Bier.save.py - - de
```
Currently the parameters `de`, `at` and `ch` are available.<br>
The files `de-Bier.save` for Germany, `ch-Bier.save` for Switzerland and thanks to
[SinH4](https://www.ratebeer.com/user/324362/) `at-Bier.save` for Austria are available in the repository
(as per Aug. 2017).

<h4 id="LHFlf">local_fruits.py</h4>
For comparison your ratings as `*.csv` files are needed.
```sh
python local_fruits.py username minimum_ratings locale
``` 
for example
```sh
python local_fruits.py neur0 200 de
``` 
generates a text file with all the German beers with more then 200 ratings that neur0 hasn't rated.

<h3 id="LHFDisclaimer">Disclaimer</h3>
I wrote this pretty quickly, half in German, half in English, so the code is close to unreadable (even for me). Also
[ratebeer.py](https://github.com/alilja/ratebeer) returned some errors and I just started ignoring them. So maybe this
will not be a complete list of <b>low hanging fruits</b>, but it's the next step to get some quick ratings.<br>
This program is only tested with Python 3.6 on a Linux machine.
