## Entities
- Hardwarebloecke werden als Entities abstrahiert
- Entities werden als Blackbox behandelt, weshalb nur Ein- und Ausgabesignale definiert werden
#### Beispiel
```vhdl
entity basic is
	port (
		a, b, c : in std_logic;
		y       : out std_logic
	);
end entity basic;
```
## Architectures
- Architectures definieren das eigentliche Verhalten von Entities
- Mithilfe von Signal Deklarationen koennen interne Signale dargestellt werden
- Ueber Operationen, wie and, or, oder not kann das Verhalten einer Architecture ausgehend von den Eingaben des Entities definiert werden
#### Beispiel
```vhdl
architecture behave of basic is

	signal and1, and2, and3 : std_logic
	
	begin
	
		and1 <= (not a) and b and c;
		and2 <= a and (not b) and c;
		and3 <= a and b and c;
	
		y <= and1 or and2 or and3;

end architecture behave;
```
## Components
- Entities sind modular und koennen von anderen Entities als Components verwendet werden
- Um Entities als Component zu verwenden, muessen der Name des Entities und der Name des Components uebereinstimmen
- Um einem Component Eingabesignale zu uebergeben und Rueckgabesignale zu empfangen, muss ein port map verwendet werden 
#### Beispiel
```vhdl
entity or4 is
	port (
		a : in std_logic_vector(3 downto 0);
		y : out std_logic
	);
end entity or4;

architecture struct of or4 is

	component or2 is 
		port (
			a, b : in std_logic;
			y    : out std_logic
		);
	end component or2;
	
	signal or_res1, or_res2 : std_logic;
	
	begin
	
		or_comp1: or2 port map(a => a(0), b => a(1), y => or_res1);
		or_comp2: or2 port map(a => a(2), b => a(3), y => or_res2);
		or_comp3: or2 port map(a => or_res1, b => or_res2, y => y);

end architecture struct;
```
## Ausfuehrungsreihenfolge
- Innerhalb einer Architecture werden Signalzuweisungen parallel ausgefuehrt
## Datentypen
#### std_logic
- Dieser Datentyp repraesentiert einzelne Bits
- Es koennen somit die Werte 1 oder 0 angenommen werden
- Logische Operationen, wie and, or, oder not koennen auf diesem Typ ausgefuehrt werden
###### Beispiel
```vhdl
architecture behave of example is

	signal one, zero : std_logic;

	begin

		one <= '1';
		zero <= '0';

end architecture behave;
```
#### std_logic_vector
- Signale mit groesserer Bitbreite koennen mithilfe von std_logic_vector realisiert werden
- Diese entsprechen Arrays aus Bits
- Vektoren koennen zudem ueber Bit Swizzling zusammengesetzt werden  
###### Beispiel
```vhdl
architecture behave of example is

	signal a : std_logic_vector(3 downto 0);
	signal b : std_logic_vector(3 downto 0);
	signal c : std_logic_vector(7 downto 0);

	begin

		a <= 4b"1010"; -- a = 1010
		b <= 4b"11"; -- b = 0011
		c <= (a(3 downto 2), b(3), b(1), a(1), a(0), 2b"01"); -- c = 1001 1001

end architecture behave;
```
## Testbenches
- Um die Funktionsweise eines Entitys zu testen, muessen Stimuli angelegt und Ausgabe- mit Sollwerten verglichen werden
- Stimuli werden ueber Signale an den Device Under Test (DUT) weitergegeben
- Ausgabewerte werden ueber asserts mit Sollwerten verglichen
#### Beispiel
```vhdl
entity testbench is

end entity testbench;

architecture behave of testbench is:

	component basic is
		port (
			a, b, c : in std_logic;
			y       : out std_logic
			);
	end conponent basic;

	signal stim : std_logic_vector(2 downto 0);
	signal y : std_logic;

	begin

		DUT : basic port map(a => stim(2), b => stim(1), c => stim(0), y => y);

	process

		begin
			stim <= "011";
			wait for 20 ns;
			assert(y = '1')
				report "Error" severity error;
			wait;

	end process;

end architecture behave;
```