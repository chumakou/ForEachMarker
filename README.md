# ForEachMarker
ForEachMarker allows to generate and maintain a number of structured documents. Generated documents can contain specific data or fields.<br>
### Usage:
>java ForEachMarker.java \<templateFileName><br>
### Example:
Let's create template file with name <b>langconfigs.template</b> and the following content:<br>
<br>
\=====================================<br>

\# comments start with '#' character  <br>
<br>
\# this script will be executed for each language in the following list:  <br>
<b>foreach lang = en,fr,pl</b><br>

\# this command will save config to file <br>
<b>save <%config%> to ./configs/config_<%lang%>.ini </b><br>
<br>
\# let's define some default fields <br>
<b>langDescriptionFile = lang/description_<%lang%>.txt <br>
langGroup = Romance <br></b>

\# specific field value for pl language <br>
<b>langGroup.pl = Slavic</b>

\# miltiline field starts with ={{ <br>
<b>
config ={{ <br> 
language=<%lang%>; <br>
descriptionLocation=<%langDescriptionFile%>; <br>
languageGroup=<%langGroup%>; <br>
}} <br>
</b>
\=====================================<br>
<br>
Runs ForEachMarker with <b>langconfigs.template</b> template: <br>
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

