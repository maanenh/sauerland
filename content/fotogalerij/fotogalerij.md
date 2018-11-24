

<style>

.pwi_container {
	xbackground-color: #D3DEE0;

	border-style:solid;
	border-width:2px;
}

.pwi_album_description{
	xbackground-color: #D3DEE0;
	background-color: #DDD;
	border-bottom-style:solid;
	border-width:1px;
}

.pwi_album_backlink {
	font-size: 12pt;

}
</style>


<script type="text/javascript">
        console.log('voor handler');
      $(document).ready(function () {
        console.log('in handler');
        var settings = {
          username: '112555672993371872022',
		  showPager: 'both',
		  sortAlbums: 'DESC_DATE',
		  labels: {photo:"foto",
                   photos: "foto's",
                   albums: "&lt; Terug naar albumoverzicht"
                  }
          };
        $("#container").pwi(settings);
      });

</script>
<div id="container"> </div>

