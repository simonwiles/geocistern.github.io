---
layout: page
title: Database
permalink: /database/
order: 2
---

<head>
    <style type="text/css">
        h3 span {
            font-size: 36px;
        }
        .button-default{
          height: 30px;
          width: 30px;
          float: center;
          border: white;
          border-radius: 8px;
          margin: 3px;
          margin-bottom: 30px;
        }
        .search-box{
          width: 70%;
          float: left;
          padding: 10px;
          margin-bottom: 20px;
        }

        .filter-box{
          width: 25%;
          float: right;
          padding: 10px;
          margin-bottom: 20px;
          background-color: WhiteSmoke;
        }

    </style>
</head>
<body class="mt32">
    <div>
      <h3>
      <input type="text" id="seInput" class="search-box" onkeyup="myFunction(category.value)" placeholder="Search">
      </h3>

      <select name="category" id="category" class="filter-box">
        <option value="1">Author</option>
        <option value="3">Title</option>
      </select>
    </div>

    <div>
      <button type="button" class = "button-default"
      onclick="input('â')">â</button>
      <button type="button" class = "button-default"
      onclick="input('ç')">ç</button>
      <button type="button" class = "button-default"
      onclick="input('ğ')">ğ</button>
      <button type="button" class = "button-default"
      onclick="input('ı')">ı</button>  
      <button type="button" class = "button-default"
      onclick="input('İ')">İ</button>
      <button type="button" class = "button-default"
      onclick="input('î')">î</button>
      <button type="button" class = "button-default"
      onclick="input('ö')">ö</button>
      <button type="button" class = "button-default"
      onclick="input('ş')">ş</button>
      <button type="button" class = "button-default"
      onclick="input('ü')">ü</button>
      <button type="button" class = "button-default"
      onclick="input('û')">û</button>
      </div>
        <script>
          function input(e){
            var seInput = document.getElementById("seInput");
            seInput.value = seInput.value + e;
            document.getElementById("seInput").focus();
          }
        </script>


  <table id="myTable">
  {% for row in site.data.database-august-2 %}
  <!-- table head -->
    {% if forloop.first %}

      {% for pair in row limit: 6%}
        <th>{{ pair[0] }}</th>
        {% endfor %}

    {% endif %}

<!-- table body -->
    {% tablerow pair in row limit: 6 %}
      {{ pair[1] }}
   {% endtablerow %}

{% endfor %}



<!-- source : https://www.w3schools.com/howto/tryit.asp?filename=tryhow_js_filter_table -->
 <script>
 function myFunction(val) {
   var input, filter, table, tr, td, i, txtValue;
   input = document.getElementById("seInput");
   filter = input.value.toUpperCase();
   table = document.getElementById("myTable");
   tr = table.getElementsByTagName("tr");
   for (i = 0; i < tr.length; i++) {
     td = tr[i].getElementsByTagName("td")[val];
     if (td) {
       txtValue = td.textContent || td.innerText;
       if (txtValue.toUpperCase().indexOf(filter) > -1) {
         tr[i].style.display = "";
       } else {
         tr[i].style.display = "none";
       }
     }       
   }
 }
 </script>
