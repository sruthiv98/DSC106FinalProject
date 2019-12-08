<!DOCTYPE html>
<html lang="en">
<head>
  <title>Taylor Swift</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css">
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
  <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js"></script>
  <style>
    /* Set height of the grid so .sidenav can be 100% (adjust as needed) */
    .row.content {height: 550px}
    
    /* Set gray background color and 100% height */
    .sidenav {
      background-color: #f1f1f1;
      height: 100%;
    }
        
    /* On small screens, set height to 'auto' for the grid */
    @media screen and (max-width: 767px) {
      .row.content {height: auto;} 
    }
  </style>
</head>
<body style="background-color:#9B7A8F;">

<nav class="navbar navbar-inverse visible-xs">
  <div class="container-fluid">
    <div class="navbar-header">
      
      <a class="navbar-brand" href="#">Logo</a>
    </div>
    <div class="collapse navbar-collapse" id="myNavbar">
      
    </div>
  </div>
</nav>

<div class="container-fluid">
  <div class="row content">
    <div class="col-sm-3 sidenav hidden-xs" style="background-color:#9B7A8F;">
      <h2 style="font-family:roboto;font-width:bold;">Miss Americana</h2>
      <p style="font-family:roboto;">The Journey of Taylor Swift from Country to Pop</p>
            <img src = 'countryts.jpg' width=100% size='auto'>

            <img src = 'popts.jpg' width=100% size='auto'>
            <img src = '1989.jpg' width=100% size='auto'>
            <img src = 'crowd.jpg' width=100% size='auto'>
            <img src = 'tsgrammy.jpg' width=100% size='auto'>


            <p style="font-family:roboto;">Saveree Joshipura and Sruthi Vedantham</p>

      <ul class="nav nav-pills nav-stacked">
       
        
      </ul><br>
    </div>
    <br>
    
    <div class="col-sm-9">
            <div class="row">
                    <div class="col-sm-6" >
                            <div class="well" style="background-color:#B08F80;">
                            <h4 style="font-family:roboto;font-width:bold;">Most Occuring Country Lyrics </h4>

                                    <img src='country.png' width = 100%; height= 'auto'>
                                    <p style="font-family:roboto;">Taylor's Country lyrics emphasize idealistic ideas, showing her youth as an artist, with words such as "hope", "spotlight", 
                                    "happiness", etc.  </p>
                              
                            </div>
                            </div>
                            <div class="col-sm-6">
                                    <div class="well" style="background-color:#B08F80;">
                                    <h4 style="font-family:roboto;font-width:bold;">Most Occuring Pop Lyrics</h4>

                                    <img src='pop.png' width = 100%; height= 'auto'>    
                                    <p style="font-family:roboto;">Taylor's Pop lyrics feature more negative sentiments, indicating her dive into deeper, more emotional music, with words such as "never", "missing", "losing", "forgetting", etc.  </p>
                                    </div>
                                  </div>
              </div>
            <div class="row">
                    <div class="col-sm-6">
                            <div class="well" style="background-color:#B08F80;">
                              <h4 style="font-family:roboto;font-width:bold;">Fearless Tour 2009-2010</h4>
                              <script src="https://cdnjs.cloudflare.com/ajax/libs/proj4js/2.3.6/proj4.js"></script>
                              <script src="https://code.highcharts.com/maps/highmaps.js"></script>
                              <script src="https://code.highcharts.com/maps/modules/data.js"></script>
                              <script src="https://code.highcharts.com/maps/modules/exporting.js"></script>
                              <script src="https://code.highcharts.com/maps/modules/offline-exporting.js"></script>
                              <script src="https://code.highcharts.com/mapdata/countries/us/us-all.js"></script>
                              
                              <div id="container"></div>
                              
                              <script>
                              var H = Highcharts,
                                  map = H.maps['countries/us/us-all'],
                                  chart;
                              
                              // Add series with state capital bubbles
                              Highcharts.getJSON('https://gist.githubusercontent.com/saveree/0761239330e43b0da9ddd713946f5a73/raw/e81b33976556347084c08facd2f5657a3c88f156/gistfile1.txt', function (json) {
                                  var data = [];
                                  json.forEach(function (p) {
                                      p.z = p.population;
                                      data.push(p);
                                  });
                              
                                  chart = Highcharts.mapChart('container', {
                                      title: {
                                          text: ''
                                      },
                              
                                      tooltip: {
                                          pointFormat: '{point.capital}, {point.parentState}<br>' +
                                              'Lat: {point.lat}<br>' +
                                              'Lon: {point.lon}<br>' +
                                              'Population: {point.population}'
                                      },
                              
                                      xAxis: {
                                          crosshair: {
                                              zIndex: 5,
                                              dashStyle: 'dot',
                                              snap: false,
                                              color: 'gray'
                                          }
                                      },
                              
                                      yAxis: {
                                          crosshair: {
                                              zIndex: 5,
                                              dashStyle: 'dot',
                                              snap: false,
                                              color: 'gray'
                                          }
                                      },
                              
                                      series: [{
                                          name: 'Basemap',
                                          mapData: map,
                                          borderColor: '#606060',
                                          nullColor: 'rgba(200, 200, 200, 0.2)',
                                          showInLegend: false
                                      }, {
                                          name: 'Separators',
                                          type: 'mapline',
                                          data: H.geojson(map, 'mapline'),
                                          color: '#101010',
                                          enableMouseTracking: false,
                                          showInLegend: false
                                      }, {
                                          type: 'mapbubble',
                                          dataLabels: {
                                              enabled: true,
                                              format: '{point.capital}'
                                          },
                                          name: 'Tour Cities',
                                          data: data,
                                          maxSize: '12%',
                                          color: '#c7603d' 
                                      }]
                                  });
                              });
                              
                              // Display custom label with lat/lon next to crosshairs
                              document.getElementById('container').addEventListener('mousemove', function (e) {
                                  var position;
                                  if (chart) {
                                      if (!chart.lab) {
                                          chart.lab = chart.renderer.text('', 0, 0)
                                              .attr({
                                                  zIndex: 5
                                              })
                                              .css({
                                                  color: '#505050'
                                              })
                                              .add();
                                      }
                              
                                      e = chart.pointer.normalize(e);
                                      position = chart.fromPointToLatLon({
                                          x: chart.xAxis[0].toValue(e.chartX),
                                          y: chart.yAxis[0].toValue(e.chartY)
                                      });
                              
                                      chart.lab.attr({
                                          x: e.chartX + 5,
                                          y: e.chartY - 22,
                                          text: 'Lat: ' + position.lat.toFixed(2) + '<br>Lon: ' + position.lon.toFixed(2)
                                      });
                                  }
                              });
                              
                              document.getElementById('container').addEventListener('mouseout', function () {
                                  if (chart && chart.lab) {
                                      chart.lab.destroy();
                                      chart.lab = null;
                                  }
                              });
                              </script>

                              <p style="font-family:roboto;" class="highcharts-description">
                                    Taylor took her Fearless tour, a Country music tour, to cities in the US where Country music is more popular. These include
                                    smaller, less metropolitan cities in the South and Mid-West. 
                                </p>
                              
                            </div>
                          </div>
                          <div class="col-sm-6">
                            <div class="well" style="background-color:#B08F80;">
                              <h4 style="font-family:roboto;font-width:bold;">The Red Tour: 2013-2014</h4>
                              <script src="https://cdnjs.cloudflare.com/ajax/libs/proj4js/2.3.6/proj4.js"></script>
                            <script src="https://code.highcharts.com/maps/highmaps.js"></script>
                            <script src="https://code.highcharts.com/maps/modules/data.js"></script>
                            <script src="https://code.highcharts.com/maps/modules/exporting.js"></script>
                            <script src="https://code.highcharts.com/maps/modules/offline-exporting.js"></script>
                            <script src="https://code.highcharts.com/mapdata/countries/us/us-all.js"></script>

                            <div id="container2"></div>

                            <script>
                            var H = Highcharts,
                                map = H.maps['countries/us/us-all'],
                                chart;
                            // Add series with state capital bubbles
                            Highcharts.getJSON('https://gist.githubusercontent.com/sruthiv98/67d12faa58c35c8915d324a5137ca3da/raw/9265549e1e5597357c5187c103376b3104060dac/proj2.json', function (json) {
                                var data = [];
                                json.forEach(function (p) {
                                    p.z = p.population;
                                    data.push(p);
                                });
                                chart = Highcharts.mapChart('container2', {
                                    title: {
                                        text: ''
                                    },
                                    tooltip: {
                                        pointFormat: '{point.capital}, {point.parentState}<br>' +
                                            'Lat: {point.lat}<br>' +
                                            'Lon: {point.lon}<br>' +
                                            'Population: {point.population}'
                                    },
                                    xAxis: {
                                        crosshair: {
                                            zIndex: 5,
                                            dashStyle: 'dot',
                                            snap: false,
                                            color: 'gray'
                                        }
                                    },
                                    yAxis: {
                                        crosshair: {
                                            zIndex: 5,
                                            dashStyle: 'dot',
                                            snap: false,
                                            color: 'gray'
                                        }
                                    },
                                    series: [{
                                        name: 'Basemap',
                                        mapData: map,
                                        borderColor: '#606060',
                                        nullColor: 'rgba(200, 200, 200, 0.2)',
                                        showInLegend: false
                                    }, {
                                        name: 'Separators',
                                        type: 'mapline',
                                        data: H.geojson(map, 'mapline'),
                                        color: '#101010',
                                        enableMouseTracking: false,
                                        showInLegend: false
                                    }, {
                                        type: 'mapbubble',
                                        dataLabels: {
                                            enabled: true,
                                            format: '{point.capital}'
                                        },
                                        name: 'Cities',
                                        data: data,
                                        maxSize: '12%',
                                        color: '#c7603d'
                                    }]
                                });
                            });
                            // Display custom label with lat/lon next to crosshairs
                            document.getElementById('container2').addEventListener('mousemove', function (e) {
                                var position;
                                if (chart) {
                                    if (!chart.lab) {
                                        chart.lab = chart.renderer.text('', 0, 0)
                                            .attr({
                                                zIndex: 5
                                            })
                                            .css({
                                                color: '#505050'
                                            })
                                            .add();
                                    }
                                    e = chart.pointer.normalize(e);
                                    position = chart.fromPointToLatLon({
                                        x: chart.xAxis[0].toValue(e.chartX),
                                        y: chart.yAxis[0].toValue(e.chartY)
                                    });
                                    chart.lab.attr({
                                        x: e.chartX + 5,
                                        y: e.chartY - 22,
                                        text: 'Lat: ' + position.lat.toFixed(2) + '<br>Lon: ' + position.lon.toFixed(2)
                                    });
                                }
                            });
                            document.getElementById('container2').addEventListener('mouseout', function () {
                                if (chart && chart.lab) {
                                    chart.lab.destroy();
                                    chart.lab = null;
                                }
                            });
                            </script>

                            <p style="font-family:roboto;" class="highcharts-description">
                                    Taylor took her Red tour, a Pop music tour, to larger cities in the US, where "mainstream", or Pop music, is more popular.
                                    The shift in locations and the shift in focus from smaller Souther cities to West Coast cities show her genre transition and
                                    resulting fanbase transition. 
                                </p>    

                            </div>
                          </div>
                  </div>
      <div class="row">
            <div class="col-sm-6">
                    <div class="well" style="background-color:#B08F80;">
                      
                      <h4 style="font-family:roboto;font-width:bold;">Album Sales in the United States</h4>
                      <script src="https://code.highcharts.com/highcharts.js"></script>
<script src="https://code.highcharts.com/highcharts-3d.js"></script>
<script src="https://code.highcharts.com/modules/exporting.js"></script>
<script src="https://code.highcharts.com/modules/export-data.js"></script>
<script src="https://code.highcharts.com/modules/accessibility.js"></script>

<figure class="highcharts-figure">
    <link rel = 'stylesheet' href = '3dpie.css'>
    <div id="container3"></div>
    <p class="highcharts-description" style="font-family:roboto;font-width:bold;">
        Comparing her album sales, we can see that Fearless, a country album, and 1989, a pop album, have very similar sales. Fearless remains Taylor's top-grossing album, suggesting that she attained her highest degree of success as a country star. 
    </p>
</figure>

<script>
Highcharts.chart('container3', {
    chart: {
        type: 'pie',
        options3d: {
            enabled: true,
            alpha: 45
        }
    },
    title: {
        text: ''
    },
    subtitle: {
        text: ''
    },
    plotOptions: {
        pie: {
            colors: [
           '#d0daa3', 
           '#d0daa3', 
           '#d0daa3', 
           '#e1ba64', 
           '#e1ba64',
           '#e1ba64',
           '#e1ba64'],
            innerSize: 100,
            depth: 45,
            minSize:80
        }
    },
    series: [{
        name: 'Sales in $',
        data: [
            ['Taylor Swift', 7000000],
            ['Fearless', 12000000],
            ['Speak Now', 5000000],
            ['Red', 6000000],
            ['1989', 10100000],
            ['Reputation', 4500000],
            ['Lover', 679000]
        ]
    }]
});
</script>
                      
                    </div>
                    </div>
                    <div class="col-sm-6">
                            <div class="well" style="background-color:#B08F80;">
                            <h4 style="font-family:roboto;font-width:bold;">GRAMMYs</h4>

                                <img src='GrammysPerAlbum.png' width = 100%; height= 'auto'>
                                <p style="font-family:roboto;"> 1989 was Taylor's album of greatest critical acclaim, showing that her transition from a Country to 
                                    Pop artist was truly complete. 
                                </p>
                            </div>
                          </div>
      </div>
      <div class="row">
            <div class="col-sm-6">
                    <div class="well" style="background-color:#B08F80;">
                      <h4 style="font-family:roboto;font-width:bold;">Taylor's Top 20 Songs on Billboard Hot 100: Country</h4>

                            <script src="https://code.highcharts.com/highcharts.js"></script>
                            <script src="https://code.highcharts.com/highcharts-3d.js"></script>
                            <script src="https://code.highcharts.com/modules/exporting.js"></script>
                            <script src="https://code.highcharts.com/modules/export-data.js"></script>
                            <script src="https://code.highcharts.com/modules/accessibility.js"></script>
                            
                            <figure class="highcharts-figure">
                                <div id="container4"></div>
                            </figure>
                            
                            <script> 
                            Highcharts.chart('container4', {
                                chart: {
                                    type: 'pie',
                                    options3d: {
                                        enabled: true,
                                        alpha: 45,
                                        beta: 0
                                    }
                                },
                                title: {
                                    text: ''
                                },
                                accessibility: {
                                    point: {
                                        valueSuffix: '%'
                                    }
                                },
                                tooltip: {
                                    pointFormat: '{series.name}: <b>{point.percentage:.1f}%</b>'
                                },
                                plotOptions: {
                                    pie: {
                                          colors: [
                                       '#774f20', 
                                       '#d3b282', 
                                       '#e6b05b', 
                                       '#d07953', 
                                       '#5a3931'],
                                        allowPointSelect: true,
                                        cursor: 'pointer',
                                        depth: 35,
                                        dataLabels: {
                                            enabled: true,
                                            format: '{point.name}'
                                        
                                        }
                                    }
                                },
                                series: [{
                                    type: 'pie',
                                    name: 'Share of Taylors Top 20 Songs',
                                    data: [
                                        ['Billboard #1', 7.0],
                                        ['Billboard #2', 5.0],
                                        ['Billboard #3', 2.0],
                                        ['Billboard #4', 1.0],
                                        ['Billboard #5 and beyond', 5]
                                    ]
                                }]
                            });
                            </script>
                            <p style="font-family:roboto;" class="highcharts-description">
                                        Taylor's top Country hits are better distributed than her Pop hits, with a large number of Billboard #1s, #2s, and #3s.  
                                    </p>
                      
                    </div>
                    </div>
                    <div class="col-sm-6">
                            <div class="well" style="background-color:#B08F80;" >
                              <h4 style="font-family:roboto;font-width:bold;">Taylor's Top 20 Songs on Billboard Hot 100: Pop</h4>
                                    <script src="https://code.highcharts.com/highcharts.js"></script>
                                    <script src="https://code.highcharts.com/highcharts-3d.js"></script>
                                    <script src="https://code.highcharts.com/modules/exporting.js"></script>
                                    <script src="https://code.highcharts.com/modules/export-data.js"></script>
                                    <script src="https://code.highcharts.com/modules/accessibility.js"></script>
                                    
                                    <figure class="highcharts-figure">
                                        <div id="container5"></div>
                                    
                                    </figure>
                                    
                                    <script> 
                                    Highcharts.chart('container5', {
                                        chart: {
                                            type: 'pie',
                                            options3d: {
                                                enabled: true,
                                                alpha: 45,
                                                beta: 0
                                            }
                                        },
                                        title: {
                                            text: ""
                                        },
                                        accessibility: {
                                            point: {
                                                valueSuffix: '%'
                                            }
                                        },
                                        tooltip: {
                                            pointFormat: '{series.name}: <b>{point.percentage:.1f}%</b>'
                                        },
                                        plotOptions: {
                                            pie: {
                                                  colors: [
                                               '#a14f4d', 
                                               '#8f5c57', 
                                               '#d07e84'],
                                                allowPointSelect: true,
                                                cursor: 'pointer',
                                                depth: 35,
                                                dataLabels: {
                                                    enabled: true,
                                                    format: '{point.name}'
                                                
                                                }
                                            }
                                        },
                                        series: [{
                                            type: 'pie',
                                            name: "Share of Taylor's Top 20 Songs",
                                            data: [
                                                ['Billboard #1', 5],
                                                ['Billboard #2', 6],
                                                ['Billboard #5 and beyond', 9]
                                            ]
                                        }]
                                    });
                                    </script>
                                    <p style="font-family:roboto;" class="highcharts-description">
                                                Taylor's top Pop hits are less distributed than her top Country hits, with it being divided between Billboard #1s and #2s and then #5s onward. The smaller 
                                                distribution indicates that she had a higher quantity of bigger hits with her Country songs.   
                                            </p>

                            </div>
                          </div>
      </div>

    </div>
  </div>
</div>

</body>
</html>
