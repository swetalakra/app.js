app.js
======
<!doctype html>
 
<html lang="en">
  <head>
    <meta charset="utf-8">
 
    <title>NoWork &amp; Job</title>
 
    <style type="text/css">
      body{ font:12px arial, sans-serif; line-height:1.6em; margin:0 auto; max-width:960px; }
      form{ text-align:right; }
      h1, h2, hr, p, table{ margin-bottom:20px; }
      table{ width:100%; }
      th, td{ padding:5px; text-align:left; vertical-align:top; }
      th{ background:#F0FFFF; }
      .even{ background-color:#F0FFFF; }
	  .tHi:hover
	  {
	     cursor:pointer;
		 background-color: #90EE90 !important;	 
	   
	  }
	  background-color:#9f9 !important;
    </style>
 
    
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.0.1/angular.min.js"></script>
	<link rel="stylesheet" type="text/css" href="http://twitter.github.com/bootstrap/assets/css/bootstrap.css">
	<script>
    
    function CountryListCtrl($scope){
    $scope.countrylist=[
    
    {country:'Australia'},
    {country:'Bangladesh'},
    {country:'England'},
    {country:'India'},
    {country:'Italy'},
    {country:'Spain'},
    {country:'USA'},
      ];
     
      $scope.country = [
        { id: 1, "name":"Manchester United", "type":"Soccer", "featured":"true", "country":"England"},
        { id: 2, "name":"Manchester City", "type":"Soccer", "featured":"false", "country":"England"},
		    { id: 3, "name":"Dallas Mavericks", "type":"Basketball", "featured":"true", "country":"USA"},
        { id: 4, "name":"Indian Cricket Team", "type":"Cricket", "featured":"true", "country":"India"},
        { id: 5, "name":"Australian Cricket Team", "type":"Cricket", "featured": "false", "country":"Australia"},
        { id: 6, "name":"Los Angeles Lakers", "type": "Basketball", "featured": "true", "country": "USA"},
        { id: 7, "name":"Los Angeles Clippers", "type": "Basketball", "featured": "false", "country": "USA"},
        { id: 8, "name":"Real Madrid", "type": "Soccer", "featured": "true", "country": "Spain"},
        { id: 9, "name":"Dallas Cowboys", "type": "American Football", "featured": "true", "country": "USA"},
        { id: 10, "name":"New York Giants", "type": "American Football", "featured": "false", "country": "USA"},
        { id: 11, "name":"Derbyshire Cricket Team", "type": "Cricket", "featured": "false", "country": "England"},
        { id: 12, "name":"Bangladesh Cricket Team", "type": "Cricket", "featured": "false", "country": "Bangladesh"},
        { id: 13, "name":"New York Knicks", "type": "Basketball", "featured": "false", "country": "USA"},
        { id: 14, "name":"Ferrari", "type": "Formula 1", "featured": "true", "country": "Italy"},
        { id: 15, "name":"Force One", "type": "Formula 1", "featured": "true", "country": "India"},
        { id: 16, "name":"New York Jets", "type": "American Football", "featured": "false", "country": "USA"}
		
		];
     };		
			
	   
	</script>
	
  </head>
  
 
  
  <body ng-app ng-controller="CountryListCtrl">
    <h1>NoWork &amp; Job</h1>
  	  
    
    <form>
      
      Search: <input ng-model="query">
      Check box: <input type="checkbox" ng-model="search">
 
      
      <select ng-model="sortorder">
        <option value="">-- sort order --</option>
        <option value="name">Name</option>
        <option value="type">Type</option>
	    	<option value="country">Country</option>
      </select>
    </form>
    
    
    <p>There are <strong>{{(country|filter:query|filter:search).length}}</strong> country<span ng-show="query.length"> matching &quot;{{query}}&quot;</span>.</p>
    
     
    
    <table class="countries" ng-show="(country|filter:query).length">
      <tr>
        <th>Name</th>
        <th>type</th>
		    <th>country</th>
		    <th>featured</th>
      </tr>
 
      
      <tr ng-repeat="country in country|filter:query|filter:search|orderBy:sortorder">
        
        <td ng-class-even="'even'">{{country.name}}</td>
        <td ng-class-even="'even'">{{country.type}}</td>
		    <td ng-class-even="'even'">{{country.country}}</td>
		    <td ng-class-even="'even'">{{country.featured}}</td>
      </tr>
  
    </table>
             <div id="dropdown">
             Country Sports :<select ng-model="search"
             ng-options="c.country for c in countrylist"
              </select>
             </div>
            
         <div class="gridStyle" ng-grid="search"></div>
		
        <button class="btn btn-danger" ng-click="search">page1</button>
        <button class="btn" ng-click="addItem()" >page2</button>
        <button class="btn" ng-click="allItems()" >page3</button>
        <button class="btn btn-danger" ng-click="remove()">page4
            </button>
    
	
	
  </body>
</html>
