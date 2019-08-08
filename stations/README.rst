Stations
--------

These stations are named coded as follows:

<0-9>W - number of cargo wagons

<SS|DS> - single sided or dual sided (from the train track)

<Y|R|B>B - yellow/red/blue belted

<FI|SI|FFI|FSI> - Fast Inseter | Stack Inserter | Filter Fast Inserter | Filter Stack Inserter

<FE> - Full/Empty turn on/off circuit when station is full/empty

<IC|SC> - Iron Chest or Steel Chest

<Loader|Unloader>

<Balanced|Unbalanced>


Variables in the Constant Combinator
------------------------------------

* Iron-Chest : 32: The number of storage slots in the iron chest

* Steel Chest: 48: The number of storage slots in the steel chest

* D: Divider: Number of containers / inserters that have to be counted to make the average

* S: Stack Size: Size of the resource stored in a single slot (ie. 50 for ores, 100 for plates, 200 for Green Circuits).

* K: The value to skew the Full value so that is might be computed as non strictly FULL. Should be an int between 0 and the minimum you want.

To change which container (Iron or Steel chest) should be considered, change the input signal in the Arithmetic Combinator that computes `E`


Variables computed on the side.
------------------------------

* E: Empty: The value at which to consider the quantity of stuff in storage is low (think of the E of your car)

* F: The Value to consider the amount of resources stored is plenty enough to open the station

* I : Input: the `*` symbol from containers transformed into a specific name variable so it works for all types of resources

* Green: When I >= F

* Red: When I <= F



The Equalizor Dividor
--------------------

On the side of all that, the D signal which comes from the constant combinator is past on to the dividor which allows to do the balanced filling-in of the containers.
An additional combinator with a value of D = -1 is here to nulify the D signal when going to the inserters.
