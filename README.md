# MSA PRO — Project 3 Stage 2

Ссылка на веб-карту: https://leone991.github.io/webmap/

## Команда

- Катерина Лысенко (191) 
- Анна Соколова (192)
- Денис Тетюшкин (191)

## О городе

### История
Город-крепость Оренбург был построен в 1743 году, расположен на слиянии двух рек - Урала и Сакмары, вблизи границы с Казахстаном, и является главным связующим звеном между Европой и Азией, город с необыкновенными достопримечательностями.
До 1743 года Оренбург дважды закладывали в других местах. В 1730 году хан Младшего казахского жуза Абулхаир обратился к Российской империи с просьбой о вступлении в подданство. Таким образом, для укрепления влияния России в Зауралье была отправлена экспедиция под руководством И.К. Кирилова. Экспедиции было указано заложить город-крепость. Первая крепость была заложена в августе 1735 года на месте нынешнего Орска, откуда пошло название Оренбурга. Однако место города было выбрано весьма не рационально - оно постоянно затоплялось весенним половодьем.
В 1739 году Оренбург был заложен снова ниже по реке Яику в урочище Красная гора. По проекту И. И. Неплюева в 1743 году город был перенесен на свое нынешнее месторасположение. В связи этими событиями Оренбург называют «трижды зачатым и единожды рождённым».
Именно из - за своей богатой истории  и связью с именами многих известных людей Оренбург обладает большим количеством объектов культурного наследия. 

### Настоящее время
Открытие газового месторождения, которое пришлось на 70-е годы 20 века, явилось вторым рождением города. Оренбург, до открытия газового месторождения, в основном состоял из домов, которые были построены в дореволюционное время, и одноэтажных домов, относящихся к частному сектору. Благодаря развитию газового комплекса Оренбург превратился в современный многоэтажный благоустроенный город. Добыча природного газа ведется на крупнейшем в Европе Оренбургском газоконденсатном месторождении. Природный газ Оренбуржья поступает во многие регионы страны и стран Европы.

Современный Оренбург - крупный индустриальный центр, основу экономического потенциала города составляют промышленные предприятия.

>Интересный факт : Оренбург был первой столицей советского Казахстана. В 1920 году этот город стал административным центром созданной Киргизской Автономной Социалистической Советской Республики. В тот период казахи официально именовались киргизами. В апреле 1925 года Киргизская АССР была переименована в Казахскую АССР, а ее столица была перенесена из Оренбурга в Ак-Мечеть, переименованный в Кзыл-Орду. 

### ОКН
17 сентября 2003 года в области был принят закон “Об объектах культурного наследия (памятниках истории и культуры) в Оренбургской области”. Настоящий Закон регулирует отношения в сфере сохранения, использования,  популяризации  и  государственной  охраны объектов    культурного   наследия   (памятников  истории и культуры), расположенных на территории   Оренбургской  области,  в  целях    сохранения  уникального  исторического  и   культурного наследия Оренбургской области, являющегося неотъемлемой частью российской и мировой культуры.

1 марта 2023 года губернатор Оренбургской области Денис Паслер подписал постановление “Об установлении границ объединенной зоны охраны объектов культурного наследия города Оренбурга». Под охранной зоной понимается большой район старой застройки, иными словами, исторический центр Оренбурга. В границах зоны располагается 271 объект культурного значения: 22 – федерального, 236 – регионального и 13 – местного.

## Используемые данные

Для подготовки карты были использованы данные из различных источников. Объекты ОКН были переданы нашей команде как исходные данные, являющиеся выгрузкой из реестра объектов культурного наследия.

В качестве дополнительного слоя для визуализации наша команда выбрала численность отелей в Оренбурге. Датасет был собран одним из участников команды из открытых данных  в рамках выполнения другой задачи в этом же регионе некоторое время назад.

Для отрисовки иконок с фасадами ОКН были использованы фото с панорам Яндекс Карт, опубликованные материалы в сообществе “Инспекция гос. охраны ОКН Оренбургской области” в Вконтакте. 

## Методы

Исходные данные по ОКН были отфильтрованы с помощью регулярных выражений на предмет нахождения адреса в городе Оренбурге. Затем была проверена геопривязка ОКН, осуществлена перепривязка “потерявшихся” объектов и стыковка точек с полигонами зданий взятыми из OSM.

> Рассматривались только ОКН в границах города Оренбурга а не всего городского округа, и в связи с плохим качеством границы города в OpenStreetMap была вручную отрисована граница города с генплана.

Привязка к зданиям осуществлялась в QGIS с помощью join by location (была рассмотрена идея фильтрации ОКН чтобы рассматривать только памятники архитектуры и градостроительства при привязке, однако было обнаружено что часть памятников истории также является объектами капитального строительства).

Ансамбли были выделены по двум критериям: либо вид ОКН — “Ансамбль”, либо в атрибутах ОКН содержится id-идентификатор  ансамбля. На карте ансамбли показаны в виде более темных полигонов зданий.

Аналитические слои созданы скриптом на python: агрегированные по сетке ОКН с помощью geopandas и shapely, теплокарта отелей с помощью плагина HeatMap для Folium 

