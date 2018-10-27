
## Ons huisje

<div style="float:right">
<img id="huisjeFoto1" /><br/><br/><br/>
<img id="huisjeFoto3" />
</div>

Sinds 2004 hebben wij dit huisje in Sauerland. In de zomer een fijne plek om te luieren, te wandelen, te zwemmen en vuurtje te stoken.
In de winter, als er sneeuw ligt, kun je er prima langlaufen. Maar ook zonder sneeuw is het heerlijk om buiten te zijn om te wandelen.
Het huisje ligt buiten Oberhundem op een stuk grond met meerdere huisjes. Sommige huisjes worden permanent gebruikt en sommige alleen als vakantiehuisje.
Er is een grote tuin en dus zie of hoor je de buren niet. Het is er heerlijk rustig met veel groen een prettige atmosfeer.
Het huisje zelf is plezierig eenvoudig en goed ingericht.

&nbsp;

<img id="huisjeFoto2" />

&nbsp;

We verhuren het huisje graag aan vrienden en bekenden. Zie de [Verhuur pagina](#/content/Verhuur/Beschikbaarheid) voor informatie over huren.


Lies Pol<br/>
Guus Pol<br/>
Wim van der Laan<br/>
Hanno van Maanen

<script>
    function calculateSummerWinter() {
        var today = new Date();
        var first = new Date(today.getFullYear(), 0, 1);
        var dayOfYear = Math.round(((today - first) / 1000 / 60 / 60 / 24) + .5, 0);
        var result = (dayOfYear < 60 || dayOfYear > 290)? 'winter': 'summer';
        return result;
    }

    function setImageSource() {
        var period = calculateSummerWinter();
        $("#huisjeFoto1").attr("src", "fotos/" + period + "/foto1.jpg");
        $("#huisjeFoto2").attr("src", "fotos/" + period + "/foto2.jpg");
        $("#huisjeFoto3").attr("src", "fotos/" + period + "/foto3.jpg");
    }

    setImageSource();


</script>
