
<style>
   #homeControl{
      padding: 5px;
    }

    #homeControl .outer{
      background-color: #FFFFFF;
      border: 2px solid #000000;
      cursor: pointer;
      text-align: center;
      height: 20px;
    }

    #homeControl .outer .inner{
      font-family: Arial,sans-serif;
      font-size: 12px;
      padding-top: 2px;
      padding-left: 4px;
      padding-right: 4px;
      font-weight: bold;
    }
</style>

<script type="text/javascript">


    var feriendorf = new google.maps.LatLng(51.078791,8.176789);

    function HomeControl(map) {
      var $container = $(document.createElement('DIV')),
        $outer = $(document.createElement('DIV')),
        $inner = $(document.createElement('DIV'));

      $inner.addClass("inner").html("Ons huisje");
      $outer.addClass("outer").attr('title', "Click to set the map to Home");
      $container.attr("id", "homeControl");

      $container.append( $outer.append( $inner ) );

      google.maps.event.addDomListener($outer.get(0), 'click', function() {
        map.setCenter(feriendorf)
      });

      this.index = 1;
      map.controls[google.maps.ControlPosition.TOP_RIGHT].push($container.get(0));
    }


$('#map').gmap3({
 marker:{
    latLng: feriendorf,
    events:{
          click: function(marker, event, context){
            var map = $(this).gmap3("get");
            var infowindow = $(this).gmap3({get:{name:"infowindow"}});
            if (infowindow){
              infowindow.open(map, marker);
            } else {
              $(this).gmap3({
                infowindow:{
                  anchor:marker,
                  options:{content: "feriendorf 4"}
                }
              });
            }
          }}
    },
 map:{
    options:{
     zoom: 15,
     mapTypeId: google.maps.MapTypeId.HYBRID,
     mapTypeControl: true,
     navigationControl: true,
     scrollwheel: true,
     streetViewControl: true
    },
      callback: function(map){
        new HomeControl(map);
      }

 }
});

</script>

<div id="map" style="width: 700px; height: 470px"></div>
