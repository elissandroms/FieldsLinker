# FieldsLinker
Allow to make a 1 to 1 link between elements of 2 lists

Given 2 lists : for instance one from a text import, the second listing the fields a db table
the jquery plugin allos you to draw and save links between the 2 lists

My first jquery plug-in

v0.01 : first commit
TODO : set it responsive, a lot of paraméters that should not be necessary :
cellHeight,List1Width,canvasWidth,List2Width and should be calculated
tested only on Chrome ...



var fieldLinks;
		$( document ).ready(function() {
			var existingLinks = [{"from":"firstName","to":"first_name"}] ;
			var input = {
			    "options":{
					"byName" : true,
					"className":"fieldsLinker",
					"cellHeight":39,
					"List1Width":200,
					"canvasWidth" : 200,
					"List2Width":200
				},
				"listA":
					{
						"name":"columns in files",
						"list" : [
							"firstName",
							"lastName",
							"phone",
							"email",
							"role"						
						]
					},
				"listB":
					{
						"name":"Fields available",
						"list" : [
							"Id",
							"Company",
							"jobTitle",
							"adress",
							"first_name",
							"last_name",
							"email_adress"
						]
					},
				"existingLinks": existingLinks
				// ex [{"from":"firstName","to":"first_name"},{"from":2,"to":1}] 
			};
			
		  	fieldLinks=$("#bonds").fieldsLinker("init",input);
			
			$("#input").html("input => " + JSON.stringify(existingLinks));
			$(".fieldLinkerSave").on("click",function(){
				var results = fieldLinks.fieldsLinker("getLinks");
				$("#output").html("output => " + JSON.stringify(results));
			});
			
		});
 