# [Movin' Out](https://www.youtube.com/watch?v=cJtL8vWNZ4o&ab_channel=billyjoelVEVO) 馃彏:
<div align=center><img src ="https://trabajadorasocialdepueblocom.files.wordpress.com/2020/08/wp-1598249473318.gif?w=498&zoom=2" /></div>


Des de la aparici贸n de la revoluci贸n industrial la poblaci贸n de zonas rurales en Espa帽a he seguido una tend茅ncia de migraci贸n hacia las grandes ciudades. Esto ha llevado a la despoblaci贸n de ciertas zonas de Espa帽a que siguen viendo como sus datos demogr谩ficos son cada vez menos esperanzadores.

Lo cierto es que en los 煤ltimos a帽os ha aparecido el concepto de 'home office', trabajar des de casa o "tele-trabajar" es cada vez m谩s frecuente en el mundo digital, ya sea parcialmente o totalmente. Esto ha hecho que aparezcan perfiles de gente que desea mudarse fuera de las ciudades, en busca de tranquilidad y salud. 

Con el fin de crear una herramienta para toda esa gente que quiera mudarse al campo pero no sepa por donde empezar hemos decidido crear una aplicaci贸n. Para ello, hemos tenido que crear el perfil de nuestro usuario medio y ver que es lo que busca en un pueblo. Este trabajo lo ha hecho mi compa帽era de UI/UX. Mi trabajo en el proyecto ha sido generar todas las herramientas necesarias para recopilar todos los datos que se necesitar铆an de cara a la creaci贸n de la aplicaci贸n. Adem谩s de crear la infrastructura para almacenar todos esos datos de forma que sean facilmente accesibles y faciles de usar. 

Finalmente, aunque no tenemos una compa帽era para crear la aplicaci贸n como tal he decidido crear una API con flask para poder ejemplificar los resultados obtenidos.

He subido en el repo toda la info que usado, tanto el c贸digo usado (con un 1 los archivos dedicados a la recopilaci贸n, con un 2 los dedicados a la creaci贸n de la base de datos y con un 3 los dedicados a la creaci贸n de la api), como los datos. Las fuentes de los datos estan citadas en la [Bibliografia](#bibliografia). 


# La recopilaci贸n de los datos 馃懛馃徏鈥嶁檪锔?: 
Vimos que lo m谩s importante para la mayor铆a de gente que quer铆a mudarse un elemento importante era mantener una buena conexi贸n a la red. Es por eso que decid铆 basar mi base de datos en un archivo csv sacado del Instituto Nacional de Estad铆stica (INE) que indicaba la conectividad en cada Entidad poblacional de Espa帽a (a internet, >= 30mb y >= 100mb y 3g y 4g). 

Por simplicidad decid铆 ce帽irme a estudiar las entidades poblacionales en Castilla-Le贸n, por ser una comunidad aut贸noma con poca densidad de poblaci贸n, y la principal v铆ctima de la despoblaci贸n de zonas rurales. 

Pues bien, tuve que buscar informaci贸n de diferentes formas. Combine el uso de datos extra铆dos del INE en forma de csvs y el scrapeo de diferentes fuentes, tales como [Wikipedia](https://es.wikipedia.com) o [GoogleMaps](https://googlemaps.es). 

Hemos recogido datos de muchas naturalezas distintas para enriquecer la base de datos, tales como la poblaci贸n en cada poblaci贸n y del municipio al que pertenece, el partido politico que govierna en los municipios, datos climaticos o entidades cercanas (entidades como polideportivos, hospitales o centros comerciales). 

Un dato importante que no hemos recopilado pero ser铆a interesante intentar incluir de cara a un futuro es el precio del suelo en cada poblaci贸n y la disponibilidad de viviendas.

# La base de datos 馃梼:
Por la diversidad en los datos decid铆 usar el sistema de MongoDB. Es decir, la base de datos es no relacional. Aunque si que le he dado una estructura.

Todos los elementos incluidos en la base de datos tienen diferente informaci贸n referente a cada entidad. Pero hay 2 elementos presentes en todas las entidades, un geopunto que identifica la localizaci贸n de la entidad, y un elemento que describe el tipo de entidad. Es decir, que siempre podemos saber si hablamos de un pueblo, un hospital, una escuela o otra una entidad de otro tipo y sabemos donde se encuentra. 

La idea es que una futura aplicaci贸n pudiera hacer geoqueries para filtrar entre poblaciones. Si en un futuro enriquecieramos la base de datos con muchos m谩s datos de toda Espa帽a ser铆a f谩cil filtrar pueblos por distancia a centros de salud, escuelas, etc. 

# La API 馃椇:
La interfaz que he creado en el servidor de mi ordenador es muy senzilla y solo pretende ejemplificar la utilidad de la base de datos creada. La idea es que tenga dos funciones principales. 

Una de ellas esta ya terminada y operativa. Es posible buscar un pueblo de Castilla Le贸n y que nos muestre el pueblo, con informaci贸n sobre el mismo. Informaci贸n referente al clima, conectividad, etc. Adem谩s tambi茅n aparecen en el mapa un grupo de entidades cercanas a la poblaci贸n.

La otra funci贸n que deber铆a inculir esta api es un filtro. La idea ser铆a poder llamar des de la api una geoquerie y que nos diera, por ejemplo, todos los pueblos que queden a menos de 20km de un hospital. De tal forma que aplicando un numero elevado de filtros pudieramos reducir mucho el numero de pueblos, y encontrar el mejor pueblo para nuestro usuario. Esta funci贸n no la he acabado, entre otras cosas por la falta de datos en la base de datos, que se encuentra en un estadio muy inicial. 

# Further Steps 馃殌:
Este ha sido el proyecto final que he hecho en IRONHACK, he tenido apenas 10 d铆as para desarroyarlo. Es por eso que el producto final es simplemente una peque帽a muestra de lo que podr铆a llegar a ser si un d铆a decido crear, realmente, una base de datos que tenga una utilidad real y sea operativa. Hay muchisimas cosas que han quedado por hacer, as铆 que voy a listar alguna de ellas por el orden que creo m谩s adiente:
* Mejora del scrapeo, recopilaci贸n de datos sobre todos y cada uno de los pueblos de Castilla Le贸n,
* Extrapolar a todo el estado espa帽ol. La creaci贸n de funciones que valen para los datos en Castilla Le贸n admite que se pueda extrapolar a todo el estado, o incluso con las debidas modificaciones es extrapolable a cualquier zona del planeta (隆d贸nde haya pueblos!馃槀).
* Creaci贸n de geoqueries que sirvan para filtrar de forma eficiente y adequada la base de datos. 
* Mejora de la interfaz, a nivel estetico pero sobretodo funcional, incluir mucha m谩s informaci贸n y estructurarla para que sea 煤til. 

# Bibliografia 馃摎: <a name="bibliografia"></a>
### Libraries:
* [Pandas](https://pandas.pydata.org/)
* [Numpy](https://numpy.org/doc/1.18/)
* [ReGex](https://docs.python.org/3/library/re.html)
* [Flask](https://flask.palletsprojects.com/en/2.0.x/)
* [Pymongo](https://pymongo.readthedocs.io/en/stable/)
* [Selenium](https://selenium-python.readthedocs.io/)
* [Beautiful Soup (bs4)](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)

### Fuentes de datos:
* [Instituto Nacional de Estad铆stica (INE)](https://ine.es)
* [Wikipedia](https://es.wikipedia.com)
* [Weather Spark](https://es.weatherspark.com/)
* [GoogleMaps](https://googlemaps.es)

 
