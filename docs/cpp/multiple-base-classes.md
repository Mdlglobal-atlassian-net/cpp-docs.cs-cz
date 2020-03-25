---
title: Vícenásobné třídy Base
ms.date: 11/19/2018
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: b8bc411b1b8d0b459fe58a39cf351d59d09b2d0e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179470"
---
# <a name="multiple-base-classes"></a>Vícenásobné třídy Base

Třída může být odvozena z více než jedné základní třídy. V modelu vícenásobné dědičnosti (kde třídy jsou odvozeny z více než jedné základní třídy) jsou základní třídy určeny pomocí elementu gramatiky *Base-list* . Lze například určit deklaraci třídy pro `CollectionOfBook` odvozenou z `Collection` a z `Book`:

```cpp
// deriv_MultipleBaseClasses.cpp
// compile with: /LD
class Collection {
};
class Book {};
class CollectionOfBook : public Book, public Collection {
    // New members
};
```

Pořadí, ve kterém jsou základní třídy uvedeny, není důležité, kromě některých případů, kde jsou vyvolány konstruktory a destruktory. V těchto případech ovlivňuje pořadí, ve kterém jsou základní třídy uvedeny, následující:

- Pořadí, ve kterém dochází k inicializaci pomocí konstruktoru. Pořadí specifikace je důležité, závisí-li kód na inicializaci části `Book``CollectionOfBook` před částí `Collection`. Inicializace probíhá v pořadí, ve kterém jsou třídy určeny v *seznamu Base-list*.

- Pořadí, ve kterém jsou vyvolány destruktory k vyčištění. Pořadí je také důležité, pokud musí být při rušení konkrétní „části“ třídy přítomna druhá část. Destruktory jsou volány v obráceném pořadí tříd uvedených v *seznamu Base-list*.

    > [!NOTE]
    >  Pořadí specifikace základních tříd může ovlivnit rozložení paměti třídy. Neprovádějte žádné rozhodnutí v programování na základě pořadí základních členů v paměti.

Při zadávání *základního seznamu*nelze stejný název třídy zadat více než jednou. Je však možné, aby byla třída nepřímou základní třídou odvozené třídy více než jednou.

## <a name="virtual-base-classes"></a>Virtuální základní třídy

Jelikož třída může být nepřímou základní třídou odvozené třídy více než jednou, jazyk C++ poskytuje způsob, jak práci takové základní třídy optimalizovat. Virtuální základní třídy nabízejí způsob, jak ušetřit místo a vyhnout se nejasnostem v hierarchiích tříd používajících vícenásobnou dědičnost.

Všechny nevirtuální objekty obsahují kopii datových členů definovaných v základní třídě. Tato duplicita zabírá místo a vyžaduje při každém přístupu ke členům základní třídy určit, která kopie členů má být použita.

Je-li základní třída zadaná jako virtuální základ, může více než jednou fungovat jako nepřímý základ bez duplikace svých datových členů. Všechny základní třídy, které tuto třídu používají jako virtuální základ, sdílejí jedinou kopii jejích datových členů.

Při deklaraci virtuální základní třídy se klíčové slovo **Virtual** zobrazuje v základních seznamech odvozených tříd.

Prohlédněte si hierarchii tříd na následujícím obrázku, který znázorňuje simulovanou frontu na oběd.

![Graf simulované linie na oběd](../cpp/media/vc38xp1.gif "Graf simulované linie na oběd") <br/>
Graf simulované na oběd – spojnicový graf

Na obrázku je třída `Queue` základní třídou pro třídu `CashierQueue` i `LunchQueue`. Jsou-li však obě třídy kombinovány do třídy `LunchCashierQueue`, nastane následující problém: nová třída obsahuje dva podobjekty typu `Queue`, jeden z třídy `CashierQueue` a druhý z třídy `LunchQueue`. Následující obrázek ukazuje koncepční rozložení paměti (skutečné rozložení paměti může být optimalizováno).

![Objekt simulované&#45;linky na oběd](../cpp/media/vc38xp2.gif "Objekt simulované&#45;linky na oběd") <br/>
Objekt simulované na oběd-line

Povšimněte si, že v objektu `Queue` existují dva podobjekty `LunchCashierQueue`. Následující kód deklaruje základní třídu `Queue` jako virtuální:

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

Klíčové slovo **Virtual** zajišťuje, aby byla k dispozici pouze jedna kopie podobjektu `Queue` (viz následující obrázek).

![Objekt simulované&#45;linky na oběd, virtuální základní třídy](../cpp/media/vc38xp3.gif "Objekt simulované&#45;linky na oběd, virtuální základní třídy") <br/>
Objekt simulované na oběd-line s virtuálními základními třídami

Třída může mít virtuální i nevirtuální komponentu daného typu. K tomu dojde za podmínek znázorněných na následujícím obrázku.

![Virtuální a&#45;nevirtuální komponenty třídy](../cpp/media/vc38xp4.gif "Virtuální a&#45;nevirtuální komponenty třídy") <br/>
Virtuální a nevirtuální součásti stejné třídy

Na obrázku používají třídy `CashierQueue` a `LunchQueue` třídu `Queue` jako virtuální základní třídu. Třída `TakeoutQueue` však třídu `Queue` určuje jako základní třídu, nikoli jako virtuální základní třídu. Proto má třída `LunchTakeoutCashierQueue` dva podobjekty typu `Queue`: jeden z cesty dědičnosti obsahující třídu `LunchCashierQueue` a jeden z cesty obsahující třídu `TakeoutQueue`. To je znázorněno na následujícím obrázku.

![Virtuální &&#45;nevirtuální dědičnost v rozložení objektu](../cpp/media/vc38xp5.gif "Virtuální &&#45;nevirtuální dědičnost v rozložení objektu") <br/>
Rozložení objektu s virtuální a nevirtuální dědičností

> [!NOTE]
>  Virtuální dědičnost poskytuje v porovnání s nevirtuální dědičností významné výhody ve velikosti. Může však zavést další režii zpracování.

Přepisuje-li odvozená třída virtuální funkci, kterou třída dědí z virtuální základní třídy, a pokud konstruktor nebo destruktor odvozené základní třídy tuto funkci volá pomocí ukazatele na virtuální základní třídu, kompilátor může do tříd s virtuálními základy zavést dodatečná skrytá pole „vtordisp“. Možnost kompilátoru `/vd0` potlačí přidání skrytého členu přemístění konstruktoru vtordisp nebo destruktoru. Možnost kompilátoru `/vd1` ve výchozím nastavení umožňuje, aby byly v případě potřeby. Členy vtordisp vypněte pouze v případě, že jste si jisti, že všechny konstruktory a destruktory třídy volají virtuální funkce virtuálně.

Možnost kompilátoru `/vd` ovlivňuje celý modul kompilace. Pomocí direktivy pragma `vtordisp` potlačit a znovu povolit pole `vtordisp` na základě třídy podle třídy:

```cpp
#pragma vtordisp( off )
class GetReal : virtual public { ... };
\#pragma vtordisp( on )
```

## <a name="name-ambiguities"></a>Nejednoznačné názvy

Vícenásobná dědičnost umožňuje, aby byly názvy odvozeny podél více než jedné cesty. Názvy členů tříd podél těchto cest nejsou nutně jedinečné. Tyto konflikty názvů se nazývají „nejednoznačnosti“.

Libovolný výraz, který odkazuje na člen třídy, musí provést jednoznačný odkaz. Následující příklad ukazuje, jak vytvořit nejednoznačnosti:

```cpp
// deriv_NameAmbiguities.cpp
// compile with: /LD
// Declare two base classes, A and B.
class A {
public:
    unsigned a;
    unsigned b();
};

class B {
public:
    unsigned a();  // Note that class A also has a member "a"
    int b();       //  and a member "b".
    char c;
};

// Define class C as derived from A and B.
class C : public A, public B {};
```

Podle předchozí deklarace třídy je kód jako následující nejednoznačný, protože je nejasné, zda proměnná `b` odkazuje na proměnnou `b` ve třídě `A` nebo ve třídě `B`:

```cpp
C *pc = new C;

pc->b();
```

Zvažte předchozí příklad. Protože název `a` je členem třídy `A` a třídy `B`, kompilátor nedokáže určit, která funkce `a` má být zavolána. Přístup ke členu je nejednoznačný, pokud může odkazovat na více než jednu funkci, objekt, typ nebo enumerátor.

Kompilátor nejednoznačnosti zjistí pomocí provedení zkoušek v tomto pořadí:

1. Je-li přístup k názvu nejednoznačný (jak bylo právě popsáno), je vygenerována chybová zpráva.

1. Jsou-li přetížené funkce nejednoznačné, jsou vyřešeny.

1. Pokud přístup k názvu porušuje oprávnění členského přístupu, je vygenerována chybová zpráva. (Další informace naleznete v tématu [Member-Access Control](../cpp/member-access-control-cpp.md).)

Pokud výraz vytvoří nejednoznačnost prostřednictvím dědičnosti, lze tuto nejednoznačnost vyřešit ručním kvalifikováním názvu pomocí názvu třídy. Aby se předchozí příklad zkompiloval správně bez nejednoznačností, použijte kód jako například:

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
>  Když je deklarován typ `C`, má potenciál způsobit chyby, pokud je typ `B` odkazován v rozsahu typu `C`. Avšak žádná chybová zpráva není vygenerována, dokud v rozsahu typu `B` není skutečně proveden nekvalifikovaný odkaz na typ `C`.

### <a name="dominance"></a>Dominance

Prostřednictvím grafu dědičnosti je možné dosáhnout více než jednoho názvu (funkce, objekt nebo výčet). Takové případy jsou s nevirtuálními základními třídami považovány za nejednoznačné. Jsou také nejednoznačné s virtuálními základními třídami, pokud některý název „nedominuje“ ostatním.

Název dominuje jinému názvu, pokud je definován v obou třídách a jedna třída je odvozena od druhé. Dominantní název je název v odvozené třídě. Tento název se používá v případě, že by jinak vznikla nejednoznačnost, jak je znázorněno v následujícím příkladu:

```cpp
// deriv_Dominance.cpp
// compile with: /LD
class A {
public:
    int a;
};

class B : public virtual A {
public:
    int a();
};

class C : public virtual A {};

class D : public B, public C {
public:
    D() { a(); } // Not ambiguous. B::a() dominates A::a.
};
```

### <a name="ambiguous-conversions"></a>Dvojznačné převody

Explicitní a implicitní převody z ukazatelů na typy tříd mohou způsobit nejednoznačnost. Další obrázek – nejednoznačný převod ukazatelů na základní třídy – zobrazuje následující:

- Deklarace objektu typu `D`.

- Účinek použití operátoru address-of ( **&** ) na tento objekt. Operátor z adresy vždy poskytuje základní adresu objektu.

- Efekt explicitního převodu ukazatele získaného pomocí operátoru adresy z typu základní třídy `A`. Vynucení adresy objektu na typ `A*` vždy neposkytuje kompilátoru dostatek informací o tom, ke kterému podřízenému objektu typu `A` provést výběr. V tomto případě existují dva podřízené objekty.

![Dvojznačný převod ukazatelů na základní třídy](../cpp/media/vc38xt1.gif "Dvojznačný převod ukazatelů na základní třídy") <br/>
Dvojznačný převod ukazatelů na základní třídy

Převod na typ `A*` (ukazatel na `A`) je nejednoznačný, protože neexistuje žádný způsob, jak ověřit, který z podřízených objektů typu `A` je správný. Nejednoznačnosti se lze vyhnout explicitní specifikací podřízeného zamýšleného objektu následujícím způsobem:

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>Nejednoznačnosti a virtuální třídy Base

Pokud jsou používány virtuální základní třídy, funkce, objekty, typy a výčty lze dosáhnout prostřednictvím cest vícenásobné dědičnosti. Vzhledem k tomu, že existuje pouze jedna instance základní třídy, nedochází k nejednoznačnosti při přístupu k těmto názvům.

Následující obrázek ukazuje, jak jsou objekty složeny pomocí virtuální a nevirtuální dědičnosti.

![Virtuální odvození a&#45;nevirtuální odvození](../cpp/media/vc38xr1.gif "Virtuální odvození a&#45;nevirtuální odvození") <br/>
Virtuální vs. nevirtuální odvození

Na obrázku způsobí přístup k libovolnému členu třídy `A` prostřednictvím nevirtuální základní třídy nejednoznačnost. Kompilátor nemá žádné informace, které vysvětlují použití podobjektu souvisejícího s třídou `B` nebo podobjektu souvisejícího s třídou `C`. Nicméně, když je třída `A` zadána jako virtuální základní třída, je jasné, ke kterému podobjektu je přistupováno.

## <a name="see-also"></a>Viz také

[Dědičnost](../cpp/inheritance-cpp.md)
