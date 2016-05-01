[Opentip](http://www.opentip.org) is one of many js libraries providing tool tips.

* Download and add opentip-jquery.js and opentip.css to the asset folder.

* Three ways to use tooltip
 * add it in html tage: data-ot = "tooltip content", data-ot-option=value
 * attach it to a DOM element. $("#input").opentip("tip content", {option1: value1, option2: value2}).show()
 * Instantiate an Opentip object. var mytip = new Opentip("tip content", {options});

* Remember to trigger the show/hide event according to intent. In front.js, submitDeal() has the following block. 
The tip is hidden once focus is back on the submit box.
```
if (trim($("#submitDeal").val())=="") {var submitTip = new Opentip($('#submitDeal'), "please submit deals", {delay: 2, showOn: null});
   submitTip.show();
   $('#submitDeal').focus(function(){submitTip.hide()});
	return 0;
}
```
