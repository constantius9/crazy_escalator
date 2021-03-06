

# Моделирование пропускной способности эскалатора в условиях очереди на вход #
## Цель ##
Доказать, что толпиться на входе на эскалатор на правую сторону совокупно менее оптимально, чем при наличии очереди занимать обе стороны самим.

## Простейшие случаи ##
1. Эскалатор, на вход на который очередь, на котором люди занимают только правую сторону, давая желающим проходить слева
1. Эскалатор, на который, в случае появления очереди, люди начинают заходить и слева тоже, блокируя проход.

## Метрика ##
1. Совокупное (среднее или медианное) время, затраченное на пропускание через эскалатор заданного числа людей. Взаимозависимая метрика.
1. Время, затраченное на подъём по эскалатору для единичного пассажира, в условиях, когда он хочет идти и не хочет. Эгоистичная метрика.

## Модель ##
### Эскалатор ###
1. Скорость движения полотна
1. Ширина полотна
1. Длина пролёта

### Толпа ###
1. Вероятность занятия каждой части эскалатора
1. Вероятность желания идти по эскалатору. Зависит от спешки и от размера очереди
	1. Идти вверх
	1. Идти вниз
1. Вероятность продолжения движения, если впереди полотно занято

### Очередь на вход ###
1. Примерный размер
1. Время, потерянное на входе. Зависит от размера

### Простейшие модели ###
Во всех случаях даже с простейшей моделью нужна интенсивность входа пассажиров на эскалатор. Причём на не-пересадочных станциях она имеет прерывистый характер — всплеск при прибытии поезда, затем затишье до следующего поезда.

Скорость прибытия пассажиров к эскалатору в модели значения не имеет. Однако, интенсивность прихода рассчитывается исходя из неё.

Важно соотношение интенсивности обслуживания эскалатора и прихода пассажиров. Разумным кажется соотношение 10/12 для ситуации «пришедший поезд с средним числом пассажиров не в час пик». Ситуация наблюдается, например, на «Бауманской» в  промежутке 15-16 часов.

Следует учесть, что отношение динамически изменяется в результате прихода поездов. Соответстенно, для простоты, надо принять постоянную интенсивность пассажиров, что недалеко от истины, учитывая сильно различную скорость пассажиров (от студентов до бабушек скорость варьируется раза в 2-3) и наложение интенсивностей в результате прихода  поездов в случайные моменты времени.
#### Случай 1: только правая сторона, очередь ####
1. Источники:
	1. Ленивые пассажиры — стоят на эскалаторе, всё равно, где
	1. Спешащие пассажиры — хотят идти по эскалатору, заходят на левую сторону и идут, если свободно

	Распределение моментов времени прихода пассажиров — гауссово.

1. Устройства:
	1. Эскалатор. С определённой задержкой берёт людей на каждую из 2 сторон. В отсутствие спешащих людей на левую сторону никто не встаёт. Через фиксированное время (разное для ленивых и спешащих) отпускает пассажиров. Стороны эскалатора удобно представить 2 устройствами. Скорость движения полотна — 2 ступени в секунду. Интенсивность потребления пассажиров — 1 или 0.5 в секунду (в зависимости от того, встают пассажиры на каждую ступень или через одну)
1. Очереди:
	1. Очередь на вход на правую сторону эскалатора. Имеет бесконечный размер. На самом деле, создаёт препятствия всем пассажирам (в том числе тем, которые входят на левую сторону). Пока это не учитывается

#### Случай 2: обе стороны, отдельные очереди ####

Более-менее разумно-реалистичные результаты получаются при законе

	GENERATE	(NORMAL(1,0.5,0.02))	; Generating Passengers with delay before first passenger comes

и запуске `START 100`
