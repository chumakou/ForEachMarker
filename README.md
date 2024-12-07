# ForEachMarker
ForEachMarker allows to generate and maintain a number of structured documents. Generated documents can contain specific data or fields.<br>
### Usage:
java ForEachMarker.java \<templateFileName><br>
### Example:
Let's create template file with name <b>langconfigs.fem</b> and the following content:<br>
<br>
\=====================================<br>
<b>
\# comments start with '#' character  <br>
<br>
\# this script will be executed for each language in the following list:  <br>
foreach lang = en,fr,pl<br>

\# this command will save config to file <br>
save <%config%> to ./configs/config_<%lang%>.ini <br>
<br>
\# let's define some default fields <br>
langDescriptionFile = lang/description_<%lang%>.txt <br>
langGroup = Romance <br>

\# specific field value for pl language <br>
langGroup.pl = Slavic

\# miltiline field starts with ={{ <br>
config ={{ <br> 
language=<%lang%>; <br>
descriptionLocation=<%langDescriptionFile%>; <br>
languageGroup=<%langGroup%>; <br>
}} <br>
</b>
\=====================================<br>
<br>
Runs ForEachMarker with <b>langconfigs.fem</b> template: <br>
><b>java ForEachMarker.java langconfigs.fem</b><br>
<br>
This template will generate the following 3 config files: <br>
<br>
<b> config_en.ini: </b><br>
language=en; <br>
descriptionLocation=lang/description_en.txt; <br>
languageGroup=Romance; <br>
<br>
<b> config_fr.ini: </b> <br>
language=fr; <br>
descriptionLocation=lang/description_fr.txt; <br>
languageGroup=Romance; <br>
<br>
<b> config_pl.ini: </b> <br>
language=pl; <br>
descriptionLocation=lang/description_pl.txt; <br>
languageGroup=Slavic; <br>
<br>

