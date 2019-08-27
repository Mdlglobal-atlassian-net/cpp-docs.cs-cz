---
title: Destruktory (C++)
ms.date: 07/20/2019
helpviewer_keywords:
- objects [C++], destroying
- destructors, C++
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
ms.openlocfilehash: 1e1190f49c7ccf5c312172f265d32a4b855bd878
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060135"
---
# <a name="destructors-c"></a>Destruktory (C++)

Destruktor je členská funkce, která je vyvolána automaticky, když se objekt dostane mimo rozsah nebo je explicitně zničen voláním metody **Delete**. Destruktor má stejný název jako třída a předchází vlnovkou (`~`). Například destruktor třídy `String` je deklarován jako: `~String()`.

Pokud nedefinujete destruktor, kompilátor nabídne výchozí hodnotu. pro mnoho tříd je to dostačující. Je nutné definovat vlastní destruktor, pokud Třída ukládá popisovače na systémové prostředky, které je třeba uvolnit, nebo ukazatele, které vlastní paměť, na kterou odkazuje.

Zvažte následující deklaraci třídy `String`:

```cpp
// spec1_destructors.cpp
#include <string>

class String {
public:
   String( char *ch );  // Declare constructor
   ~String();           //  and destructor.
private:
   char    *_text;
   size_t  sizeOfText;
};

// Define the constructor.
String::String( char *ch ) {
   sizeOfText = strlen( ch ) + 1;

   // Dynamically allocate the correct amount of memory.
   _text = new char[ sizeOfText ];

   // If the allocation succeeds, copy the initialization string.
   if( _text )
      strcpy_s( _text, sizeOfText, ch );
}

// Define the destructor.
String::~String() {
   // Deallocate the memory that was previously reserved
   //  for this string.
   delete[] _text;
}

int main() {
   String str("The piper in the glen...");
}
```

V předchozím příkladu destruktor `String::~String` používá operátor **Delete** k navrácení dynamicky přiděleného prostoru pro textové úložiště.

## <a name="declaring-destructors"></a>Deklarace destruktorů

Destruktory jsou funkce se stejným názvem, jako má třída, ale předchází vlnovku (`~`).

Deklarace destruktorů se řídí několika pravidly. Destruktory:

- Nepřebírají argumenty.

- Nevracet hodnotu (nebo **void**).

- Nelze deklarovat jako **const**, **volatile**nebo **static**. Lze je však vyvolat pro zničení objektů deklarovaných jako const,volatilenebo **static**.

- Lze deklarovat jako **Virtual**. Použitím virtuálních destruktorů lze zničit objekty bez znalosti jejich typu. Správný destruktor objektu je vyvolán pomocí mechanismu virtuální funkce. Destruktory lze také deklarovat jako čistě virtuální funkce pro abstraktní třídy.

## <a name="using-destructors"></a>Použití destruktorů

Destruktory jsou zavolány, pokud dojde k jedné z následujících událostí:

- Místní (automatický) objekt s rozsahem bloku se dostane mimo rozsah.

- Objekt přidělený pomocí operátoru **New** se explicitně oddělí pomocí **Delete**.

- Doba života dočasného objektu skončí.

- Program se ukončí a globální nebo statické objekty existují.

- Destruktor je explicitně zavolán pomocí plně kvalifikovaného názvu funkce destruktoru.

Destruktory mohou volně volat členské funkce třídy a přistupovat k datům člena třídy.

Existují dvě omezení pro použití destruktorů:

- Nemůžete získat jeho adresu.

- Odvozené třídy nedědí destruktor své základní třídy.

## <a name="order-of-destruction"></a>Pořadí zničení

V případě, že se objekt dostane mimo rozsah nebo je odstraněn, sekvence událostí v jeho úplném zničení je následující:

1. Je volán destruktor třídy a text funkce destruktoru je proveden.

1. Destruktory pro nestatické členské objekty jsou volány v obráceném pořadí, ve kterém jsou uvedeny v deklaraci třídy. Volitelný seznam inicializace členů použitý při vytváření těchto členů nemá vliv na pořadí konstrukce nebo zničení.

1. Destruktory pro nevirtuální základní třídy jsou volány v obráceném pořadí deklarace.

1. Destruktory pro virtuální základní třídy jsou volány v obráceném pořadí deklarace.

```cpp
// order_of_destruction.cpp
#include <cstdio>

struct A1      { virtual ~A1() { printf("A1 dtor\n"); } };
struct A2 : A1 { virtual ~A2() { printf("A2 dtor\n"); } };
struct A3 : A2 { virtual ~A3() { printf("A3 dtor\n"); } };

struct B1      { ~B1() { printf("B1 dtor\n"); } };
struct B2 : B1 { ~B2() { printf("B2 dtor\n"); } };
struct B3 : B2 { ~B3() { printf("B3 dtor\n"); } };

int main() {
   A1 * a = new A3;
   delete a;
   printf("\n");

   B1 * b = new B3;
   delete b;
   printf("\n");

   B3 * b2 = new B3;
   delete b2;
}

Output: A3 dtor
A2 dtor
A1 dtor

B1 dtor

B3 dtor
B2 dtor
B1 dtor
```

### <a name="virtual-base-classes"></a>Virtuální základní třídy

Destruktory pro virtuální základní třídy jsou volány v obráceném pořadí jejich vzhledu v řízeném grafu acyklického (hloubka – první, zleva doprava, postorder procházení). Následující obrázek znázorňuje graf dědičnosti.

![Graf dědičnosti, který zobrazuje virtuální základní třídy](../cpp/media/vc392j1.gif "Graf dědičnosti, který zobrazuje virtuální základní třídy") <br/>
Graf dědičnosti, který zobrazuje virtuální základní třídy

Následuje seznam hlav třídy pro třídy zobrazené na obrázku.

```cpp
class A
class B
class C : virtual public A, virtual public B
class D : virtual public A, virtual public B
class E : public C, public D, virtual public B
```

Chcete-li určit pořadí zničení virtuálních základních tříd objektu typu `E`, kompilátor vytvoří seznam pomocí následujícího algoritmu:

1. Prochází graf vlevo od nejhlouběji v grafu (v tomto případě `E`).

1. Proveďte Leftward procházení, dokud nebudou všechny uzly navštíveny. Poznamenejte si název aktuálního uzlu.

1. Přečtěte si předchozí uzel (dolů a napravo), abyste zjistili, jestli je uzel, který se pamatuje, virtuální základní třídou.

1. Pokud je pamatující uzel virtuální základní třídou, prohledejte seznam a zkontrolujte, zda již byl zadán. Pokud se nejedná o virtuální základní třídu, ignorujte ji.

1. Pokud se v seznamu ještě pamatuje uzel, přidejte ho do dolní části seznamu.

1. Projde graf nahoru a podél další cesty k pravému.

1. Přejít ke kroku 2.

1. Po vyčerpání poslední cesty vzhůru si poznamenejte název aktuálního uzlu.

1. Přejít ke kroku 3.

1. Pokračujte v tomto procesu, dokud nebude dolní uzel znovu aktuální uzel.

Proto pro třídu `E`je pořadí zničení:

1. Nevirtuální základní (Base) `E`třída.

1. Nevirtuální základní (Base) `D`třída.

1. Nevirtuální základní (Base) `C`třída.

1. Virtuální základní třída `B`.

1. Virtuální základní třída `A`.

Tento proces vytvoří seřazený seznam jedinečných položek. Název třídy se nezobrazuje dvakrát. Jakmile je seznam vytvořen, je vás provedl v obráceném pořadí a destruktor pro každou třídu v seznamu od posledního do prvního je volán.

Pořadí konstrukce nebo zničení je primárně důležité, pokud konstruktory nebo destruktory v jedné třídě spoléhají na vytvořenou jinou součást nebo když je trvala, například pokud se neobjeví destruktor pro `A` (na obrázku výše). pořád `B` k dispozici, když se spustí jeho kód, nebo naopak.

Takové vzájemné závislosti mezi třídami v grafu dědičnosti jsou z vlastního podstaty nebezpečné, protože třídy odvozené později mohou změnit, která je umístěná nejvíce vlevo, a změnit tak pořadí konstrukce a zničení.

### <a name="non-virtual-base-classes"></a>Nevirtuální základní třídy

Destruktory pro nevirtuální základní třídy jsou volány v obráceném pořadí, ve kterém jsou deklarovány názvy základní třídy. Zvažte následující deklaraci třídy:

```cpp
class MultInherit : public Base1, public Base2
...
```

V předchozím příkladu je destruktor pro `Base2` volán před Destruktorem pro. `Base1`

## <a name="explicit-destructor-calls"></a>Explicitní volání destruktoru

Explicitní volání destruktoru je zřídka nezbytné. Avšak může být užitečné pro vyčištění objektů umístěných na absolutních adresách. Tyto objekty jsou obvykle přidělovány pomocí uživatelsky definovaného operátoru **New** , který přijímá argument umístění. Operátor **DELETE nemůže zrušit** přidělení této paměti, protože není přidělený z bezplatného úložiště (Další informace najdete v tématu [operátory New a DELETE](../cpp/new-and-delete-operators.md)). Volání destruktoru však může provádět odpovídající vyčištění. Chcete-li explicitně zavolat destruktor objektu `s` třídy `String`, použijte jeden z následujících příkazů:

```cpp
s.String::~String();     // non-virtual call
ps->String::~String();   // non-virtual call

s.~String();       // Virtual call
ps->~String();     // Virtual call
```

Zápis explicitního volání destruktorů, ukázaný v předchozím příkladu, lze použít bez ohledu na to, zda typ destruktor definuje. To umožňuje provést explicitní volání bez znalosti, zda je definován destruktor typu. Explicitní volání destruktoru, který není definován, nemá žádný vliv.

## <a name="robust-programming"></a>Robustní programování

Třída potřebuje destruktor, pokud získá prostředek a bezpečně spravuje prostředek. pravděpodobně vyžaduje implementaci konstruktoru kopírování a přiřazení kopírování.

Pokud tyto speciální funkce nejsou definovány uživatelem, jsou implicitně definovány kompilátorem. Implicitně generované konstruktory a operátory přiřazení provádějí kopírování členů kopii, která je téměř jistě chybná, pokud objekt spravuje prostředek.

V dalším příkladu implicitně generovaný kopírovací konstruktor provede ukazatel `str1.text` a `str2.text` bude odkazovat na stejnou paměť a při návratu z `copy_strings()`, bude tato paměť dvakrát odstraněna, což je nedefinované chování:

```cpp
void copy_strings()
{
   String str1("I have a sense of impending disaster...");
   String str2 = str1; // str1.text and str2.text now refer to the same object
} // delete[] _text; deallocates the same memory twice
  // undefined behavior
```

Explicitní definování destruktoru, kopírovacího konstruktoru nebo kopírování operátoru přiřazení zabraňuje implicitní definici konstruktoru přesunutí a operátoru přiřazení přesunutí. V takovém případě neúspěšné poskytnutí operací přesunutí obvykle znamená, že pokud je kopírování nákladné, vynechání možnosti optimalizace.

## <a name="see-also"></a>Viz také:

[Konstruktory a operátory přiřazení pro kopírování](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)</br>
[Konstruktory a operátory přiřazení pro přesunutí](../cpp/move-constructors-and-move-assignment-operators-cpp.md)
