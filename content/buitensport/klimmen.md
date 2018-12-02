
<style>
.floatStyle {
	float: right;
}
#map-canvas {
	height: 600px;
	width: 690px;
	
}

#map-canvas img {
	margin: 0px;
}

</style>

<script type="text/javascript">

	var map;
	var bounds;
	var infowindow;

	function HomeControl(controlDiv, map) {

	  // Set CSS styles for the DIV containing the control
	  // Setting padding to 5 px will offset the control
	  // from the edge of the map
	  controlDiv.style.padding = '5px';

	  // Set CSS for the control border
	  var controlUI = document.createElement('div');
	  controlUI.style.backgroundColor = 'white';
	  controlUI.style.borderStyle = 'solid';
	  controlUI.style.borderWidth = '2px';
	  controlUI.style.cursor = 'pointer';
	  controlUI.style.textAlign = 'center';
	  controlUI.title = 'Click to set the map to Home';
	  controlDiv.appendChild(controlUI);

	  // Set CSS for the control interior
	  var controlText = document.createElement('div');
	  controlText.style.fontFamily = 'Arial,sans-serif';
	  controlText.style.fontSize = '12px';
	  controlText.style.paddingLeft = '4px';
	  controlText.style.paddingRight = '4px';
	  controlText.innerHTML = '<b>Home</b>';
	  controlUI.appendChild(controlText);

	  
	  // Setup the click event listeners
	  google.maps.event.addDomListener(controlUI, 'click', function() {
		 map.fitBounds(bounds);		  
	  });
	}	
	
    function initialize() {


        var pinImage = null;
        var pinImageHome = 'http://maps.google.com/mapfiles/ms/icons/green-dot.png';

        var locations = [{
              name: 'Home',
              latLng: new google.maps.LatLng(51.07901,8.1765),
              icon: pinImageHome,
              felsInfo: []
            },{
              name: 'Honnetal',
              latLng: new google.maps.LatLng(51.375376,7.8603642),
              icon: pinImage,
              felsInfo: [
                    {ref: "hoennetal/4566", name: "Afrikafels"},
                    {ref: "hoennetal/4280", name: "Bärenstein"},
                    {ref: "hoennetal/4283", name: "Gnom"},
                    {ref: "hoennetal/4282", name: "Hausstadtfelsen"},
                    {ref: "hoennetal/4565", name: "Karhoffhöhle"},
                    {ref: "hoennetal/4564", name: "Kleiner Fels"},
                    {ref: "hoennetal/4561", name: "Linker Burschenfels"},
                    {ref: "hoennetal/4563", name: "Loch Näss"},
                    {ref: "hoennetal/4567", name: "Offener Fels"},
                    {ref: "hoennetal/4562", name: "Rechter Burschenfels"},
                    {ref: "hoennetal/4568", name: "Versteckter Fels"},
                    {ref: "hoennetal/4281", name: "Waldstein"}
              ]
            },{
              name: 'Werdohler Lenneplatte',
              latLng: new google.maps.LatLng(51.262173,7.7567593),
              icon: pinImage,
              felsInfo: [
                    {ref: "unteres_lennetal/4757", name: "Denkmalwand"},
                    {ref: "unteres_lennetal/4758", name: "Lennewächter"},
                    {ref: "unteres_lennetal/4279", name: "Werdohler Lenneplatte"}
              ]
            },{
              name: 'Unterer Elberskamp',
              latLng: new google.maps.LatLng(51.151421,7.9574343),
              icon: pinImage,
              felsInfo: [{ref: 'biggetal/2144'}]
            },{
              name: 'Scharpenbeul',
              latLng: new google.maps.LatLng(51.088989,7.8088821),
              icon: pinImage,
              felsInfo: [{ref: 'biggetal/4704'}]
            },{
              name: 'BorghauserWand',
              latLng: new google.maps.LatLng(51.151336,7.9973096),
              icon: pinImage,
              felsInfo: [{ref: 'oberes_lennetal/4276'}]
            },{
              name: 'Hillenberg Warstein',
              latLng: new google.maps.LatLng(51.435193,8.3528023),
              icon: pinImage,
              felsInfo: []
            },{
              name: 'Am Bahnchen Bestwig',
              latLng: new google.maps.LatLng(51.351670,8.4103590),
              icon: pinImage,
              felsInfo: [{ref: 'hochsauerland/4546'}]
            },{
              name: 'Bruchhauser Steine',
              latLng: new google.maps.LatLng(51.320278,8.544167),
              icon: pinImage,
              felsInfo: []
            },{
              name: 'Meisterstein bei Siedlinghausen',
              latLng: new google.maps.LatLng(51.240970,8.4757293),
              icon: pinImage,
              felsInfo: [{ref: 'hochsauerland/4011'}]
            },{
              name: 'Steinkuhle Neuastenberg',
              latLng: new google.maps.LatLng(51.160375,8.4783970),
              icon: pinImage,
              felsInfo: [{ref: 'hochsauerland/4703'}]
            },{
              name: 'Steinschab',
              latLng: new google.maps.LatLng(51.126606,8.6029966),
              icon: pinImage,
              felsInfo: [{ref: 'hochsauerland/1891'}]
            },{
              name: 'Kapplerstein',
              latLng: new google.maps.LatLng(51.057327,8.2855595),
              icon: pinImage,
              felsInfo: [{ref: 'hochsauerland/4665'}]
            }];

        var southWest = new google.maps.LatLng(51.05, 7.75);
        var northEast = new google.maps.LatLng(51.43, 8.61);

        bounds = new google.maps.LatLngBounds(southWest, northEast);

        google.maps.visualRefresh = true;

        infowindow = new google.maps.InfoWindow();


        var mapOptions = {
          zoom: 1,
		  scaleControl: true,
		  overviewMapControl: true,
          mapTypeId: google.maps.MapTypeId.ROADMAP
        };
        map = new google.maps.Map(document.getElementById("map-canvas"),
            mapOptions);
					
		  // Create the DIV to hold the control and
		  // call the HomeControl() constructor passing
		  // in this DIV.
		  var homeControlDiv = document.createElement('div');
		  var homeControl = new HomeControl(homeControlDiv, map);

		  homeControlDiv.index = 1;
		  map.controls[google.maps.ControlPosition.TOP_RIGHT].push(homeControlDiv);		

		  map.fitBounds(bounds);		  
 		  
		  var i;
		  for (i in locations) {
			var location = locations[i];
			
			var marker = new google.maps.Marker({
				position: location.latLng,
				map: map,
				icon: location.icon,				
				title: location.name
			});

			attachInfoWindow(marker, location.name, location.felsInfo);			
		  }
    }
		
	function attachInfoWindow(marker, text, felsInfoList) {

	  google.maps.event.addListener(marker, 'click', function() {
	  
		var routeHref = 'http://maps.google.com/maps?hl=nl&t=m&saddr=51.078791,8.176789&daddr=' + marker.getPosition().lat() + ',' + marker.getPosition().lng();
		var inhoud = '<i><b>' + text + '</b></i><br/><a href="' + routeHref + '" target="_blank">Routebeschrijving</a>';
		
		var i;
		for (i in felsInfoList) {
			var felsInfo = felsInfoList[i];
			var descHref = 'http://felsinfo.alpenverein.de/felsinfo/sauerland/' + felsInfo.ref;
			var desc = 'Beschrijving';
			if (felsInfo.name) {
				desc += ': ' + felsInfo.name;
			}
			inhoud += '<br/><a href="' + descHref + '" target="_blank">' + desc + '</a>';
		}
	  
		infowindow.setContent(inhoud);
		infowindow.open(marker.get('map'), marker);
	  });
	}	  




    $(document).ready(function() {
        initialize();
    });

</script>


<p>
Bij Nederlandse klimmers zijn de klimgebieden van het Sauerland nog niet erg bekend. Toch zijn hier tal van kleine klimgebieden. Eind mei 2013 is één van de grootste klimgebieden van het Sauerland feestelijk geopend; <br/>de <a href="http://kletterarena.info/hillenberg.php">Hilleberg bij Warstein.</a>
</p>

<p>
Voor meer info zie: <a href="http://kletterarena.info/">http://kletterarena.info</a> en <a href="http://felsinfo.alpenverein.de/">http://felsinfo.alpenverein.de/</a>. Ook op de site van de NKBV is informatie te vinden over deze gebieden. Zie: <a href="http://www.nkbv.nl/sportklimmen/klimgebieden/klimmen-in-duitsland">http://www.nkbv.nl/sportklimmen/klimgebieden/klimmen-in-duitsland</a>.
</p>
<p>
In de NKBV-webshop kun je de <a href="http://www.nkbv.nl/webshop/Land+der+tausend+Berge+-+Sauerland+/112">klimtopo van het Sauerland</a> kopen. 
</p>
<p style="color: red;">Let op: Sommige gebieden kunnen gesloten zijn vanwege steenslaggevaar of natuurbescherming. Kijk daarom ook altijd op <a href="http://kletterarena.info/klettergebiete.php">http://kletterarena.info/klettergebiete.php</a>.</p>
<img src="../../fotos/klimmen.jpg"/>

<h2>Lokaties van de klimrotsen</h2>
<p>Hieronder op de kaart de kliklocaties. Door te klikken op de "markers" is meer informatie te krijgen.</p>
<div id="map-canvas"></div>
<div>&nbsp;</div>
