# flow5.1
En este repositorio se explica la actividad que se le agrego al flow5, es por ello que se llama flow5.1


La siguiente actividad consta de agregar la gráficas:
 UV
 aqi: Calidad del Aíre en la ubicación seleccionada


Primero involucramos las varibales globales con el siguiente codigo en el Nodo Function:


msg.payload = '{"id":"Zuriel","temp":'+global.get ("tempFlow5")+',"hum":'+global.get ("humFlow5")+',"uv":'+global.get ("uviFlow5")+',"aqi":'+global.get ("aqi")+'}';

return msg;

Ahora en los Nodos http request tendra la siguiente forma particular:

Nodo uno http request con onecall:

https://api.openweathermap.org/data/2.5/onecall?lat=19.44519163299204&lon=-99.20614630492445&exclude=hourly,daily&appid=520c194bdaaacfb92a1c81ca67c668b6&units=metric


Nodo dos http request con Pollution:

http://api.openweathermap.org/data/2.5/air_pollution?lat=19.44519163299204&lon=-99.20614630492445&appid=520c194bdaaacfb92a1c81ca67c668b6&units=metric

*Nota: es importante rercordar que la ip cambia por lo que se tiene que realizar su respectivo cambio*
*Nota2: la ubicación utilizada es la misma que se utilizó en el flow5*


Seccion Información general

---------------------------------------------------------------------------
Funcion UV

msg.topic = msg.payload.id;

msg.payload = msg.payload.uv;

return msg;

---------------------------------------------------------------------------
Funcion AQI

msg.topic = msg.payload.id;

msg.payload = msg.payload.aqi;

return msg;


---------------------------------------------------------------------------
Para el enviador en el nodo function


msg.payload = '{"id":"Zuriel","temp":'+global.get ("tempFlow5")+',"hum":'+global.get ("humFlow5")+',"uv":'+global.get ("uviFlow5")+',"aqi":'+global.get ("aqi")+'}';

return msg;


Los nodos estan colcados de la siguiente manera:


[![flow5-1.png](https://i.postimg.cc/wv7dZk21/flow5-1.png)](https://postimg.cc/qhVYCy9r)



El interfaz se observa de la siguiente manera:

[![flow5-1-1.png](https://i.postimg.cc/mr6rPk6F/flow5-1-1.png)](https://postimg.cc/Z9pmgbmT)



Recordar que la posición que se colocaron las gráficas fue:

1.Dashboard
2.En flow5 seleccionar layout
3.Con los candados puedes mover el tamaño de las gráficas de acuerdo a la anchura seleccionada anteriormente.