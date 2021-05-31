function vd_noErrorMessages () { return true; }
window.onerror = vd_noErrorMessages;
if(typeof dictionaries == "undefined") 
{
    var dictionaries = "eng2vie_vie2eng_foldoc";
}
document.write("<div id='addVdictOnYourWeb'  style='position: absolute;left: -300px;width: 300px;border: 1px solid black;padding: 2px;background-color: lightyellow;visibility: hidden;z-index: 100;'>VDict quick lookup</div>");
var vdict_offsetfromcursorX=12 //Customize x offset of tooltip
var vdict_offsetfromcursorY=10 //Customize y offset of tooltip
var vdict_ie=document.all
var vdict_ns6=document.getElementById && !document.all
var vdict_enabletip=false
if (vdict_ie||vdict_ns6)
var vdict_tipobj=document.all? document.all["addVdictOnYourWeb"] : document.getElementById? document.getElementById("addVdictOnYourWeb") : ""

function vdict_ietruebody(){
    return (document.compatMode && document.compatMode!="BackCompat")? document.documentElement : document.body;
}
//////////////////////////////////////////
//////////////////move mouse///////////////////////////////////////////////
///////////////////////////////////////////////////////////////////////////
function vdict_positiontip(e){
    if (vdict_enabletip){
        var nondefaultpos=false
        var curX=(vdict_ns6)?e.pageX : event.clientX+vdict_ietruebody().scrollLeft;
        var curY=(vdict_ns6)?e.pageY : event.clientY+vdict_ietruebody().scrollTop;
        //Find out how close the mouse is to the corner of the window
        var winwidth=vdict_ie&&!window.opera? vdict_ietruebody().clientWidth : window.innerWidth-20
        var winheight=vdict_ie&&!window.opera? vdict_ietruebody().clientHeight : window.innerHeight-20
        
        var rightedge=vdict_ie&&!window.opera? winwidth-event.clientX-vdict_offsetfromcursorX : winwidth-e.clientX-vdict_offsetfromcursorX
        var bottomedge=vdict_ie&&!window.opera? winheight-event.clientY-vdict_offsetfromcursorY : winheight-e.clientY-vdict_offsetfromcursorY
        
        var leftedge=(vdict_offsetfromcursorX<0)? vdict_offsetfromcursorX*(-1) : -1000
        
        //if the horizontal distance isn't enough to accomodate the width of the context menu
        if (rightedge<vdict_tipobj.offsetWidth){
            //move the horizontal position of the menu to the left by it's width
            vdict_tipobj.style.left=curX-vdict_tipobj.offsetWidth+"px"
            nondefaultpos=true
        }
        else if (curX<leftedge)
                vdict_tipobj.style.left="5px"
            else{
                //position the horizontal position of the menu where the mouse is positioned
                vdict_tipobj.style.left=curX+vdict_offsetfromcursorX+"px"
            }
        
        //same concept with the vertical position
        if (bottomedge<vdict_tipobj.offsetHeight){
            vdict_tipobj.style.top=curY-vdict_tipobj.offsetHeight-vdict_offsetfromcursorY+"px"
            nondefaultpos=true
        }
        else{
            vdict_tipobj.style.top=curY+vdict_offsetfromcursorY+"px"
        }
        vdict_tipobj.style.visibility="visible"
    }
}
///////////////////////////////
//////////////////////////////
/////////////////////////////////////////
var base_url = "http://vdict.com/";
var text = "";
function calldict(word, dict ){
    http://window.open(base_url+'gateway.php?word='+word+'&dictionaries='+dict,'Vdict','toolbar=no,status=no,scrollbars=yes,location=no,menubar=no,directories=no,titlebar=no,width=620,height=400')
    vdict_url    =    base_url+'fsearch.php?word='+word+'&dictionaries='+dict;
    //create iframe
    str    =    "<div style='float: left; border-bottom: 1px solid #000000; background: #ffffff;'>";
    str    +=    " <div style='float:left;'><a href='"+base_url+"' target='_blank'><img src='"+base_url+"small_logo.gif' border=0 /></a> <span name='vdict_dictionary_name' id='vdict_dictionary_name'></span> </div>";
    str    +=    " <div style='float:right;'><a href='#' onclick="doCloseVdict();return false;"><img src='"+base_url+"close.gif' border=0 /></a></div>";
    str    +=    "</div>";
    str    +=    "<div>";
    str    +=    "<iframe id='myIframe' src='"+vdict_url+"' style='width: 100%; height: 200px; border: 0px;'></iframe>";
    str    +=    "</div>";
    document.getElementById('addVdictOnYourWeb').innerHTML = str;
}
function doCloseVdict()
{
    document.getElementById('addVdictOnYourWeb').innerHTML='';
    document.getElementById('addVdictOnYourWeb').style.visibility="hidden";
}

function ctrlrightclick(evt) {
    evt = (evt) ? evt : ((window.event) ? window.event : "")
    if (!evt.ctrlKey) return true
//    var x=document.body.createTextRange();
//    var x=(document.all) ? document.body.createTextRange() : document.setSelectionRange();
//    x.moveToPoint(evt.x, evt.y);
//    x.expand("word");
//    if (x.text)
//    {
//        calldict(x.text, dictionaries);
//    }
    //text    =    
    return false
}

function detectKey(evt) 
{
    evt = (evt) ? evt : ((window.event) ? window.event : "")
    if(evt.type == 'keydown' && ( (evt.keyCode == "A".charCodeAt(0)) || (evt.keyCode == "a".charCodeAt(0)) ) )
    {
        if ( (evt.ctrlKey) && (evt.shiftKey) )
        {
            text = (document.all) ? document.selection.createRange().text : document.getSelection();
            if (text.length > 1)
            {
                vdict_enabletip=true;
                vdict_positiontip(evt);
                calldict(text, dictionaries);
            }
        }
    }
    return true
}
function doDblClick(evt) 
{
    evt = (evt) ? evt : ((window.event) ? window.event : "")
    text = (document.all) ? document.selection.createRange().text : document.getSelection();
    if (text.length > 1)
    {
        vdict_enabletip=true;
        vdict_positiontip(evt);
        calldict(text, dictionaries);
    }
    return true
}


///////////////////////////////
///////////////////////////////
///////////////////////////////
function getWordFromEvent (evt) {
  if (document.body && document.body.createTextRange) {
    var range = document.body.createTextRange();
    range.moveToPoint(evt.clientX, evt.clientY);
    range.expand('word');
    return range.text;
  }
  else if (evt.rangeParent && document.createRange) {
    var range = document.createRange();
    range.setStart(evt.rangeParent, evt.rangeOffset);
    range.setEnd(evt.rangeParent, evt.rangeOffset);
    expandRangeToWord(range);
    var word = range.toString();
    range.detach();
    return word;    
  }
  else {
    return null;
  }
}

function expandRangeToWord (range) {
  var startOfWord    =    /^\s\S+$/;
  var endOfWord    =    /^\S+\s$/;
  var whitespace    =    /^\s+$/;
  // if offset is inside whitespace
  range.setStart(range.startContainer, range.startOffset - 1);
  while (whitespace.test(range.toString())) {
    range.setEnd(range.endContainer, range.endOffset + 1);
    range.setStart(range.startContainer, range.startOffset + 1);
  }
  while (!startOfWord.test(range.toString())) {
    range.setStart(range.startContainer, range.startOffset - 1);
  }
  range.setStart(range.startContainer, range.startOffset + 1);
  while (!endOfWord.test(range.toString())) {
    range.setEnd(range.endContainer, range.endOffset + 1);
  }
  range.setEnd(range.endContainer, range.endOffset - 1);
  return range.toString();
}

function testSelectText(evt)
{
    evt = (evt) ? evt : ((window.event) ? window.event : "")
    text =    getWordFromEvent(evt);
    alert(text);
    vdict_enabletip=true;
    vdict_positiontip(evt);
    calldict(text, dictionaries);
}

document.ondblclick =    doDblClick; //ctrlrightclick;
document.onkeydown    =    detectKey;
//document.onmousemove    =    vdict_positiontip;
