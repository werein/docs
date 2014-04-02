# Ruby on Rails

Jedná se o framework pro tvorbu webových aplikací napsaný v právě zmíněném jazyce Ruby. Jeho první verze byla uvedena v roce 2004. Framework vytvořil David Heinemeier Hansson při práci na projektu Basecamp. Nyní na něm pracuje tým vývojářů Rails Core Team. Co je atypické na tomto frameworku je to, že většina z nich vzniká na teoretické úrovni a je až příliš abstraktních. Naopak Rails je v podstatě vyextrahovaný framework z již hotového, výše zmíněného projektu, tudíž doopravdy reflektuje potřeby reálného světa.

> „Toto je sněhová vločka. Vaše aplikace není jedna z nich. Většina věcí, které většina lidí dělá, není nijak unikátní. Vaše potřeby nejsou nijak zvláštní.“
> *David Heinemeier Hansson*

Stejně tak jako většina webových frameworků, tak i Rails dodržuje MVC návrhovou architekturu, přesněji Model2 architekturu. Původní význam MVC je jiný než je dnes běžně používaný. Využívá vlastního ORM zvané ActiveRecord, umožňuje automatické mapování URL a automaticky využívá webového serveru WEBrick. Velice rozšířené jsou mezi Rails vývojáři vylepšení standardního HTML, CSS a JavaScriptu a to pomocí HAML, Sass a CoffeeScript.

## Filosofie

Rails se snaží dodržovat principy konvence nad konfigurací v originále Convention over Configuration (CoC) a čistého kódu, který se neopakuje, neboli Don’t Repeat Yourself (DRY).

Konvence má přednost před konfigurací. Je jeden z hlavních principů Rails. Zvyšuje produktivitu a usnadňuje tvorbu celé webové aplikace. Předpokládají co chcete udělat, i jak to chcete udělat a pokud to nedefinujete jinak, nemusíte nic nastavovat.

V případě, že vygenerujeme stránku uživatele person, vytvoří se nám automaticky model person, který získává data z tabulky people. Primární klíč je id, názvy sloupců jsou atributy objektu. Přidá se nám nastavení do routes, vytvoří se nám controller, views, a nejen to. Dokonce nám je naplní předdefinovanými metodami a views podle atributů, které jsme zadali při generování. V controller nalezneme metody index, show, new, edit, create, update, destroy. Ve view najdeme index, show, new, edit. To nám velice usnadňuje práci. V podstatě máme hotovou aplikaci, kde můžeme zobrazit všechny uživatele, jejich detail, přidat, upravit nebo je smazat.

Neopakujte se, veškerý kód v aplikaci by měl být napsaný pouze jednou a na jednom místě. Pokud bychom měli mít něco dvakrát, vyextrahujeme danou funkcionalitu do concern, což je mixin rozšířený o vzorový návrh využívaný v Rails.

Soubor/složka								|	Účel
----------------------------|---------
app/												|	Obsahuje kontrolery (controllers), modely (models) a pohledy (views)
bin/												|	Obsahuje Rails script pro spuštění aplikace, může také obsahovat další skripty.
config/											|	Konfigurace aplikace, směrování požadavků (routes.rb), definice přístupových údajů k databázi a podobně.
config.ru										|	Konfigurace pro spuštění aplikace prostřednictvím webových serverů využívajících rozhraní Rack.
db/													|	Aktuální schéma databáze a databázové migrace.
"Gemfile","Gemfile.lock"		|	Specifikace gemů (a případně jejich verzí), které vaše aplikace vyžaduje.
lib/												|	Rozšíření a doplňkové soubory vyžadované aplikací.
log/												|	Logy aplikace.
public/											|	Jediná složka, která je přístupná přes web. Obsahuje obrázky, JavaScript, stylové předpisy (CSS) a další statické soubory.
Rakefile										|	Načítá definice konzolových příkazů pro nástroj Rake (definované v Rails a v aplikaci).
README.rdoc									|	Návod k aplikaci. Slouží k popisu, co aplikace dělá, jak ji nainstalovat, nastavit, apod. Slouží též jako úvodní stránka vygenerované dokumentace.
test/												|	Testy, testovací data a ostatní nástroje pro automatizované testování aplikace.
tmp/												|	Dočasné soubory.
vendor/											|	Místo pro zdrojové soubory třetích stran. V typické Rails aplikaci jsou to například gemy a pluginy rozšiřující funkce Rails, případně též zdrojový kód Rails.

## Bundler

Pro správu gemů, které v aplikaci využíváme slouží Bundler. V hlavním kořenovém adresáři aplikace se nachází soubor Gemfile, kde je definováno jaké gemy využíváme (kód č. 43). Tento soubor se po instalaci gemů uzamkne a vytvoří se soubor Gemfile.lock. Jedná se o uzamčený Gemfile, kde jsou definovány nejen gemy, ale jejich aktuální verze či zdroje, využívané v konkrétní aplikaci. Tudíž se nemůže stát, že bychom při instalaci na server využili novější verze, které nemusejí být kompatibilní.

**Kód č. 43 - Rails ve verzi 4**

```ruby
gem 'rails', '~> 4.0.0'
```

## Příkazy

Ovládání frameworku se provádí pomocí příkazů z terminálu v adresáři aplikace. Nejčastěji používané jsou právě tyto příkazy.

Účel														|	Příkaz
--------------------------------|----------
Vytvoření nové aplikace					|	rails new
IRB pro Rails aplikaci					|	rails console
Ovládání databáze								|	rails dbconsole
Generátor/instalátor komponent	|	rails generate
Maže kompomenty									|	rails destroy
Spouští lokální server					|	rails server
Spouští metody									|	rails runner


### Rake

Účel														|	Příkaz
--------------------------------|----------
Vytvoření databáze							|	rake db:create
Migrace databáze								|	rake db:migrate
Vrácení databáze o krok zpět		|	rake db:rollback
Kompilace assets								|	rake assets:precompile

Další metodou spouštění jednotlivých úloh je rake. Jedná se o obdobu make, avšak pro Ruby, tudíž Rake. Tento gem nám umožňuje jednoduše spouštět jednotlivé úlohy pomocí příkazového řádku, stejně tak jako příkaz rails. Tyto soubory mají koncovku .rake a je možné si definovat vlastní úlohy. Rails tento gem využívá pro práci s databází, spouštění testů, výpisu dostupných url adres, generování dokumentace nebo komprimování assets.


## Základní principy Ruby on Rails

Rails využívá MVC, t.j. architektura, která odděluje řídící logiku od uživatelského rozhraní a datového modelu aplikace. To nám umožňuje lépe rozdělit strukturu webové aplikace. Modifikace některé z částí má následně minimální vliv na ostatní.

Vytvořit model, controller nebo view a dokonce assets s namapováním url můžeme pomocí příkazů Rails. Pro vytvoření kompletní šablony můžeme využít scaffold generátoru, který vytvoří vše naráz. V následujících příkladech využijeme vytvoření modelu Person s atributem name.

**Scaffold generátor**

	rails generate scaffold person name:string —spec

### Model

Obsahuje logiku aplikace. Může reprezentovat objekt či provádět určitou operaci, kterou potřebujeme vykonat. Pokud chceme vytvořit pouze model pomocí generátoru, uvedeme do příkazového řádku rails generete model, název modelu následovaného attributy a datovým typem.

Umístění modelu se nachází v adresáři app/models (kód č. 44), generátor zároveň vytváří migrační tabulku (kód č. 45), protože předpokládá navázanost na databázi, testovací soubor (kód č. 46) a dědí z modulu ActiveRecord a třídy Base. Můžeme si všimnout, že vytvořený model je pojmenován Person, tabulka v databázi ovšem People.

**Generátor pro model**

	rails generate model person name:string —spec


**Kód č. 44 - Model Person**

```ruby
class Person < ActiveRecord::Base
end
```


**Kód č. 45 - Migrace databáze**

```ruby
class CreatePeople < ActiveRecord::Migration
  def change
    create_table :people do |t|
      t.string :name
      t.timestamps
    end
  end
end
```

**Kód č. 46 - Test modelu**

```ruby
require "test_helper"
describe Person do
  before do
    @person = Person.new
  end
  it "must be valid" do
    @person.valid?.must_equal true
  end
end
```

### Controller

Se stará o propojení komponent. Přijímá požadavky, volá požadované metody a určuje co uživateli zobrazí. Pokud chceme vytvořit controller pomocí generátoru, za rails generete uvedeme controller, název v množném čísle, následován akcemi index/show atd. Generátor nám také vytvoří příslušné Stylesheet, JavaScript a view soubory.

Controller je umístěn v adresáři app/controllers a jeho název. Název musí být uveden v množném čísle oproti jednotnému číslu modelu, protože pracujeme s více objekty.

**Generátor pro controller**

	rails generate model people index show —spec

Námi vygenerovaná třída dědí z ApplicationController. Před metodami show, edit, update a destroy, které nám vytvořil generátor, stojí za zmínku to, že se provede metoda set_person (kód č. 47), která nastaví uživatele podle parametru ID do instanční proměnné person.


**Kód č. 47 - Metoda set_person**

```ruby
class PeopleController < ApplicationController
  before_action :set_person, only: [:show, :edit, :update, :destroy]
  private
	# Use callbacks to share common setup or constraints between actions.
    def set_person
      @person = Person.find(params[:id])
    end
end
```

Stejně tak jak metoda předcházející, je v privátní části metoda person_params (kód č. 48), která nám načítá parametry a povolí nám pouze určité hodnoty. Tyto dvě metody jsou využívány od Rails 4.


**Kód č. 48 - Metoda person_params**

```ruby
class PeopleController < ApplicationController
  # …
  private
    # Never trust parameters from the scary internet, only allow the white list through.
    def person_params
      params.require(:person).permit(:name)
    end
end
```

K dalším vygenerovaným metodám patří metoda index, která načítá veškeré osoby. Metoda show, která nemusí obsahovat již žádný kód, vystačí si totiž s instanční proměnou nadefinovanou z set_person metody. Metoda new nám vytvoří proměnnou s instancí nové osoby. Metoda edit je stejná jako metoda show. Metoda create vytváří novou osobu, za pomoci post parametrů, v případě úspěchu jsme přesměrování na danou osobu, v případě neúspěchu vráceni zpět k vytvoření nové osoby. Metoda update aktualizuje osobu a je prováděna obdobným způsobem jako vytváření. Poslední metoda je metoda destroy, která jak už název napovídá maže osobu.

### View

Se stará o interakci s uživatelem. Slouží k zobrazení výsledků, ať už se jedná o HTML kód nebo například XML soubor a následnou další komunikaci zpět k aplikaci. Rails v základu využívají html erb, kdy je Ruby kód vložen do HTML kódu. Takovéto HTML se pak velmi podobá PHP a není zrovna přehledné. Velice často proto Rails vývojáři využívají HAML - HTML Abstract Markup Language.

Základní soubor, kde máme celé rozložení webu, který je vytvořený rovnou s novou aplikací se nachází v layouts/application.html.haml. Pokud však chceme zobrazovat stránky, musíme k nim vytvořit odpovídající view a ten se nám bude zobrazovat do části webu, kde máme tag: "yield" . Do těchto souborů zapisujeme HAML a Ruby kód. U Ruby kódu rozlišujeme dvě možnosti, zdali se jedná o funkční kód, který nechceme, aby byl vidět, od zobrazovaného kódu. Funkční kód je označován pomlčkou, zobrazovací kód pomocí znaku rovná se. Ve view využíváme instančních proměnných definovaných v controller.

### Assets

Slouží k ukládání stylesheets, javascriptů a obrázků, podle toho odpovídají i názvy podsložek. Pro naše soubory se používá adresář app, pro externí soubory třetích stran vytvoříme v kořenovém adresáři složku vendor/assets, která bude mít stejnou strukturu jako app/assets. Při komprimování pro produkční prostředí se vytváří unikátní digest název pro daný soubor, který se v případě změny souboru změní také, a to následně umožní využití nového souboru na webu, nikoliv cache starého.

Hlavní layout je pojmenován application, ten je načítán v hlavičce a v případě javascriptu patičce webu. Do těchto souboru načítáme jak naše stylesheets a javascripts, tak externí knihovny z vendor/assets. Místo standardního css je v Rails využíváné SCSS, případně Sass a místo JavaScript se používá CoffeeScript.

#### HAML

Je značkovací jazyk, který umožňuje čistě a jednoduše vytvářet HTML bez použití inline funkčního kódu, jak je to u HTML erb. Hlavní principy HAML jsou vytvoření hezkého kódu, který se nesmí opakovat, bude správně odrážkovaný a lehce pochopitelný (kód č. 49).


**Kód č. 49 - HTML vs HAML**

```html
<section class="container">
  <h1><%= post.title %></h1>
  <h2><%= post.subtitle %></h2>
  <div class="content">
    <%= post.content %>
  </div>
</section>
```

**HAML**

```haml
%section.container
  %h1= post.title
  %h2= post.subtitle
  .content= post.content
```

#### SASS

Je zkratka pro Syntatically Awesome Style Sheets. Veškeré Sass jsou komprimované do čístého CSS, tudíž funguje ve všech prohlížečích jako kdybychom Sass nevyužily. SCSS je zpětně kompatibilní s CSS, tudíž veškerý kód z CSS funguje i zde. Sass je již bez závorek, středníků a musí být správně odsazený. Mezi hlavní přednosti Sass patří proměnné, vnoření, partials, mixini, dědění, operátory a cykly.

##### Proměnné

Stejně tak jako v programovacích jazycích můžeme využívat proměnné, které označujeme znakem $ na začátku. Do těchto proměnných můžeme ukládat jak barvy, velikosti, tak vše, co bychom chtěli použít častěji (kód č. 50). Následná změna barevného schématu je záležitostí úpravy jedné proměnné.

**Kód č. 50 - Sass VS CSS**

```css
body {
  color: rgb(252,252,252);
  font-size: 1.5em;
}
```

**Sass**

```sass
$color: rgb(252,252,252)
$font-size: 1.5em
body
  color: $color
  font-size: $font-size
```

##### Vnoření
Organizace klasického CSS je poměrně nepřehledná, naopak Sass nám umožňuje vnořit do sebe více definicí (kód č. 51).

**Kód č. 51 - Sass VS CSS**

```css
nav ul {
  margin: 0;
}
nav ul li {
  color: rgb(252,252,252);
}
```

**Sass**

```sass
nav
  ul
    margin: 0
    li
      color: $color
```

#### Partials
Nám umožňuje modularizovat CSS a oddělit například definice proměnných na jiné místo (kód č. 52), které následně načteme (kód č. 53). Partials se označují podtržítka před názvem.

**Kód č. 52- Partial s definicemi barev**

```sass
/* _colors.sass */
$color: rgb(252,252,252)
```

**Kód č. 53 - Použití**

```ruby
@import colors
```

##### Mixiny a dědění

Mixiny umožňují vytvořit set CSS deklarací (kód č. 54) a ty následně vložit do sekce, kde je potřebujeme (kód č. 55). Využít můžeme i parametrů podle kterých se daná deklarace přizpůsobí. Další možností je také dědění (kód č. 56). Velmi rozšířený je Compass, kde už jsou veškeré definice pro CSS3 již hotové. V Sass můžeme dokonce dědit, rozšiřovat, od jiných tříd nebo id. Tyto metody nám umožňují psát kód tak, aby se neopakoval, stejně tak jako je to u principů Ruby nebo Rails.

**Kód č. 54 - Vytvoření mixinu**

```sass
=border-radius($radius)
  -webkit-border-radius: $radius
  border-radius: $radius
```

**Kód č. 55 - Použití mixinu**

```sass
.box
  +border-radius(10px)
```

**Kód č. 56 - Dědění**

```sass
.message
  border: 1px solid #ccc
.success
  @extend .message
  border-color: green
```

##### Operátory a cykly

Nesmíme opomenout ani operátory, v Sass je možné provádět základní matematické operace jako je +, -, /, *. Můžeme také vytvořit pole, které následně budeme procházet a na základě informací v poli vytvářet nové deklarace (kód č. 57).

**Kód č. 57 - Pole 3 barev, z kterých jsou následně vytvořeny 3 třídy s danými barvami**

```sass
$colors: rgb(27, 163, 223), rgb(70, 79, 159), rgb(225, 28, 126)

@for $i from 1 through length($colors)
  $c: nth($colors, $i)
  .post-#{$i}
    background: $c
```

### CoffeeScript

Je programovací jazyk, který je kompilován do JavaScriptu. Snaží se vyzdvihnout dobré části JavaScriptu a udělat ho jednodušší. Syntaxe jazyka je podobná Ruby, nemáme zde středníky, složené závorky nebo nemusíme deklarovat proměnné. Hlavní pravidlo CoffeeScriptu: “Je to pouze JavaScript”. 

Porovnání CoffeeScriptu jako první s JavaScriptem jako druhý.

```javascript
var cubes, list, math, num, number, opposite, race, square,
  __slice = [].slice;

number = 42;

opposite = true;

if (opposite) {
  number = -42;
}

square = function(x) {
  return x * x;
};

list = [1, 2, 3, 4, 5];

math = {
  root: Math.sqrt,
  square: square,
  cube: function(x) {
    return x * square(x);
  }
};

race = function() {
  var runners, winner;
  winner = arguments[0], runners = 2 <= arguments.length ? __slice.call(arguments, 1) : [];
  return print(winner, runners);
};

if (typeof elvis !== "undefined" && elvis !== null) {
  alert("I knew it!");
}

cubes = (function() {
  var _i, _len, _results;
  _results = [];
  for (_i = 0, _len = list.length; _i < _len; _i++) {
    num = list[_i];
    _results.push(math.cube(num));
  }
  return _results;
})();
```

**CoffeeScript**

```coffee
# Assignment:
number   = 42
opposite = true

# Conditions:
number = -42 if opposite

# Functions:
square = (x) -> x * x

# Arrays:
list = [1, 2, 3, 4, 5]

# Objects:
math =
  root:   Math.sqrt
  square: square
  cube:   (x) -> x * square x

# Splats:
race = (winner, runners...) ->
  print winner, runners

# Existence:
alert "I knew it!" if elvis?

# Array comprehensions:
cubes = (math.cube num for num in list)
```

## ORM

ORM je zkratka pro Object-Related-Mapping neboli objektově relační mapování. Rails jako ORM využívá ActiveRecord, který mapuje databázové tabulky a následně převádí na třídy, řádky na jednotlivé objekty a sloupce na jejich atributy. Zároveň obsahuje nástroj pro práci s daty jako například čtení, zápis a další nástroje, které umožňují propojovat tabulky mezi sebou. Každý model má nadefinované metody pro práci s daty. Hlavními přednostmi jsou již zmíněné mapování databázové tabulky na objekt, asociace, validace, callbacks, dědění, agregace, transakce a reflekce. V základu je kompatibilní s adaptéry MySQL, PostreSQL a SQLite3.

Associate mezi objekty (kód č. 58) nám určují vzájemnou závislost objektů mezi sebou. V Rails se používá označení has_many, has_one, belogns_to, has_and_belongs_to_many, kde již z názvu je zřetelné jaký vztah mezi objekty deklarují.

**Kód č. 58 - Model Person s asociací na projects a company**

```ruby
class Person < ActiveRecord::Base
  has_and_belongs_to_many :projects
  belongs_to :company
end
```

Validaci (kód č. 59), kde na základě podmínek je či není umožněno uložení záznamu do databáze. 

**Kód č. 59 - Person vždý musí mít přiřazenou roli**

```ruby
class Person < ActiveRecord::Base
  # …
  validates :roles, presence: true
end
```

Callbacks (kód č. 60) nám umožňují zařadit metodu do cyklu událostí v závislosti na tom, v jaké fázy cyklu se nacházíme.

**Kód č. 60 - Před validací se provede metoda set_role**

```ruby
class Person < ActiveRecord::Base
  # …
  before_validation :set_role
end
```

## Routes

Nám mapují URL na určenou činnost systému na základě definice v konfiguračním souboru routes. Obsah tohoto souboru je zpracováván od shora dolů, čím je více nahoře, tím má větší důležitost. Využít zde můžeme standardních get/post metod nebo využít speciálního resources (kód č. 61), který nám automaticky vytvoří adresy ke všem základním adresám uvedených v controller.


**Kód č. 61 - Mapování people**

```ruby
resources :people
```

HTTP				|	Adresa						|	Akce		|	Použití
------------|-------------------|---------|-------------
GET					|	/people						|	index		|	zobrazí všechny osoby
GET					|	/people/new				|	new			|	zobrazí formulář pro vytvoření osoby
POST				|	/people						|	create	|	vytvoří novou osobu
GET					|	/people/:id				|	show		|	zobrazí konkrétní osobu
GET					|	/people/:id/edit	|	edit		|	zobrazí formulář pro úpravu osoby
PATCH/PUT		|	/people/:id				|	update	|	aktualizuje konkrétní osobu
DELETE			|	/people/:id				|	destroy	|	smaže konkrétní osobu

Zároveň pak můžeme využit url helperů, které nám generují url na základě jména helperu a objektu.

HTTP			|	Adresa						|	Akce		|	URL Helper
----------|-------------------|---------|-------------
GET				|	/people						|	index		|	posts_path
GET				|	/people/new				|	new			|	new_person_path
POST			|	/people						|	create	|	people_path
GET				|	/people/:id				|	show		|	person_path(:id)
GET				|	/people/:id/edit	|	edit		|	edit_person_path(:id)
PATCH/PUT	|	/people/:id				|	update	|	person_path(:id)
DELETE		|	/people/:id				|	destroy	|	person_path(:id)

## Engine

Je miniaturní aplikace, která rozšiřuje funkcionalitu hlavní aplikace. Rails je v podstatě také engine. U enginů rozslišujeme především to, zdali je mountable či není. Pokud využijeme mountable engine, izoluje nám to veškerou funkconalitu od hlavní aplikace, vytvoří jmenný prostor pro celý engine, přidá prefix do tabulek databáze, namapuje url adresy, které následně můžeme připojit do své aplikace. Naopak full engine nám nijak aplikaci neizoluje a je přímo dostupná pro hlavní aplikaci. Zde může nastat problém s kolizí jmen. Hlavní aplikace má vždy přednost před enginem, který musí vždy poslechnout hlavní aplikaci.

Využití mountable engine se hodí především pro miniaturní aplikace, kterými hlavní aplikaci rozšiřujeme o kompletní aplikaci, Mezi její zástupce patří RailsAdmin, který nám vytváří administrační rozhraní nebo Devise, jedná se o autorizační rozhraní.

Pokud chceme vytvořit gem, který má pouze nějaké assets, které chceme, aby byly dostupné i v hlavní aplikaci jako například gem x-editable-rails, který nám umožňuje vzdáleně upravovat záznamy. Nemusíme vytvářet kompletní mountable engine. Stačí nám vytvořit gem a v něm třídu, která dědí z Rails::Engine nebo full engine a nepotřebné soubory a složky smazat.

## Deploy

Po vytvoření aplikace je vždy zapotřebí ji nasadit v produkčním prostředí, nejčastěji se pro správu projektu využívá Git. Ten nám umožňuje sdílet aplikaci s ostatními členy, kteří se podílejí na vývoji, přidávat nové funkce a mít přehled o tom, co jsme vytvořili nového. Nejčastější formou umístění aplikace na server je deploy pomocí gemu Capistrano. Jedná se o aplikaci, která nám umožňuje nakonfigurovat si parametry hostingu, postup co vše se má provést a následně přes SSH nahrát na server.

### Nezapomínat na errory

I přes všechny testy, které jsme na aplikaci provedli, nesmíme zapomenout na to, že i tak se nám může na stránkách vyskytnout problém. Všechen pohyb na stránkách je logován do souboru log/production.log, nicméně hledat v tomto souboru není nic příjemného. Využít tak můžeme aplikace airbrake.com nebo alternativy Errbit, která je zdarma a je kompatibilní s gemem, který airbrake, který nám chyby zachycuje, ukládá na server a případně nás upozorní na chybu, která vznikla.

---

Author: [Jiri Kolarik](http://jirikolarik.com) @ [We're in s.r.o.](http://werein.cz)