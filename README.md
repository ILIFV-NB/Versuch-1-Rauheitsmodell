<!--

author:   Nancy Brinkmann, Ronny Stolze

email:    nancy.brinkmann@hs-magdeburg.de, ronny.stolze@hs-magdeburg.de

version:  11.20

language: de

comment:  Versuch 1: Ermittlung von Bearbeitungsparametern zur Realisierung von Oberflächengüten

narrator: DE FEMALE

script:  https://cdnjs.cloudflare.com/ajax/libs/echarts/4.2.1/echarts-en.js

-->

# Versuch 1: Rauheitsmodell

Für die Versuche 1 - 4 werden Ihnen zu erzielende Oberflächengüten vorgegeben. Ermitteln Sie mithilfe des
Oberflächenmodells und unter Berücksichtigung des ausgewählten Werkzeuges geeignete Bearbeitungsparameter und tragen diese in untenstehende Tabelle ein. Diese Parameter benötigen Sie für Ihre praktischen Untersuchungen vor Ort und sind in der Maschinensteuerung anzuwählen.

Mit Hilfe der im Labor zur Verfügung stehenden geeigneten Messtechnik sind anschließend die erreichten Oberflächengüten (Experimentell) zu messen und die Ergebnisse im Protokoll auszuwerten.

<br/>

<!--
style="font-size: 14px; width: 100%; margin: 0.25em 1;"
-->
***Tabelle:*** *Technologiewerte – Oberflächenmodell*

<!--
style="width: 100%; "
-->
| **Eckenradius <br/> WSPL** | | | | | | |
| |**Parameter**	| | | | **Oberflächengüte**| |
| | Schnitt- <br/> tiefe |Schnitt- <br/> geschw. |Vorschub |Drehzahl | gemittelte Rautiefe <br/> Rz in µm| |
|**Versuch** |**ap** <br/> $[mm]$ |**vc** $[m/min]$ |**f** $[mm/U]$| **n** $[U/min]$ | Vorgabe | Experimentell |
| | | | | | | |
|**1**| | | | | **16** | |
|**2**| | | | | **12** | |
|**3**| | | | | **6,3** | |
|**4**| | | | | **3,2** | |


<br/>

Tragen Sie hier bitte jeweils unter **.1** hintereinander (ap - vc - f - n) alle Parameter zu den Versuchen 1 - 4 ein! Während des Praktikums tragen Sie die experimentell ermittelten Werte jeweils unter **.2** nach.

**Versuch 1.1:** (ap - vc - f - n)

[[___ ___]]

**Versuch 1.2:** (Rz **exp.**)

[[___ ___]]

<br/>

**Versuch 2.1:** (ap - vc - f - n)

[[___ ___]]

**Versuch 2.2:** (Rz **exp.**)

[[___ ___]]

<br/>

**Versuch 3.1:** (ap - vc - f - n)

[[___ ___]]

**Versuch 3.2:** (Rz **exp.**)

[[___ ___]]

<br/>

**Versuch 4.1:** (ap - vc - f - n)

[[___ ___]]

**Versuch 4.2:** (Rz **exp.**)

[[___ ___]]


# Hilfe zur Protokollerstellung

Um das Praktikum abzuschließen, fassen Sie Ihre Beobachtungen und Ergebnisse der Versuche bis zu einer festgesetzten Frist zusammen.

Die folgenden Eingabemasken unterstützen Sie dabei, Ihre generierten Texdateien in Diagramme umzuwandeln. Kopieren Sie dafür den Dateninhalt (ausschließlich aufgelistete Werte) aus Ihrer Textdatei und kopieren Sie diesen in das Eingabefeld. Mit einem Klick auf den Pfeil erhalten Sie Ihr Diagramm.

Dieses können Sie nun auswerten und sich als Bild herunterladen. Um einzelne Graphen auszublenden, klicken Sie auf das jeweilige Symbol in der Legende.

Nutzen Sie für die Erstellung Ihres Protokolls bitte auch die Kurse ~~Theoretische Grundlagen~~, ~~Maschinen- und Gerätetechnik~~ sowie ~~Gesamtsystem WSWW+H~~!


## Rauheitskenngrößen

``` cvs (Ra in µm - Rz in µm - Rmax in µm)
```
<script>
let data1 = `@input`.replace(/,/g, ".");

let split1 = data1.match(/\d+(?:\.\d+)?|\-\d+(?:\.\d+)?/g);
//document.write(split1);
let M = []
let Ra = []
let Rz = []
let Rmax = []
let j = 1

for(let i=0; i<split1.length; i=i+3) {
  M.push(j);
  Ra.push(parseFloat(split1[i]));
  Rz.push(parseFloat(split1[i+1]));
  Rmax.push(parseFloat(split1[i+2]));
  j=j+1;
};

plotData(M, Ra, Rz, Rmax);

function plotData(t1, x1, y1, z1) {

  let main1 = document.getElementById('main1');
  main1.hidden = false;

  let ra = []
  let rz = []
  let rmax = []

  for(let i=0; i<t1.length; i++) {1;2,3;5
    ra.push([t1[i], x1[i]])
    rz.push([t1[i], y1[i]])
    rmax.push([t1[i], z1[i]])
  }

  let chart1 = echarts.init(main1);

  let option1 = {

    title : {
      display: false,
      text: "Rauheit",
      subtext: 'Kenngrößen',
      itemGap: 10,
      textAlign: 'auto',
      textVerticalAlign: 'middle',
      textStyle: {
        fontSize: 30,
      },
      subtextStyle: {
        fontSize: 20,
      },
    },

    grid: {
      top: 120,
    },

    legend: {
        data:['Ra', 'Rz', 'Rmax'],
        top: 80,
        itemGap: 40,
        itemWidth: 50,
        itemHeight: 20,
        textStyle: {
          fontSize: 24,
        },
    },

    toolbox: {
      show : true,
      feature : {
        mark : {show: true},
        dataZoom : {show: true},
        dataView : {show: true, readOnly: false},
        restore : {show: true},
        saveAsImage : {
          show: true,
          pixelRatio: 4,
        },
      },
    },

    xAxis: [{
      type: 'category',
      nameLocation: 'middle',
      nameGap: 30,
      axisLabel: {
        fontSize: 20,
        formatter: 'Messung {value}'
      },
      nameTextStyle: {
        fontSize: 20,
      },
    }],

    yAxis: [{
      type : 'value',
      name: 'Rauheit in µm',
      nameLocation: 'middle',
      nameGap: 60,
      axisLabel: {
        fontSize: 20,
      },
      nameTextStyle: {
        fontSize: 20,
      },
    }],

    series : [
    {
      name:'Ra',
      type:'bar',
      data: ra,
      label: {
        show: true,
        rotate: 90,
        formatter: ra,
        fontSize: 18,
      },
    },
    {
      name:'Rz',
      type:'bar',
      data: rz,
      label: {
        show: true,
        rotate: 90,
        formatter: rz,
        fontSize: 18,
      },
    },
    {
      name:'Rmax',
      type:'bar',
      data: rmax,
      label: {
        show: true,
        rotate: 90,
        formatter: rmax,
        fontSize: 18,
      },
    }
    ]
  };

  // use configuration item and data specified to show chart
  chart1.setOption(option1);

  window.addEventListener('resize', chart1.resize);
}
</script>


<div id="main1" style="position: relative; width:100%; height:600%;" hidden="true"></div>


## Rauheitsprofil

<!--
style="font-size: 30px; margin: 0 0;"
-->
**P-Profil**


``` cvs (Taststrecke in mm - P-Profil in µm)

```
<script>
let data2 = `@input`.replace(/,/g, ".");

let split2 = data2.match(/\d+(?:\.\d+)?|\-\d+(?:\.\d+)?/g);
//document.write(split2);
let Lt = []
let P = []


for(let i=0; i<split2.length; i=i+2) {
  Lt.push(parseFloat(split2[i]));
  P.push(parseFloat(split2[i+1]));
};

plotData(Lt, P);

function plotData(t2, x2) {

  let main2 = document.getElementById('main2');
  main2.hidden = false;

  let p = []

  for(let i=0; i<t2.length; i++) {
    p.push([t2[i], x2[i]])
  }

  let chart2 = echarts.init(main2);

  let option2 = {

    title : {
      display: false,
      text: "Primärprofil",
      subtext: 'P-Profil',
      itemGap: 10,
      textAlign: 'auto',
      textVerticalAlign: 'middle',
      textStyle: {
        fontSize: 30,
      },
      subtextStyle: {
        fontSize: 20,
      },
    },

    grid: {
      top: 120,
    },

    legend: {
        data:['P-Profil'],
        top: 80,
        itemGap: 40,
        itemWidth: 50,
        itemHeight: 20,
        textStyle: {
          fontSize: 24,
          color: 'black',
        },
    },

    toolbox: {
      show : true,
      feature : {
        mark : {show: true},
        dataZoom : {show: true},
        dataView : {show: true, readOnly: false},
        restore : {show: true},
        saveAsImage : {
          show: true,
          pixelRatio: 4,
        },
      },
    },

    xAxis: [{
      type: 'value',
      name: 'Taststrecke in mm',
      nameLocation: 'middle',
      nameGap: 40,
      min: 0,
      max: 4.8,
      interval: 0.8,
      axisLabel: {
        fontSize: 20,
      },
      nameTextStyle: {
        fontSize: 20,
      },
    }],

    yAxis: [{
      type : 'value',
      name: 'Profil in µm',
      nameLocation: 'middle',
      nameGap: 60,
      axisLabel: {
        fontSize: 20,
      },
      nameTextStyle: {
        fontSize: 20,
      },
    }],

    series : [
    {
      name:'P-Profil',
      type:'line',
      data: p,
      symbol: 'none',
      color: 'black',
      lineStyle: {
        width: 1,
        color: 'black',
      },
    },
    ]
  };

  // use configuration item and data specified to show chart
  chart2.setOption(option2);

  window.addEventListener('resize', chart2.resize);
}
</script>

<div id="main2" style="position: relative; width:100%; height:600%;" hidden="true"></div>

<br/>


## Durchmesser


``` cvs (Ø d in mm)
```
<script>
let data5 = `@input`.replace(/,/g, ".");

let split5 = data5.match(/\d+(?:\.\d+)?|\-\d+(?:\.\d+)?/g);
//document.write(split5);
let M1 = []
let D = []
let n = 1

for(let i=0; i<split5.length; i=i+1) {
  M1.push(n);
  D.push(parseFloat(split5[i]));
  n++;
};

plotData(M1, D);

function plotData(t5, x5) {

  let main5 = document.getElementById('main5');
  main5.hidden = false;

  let d = []

  for(let i=0; i<t5.length; i++) {
    d.push([t5[i], x5[i]])
  }

  let chart5 = echarts.init(main5);

  let option5 = {

    title : {
      display: false,
      text: "Durchmesser",
      subtext: 'Welle/Passsitz',
      itemGap: 10,
      textAlign: 'auto',
      textVerticalAlign: 'middle',
      textStyle: {
        fontSize: 30,
      },
      subtextStyle: {
        fontSize: 20,
      },
    },

    grid: {
      top: 120,
    },

    legend: {
        data:['Durchmesser'],
        top: 80,
        itemGap: 40,
        itemWidth: 50,
        itemHeight: 20,
        textStyle: {
          fontSize: 24,
        },
    },

    toolbox: {
      show : true,
      feature : {
        mark : {show: true},
        dataZoom : {show: true},
        dataView : {show: true, readOnly: false},
        restore : {show: true},
        saveAsImage : {
          show: true,
          pixelRatio: 4,
        },
      },
    },

    xAxis: [{
      type: 'category',
      nameLocation: 'middle',
      nameGap: 30,
      axisLabel: {
        fontSize: 20,
        formatter: 'Messung {value}'
      },
      nameTextStyle: {
        fontSize: 20,
      },
    }],

    yAxis: [{
      type : 'value',
      name: 'Messwert in mm',
      nameLocation: 'middle',
      nameGap: 60,
      axisLabel: {
        fontSize: 20,
      },
      nameTextStyle: {
        fontSize: 20,
      },
    }],

    series : [
    {
      name:'Durchmesser',
      type:'bar',
      data: d,
      label: {
        show: true,
        rotate: 90,
        formatter: d,
        fontSize: 18,
      },
    },
    ]
  };

  // use configuration item and data specified to show chart
  chart5.setOption(option5);

  window.addEventListener('resize', chart5.resize);
}
</script>


<div id="main5" style="position: relative; width:100%; height:600%;" hidden="true"></div>


## Hinweise

* Betätigen der Funktionstaste F5 aktualisiert die Seite und lässt alle Diagramme verschwinden. Ein erneuter Klick auf den Pfeil unter dem Eingabefeld erzeugt ein neues Diagramm.
* Um sich einen Ausschnitt im Diagramm näher anzuschauen, klicken Sie über dem Diagramm auf das Zoom-Icon und wählen den zu betrachtenden Bereich im Diagramm aus. Den Ausgangszustand erhalten Sie mit Zoom-Reset (Icon daneben).
* Wenn Sie erfahren möchten, welche Daten das aktuelle Diagramm beinhaltet, klicken Sie auf das Icon in Form eines Dokumentes.
