# Ruby

Ruby je plně objektový, skriptovací programovací jazyk navržený začátkem 90. let, navrhnul a vytvořil ho jediný člověk, Yukihiro Matsumoto, známý spíše pod svojí přezdívkou „Matz“. Nejznámější implementace se nazývá MRI, neboli Mat’z Ruby Implementation, také známý jako CRuby, protože je napsaný v Jazyce C. Dále se můžeme setkat s dalšími implementacemi jako je Rubinius v C++ nebo JRuby v Javě.


> "Ruby je jednoduché na první pohled, ale velice složité uvnitř, stejně tak jako naše tělo.”
> *Yukihiro Matsumoto (Matz), autor Ruby*


Pracovat na tomto jazyce začal Matz roku 1993 a o dva roky později byla uvedena jeho první verze. Aktuální verze je 2.0, která ovšem nemá žádné zásadní změny od verze 1.9.3, jak řekl Matz, vývoj této verze byl veden pod "návrhovým" vzorem anniversary driven development, neboli verze vydaná k 20. výročí jazyka.

## Filosofie

Primárním cílem je co největší usnadnění vývoje pod tímto jazykem, pod tím si Matz představuje minimalizování potřebné práce programátora, aby programátor dělal jen to nezbytné co doopravdy musí a předpovídatelnost toho, co jazyk udělá. Sám programoval v C++, který ho i po několika letech programování neustále překvapoval, toho se snažil co nejvíce vyvarovat při tvorbě Ruby.

> “Chcete si užívat života nebo ne? Jestliže uděláte vaši práci rychle a zároveň je to zábava, je to dobře, je to tak? To je důvod života, Váš život je lepší. Chci řešit problémy, se kterými se setkávám v každodenním životě, když používám počítač, takže potřebuji programovat. Používáním Ruby se mohu soustředit na věci, které dělám a ne na magická pravidla programovacích jazyků, jako například public void něco něco, k tomu přidat “print hello world”. Chci pouze napsat: “print this”, nechci žádná obklopující magická slova. Chci se soustředit pouze na danou úlohu. To je hlavní myšlenka. Takže proto jsem se snažil vytvořit Ruby stručný a strohý.”
> *Yukihiro Matsumoto (Matz), autor Ruby*

## Vlastnosti

Matz ze začátku hledal jazyk, který by mu vyhovoval, naštěstí mu žádný nevyhovoval. "Chtěl jsem skriptovací jazyk, který bude výkonější než Perl a zároveň více objektový než Python." A tak se u syntaxe inspiroval především u Perlu a SmallTalku, zároveň ho také ovlivnil Eiffel či Lisp.

Vše v Ruby je objekt a to včetně primitivních datových typů, tudíž je plně objektový, mezi jeho další základní vlastnosti patří, že se jedná o silně typový jazyk a nepovolí nám v žádném případě interakci s typy, které nejsou navzájem kompatibilní, zároveň není nutno tyto typy explicitně deklarovat, jazyk sám pozná o jaký typ se jedná. Velice často se můžeme setkat s pojmem duck typing. Původ dynamického typování je u Jamese Whitcomba Rileyho, který řekl: "Pokud vidím ptáka, který chodí jako kachna, plave jako kachna a kváká jako kachna, tak o tomto ptáku tvrdím, že je to kachna."

Velice důležitou částí jazyka je schopnost metaprogrammingu, Ruby se snaží neomezovat vývojáře, a proto jsou veškeré třídy otevřené a můžeme do nich nejen přistupovat, ale mazat nebo je upravovat. To nám umožňuje naprogramovat v rámci několika minut něco, co by v jiných jazycích trvalo hodiny. Díky metaprogrammingu můžeme psát více čistý a intuitivní kód. V podstatě by se dalo říci, že nám to umožňuje psát kód, který píše další kód.

Nesmíme opomenout ani Interactive Ruby Shell, známý pod zkratkou irb, který nám umožňuje spouštět Ruby kód z příkazového řádku, dále centralizovaný package managment označovaný jako RubyGems a mnoho dalších možností jazyka, kterých je díky velké standardní knihovně opravdu mnoho.

Ruby běží na všech majoritních platformách, tento pojem nám zahrnuje Mac OS, Windows, Linux. Nejčastěji ovšem uvidíme Ruby vývojáře se zařízením od Apple. Pokud chceme využívat námi vyrobené aplikace pro komerční použití, Ruby nám v tom rozhodně bránit nebude a to z důvodu, že je úplně zdarma a to včetně jeho úpravy i jeho následné distribuce.

## Úvod do jazyka

Ruby je plně objektový programovací jazyk, to znamená, že veškeré objekty, které v  Ruby vytvoříme jsou odvozeny z nějaké třídy, mají svoje vlastnosti a metody.

### Třídy

Třída je základní stavební prvek, pokud napíšeme i pouze takto jednoduchý text "Hello world" vytvoříme tím instanci třídy `String`, napíšeme-li v Ruby nějaké číslo, vytvoříme tím instanci třídy `Integer`. Proto je třída hlavním prvkem v objektově orientovaném programování.

Vytvoření nové třídy je velice jednoduché, označuje se klíčovým slovem `class`, za ním následuje název třídy s velkým počátečním písmenem, to vše je ukončeno dalším klíčovým slovem `end` na novém řádku (kód č.1).

**Kód č.1 - Vytvoření nové třídy Person**

```ruby
class Person
end
```

Každá naše třída je instancí třídy `Class`, pokud tedy vytvoříme třídu, jakou jsem uvedl v příkladu, vytvoří se nám objekt typu třída, který se přiřadí ke globální konstantě, v našem případě `Person`.

### Metody

Jsou ve své podstatě funkce, které pracují s konkrétní třídou nebo instancí. Zápis metody je tvořen klíčovým slovem `def`, následovaný názvem metody, případně parametry. Na dalším řádku začíná tělo metody a stejně jako u třídy je metoda zakončena klíčovým slovem `end`. K metodám přistupujeme pomocí tečkové notace. Speciální metoda, která je obsažena ve všech třídách, označována klíčovým slovem `initialize` je konstruktor třídy. Ten je volán dalším klíčovým slovem new na danou metodu. V našem případě by se jednalo o `Person.new` (kód č.2), to by mělo za následek vytvoření nového objektu typu `Person`.

**Kód č. 2 - Vytvoření nového objektu person bez parametrů**

```ruby
class Person; end
Person.new
```

Metody rozlišujeme na metody bez parametru (kód č.3) a s parametrem (kód č.4). Pokud chceme, aby byla metoda s parametrem, uvedeme je za název metody a jednotlivé parametry oddělíme čárkou. Zdali uvedeme parametry v kulatých závorkách nebo ne, je jen na nás. Můžeme definovat jejich defaultní hodnotu v hlavičce metody. Další možností je využít parametr jako hash (kód č.5), kdy poté není důležité pořadí parametrů, ale klíč. Nebo blok, který vezme celý kód jako parametr (kód č.6).

**Kód č. 3 - Metoda bez parametru**

```ruby
def say_hi
  "Hello"
end
```

**Kód č. 4 - Metoda s parametrem**

```ruby
def say_hi name
  "Hello #{name}"
end
```

**Kód č. 5 - Metoda s více parametry v podobě inline hashe**

```ruby
def say_hi *args
  "Hello #{args[:name]} #{args[:surname]}"
end
```

**Kód č. 6 - Metoda s blokem**

```ruby
def say_hi name, &block
  "Hello #{name}"
  yield if block_given?
end
```

Jak už jsem zmínil, metody obsahují malá písmena, čísla a podtržítko. Dále se může u názvu metody objevit otazník, vykřičník či rovná se. Pokud metodu zakončíme otazníkem, podle konvencí by nám měla vrátit hodnotu true nebo false. Metody končící vykřičníkem obvykle označují nebezpečné metody, konkrétně by měly dané metody přepisovat objekty, na které jsou volány. Metody končící rovná se, slouží k přiřazení hodnot.

U metod rozlišujeme také jejich přístupnost a to public, private, protected (kód č.7). Pokud nespecifikujeme jinak, jsou veškeré metody v Ruby public a jsou přístupné odkudkoli. Změnu přístupnosti provedeme tak, že napíšeme o jakou přístupnost se bude dále jednat a veškeré metody níže od tohoto klíčového slova jsou dané přístupnosti.

**Kód č. 7 - Třída, která nám definuje veřejnou metodu `say_hi` a private metodu secret.**

```ruby
class Person
  def say_hi
    "Hello world"
  end
  private
    def secret
      "I'm private method"
    end
end
```

U metod nemusíme deklarovat návratový typ, metoda nám vždy vrátí výsledek posledního řádku a pokud ho nevyužijeme, automaticky ho vyhodí. Pokud jsme k výsledku v těle metody došli a nepotřebujeme v ní nadále pokračovat, vrátíme náš výsledek pomocí return.

### Datové typy

Konstanta (kód č. 8) je obecný datový typ o stále stejné hodnotě. Veškeré názvy tříd jsou konstanty, které na danou třídu odkazují, příkladem může být String. V případě, že budeme chtít hodnotu konstanty změnit, můžeme, nicméně nám Ruby vypíše varovné hlášení. Odlišují se tím, že musí začínat pouze velkým písmenem.

**Kód č. 8 - Konstanta constant**

```ruby
CONSTANT = 10
```

Symbol (kód č. 9) je v Ruby velice často používaný typ. Pokaždé, když napíšeme nějaký text, Ruby nám vytvoří nový objekt, samozřejmě i v případě, že se jedná o úplně totožný text, bude se jednat o nový objekt. Proto zde na řadu přichází symbol. Jedná se o odlehčený objekt, používaný k identifikaci a interní logice, kde neexistují dva stejnojmenné, avšak rozdílné symboly. Označují se dvojtečkou před názvem a obsahují pouze malá písmena, čísla a podtržítko.

**Kód č. 9 - Symbol my name**

```ruby
:my_name
```

Hash, (kód č. 10), jinými slovy seznam, sloužící k uchování více informací v jedné proměnné na základě klíče. Každý hash obsahuje klíč, který je vždy unikátní a má přiřazenou další hodnotu, to znamená, že může obsahovat text, nic nebo například další hash, výsledkem může být velmi rozsáhlý strom informací.

**Kód č. 10 - Hash uživatele**

```ruby
{ username: 'steve', name: 'Steve', surname: 'Jobs' }
```

Pole (kód č. 11) je obdobné jako Hash. Slouží k uchování více informací v jedné proměnné. U pole bývá zvykem, že veškerý obsah je stejného typu. Místo libovolného unikátního klíče však obsahuje číslo a stejně tak jako u jiných jazyků začíná nulou. Vše co umíme s Hashem, použijeme i u pole.

**Kód č. 11 - Pole položek, Alternativní zápis**

```ruby
['Apple', 'Strawberry', 'Pineapple']
%w(Apple Strawberry Pineapple)
```

`String` a `Fixnum` jsou jednoduché datové typy, kdy `String` obsahuje text, `Fixnum` obsahuje čísla a je dále rozdělen na `Integer` a `Float`.

### Proměnné

Jsou dalším ze základních prvků všech interpretovaných či kompilovaných jazyků a v Ruby tomu není jinak. V Ruby je ovšem nemusíme přesně definovat, určovat jejich hodnoty, přístupnosti, jak je tomu v jiných jazycích jako např. Java, kde musí být vždy vše přesně definované. Proměnná v Ruby vzniká v místě kde ji založíme a existuje až do konce její platnosti v aplikaci. V Ruby rozlišujeme více druhů proměnných, rozdělujeme je na lokální proměnné, instanční proměnné, proměnné tříd a globální proměnné.

Lokální proměnné (kód č. 12), neboli local variables jsou omezeny svojí platností a jsou určeny pouze pro lokální použití. To znamená, že je nelze používat v celé aplikaci, ale pouze v dané metodě.


**Kód č. 12 - Lokální proměná name**

```ruby
name = 'Steve'
```

Dalším typem proměnných je instanční proměnná (kód č. 13), v originálním znění instance variable. Ta je přístupná v konkrétní instanci třídy. Instanční proměnná je označena znakem `@` před názvem proměnné.

**Kód č. 13 - Instanční proměnná person**

```ruby
@person = Person.new
```

Class variable aneb proměnná třídy (kód č. 14) je daná pro celou třídu, nikoliv pouze pro instanci třídy. Problém s těmito proměnnými může nastat při multi-thread aplikaci, kdy tato proměnná není v každém threadu stejná. Tyto proměnné jsou označeny `@@`.

**Kód č. 14 - Proměnná třídy counter**

```ruby
@@counter = 123
```

Globální proměnná, (kód č. 15) global variable, je přístupná kdekoliv v aplikaci. Používání této proměnné se doporučuje pouze velice omezeně. Označuje se znakem `$` na začátku proměnné.

**Kód č. 15 - Globální proměnná**

```ruby
$server = :localhost
```

### Operátory, podmínky, cykly a blok

Operátory v Ruby se stejně tak jako ve většině ostatních jazycích rozlišují na aritmetické, porovnávací, přiřazovací, bitové, logické, ternární a rozsahové. Speciálním operátorem v Ruby je defined?. Tento operátor nám zjišťuje zdali je výraz definovaný. Většina operátorů jsou ve skutečnosti metody, proto například `a + b` je interpretováno jako `a.+(b)`, kdy je volána metoda `+` na objekt a s argumentem b.

Název						| Operátor
----------------------------|--------------------------------------
Aritmetické operátory		| `+` `-` `*` `/` `%` `**`
Porovnávací operátory		| `==` `!=` `>` `<` `>=` `<=` `<=>` `===` `.eql?` `.equal?`
Přiřazovací operátory		| `=` `+=` `-=` `*=` `/=` `%=` `**=`
Bitové operátory			| `&` `I` `^` `~` `<<` `>>`
Logické operátory			| `and` `or` `&&` `II` `!` `not`
Ternární operátor			| `?` `:`
Rozsahové operátory			| `..` `…`

Podmínky jsou obdobné jako u všech programovacích jazyků. Zajímavostí ovšem pro mnohé může být, že díky svým konvencím, kdy Matz chtěl docílit lepší struktury kódu, se v Ruby místo: `if !=` používá `unless` (kód č. 16), tato podmínka je rozhodně srozumitelnější než negace podmínky, neznamená to ovšem, že by první podmínka neexistovala. Podmínky je také možné definovat na konci řádku (kód č. 17), pokud platí pouze pro jeden řádek nebo bloku.

**Kód č. 16 - Podmínka unless**

```ruby
unless name == 'Steve'
  print "It's not Steve"
end
```

**Kód č. 17 - Podmínka if jednořádková**

```ruby
print "Active" if active?
```

Cykly jsou v Ruby méně matematické, nemusíme inkrementovat proměnnou, stačí nám například zavolat `5.times do` (kód č. 18), neboli pětkrát udělej. Pokud máme pole, projdeme ho celé metodou `each` (kód č. 19). For cyklus můžeme nahradit metodou upto, downto nebo zůstat u `for i in 1..5`.

**Kód č. 18 - Cyklus s 5 opakováním**

```ruby
5.times do
  print 'Hello world'
end
```

**Kód č. 19 - Vypiš vše z pole**

```ruby
%w(Steve Lisa John).each do |name|
  print name
end
```

### Práce s objekty

Jak jsem zmínil na začátku, nový objekt vytvoříme zavoláním `new` na naší třídu. Takto vytvořený objekt ovšem neobsahuje žádné informace. Nejjednodušší jak uschovat potřebné informace je vytvoření speciální metody `initialize` (kód č. 20), která nám umožní uložit si potřebné informace do již zmíněných instančních proměnných. U třídy `Person` můžeme uchovávat například proměnnou name.

**Kód č. 20 - Třída Person s hodnotou name**

```ruby
class Person
  def initialize name
    @name = name
  end
end
```

Tato instanční proměnná je privátní a přístup k ní má pouze daná třída, tudíž nemůžeme přistoupit k jménu uživatele. Musíme vytvořit metodu (kód č. 21), která nám jí zpřístupní, tomu pak říkáme atribut.

**Kód č. 21 - Třída Person s hodnotou name a přístupným parametrem name**

```ruby
class Person
  # …
  def name
    @name
  end
end
```

Tato metoda nám jednoduše pouze vrátí hodnotu instanční proměnné name, v jiných jazycích jsou takto označované metody jako getter. Protože vytváření těchto metod je velice časté, Ruby nám umožňuje tuto definici zkrátit a to pomocí attr_reader (kód č. 22). To nám vytvoří accessor metody přistupující k instanční proměnné stejného názvu. Pro identifikaci používáme symbol, který nám zastupuje název metody.


**Kód č. 22 - Třída Person s hodnotou name a přístupným parametrem name**

```ruby
class Person
  attr_reader :name
  # …
end
```

Změnit hodnotu však stále nebude možné, protože jsme nadefinovali pouze přístupovou metodu. Pro úpravu attributu name je zapotřebí vytvoření nové metody (kód č. 23), která nám danou hodnotu změní. V jiných jazycích je tento pojem označován jako setter.

**Kód č. 23 - Třída Person s hodnotou name a přístupným parametrem name**

```ruby
class Person
  # …
  attr_reader :name
  def name= name
    @name = name
  end
end
```

Metoda, která nám mění hodnotu je zakončená znakem `=`, to nám značí, že se jedná o metodu, která přiřazuje nějakou hodnotu. Definice těchto metod je opět velice častá, proto je v Ruby možné vytvoření pomocí `attr_writer` (kód č. 24).

**Kód č. 24 - Třída Person s hodnotou name a přístupným parametrem name**

```ruby
class Person
  # …
  attr_reader :name
  attr_writer :name
end
```

Protože v našem případě chceme jak daný atribut čist, tak zapisovat, nemusíme proto definovat jak `attr_reader` a `attr_writer`, můžeme využít `attr_accessor`, který nám zpřístupní obě metody.

### Dědičnost

Naším hlavním cílem je, aby kód zůstal čistý a neopakoval se. Snažíme vytvářet kód tak, aby byl definován pouze jednou a k tomu nám pomáhá dědičnost a mixiny. Řekněme, že ve firmě máme ředitele a asistentku, jejich pracovní náplň bude zcela odlišná, ale zajisté budou mít oba nějaké jméno a vykonávat nějakou stejnou činnost, například docházet do práce. Můžeme si ponechat naši stávající třídu Person, té se říká rodič, v původním znění parent a k ní vytvoříme další dvě třídy `Manager` a `Assistant` (kód č. 25), těmto třídám se říká potomek, v původním znění child. Tomuto procesu se říká dědičnost, v originále inheritance a je označován symbolem `<` mezi názvem potomka a rodiče.

**Kód č. 25 - Třída Manager a Assistant dědí ze třídy Person**

```ruby
class Person; end
class Manager < Person ; end
class Assistant < Person ; end
```

Zjistit rodičovskou třídu můžeme zavoláním metody `superclass`, která je definovaná ve všech třídách (kód č. 26).

**Kód č. 26 - Zjištění rodiče**

```ruby
Manager.superclass # => Person
```

Pokud budeme chtít zjistit rodiče třídy `Person`, zjistíme, že i tato třída je zděděná a to od třídy Object (pokud jsme nenadefinovali jinak). Můžeme to zkusit znovu a zjistíme, že ani tato třída však není ta hlavní a dědí ze třídy `BasicObject`, tím jsme však dosáhli úplného vrcholu.

### Moduly a Mixiny

Dalším prvkem jazyka Ruby jsou moduly. Mají dvě hlavní využití. Buď použití jako jmenný prostor nebo se využívají jako mixiny. Pokud budeme mluvit o modulu jako o jmenném prostoru (kód č. 27), využívají se k ošetření možné záměny jmen. Při tvorbě větší Ruby aplikace vytvoříme totiž spousty tříd, které spolu nemusí mít nic společného, avšak se stejně jmenují. Proto je celé zabalíme do modulu a zajistíme si tak nemožnost záměny s třídou o stejném jméně v jiném modulu.


**Kód č. 27 - Vytvoření modulu Company jako jmenný prostor se třídou Person**

```ruby
module Company
  class Person
    # ..
  end
end
```

Ke třídám uvnitř modulu se přistupuje pomocí dvojtečkové notace (kód č. 28). Na prvním místě je uveden název modulu a za ní název třídy nebo dalšího modulu.

**Kód č. 28 - Nový uživatel**

```ruby
Company::Person.new
```

Dalším využitím modulů jsou mixiny. U modulů nemůžeme tvořit instance, protože to nejsou třídy, můžeme je ovšem vložit do stávající třídy a rozšířit tím její funkci. Tento modul se stane součástí dané třídy a veškeré metody modulu můžeme využívat i v rámci té dané třídy. Takto můžeme sdílet kód mezi více třídami.

**Kód č. 29 - Třída Person s hodnotou name a přístupným parametrem name, rozšířená o mixin Described.**

```ruby
module Described
  def is
    "#{self.class.name}: #{self.name}"
  end
end
class Manager
  include Described
  attr_reader :name
  # …
end

Manager.new('Steve').is # => "Manager: Steve"
```

Budeme-li pokračovat v našem příkladu (kód č. 29), nadefinujeme si modul `Described`, který následně použijeme jako mixin. Tento modul nám obsahuje jednoduchou metodu is, která vypíše název třídy, ke které ho přiřadíme a jméno uživatele. Pokud chceme naší metodu využít jako instanční, vložíme modul do třídy pomocí `include`. Výsledek v tomto případě bude "Manager: Steve". Mixiny nepřistupují k instančním proměnným, ale přes atributy, proto jsme v našem případě definovali attribut `name`. Pokud si chceme držet nějakou proměnnou v modulu, můžeme zde instanční proměnné využít, ale je důležité zvolit unikátní název, abychom se vyvarovali kolizí s instančními proměnnými ve třídě.

### Self

Jak jsme si mohli všimnout při vytváření nového uživatele, volali jsme speciální metodu `new`. Ruby totiž rozlišuje instanční metody a metody tříd. Rozdíl mezi nimi je patrný již na první pohled. Vytvoříme-li novou instanci třídy, vytvoří se nám objekt, který spadá pod danou třídu a voláme metody, které mají spojitost přímo s konkretním objektem, zatímco metody tříd se vážou přímo na naši třídu, nikoliv na instanci třídy.


**Kód č. 30 - Třída Person s metodou say_hi jako instanční metodou a metodou třídy.**

```ruby
class Person
  attr_reader :name
  # initialize ..
  def say_hi
    "Hi #{name}"
  end
  def self.say_hi
    "Hi frend"
  end
end
```

Vytvořili jsme si třídu `Person`, s jednou instanční metodou a metodou třídy, začínající slovem `self` (kód č. 30). Tato metoda nemá přístup k instančním proměnným nebo atributům a to zcela jasného důvodu, neboť žádná instance není vytvořena. Alternativní způsob zápisu je vytvoření třídy self uvnitř třídy (kód č. 33).


**Kód č. 31 - Volání metody třídy**

```ruby
Person.say_hi # => "Hi frend"
```

**Kód č. 32 - Volání metody objektu**

```ruby
person = Person.new "Steve"
person.say_hi # => "Hi Steve"
```

**Kód č. 33 - Metoda Person s metodou třídy say_hi**

```ruby
class Person
  class << self
    def say_hi
      "Hi frend"
    end
  end
end
```

Tato skutečnost nám samozřejmě ovlivní tvorbu modulů a mixinů. Můžeme si všimnout, pokud používame nějaké Ruby IDE, že nám při tvorbě modulů dalo možnost využít šablony modulu (kód č. 34).

**Kód č. 34 - Modul Personable obsahující metody tříd a instanční metody.**

```ruby
module Personable
  module ClassMethods
  end
  module InstanceMethods
  end
  def self.included(receiver)
    receiver.extend
    receiver.send :include, InstanceMethods
  end
end
```

Na tomto příkladu je vidět, že metody, které využívají instanční proměnné uvádíme do modulu `Instance Methods`, metody tříd do modulu `Class Methods`. Metoda included nám poté zajistí to, že se nám třída rozšíří o správné metody v závislosti na tom, jakým způsobem mixin voláme. Pro využití instančních metod používáme include, pro metody tříd extend.

### Otevřené třídy

Další z vlastností Ruby je, že má otevřené třídy, do těchto tříd můžeme kdykoliv nejen přistupovat, ale zároveň je měnit. To platí u všech tříd, včetně těch, které jsou implementovány přímo v Ruby. Změny které jsme provedli se projeví jak u nových objektů, tak i u již existujících. Veškeré tyto operace jsou prováděny podle námi nově definovaného chování v rámci aplikace tam, kde tyto úpravy načítáme. 

**Kód č. 35 - Úprava chování znaku + u čísel**

```ruby
class Fixnum
  def + number
    self - number
  end
end
7+3 # => 4
```

Na příkladu (kód č. 35) je vidět, že jsme přistoupili k třídě `Fixnum` a změnili standardní chování znaku `+`, neboli sčítání a nyní nám tato metoda odčítá.

## RubyGems

Balíčkový manažer v Ruby je označován jako RubyGems, je určený k oddělení určité části aplikace, kterou chceme spravovat externě, využít ji v jiné aplikaci nebo nabídnout dále ke sdílení. Od Ruby 1.9 je součástí knihovny Ruby. Hostovat tyto balíčky je možné zdarma na stránce RubyGems.org. Je také možné spustit si vlastní hostovací stránku například s využitím GemInABox.

Používání RubyGems je velice jednoduché, obdobné funkci `apt-get`, pokud máme zkušenosti s linuxovou distribucí Debian nebo `npm`, pokud máme zkušenosti s Node.js. Využít tak můžeme například instalaci gemu příkazem `gem install rails` nebo odinstalací `gem uninstall rails`. Každý gem obsahuje takzvaný gemspec soubor, který obsahuje základní informace o gemu, jako je jeho název, verze, licence, vývojář, jaké soubory jsou v gemu použity, či jaké další gemy jsou potřeba pro správný běh našeho gem. Pokud se rozhodneme gem vypustit do světa, musíme vytvořit jeho balíček, toho docílíme pomocí `gem build mygem.gemspec` a následná distribuce pomocí `gem push mygem-1.0.0.gem`.

Můžeme také využít gemu Bundler, který nám s pomocí gemu Rake a jednoduchého příkazu `rake relase` v terminálu zabalí gem a umístí jej na RubyGems, zároveň pokud využíváme pro správu repozitářů git, vytvoří nám tag o dané verzi a odešle jej na příslušný git server.

## Vývojové cykly a knihovny

Od Ruby 1.9 je základní testovací knihovnou MiniTest, možností je i využití "hezčího" MiniTest::Spec. Tato knihovna nám slouží k testování kódu. V posledních letech se stal standardem vývoj pomocí takzvaných TDD a BDD metod. Jedná se o Test Driven Development a Behavior Driven Development.

### Test Driven Development

Je metoda, kdy prvně napíšeme test, ujistíme se, že nedopadl dobře, napíšeme co nejméně kódu, aby test prošel, refaktorujeme a pokračujeme v tomto cyklu, často se setkáme s popisem postupu "Red, green, refactor". Rozdíl mezi MiniTest a MiniTest::Spec je pouze o uživatelské přívětivosti, kdy čtením testu bychom měli pochopit jeho význam bez znalosti daného programovacího jazyka. Test spouštíme v terminálu pomocí příkazu: `ruby -Itest cesta/k/souboru/test.rb`

**Kód č. 36 - Prázdná třída Person**

```ruby
#./person.rb
class Person; end
```

**Kód č. 37 - Test třídy Person**

```ruby
#./person_test.rb
require 'minitest/spec'
require 'minitest/autorun'
require_relative 'person'
describe Person
  it "should work"
end
```

Vytvořili jsme si třídu Person (kód č. 36), která je prázdná a prázdný test (kód č. 37). Slovem `describe` označujeme co budeme testovat, `it` nám pak označuje konkrétní test, za kterým následuje stručný popis daného testu.

Od naší aplikace budeme chtít, aby bylo možné vytvořit novou osobu, která má jméno a toto jméno si můžeme zobrazit (kód č. 38).

**Kód č. 38 - Rozšíření testu o test zjišťující funkčnost atributu name**

```ruby
#…
it "should have name" do
  person = Person.new 'Steve'
  person.name.must_equal 'Steve'
end
```

Výsledek testu bude následující:

	# Running tests:
    E
    Finished tests in 0.000483s, 2070.3934 tests/s, 0.0000 assertions/s.
      1) Error:
        User#test_0001_should have name:
        ArgumentError: wrong number of arguments (1 for 0)
            user.rb:9:in `initialize'
            user.rb:9:in `new'
        user.rb:9:in `block (2 levels) in <main>'

Je zde vypsáno jaká se stala chyba a na jakém řádku. V našem konkrétním případě nemá náš konstruktor žádný parametr, ale při vytváření nové osoby ho zadáváme.

**Kód č. 39 - Doplnění třídy o požadovanou funkcionalitu**

```ruby
class Person
  def initialize name
    @name = name
  end
end
```

Vytvořili jsme si konstruktor, který nám nyní přebírá jeden parametr (kód č. 39), tím jsme opravili chybu, kterou nám test vypsal. Test ovšem opět dopadl špatně, protože jsme zapomněli definovat metodu, která nám jméno vypíše. To stejné nám řekl i test, zároveň nám ukázal, že pracujeme s třídou Person, s unikátním kódem objektu a instanční proměnnou, kde právě jméno osoby máme, ovšem nemáme k němu přístup.

	# Running tests:
    E
    Finished tests in 0.000524s, 1908.3969 tests/s, 0.0000 assertions/s.
      1) Error:
    	Person#test_0001_should have name:
    	NoMethodError: undefined method `name' for #<Person:0x007fb3ea1113e0 @name="Steve">
        	user.rb:13:in `block (2 levels) in <main>'

    1 tests, 0 assertions, 0 failures, 1 errors, 0 skips

Třídu doplníme o potřebnou metodu (kód č. 40) a opětovně spustíme test.

**Kód č. 40 - Doplnění třídy Person o požadovanou funkconalitu**

```ruby
class Person
  # initialize…
  def name
    @name
  end
end
```

Výsledek testu bude následující:

	# Running tests:
    .
    Finished tests in 0.000428s, 2336.4486 tests/s, 2336.4486 assertions/s.

    1 tests, 1 assertions, 0 failures, 0 errors, 0 skips

Test prošel, dostáváme se k dalšímu kroku, a to je refaktorování kódu. Metodu můžeme nadefinovat jednodušeji, tak proč to tak neudělat (kód č. 41). Test spustíme znovu a skončí se stejným výsledkem a můžeme si všimnout, že rychleji.


**Kód č. 41 - Zjednodušení kódu**

```ruby
class Person
  attr_reader :name
  # initialize…
end
```

Výsledek testu bude následující:

	# Running tests:
    .
    Finished tests in 0.000417s, 2398.0815 tests/s, 2398.0815 assertions/s.

    1 tests, 1 assertions, 0 failures, 0 errors, 0 skips

### Behavior Driven Development

Další rozšířenou metodou vývoje aplikace je BDD. Jedná se o obdobu TDD, ovšem se snahou o prolnutí mezi klientem, manažerem a vývojáři. Vývoj tímto způsobem funguje tak, že se při zadávání projektů vytvoří seznam funkčních požadavků, které aplikace má splňovat. Tyto požadavky jsou psané v angličtině, případně i češtině a není potřeba k jejich zvládnutí žádné technické znalosti. Následně se k těmto požadavkům napíše funkční kód a na konci vývoje musí všechny testy projít. Je v podstatě nereálné nahrazovat testování aplikace pouze tímto, neboť nemůžeme pokrýt veškeré testy. Nahradit či doplnit se takto dají integrační testy, nicméně nikoliv veškeré testy. Optimální je spojení BDD s TDD, kdy si zajistíme to, že všechna funkcionalita, kterou požaduje manažer projektu, projde v daných krocích a pro sebe a své kolegy zůstaneme u TDD.

Cucumber patří mezi nejznámější BDD a je nezávislá na platformě, tudíž není pouze pro Ruby. Další knihovna, která je použita spolu s Cucumber je Capybara, ta nám slouží k pohybování se na stránkách. Testy se označují jako features, definice požadavků jako steps.

### Test coverage

Při vývoji nějaké aplikace se dostaneme k tomu, že naše aplikace má tolik řádků kódu, že si nejsme úplně jisti, že veškerý kód máme otestovaný. Ruby 1.9 obsahuje Coverage modul, který nám kontroluje, který kód byl spuštěn, a který ne. Díky gemu simplecov si tyto informace můžeme velice hezky zobrazit (kód č. 42). Při opětovném testu je na konci uvedena cesta k vygenerovanému reportu.


**Kód č. 42 - Rozšíření testu o kontrolu otestování**

```ruby
require 'simplecov'
SimpleCov.start
```

---

Author: [Jiri Kolarik](http://jirikolarik.com) @ [We're in s.r.o.](http://werein.cz)