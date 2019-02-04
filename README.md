<%@page import="java.sql.ResultSet"%>
<%@page import="java.sql.PreparedStatement"%>
<%@page import="Util.ConnectionUtil"%>
<%@page import="java.sql.Connection"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>

<html>
<meta name="viewport" content="width=device-width, initial-scale=1">

	<head>
<style>
.tb1 tr{
	
text-align:center;	
	
}


* {
	box-sizing: border-box;
	margin:0;
}
body{
	background-color: #f2f2f2;
 	font-family: Arial;
}
.tab{
    overflow: hidden;
    border: 1px solid #ccc;
    background-color: #f1f1f1;
}
.tab a{
    background-color: inherit;
    float: left;
    border: none;
	outline: none;
	cursor: pointer;
	padding: 11px 11px;
	transition: 0.3s;
	font-size: 17px;
}
.tab a:hover {
    background-color: #ddd;
}
.tab a.active {
    background-color: #ccc;
}
.tabcontent {
    display: none;
    padding: 6px 12px;
    border: 1px solid #ccc;
    border-top: none;
	
}
#Address {
		width:100%;
 		height:31vh;
 
}
#Document{
		width:100%;
 		height:31vh;

}
#Account{
		width:100%;
 		height:31vh;
 }
#Other{
		width:100%;
 		height:31vh;
 }
#UnicodeAddress{
		width:100%;
 		height:31vh;
  }
#Contact{
		width:100%;
 		height:31vh;
 }
.button {
    background-color: #f486d5;
    border: none;
    color: white;
    padding: 7.5px 22px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 12px;
    margin: 4px 2px;
    cursor: pointer;
}
#fdiv{
    float: left;
    width: 51%;
}


h2{
	text-align:center;
	background-color: #e6e6ff;
}

select{

	width:100%;
}


input,select
{	
	cursor:pointer;
	border:1px solid black;
	padding:3.8px;
}


 select:hover:not([disabled]),input:hover:not([disabled]) {background-color: powderblue;}
.tabcontent tr:hover {background-color: powderblue;}

.error {
    color: red;
    float: left !important;
	}
.col-25 {	
	width: 25%;
	float:left;
	padding-top:2px;
}
#col-20{
width: 20%;
	float:left;
	padding-top:2px;
}
.col-50 {	
	width: 50%;
	float:left;
	padding-top:2px;
}
.col-75 {	
	width:75%;
	float:left;
	padding-top:2px;
}
.col-100 {
	width:100%;
	float:left;
	padding-top:2px;
}
.row {
	width:100%;
}
.col-19 {	
	width:22%;
	float:left;
	padding-top:2x;

}
.col-81 {	
	width:78%;
	float:left;
	padding-top:2px;
}
.col-38 {	
	width:40%;
	float:left;
	padding-top:2px;
	white-space:nowrap;

}
.col-60 {	
	width:60%;
	float:left;
	padding-top:2px;
	white-space:nowrap;
}
input[type="text"],input[type="date"],textarea {
	width:100%;
	  height: 20px;
	border:1px solid #ccc;
	resize:vertical;
	
}
select{
	width:100%;
	  height: 25px;
	border:1px solid #ccc;
	resize:vertical;
	

}
label {	

	display:inline-block;	
}
.container {
	width:100%;	
    border-radius: 5px;
    background-color: #f2f2f2;
}
.container:after {
	content:"";
	display:table;
	clear:both;	
}

input[type="submit"],input[type="reset"] {
	background-color: #3399ff;
	border: none;
	color: white;
	padding: 7.5px 22px;
	text-align: center;
	text-decoration: none;
	display: inline-block;
	font-size: 14px;
	margin: 4px 2px;
	cursor: pointer;
}

input[type="submit"]:hover,input[type="reset"]:hover {
		background-color: red;
}

.section {
	width:60%;
	float:left;
}
.section2{
	width:40%;
	float:right;
	overflow-x:auto;
   
}

.lbl{
	padding: 4% 0 0 18%;
}

.col-25 a {
	width:100%;
    background-color: #f2f2f2;
    float: left;
    border: none;
    outline: none;
    cursor: pointer;
    padding: 14px 16px;
    transition: 0.3s;
    font-size: 17px;
	text-align:center;
	overflow:hidden;

}

.col-25 a:hover {
    background-color: #ddd;
}

.col-25 a.active {
    background-color: #ccc;
}

.col-100 .inpbtn {
	width:50%;
	text-align:center;
}

.col-50 table {
	
	text-align:center;
	
}

@media screen and (max-width:600px) {
	.container,.col-25,.col-75,.col-19,.col-81,.col-38 ,.col-62 ,.section,.section2,li,.menu,.col-50 {
		width:100%;
		margin-top:0;
		text-align:left;
	}	
	input[type="submit"] {
		text-align:center;
		
	}
	.col-25 label {
			white-space:nowrap;		
	}
	.btn {
		visibility:visible;
	}		
	.lbl {padding:0;}
	.lst {
		margin-bottom:10px;
	}

	.col-25 a {
		white-space:nowrap;
   		padding: 4px 4px;
	}


	.tab a{
		font-size:12px;
	}	
	
#Address input, #Account input, #Other input, #UnicodeAddress input,#Contact input{
		width:100%;
}
	
 #Address,#Account {
		height:80vh;
} 
#Other {
	height:40vh;
}
#UnicodeAddress {
		height:50vh;
	
}
#Contact {height:70vh;}#Document {height:30vh;}
.scrollTable {
	overflow: scroll;
	width: 100%;
}
}

.hh3{
	    padding-right: 25%;
}
</style>
<style>
*{
	margin:0;
}
.hoverTable{
                width:100%; 
                border-collapse:collapse; 
        }
        .hoverTable td{ 
                padding:7px; 
                border:#4e95f4 1px solid;
        }
        /* Define the default color for all the table rows */
        .hoverTable tr{
                background: ;
        }
        /* Define the hover highlight color for the table row */
    .hoverTable tr:hover {
          background-color:lightgray;
    }
        
        input[type=number]::-webkit-inner-spin-button, 
input[type=number]::-webkit-outer-spin-button { 
  -webkit-appearance: none; 
  margin: 0; 
}
.button {
    background-color: #3399ff;
    border: none;
    color: white;
    padding: 7.5px 22px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 14px;
    margin: 4px 2px;
    cursor: pointer;
}
.button:hover{
    background-color:red;
}
.ab1{
        margin-left:5%;
}
.ab2{
        margin-left:13%;
}
input[name=abhi] {
    width: 273px;
	margin-left:14%;
}
input[name=sss]{
   width:80px;
}
input[name=ddd]{
   width:95%;
}
@media only screen and (max-width: 1280px),
(min-device-width: 450px) and (max-device-width: 1024px)  {

        .hoverTable{
                width:100%; 
                border-collapse:collapse; 
        }
        .hoverTable td{ 
                padding:7px; 
                border:#4e95f4 1px solid;
        }
        /* Define the default color for all the table rows */
        .hoverTable tr{
                background: ;
        }
        /* Define the hover highlight color for the table row */
    .hoverTable tr:hover {
          background-color:lightgray;
    }
        table { 
  width: 100%; 
  border-collapse: collapse; 
}
/* Zebra striping */
tr:nth-of-type(odd) { 
 
}
th {  
  font-weight: bold;   
}
.ab1{
        margin-left:-16%;
}
.ab2{
        margin-left:-27%;
}
#ab3{
        width:47px;

}
input[name=abhi] {
      width:80px;
	  margin-left:14%;
}
input[name=sss]{
   width:25px;
}
h4{
   margin-top:13%;
}
#jv2{
   width:46%;
}
#jv3{
   width:49%;
}
input[name=ddd]{
   margin-left:14%;
   width:77%;
}
.qqq{
  width: 80%;
  margin-left:-11px; 
}
input[name=www]{
   width: 80px;
}
input[name=wwe]{
   width: 100%;
}
.btnn{
  margin-top=-42%;
  margin-right=-74%;
}
</style>
<style>

div.awe {
  max-height: 178px;
  overflow-y: auto;
height: 200px;
}
div.awe1 {
  max-height: 145px;
  overflow-y: auto;
height: 200px;
}
.section3{
	
	width:22%;
	float:left;
	padding:5px;
	text-align:center;
		
	
}
section.awe{
  position: relative;
  border:;
  padding-top: 25px;
  background: #0099ff ;
  width: 106%;
}
section.positioned.awe {
  position: absolute;
 }


.awe th {
  height: 0;
  line-height: 0;
  padding-top: 0;
  padding-bottom: 0;
  color: transparent;
  border: none;
  white-space: nowrap;

	


}
.awe th div{
  position: absolute;
  background: transparent;
  color: white;
 padding: 9px 25px;
  top: 0;
  margin-left: -25px;
  line-height: normal;
  color:white;
  HEIGHT: 8vh;
 
}
table.awe {
  width: 100%
}
thead.awe tr,
tfoot.awe tr {
  position: absolute;
  left: 0;
  right: ;
  /* to not cover the scrollbar*/
}
thead.awe th,
tfoot.awe td {
  display: inline-block;
}
thead.awe tr {
  top: 0
}
tfoot.awe tr {
  top: 500px/* same value has max-height from div */
}
.awe th,
.awe td {
  
  font-size: 12px;
  text-align: center;
 background: #ddd;
  color: #000;
}
/*give some space between thead and tfoot*/

tbody.awe tr:first-of-type td {
  padding-top: 35px;
}
tbody.awe tr:last-of-type td {
  padding-bottom: 35px;
}

</style>
<style>
#modal {
  left: 50%;
  margin: -250px 0 0 -40%;
  opacity: 0;
  position: absolute;
  top: -50%;
  visibility: hidden;
  width: 80%;
  box-shadow: 0 3px 7px rgba(0,0,0,.25);
  box-sizing: border-box;
  transition: all .4s ease-in-out;
  -moz-transition: all .4s ease-in-out;
  -webkit-transition: all .4s ease-in-out
}

#modal:target {
  opacity: 1;
  top: 50%;
  visibility: visible
}
#modal .header, #modal .footer {
  border-bottom: 1px solid white;
  border-radius: 5px 5px 0 0
}

#modal .footer {
  border: none;
  border-top: 1px solid #e7e7e7;
  border-radius: 0 0 5px 5px
}

#modal h2 {
  margin: 0;
  color: #fff
}

#modal .btn { float: right }

#modal .copy, #modal .header, #modal .footer {
  padding: 10px;
  color: #fff
}

.modal-content {
  background: white;
  position: relative;
  z-index: 20;
  border-radius: 5px;
  color: black;
}

#modal .copy { background:white;}

#modal .overlay {
  background-color: #000;
  background: rgba(0,0,0,.8);
  height: 100%;
  left: 0;
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 10
}

.copy a {
  color: #fff;
  text-decoration: none;
  display: inline-block;
  padding: 5px 10px;
  border-radius: 5px;
  background-color: #E74C3C;
}

.close {
        background: #606061;
        color: #FFFFFF;
        line-height: 25px;
        position: absolute;
        right: -12px;
        text-align: center;
        top: -10px;
        width: 24px;
        text-decoration: none;
        font-weight: bold;
        -webkit-border-radius: 12px;
        -moz-border-radius: 12px;
        border-radius: 12px;
        -moz-box-shadow: 1px 1px 3px #000;
        -webkit-box-shadow: 1px 1px 3px #000;
        box-shadow: 1px 1px 3px #000;
}

.close:hover { background: #00d9ff; }
</style>

<style>
.tb1{
	
	float:left;
	width:50%;
	text-align:right;
	white-space:nowrap;

}
.tb1 td ,tr{
	
		padding-right:2%;
}
.tb2{
	border:1px solid black;
	border-collapse:collapse;
	float:right;
	width:36%;
}
.tb2 td ,tr{
	border:1px solid black;
	border-collapse:collapse;
}
.tb{
	border:1px solid black;
	border-collapse:collapse;
	width:100%;
	
}
.tb td ,tr ,th{
	border:1px solid black;
	border-collapse:collapse;
}
input {
	width:100%;
}

select {
width:100%;
}
h1{
	background-color:powderblue;
	border:1px solid black;
	}
.tb5{
	float:right;
	width:40%;
}
.mm{
	white-space:nowrap;
}
th{
	font-size:12.5px;
}
.mj{
	 
      overflow-x:scroll;

	  width:80%;
	  float:left;
	  
}
.fc{
	width:24%;
	float:left;
	text-align:right;


}
.oi{
border:1px solid black;
	border-collapse:collapse;

}
.oi tr , .oi td ,oi th{
	border:1px solid black;
	border-collapse:collapse;
	}

.col-33 {	
	width: 33%;
	float:left;'
	padding-top:2px;
}
.col-34{
	padding-right: 5%;
}
.col-30 {	
	width: 30%;
	float:left;'
	padding-top:2px;
}
.col-70 {	
	width: 70%;
	float:left;
		padding-top:2px;
}
.col-20 {	
	width: 20%;
	float:left;
			padding-top:2px;

}
.col-80 {	
	width: 80%;
	float:left;
			padding-top:2px;

}
.col-100 {	
	width: 100%;
	float:left;
			padding-top:2px;

}
.col-10 {	
	width: 10%;
	float:left;
	padding-top:2px;

}
.col-40 {	
	width: 40%;
	float:left;
	padding-top:2px;

}
.col-15 {	
	width: 15%;
	float:left;
		padding-top:2px;
}
.col-50 .col-25 {	
	text-align:right;
	padding-right:2%;
}
.col-100 .col-25 {	
	text-align:right;
	padding-right:2%;
}
.col-18 {	
	width: 18%;
	float:left;
		padding-top:2px;
}

.m1{
	border:1px solid black;
}


		</style>
<style>
div.aa6 {
  max-height: 145px;
  overflow-y: auto;
height: 200px;
}

section {
  position: relative;
  border:;
  padding-top: 37px;
  background: #500;
}
section.positioned {
  position: absolute;
 }


.aa6 th {
  height: 0;
  line-height: 0;
  padding-top: 0;
  padding-bottom: 0;
  color: transparent;
  border: none;
  white-space: nowrap;
}
.aa6 th div{
  position: absolute;
  background: transparent;
  color: white;
 padding: 9px 25px;
  top: 0;
  margin-left: -25px;
  line-height: normal;
  color:white;
  
}

table.aa6 {
  width: 100%
}

thead.aa6 tr,
tfoot.aa6 tr {
  position: absolute;
  left: 0;
  right: 15px;
  /* to not cover the scrollbar*/
 
}

thead.aa6 th,
tfoot.aa6 td {
  display: inline-block;
}

thead.aa6 tr {
  top: 0
}

tfoot.aa6 tr {
  top: 500px/* same value has max-height from div */
}

.aa6 th,
.aa6 td {
  width: calc((100%/3) - 5px);
  font-size: 12px;
  text-align: center;
 background: #ddd;
  color: #000;
}


/*give some space between thead and tfoot*/

tbody.aa6 tr:first-of-type td {
  padding-top: 35px;
}

tbody.aa6 tr:last-of-type td {
  padding-bottom: 35px;
}
</style>
<style>

.hh{
	padding-right:52%;
}
.hh1{
	padding-right:10%;
}
.hh3{
	    padding-right: 25%;
}
.gg{
	padding-left:5%;
}
.gg1{
	padding-left:5%;
}
.gg2{
	padding-left:10%;
}
.stb{
		width:100%;
		border:1px solid black;
		border-collapse:collapse;
}
.stb td , .stb tr{
		
		border:1px solid black;
		border-collapse:collapse;
}
.col-35 {	
	width: 35%;
	float:left;
		padding-top:2px;
}
.pd{
	padding-top:2px;
}
.ali{
	 padding-left: 10%;
}

@media only screen and (max-width:600px){


.hh{
	padding-right:0%;
}
.hh1{
	padding-right:0%;
}
.gg{
	padding-left:0%;
}
.gg1{
	padding-left:0%;
}
.gg2{
	padding-left:0%;
}
.stb{
		width:100%;
		border:1px solid black;
		border-collapse:collapse;
}
.col-50 .col-25 {	
	text-align:left;
	padding-right:0%;
}
.col-100 .col-25 {	
	text-align:left;
	padding-right:0%;
}
.col-34{
	padding-right: 5%;
}
.col-35,.col-30,.col-70,.col-10,col-50,.col-20,.col-33,.col-40 {
		width:100%;
		margin-top:0;
		text-align:left;
	}	
}

</style>
	<script>
		function abc(a){
		
		  
	if(a=="Cash"){
	document.getElementById("txt").disabled = false;
	document.getElementById("txt").focus();
	}
		else{
		
		document.getElementById("txt").disabled = true;
		}
		
		}

</script>

      <script type = "text/javascript">
         window.addEventListener('load',carr)
         var db = openDatabase('as<%=comp%>', '1.0', 'TIPS', 2 * 1024 * 1024); 
         var msg;
     <% 
     String itm="";
     %>
        <%--   db.transaction(function (tx) { 
    	   tx.executeSql('CREATE TABLE IF NOT mst_item(id unique, itm_cd, itm_nm,)'); 
    	   <% 
			String db=(String)session.getAttribute("db");
			String host=(String)session.getAttribute("host");
    	   Connection con = ConnectionUtil.getConnection(db, host);
    	   PreparedStatement ps = con.prepareStatement("select Itm_Cd ,itm_nm from mst_item ");
    	   ResultSet rs = ps.executeQuery();    
    	   if(rs.next()){
    		   do{
    			   
    		 itm+="<option value ='"+rs.getString(2)+"'>"+rs.getString(2)+"</option> ";
    		   %>
    		   tx.executeSql('INSERT INTO mst_item (id,Itm_cd,itm_nm)values(<%=rs.getInt(1)%>,"<%=rs.getInt(1)%>","<%=rs.getString(2)%>")');
    		   <%
    		   
    		   }while(rs.next());ps.close();con.close();rs.close();
    		   
    	   }
    	   %>
    	   
    	   });
     
 --%>
     
 db.transaction(function (tx) { 
	 tx.executeSql('CREATE TABLE IF NOT EXISTS Itam (id INTEGER PRIMARY KEY, name, desc, sunit, perunit, gst, cess,Srate)'); 
	 <%
	 String db=(String)session.getAttribute("db");
		String host=(String)session.getAttribute("host");
	 Connection con=ConnectionUtil.getConnection(db, host);
	 PreparedStatement stmt =con.prepareStatement("SELECT Itm_Cd,itm_nm,Item_desc,mst_unit.Unit_NM,Itm_unit_p,mst_taxrate.Tax_Cess AS cess ,mst_taxrate.Tax_Per AS gst,Itm_Srate FROM mst_item,mst_taxrate,mst_unit WHERE  mst_item.Tax_Cd=mst_taxrate.Tax_cd AND mst_item.Itm_unit_S=mst_unit.Unit_Cd AND mst_item.C_Cd='"+comp+"'");
	 ResultSet rs=stmt.executeQuery();
	 if(rs.next()){
	 do{%>
	 tx.executeSql('INSERT INTO Itam (id, name ,desc, sunit, perunit, gst, cess,Srate) VALUES (<%=rs.getInt(1)%>, "<%=rs.getString(2)%>","<%=rs.getString(3)%>","<%=rs.getString(4)%>","<%=rs.getString(5)%>","<%=rs.getString(7)%>","<%=rs.getString(6)%>","<%=rs.getString(8)%>")'); 
	 <%
	 }while(rs.next());rs.close();stmt.close();con.close(); session.setAttribute("Itam1", "ok");}
		 
		 %>
	});

	   db.transaction(function (tx) { 
	   	 var s="sandep";
	       tx.executeSql("SELECT id,name FROM itam ", [], function (tx, rs) { 
	          var len = rs.rows.length, i; 
	          msg = "<p>Found rows: " + len + "</p>"; 
	       /*    document.querySelector('#status').innerHTML =  msg; */ 
	 
	          for (i = 0; i < len; i++) { 
	             msg += "<option value="+ rs.rows.item(i).id+">" + rs.rows.item(i).name + "</option>"; 
	            
	          } 
	          document.querySelector('#itmm').innerHTML =  msg; 
	       }, null); 
	    }); 

     
         db.transaction(function (tx) { 
            tx.executeSql('CREATE TABLE IF NOT EXISTS purchase (id INTEGER PRIMARY KEY, name, desc, punit, sunit, qty, fqty, toty, dis, gst, cess, fix, tamt   )'); 
         });
                 function carr(){
                      document.getElementById('a12').addEventListener('blur',acd);
                          asdde();
                 }

                 function acd(){ 
                  var id=document.getElementById('a0').value;   
                  var name=document.getElementById('a1').value;        
                  var desc=document.getElementById('a2').value;
                  var punit=document.getElementById('a3').value;
                  var sunit=document.getElementById('a4').value;
                  var qty=document.getElementById('a5').value;        
                  var fqty=document.getElementById('a6').value;
                  var toty=document.getElementById('a7').value;
                  var dis=document.getElementById('a8').value;
                  var gst=document.getElementById('a9').value;        
                  var cess=document.getElementById('a10').value;
                  var fix=document.getElementById('a11').value;
                  var tamt=document.getElementById('a12').value;
                  
                   db.transaction(function (tx) { 

             			if(id){
             				tx.executeSql('Update purchase set  name=?, desc=?, punit=?, sunit=?, qty=?, fqty=?, toty=?, dis=?, gst=?, cess=?, fix=?, tamt=? WHERE id=?' ,[name, desc, punit, sunit, qty, fqty, toty, dis, gst, cess, fix, tamt,id]);
             			}
             			else{
                    	tx.executeSql('INSERT INTO purchase( name, desc, punit, sunit, qty, fqty, toty, dis, gst, cess, fix, tamt ) VALUES (?,?,?,?,?,?,?,?,?,?,?,?)',[name, desc, punit, sunit, qty, fqty, toty, dis, gst, cess, fix, tamt]);
             			}
        
                          });
                    asdde();                         
          }                
                  function asdde(){
                       var c= document.getElementById('tbl');
                     db.transaction(function (tx) {
                           tx.executeSql('select * from purchase',[], function(tx,results){
                            var rows= results.rows;
                                var tr="";
                                 for(i=0;i<rows.length;i++){
                                   tr +='<tr onclick="sendinfo(this)">';
								  tr +='<td >'+rows[i].id+'</td>';
                                   tr +='<td>'+rows[i].name+'</td>';
                                   tr +='<td style="display:none">'+rows[i].desc+'</td>';
                                   tr +='<td style="display:none">'+rows[i].punit+'</td>';
                                   tr +='<td>'+rows[i].sunit+'</td>';
                                   tr +='<td>'+rows[i].qty+'</td>';
                             	  tr +='<td >'+rows[i].fqty+'</td>';
                             	   tr +='<td style="display:none">'+rows[i].toty+'</td>';
                                  tr +='<td>'+rows[i].dis+'</td>';
                                  tr +='<td>'+rows[i].gst+'</td>';
                                  tr +='<td style="display:none">'+rows[i].cess+'</td>';
                                  tr +='<td style="display:none">'+rows[i].fix+'</td>';
                                  tr +='<td>'+rows[i].tamt+'</td>';
                                  
                                   tr +='</tr>';
                                }
                                
                                c.innerHTML = tr;
                           
                        });
                        },null);
                      }
                    function sendinfo(a){
                      var x=a.rowIndex;
                      var s=document.getElementById('tbl');
                      var r1=s.rows[x].cells.length;
                         for(var i=0;i<r1;i++){
                              document.getElementById('a'+i).value=s.rows[x].cells[i].innerHTML;
                      }
               }   
                    function det(){ 
                        var id=document.getElementById('a0').value;   
                                               db.transaction(function (tx) { 

                 		
                 		tx.executeSql('Delete from purchase  WHERE id=?',[id] );
                 

                 			});
                                               asdde();
                    }                 
     /*                function jp() {
                    	var k = document.getElementById("a12");
                    	if(k.style.filter == blur){
                    	document.getElementById('a1').focus ; 
                    	}
                    	else{
                    		
                    	alert("notttty");
                    	}
                    } */
						
			      </script> 
</head>

<body>
	<center> <h1>Purchase Entry </h1> </center>
<form>

	<div class="col-100 " style="border:1px solid black;">
	
		<div class="col-50"> 
		
			<div class="col-25">Cash/Credit </div>
			<div class="col-25"><select> <option>Cash </option> <option> Credit </option></select> </div> 
			<div class="col-25">Account Head </div>
			<div class="col-25"><select> <option>Cash </option> <option> Credit </option></select> </div> 

			<div class="col-100">
				<div class="col-25">Bill No </div>

			<div class="col-25 hh"><input type="text"> </div> 
			<div class="col-25">Date </div>
			<div class="col-25"><input type="text"> </div>

			<div class="col-25">Bill Type</div>
			<div class="col-75 hh"><select> <option></option> <option></option></select> </div>  
			<!-- <div class="col-25">Bill Type </div>
			<div class="col-75 hh"><input type="text"> </div>   -->
			<div class="col-25">Party Name </div>
			<div class="col-75 "><input type="text"> </div> 
		</div>	
		</div>
		<div class="col-50"> 
			<div class="col-25">Extra 1: </div>
			<div class="col-25"><input type="text"> </div> 
			<div class="col-25">Extra 1: </div>
			<div class="col-25"><input type="text"> </div> 
				</div>
				<div class="col-50"> 
			<div class="col-25">Extra 2: </div>
			<div class="col-25"><input type="text"> </div> 
			<div class="col-25">Extra 2: </div>
			<div class="col-25"><input type="text"> </div> 
		</div>
	</div>
	<div class="col-100 " style="border:1px solid black;">
		<div class="col-75 hh3"> 
			<div class="col-25">Code </div>
			<div class="col-75 hh"><input type="text"> </div> 
			<div class="col-25"> Name </div>
			<div class="col-75"><input type="hidden" name="itemnm" id="a0" > 
			<select id="a1">
		<%=itm %>
			</select>
			 
			 
			 </div> </form>
		
			<div class="col-25"> Desecription </div>
			<div class="col-75"><input type="text" name="desc" id="a2"> </div> 
		</div>

		<div class="col-25 "> 
		<div class="col-100" > 
		<textarea id ="txt" rows="5" cols="10" style="height:68px">
		</textarea>
	</div>
		</div>
	</div>
	<div class="col-100" style="border:1px solid black;">
		<div class="col-25 " > 
			<div class="col-20">Pur.Unit</div>
			<div class="col-20 gg"><input type="text" name="punit" id="a3"> </div> 
			<div class="col-20">Sale.Unit</div>
			<div class="col-20 gg"><input type="text" ame="sunit" id="a4"> </div> 
			
			<div class="col-33 col-34"> Qunatity</div>
			<div class="col-33 col-34">Free Qty </div>
			<div class="col-33 col-34">Total Qty </div>
			<div class="col-33 gg"><input type="text" name="qty" id="a5"> </div> 
			<div class="col-33 gg"><input type="text" name="fqty" id="a6"> </div> 
			<div class="col-33 gg"><input type="text" name="toty" id="a7"> </div> 
			<div class="col-50"> Percentages(%)</div>
			<div class="col-50"> Amount </div>
			<div class="col-30"> Discount</div>
			<div class="col-20 gg2"><input type="text" name="dis" id="a8"> </div>
			<div class="col-50"><input type="text"></div>
			<div class="col-30"> GST:</div>
			<div class="col-20 gg2"><input type="text" name="gst" id="a9"> </div>
			<div class="col-50"><input type="text"></div>
			<div class="col-30"> Cess:</div>
			<div class="col-20 gg2"><input type="text" name="cess" id="a10"> </div>
			<div class="col-50"><input type="text"></div>
			<div class="col-30"> Fix Cess</div>
			<div class="col-20 gg2"><input type="text" name="fix" id="a11"> </div>
			<div class="col-50"><input type="text"></div>
			<div class="col-30"> Total Amt:</div>
			<div class="col-70 gg2"><input type="text" name="tamt" id="a12" ></div>
		<div class="col-50"> <input type="submit" value="Delete" onclick="det();"></div>
		</div>
		<div class="col-70   "> 
<section class="awe">
            <div class="awe1" style="height: 1vh">
            
         <table class="awe" style="width:100%" id="">
          
                  <tr>
        <th><div class="awe" style="text-align: right; padding-left: 6%">Sr.<div></th>
        <th><div class="awe ali"   style="text-align:center ;  padding-left:3% ;">Item Name</th>
        <th><div class="awe" style="text-align: right;padding-left: 4.5%;">Unit<div></th>
        <th><div class="awe" style="text-align: right;padding-left: 3%;">Qty<div></th>
		<th><div class="awe" style="text-align: right;padding-left: 1%;">Rate<div></th>
        <th><div class="awe" style="text-align: right;padding-left:1%;">Disc.AMt.<div></th>
		<th><div class="awe" style="text-align: right;padding-left: 0%;">Gst Amount<div></th>
        <th><div class="awe" style="text-align: right;"> Total Amt.<div></th>	
      </tr>
     
      </table> 
      </div>
         <div class="awe">
  <table class="awe" style="width:100%" id="tbl">
    <thead>
      <tr>
        <th><div class="awe" style="text-align: right; padding-left: 2%">Sr.<div></th>
        <th><div class="awe ali"   style="text-align: right;  padding-left: 15%;">Item Name</th>
        <th><div class="awe" style="text-align: right;padding-left: 6%;">Unit<div></th>
        <th><div class="awe" style="text-align: right;padding-left: 4%;">Qty<div></th>
		<th><div class="awe" style="text-align: right;padding-left: 5%;">Rate<div></th>
        <th><div class="awe" style="text-align: right;padding-left: 6%;">Disc.AMt.<div></th>
		<th><div class="awe" style="text-align: right;padding-left: 0%;">Gst Amount<div></th>
        <th><div class="awe" style="text-align: right;"> Total Amt.<div></th>	
      </tr>
    </thead>
    <tbody>

      <tr>
        <td id="aa0"> 1</td>
        <td id="aa1"style="width:35%">ABCAERIsndfhgltrqeotcvghtERTONASHRMVUTCF</td>
        <td  id="aa2"style="width:10%">1234</td>
		<td id="aa3">Codfg</td>
        <td id="aa4">9,99,000</td>
        <td id="aa5">90,000</td>
		  <td id="aa6">00</td>
		  <td id="aa7">00000</td>

		</tr>
		

  
    </tbody>
  </table>
		
</div>
&emsp;&emsp;
</div>
	</div>
	<div class="col-100" style="border:1px solid black;">
			
			<div class="col-30"> 
			<div class="col-25">Remark  </div>
			<div class="col-75"> <textarea col="4" rows="3" >  </textarea></div>
			<div class="col-25"> <input type="checkbox"></div>
			<!--  <div class="col-75">Traspoter Detais </div>
			<div class="col-25"> <input type="checkbox"></div>  -->
			<div class="col-75">Payment</div>
			
			<div class="col-25"> <input type="checkbox"></div>
			<div class="col-10"> Print </div>
			<div class="col-20 "> <input type="text"></div>
			<div class="col-20 "> <input type="text"></div>
			<div class="col-20 "> <input type="text"></div>
			
			<div class="100"> 
			 <div class="col-20"><input type="reset" name="btn" value="New" style="text-align: center;"> </div> 
			 <div class="col-20"><input type="submit" name="btn" value="Save" style="text-align: center;"></div> 
			 <div class="col-20"><a href="#modal" id="srch"><input type="submit" name="btn" value="Search" style="text-align: center;"></a></div> 
			 <div class="col-20"><input type="submit" name="btn" value="Print" style="text-align: center;"></div> 
			 <div class="col-20"><input type="submit" name="btn" value="Home" style="text-align: center;"></div> 
			</div>
			</div>
	<div class="col-70  "> 
		<div class="col-35 gg2  "> 
			<div class="col-30 "><input type="checkbox"> </div>
			<div class="col-50 hh1">Credit GST</div>
			<div class="col-30">Discount   </div>
			<div class="col-20 "> <input type="text"></div>
			<div class="col-50 "><input type="text"> </div> 
			<div class="col-30">Freight</div>
			<div class="col-70 "><input type="text"> </div> 
			<div class="col-30">Packing  </div>
			<div class="col-70 "><input type="text"> </div> 
			<div class="col-30">Insurance  </div>
			<div class="col-70 "><input type="text"> </div> 
			<div class="col-30">Expense </div>
			<div class="col-70 "><input type="text"> </div> 
		</div>
		<div class="col-35 gg2 "> 
			<div class="col-50"> (%)</div>
			<div class="col-50"> Amount </div>
			<div class="col-30"> SGST :</div>
			<div class="col-20"><input type="text"> </div>
			<div class="col-50"><input type="text"></div>
			<div class="col-30"> CGST :</div>
			<div class="col-20"><input type="text"> </div>
			<div class="col-50"><input type="text"></div>
			<div class="col-30"> IGST:</div>
			<div class="col-20"><input type="text"> </div>
			<div class="col-50"><input type="text"></div>
			<div class="col-30"> CESS : </div>
			<div class="col-20"><input type="text"> </div>
			<div class="col-50"><input type="text"></div>
			<div class="col-30"> Fix CESS : </div>
			<div class="col-20"><input type="text"> </div>
			<div class="col-50"><input type="text"></div>
		</div>
			<div class="col-30 gg2"> 
			<div class="col-50"> Round (+/-) :</div>
			<div class="col-50"><input type="text"></div>
			<div class="col-50"> Total Amount:</div>
			<div class="col-50"><input type="text"></div>

				</div>
		</div>
		
	

	
</div>
	<div id="modal">
  <div class="modal-content">
  <a href="#close" title="Close" class="close">X</a>
    <div class="header">
      <h2 style="text-align:center;color:black;">Journal Voucher</h2>
    </div>
    <div class="copy">
       <div>
         <a href="#close" title="Close" class="close">X</a>
		 <div>
				<table  class="qqq" >
				<tr>
				<td><input type="checkbox"></td>
			    <td>Party</td>
				<td><input type="Text" name="www"></td>
				<td>From</td>
				<td><input type="date"><input type="checkbox">Report<select><option>Dos</option></select></td>
				</tr>
				<tr>
				<td><input type="checkbox"></td>
			    <td>Amount</td>
				<td><input type="Text" name="wwe"></td>
				<td>To</td>
				<td><input type="date"><input type="submit" value="Show"><input type="submit" value="Exit" class="btnn"></td></tr>
				</table>
				</div>
<br>
<section>
               <div class="aa6">
  <table class="aa6">
    <thead>
      <tr>
        <th><div class="aa6" style="text-align: right;margin-left: 3%;">Sr</div></th>
        <th><div class="aa6" style="text-align: right;margin-left: 2%;">Jv.No</th>
        <th><div class="aa6" style="text-align: right;margin-left: 2%;">Date</div></th>
		<th><div class="aa6" style="text-align: right;margin-left: 8%;">Party Name</div></th>
        <th><div class="aa6" style="text-align: right;margin-left: -1%;">Credit</div></th>
        <th><div class="aa6" style="text-align: right;margin-left: -2%;">Debit</div></th>
      </tr>
    </thead>
    <tbody>
    <%for(int i=0;i<20 ;i++){ %>
      <tr>
        <td>Column one</td>
        <td>Column one</td>
        <td>Column three</td>
		<td>Column two *leads the width* (case 2)</td>
        <td>Cfusyd</td>
        <td>Column three</td>
      </tr>
<%} %>
    </tbody>
  </table>
</div>
</section>

	</body>
	</html>
