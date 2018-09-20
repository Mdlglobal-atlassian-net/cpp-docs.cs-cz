---
title: Deklarace objektu referenční třídy CLR | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- types [C++], reference types
- reference types, CLR
ms.assetid: 6d64f746-3715-4948-ada3-88859f4150e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f3e8ec6407e12d0c26331d45dc1659277feed016
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444577"
---
# <a name="declaration-of-a-clr-reference-class-object"></a>Deklarace objektu referenční třídy CLR

Syntaxe pro deklaraci a vytvořit instanci objektu typu referenční třídy změnil ze spravovaného rozšíření jazyka C++ pro Visual C++.

Ve spravovaných rozšíření objekt typu referenční třída je deklarována pomocí syntaxe ISO-C++ ukazatele s nepovinným použitím `__gc` – klíčové slovo doleva na hvězdičku (`*`). Například tady jsou různé odkaz deklarace objektů typu třídy v rámci spravovaných rozšíření syntaxe:

```
public __gc class Form1 : public System::Windows::Forms::Form {
private:
   System::ComponentModel::Container __gc *components;
   Button __gc *button1;
   DataGrid __gc *myDataGrid;
   DataSet __gc *myDataSet;

   void PrintValues( Array* myArr ) {
      System::Collections::IEnumerator* myEnumerator =
         myArr->GetEnumerator();

      Array *localArray;
      myArr->Copy(myArr, localArray, myArr->Length);
   }
};
```

V nové syntaxi deklarace objektu referenční třídy typu pomocí nový token deklarativní (`^`) říká formálně *sledovací popisovač* a neformálně jako *hat*. (Přídavného jména sledování znamená, že typ odkazu umístěná v haldě modulu CLR a proto může transparentně přesouvat umístění během komprimace haldy uvolňování paměti. Sledovací popisovač je transparentně aktualizovat za běhu. Jsou dvě podobné koncepce *sledovací odkaz* (`%`) a *vnitřní ukazatel* (`interior_ptr<>`) popsané v [Sémantika typu hodnoty](../dotnet/value-type-semantics.md).

Hlavní důvody přesunutí deklarativní syntaxe od opakované použití syntaxe ukazatel ISO-C++ jsou následující:

- Použití syntaxe ukazatel neumožňuje přetížené operátory přímo použít odkaz na objekt. Místo toho jeden měl volat operátor pomocí interní název, například `rV1->op_Addition(rV2)` místo mnohem intuitivnější `rV1+rV2`.

- Počet operací ukazatele, například přetypování a aritmetika ukazatele, není povolena pro objekty uložené ve uvolnění paměti haldě. Pojem sledovací popisovač lepší zachycuje povahu odkazový typ CLR.

`__gc` Modifikátor sledovací popisovač není nutný a není podporována. Použití samotného objektu se změnily. stále přistupuje prostřednictvím operátoru výběru členů ukazatelů členů (`->`). Tady je příklad, předchozí ukázce kódu spravovaného rozšíření přeložit na novou syntaxi:

```
public ref class Form1: public System::Windows::Forms::Form {
private:
   System::ComponentModel::Container^ components;
   Button^ button1;
   DataGrid^ myDataGrid;
   DataSet^ myDataSet;

   void PrintValues( Array^ myArr ) {
      System::Collections::IEnumerator^ myEnumerator =
         myArr->GetEnumerator();

      Array ^localArray;
      myArr->Copy(myArr, localArray, myArr->Length);   }
};
```

## <a name="dynamic-allocation-of-an-object-on-the-clr-heap"></a>Dynamické přidělení objektu na haldě modulu CLR

Ve spravovaných rozšíření existence dvou `new` byla z velké části transparentní výrazy pro přidělení mezi nativní a spravované haldy. V téměř všech případech je možné použít kontext k určení, jestli se má přidělit paměti z haldy nativní nebo spravovaný kompilátor. Například

```
Button *button1 = new Button; // OK: managed heap
int *pi1 = new int;           // OK: native heap
Int32 *pi2 = new Int32;       // OK: managed heap
```

Pokud nechcete, aby přidělení haldy, můžete nasměrovat kompilátoru buď `__gc` nebo `__nogc` – klíčové slovo. V nové syntaxi samostatné povaze dvou nových výrazů je explicitní po zavedení služby `gcnew` – klíčové slovo. Například předchozí tři deklarace vypadat takto v nové syntaxi:

```
Button^ button1 = gcnew Button;        // OK: managed heap
int * pi1 = new int;                   // OK: native heap
Int32^ pi2 = gcnew Int32; // OK: managed heap
```

Tady je inicializace spravovaných rozšíření `Form1` členy deklarované v předchozí části:

```
void InitializeComponent() {
   components = new System::ComponentModel::Container();
   button1 = new System::Windows::Forms::Button();
   myDataGrid = new DataGrid();

   button1->Click +=
      new System::EventHandler(this, &Form1::button1_Click);
}
```

Zde je stejný inicializace přepracována novou syntaxi. Všimněte si, že stříška není vyžadován pro typu odkazu, pokud je cílem `gcnew` výrazu.

```
void InitializeComponent() {
   components = gcnew System::ComponentModel::Container;
   button1 = gcnew System::Windows::Forms::Button;
   myDataGrid = gcnew DataGrid;

   button1->Click +=
      gcnew System::EventHandler( this, &Form1::button1_Click );
}
```

## <a name="a-tracking-reference-to-no-object"></a>Odkaz sledování na žádný objekt.

V nové syntaxi `0` již představuje adresu hodnotu null, ale je považován za celé číslo, stejně jako `1`, `10`, nebo `100`. Nový token speciální představuje pro sledovací odkaz hodnotu null. Například ve spravovaných rozšíření jsme inicializujte odkazový typ k vyřešení žádný objekt takto:

```
// OK: we set obj to refer to no object
Object * obj = 0;

// Error: no implicit boxing
Object * obj2 = 1;
```

V nové syntaxi, zadejte na jakákoli inicializace nebo přiřazení hodnoty `Object` způsobí, že implicitního zabalení tohoto typu hodnoty. V nové syntaxi obě `obj` a `obj2` jsou inicializovány na zákazníky a vyřešené zabalený Int32 objekty obsahující hodnoty 0 a 1, v uvedeném pořadí. Příklad:

```
// causes the implicit boxing of both 0 and 1
Object ^ obj = 0;
Object ^ obj2 = 1;
```

Proto, aby bylo možné provést explicitní inicializace, přiřazení a porovnání sledovací popisovač null, použijte new – klíčové slovo `nullptr`.  Správné revize původní příkladu by měl vypadat takto:

```
// OK: we set obj to refer to no object
Object ^ obj = nullptr;

// OK: we initialize obj2 to a Int32^
Object ^ obj2 = 1;
```

To komplikuje poněkud portování existující kód do nové syntaxe. Zvažte například následující deklaraci třídy hodnoty:

```
__value struct Holder {
   Holder( Continuation* c, Sexpr* v ) {
      cont = c;
      value = v;
      args = 0;
      env = 0;
   }

private:
   Continuation* cont;
   Sexpr * value;
   Environment* env;
   Sexpr * args __gc [];
};
```

Tady obě `args` a `env` jsou odkazové typy CLR. Inicializace tyto dva členy k `0` v konstruktoru nemůže zůstat beze změny při přechodu na novou syntaxi. Místo toho musí být změněn na `nullptr`:

```
value struct Holder {
   Holder( Continuation^ c, Sexpr^ v )
   {
      cont = c;
      value = v;
      args = nullptr;
      env = nullptr;
   }

private:
   Continuation^ cont;
   Sexpr^ value;
   Environment^ env;
   array<Sexpr^>^ args;
};
```

Obdobně testování těchto členů jejich porovnání s `0` nutné změnit také pro porovnání členy `nullptr`. Zde je spravovaných rozšíření syntaxe:

```
Sexpr * Loop (Sexpr* input) {
   value = 0;
   Holder holder = Interpret(this, input, env);

   while (holder.cont != 0) {
      if (holder.env != 0) {
         holder=Interpret(holder.cont,holder.value,holder.env);
      }
      else if (holder.args != 0) {
         holder =
         holder.value->closure()->
         apply(holder.cont,holder.args);
      }
   }

   return value;
}
```

Tady je revize, nahraďte každou `0` instanci s `nullptr`. Nástroj pro překladatele pomáhá v této transformace díky automatizaci mnoha, není-li využívají všechny výskyty, včetně `NULL` – makro.

```
Sexpr ^ Loop (Sexpr^ input) {
   value = nullptr;
   Holder holder = Interpret(this, input, env);

   while ( holder.cont != nullptr ) {
      if ( holder.env != nullptr ) {
         holder=Interpret(holder.cont,holder.value,holder.env);
      }
      else if (holder.args != nullptr ) {
         holder =
         holder.value->closure()->
         apply(holder.cont,holder.args);
      }
   }

   return value;
}
```

`nullptr` Je převést na libovolný typ popisovače ukazatel nebo sledování, ale není povýšen na celočíselného typu. Například v následující sadě inicializace `nullptr` je platný jenom jako počáteční hodnotu pro první dvě.

```
// OK: we set obj and pstr to refer to no object
Object^ obj = nullptr;
char*   pstr = nullptr; // 0 would also work here

// Error: no conversion of nullptr to 0
int ival = nullptr;
```

Podobně daný přetížené sadu například následujícími metodami:

```
void f( Object^ ); // (1)
void f( char* );   // (2)
void f( int );     // (3)
```

Vyvolání s `nullptr` literálu, jako je například následující příkaz,

```
// Error: ambiguous: matches (1) and (2)
f(  nullptr );
```

je nejednoznačný vzhledem k tomu, `nullptr` odpovídá sledovací popisovač a ukazatel a neexistuje žádná priorita jeden typ z nich. (Tato situace vyžaduje explicitní přetypování. aby bylo možné rozlišit.)

Vyvolání s `0` přesně odpovídá instanci (3):

```
// OK: matches (3)
f( 0 );
```

protože `0` je typu integer. Byly `f(int)` není k dispozici, volání jednoznačně odpovídají `f(char*)` pomocí standardního převodu. Pravidla pro porovnávání dávají přednost přesnou shodu přes standardní převod. Standardní převod chybí přesná shoda, je dána přednost implicitního zabalení typu hodnoty. To je důvod, proč nedochází k nejednoznačnosti.

## <a name="see-also"></a>Viz také

[Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)<br/>
[Třídy a struktury](../windows/classes-and-structs-cpp-component-extensions.md)<br/>
[Operátor popisovače objektu (^)](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)<br/>
[nullptr](../windows/nullptr-cpp-component-extensions.md)