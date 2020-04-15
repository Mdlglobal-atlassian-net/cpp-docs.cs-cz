---
title: Vícenásobné třídy Base
ms.date: 11/19/2018
helpviewer_keywords:
- base classes [C++], multiple
- derived classes [C++], multiple bases
- multiple inheritance, class declaration
- multiple base classes [C++]
ms.assetid: a30c69fe-401c-4a87-96a0-e0da70c7c740
ms.openlocfilehash: 7cac70da5dd7093ce3e9c1cf3d2350d780c6b391
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353724"
---
# <a name="multiple-base-classes"></a>Vícenásobné třídy Base

Třídu lze odvodit z více než jedné základní třídy. V modelu s více dědičnostmi (kde jsou třídy odvozeny z více než jedné základní třídy) jsou základní třídy určeny pomocí elementu gramatiky *základního seznamu.* Lze například určit deklaraci třídy pro `CollectionOfBook` odvozenou z `Collection` a z `Book`:

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

- Pořadí, ve kterém dochází k inicializaci pomocí konstruktoru. Pořadí specifikace je důležité, závisí-li kód na inicializaci části `Book``CollectionOfBook` před částí `Collection`. Inicializace probíhá v pořadí, v jakém jsou třídy uvedeny v *základním seznamu*.

- Pořadí, ve kterém jsou vyvolány destruktory k vyčištění. Pořadí je také důležité, pokud musí být při rušení konkrétní „části“ třídy přítomna druhá část. Destruktory jsou volány v obráceném pořadí tříd zadaných v *základním seznamu*.

    > [!NOTE]
    >  Pořadí specifikace základních tříd může ovlivnit rozložení paměti třídy. Neprovádějte žádné rozhodnutí v programování na základě pořadí základních členů v paměti.

Při zadávání *základního seznamu*nelze zadat stejný název třídy více než jednou. Je však možné, aby byla třída nepřímou základní třídou odvozené třídy více než jednou.

## <a name="virtual-base-classes"></a>Virtuální základní třídy

Jelikož třída může být nepřímou základní třídou odvozené třídy více než jednou, jazyk C++ poskytuje způsob, jak práci takové základní třídy optimalizovat. Virtuální základní třídy nabízejí způsob, jak ušetřit místo a vyhnout se nejasnostem v hierarchiích tříd používajících vícenásobnou dědičnost.

Všechny nevirtuální objekty obsahují kopii datových členů definovaných v základní třídě. Tato duplicita zabírá místo a vyžaduje při každém přístupu ke členům základní třídy určit, která kopie členů má být použita.

Je-li základní třída zadaná jako virtuální základ, může více než jednou fungovat jako nepřímý základ bez duplikace svých datových členů. Všechny základní třídy, které tuto třídu používají jako virtuální základ, sdílejí jedinou kopii jejích datových členů.

Při deklarování virtuální základní třídy se **virtuální** klíčové slovo zobrazí v základních seznamech odvozených tříd.

Prohlédněte si hierarchii tříd na následujícím obrázku, který znázorňuje simulovanou frontu na oběd.

![Graf simulované polední linky](../cpp/media/vc38xp1.gif "Graf simulované polední linky") <br/>
Simulovaný graf polední čáry

Na obrázku je třída `Queue` základní třídou pro třídu `CashierQueue` i `LunchQueue`. Jsou-li však obě třídy kombinovány do třídy `LunchCashierQueue`, nastane následující problém: nová třída obsahuje dva podobjekty typu `Queue`, jeden z třídy `CashierQueue` a druhý z třídy `LunchQueue`. Následující obrázek ukazuje koncepční rozložení paměti (skutečné rozložení paměti může být optimalizováno).

![Simulovaný objekt&#45;řádku oběda](../cpp/media/vc38xp2.gif "Simulovaný objekt&#45;řádku oběda") <br/>
Simulovaný objekt polední linie

Povšimněte si, že v objektu `Queue` existují dva podobjekty `LunchCashierQueue`. Následující kód deklaruje základní třídu `Queue` jako virtuální:

```cpp
// deriv_VirtualBaseClasses.cpp
// compile with: /LD
class Queue {};
class CashierQueue : virtual public Queue {};
class LunchQueue : virtual public Queue {};
class LunchCashierQueue : public LunchQueue, public CashierQueue {};
```

**Virtuální** klíčové slovo zajišťuje, že je `Queue` zahrnuta pouze jedna kopie podobjektu (viz následující obrázek).

![Simulovaný oběd&#45;objekt, virtuální základní třídy](../cpp/media/vc38xp3.gif "Simulovaný oběd&#45;objekt, virtuální základní třídy") <br/>
Simulovaný objekt polední čáry s virtuálními základními třídami

Třída může mít virtuální i nevirtuální komponentu daného typu. K tomu dojde za podmínek znázorněných na následujícím obrázku.

![Virtuální a ne&#45;virtuální součásti třídy](../cpp/media/vc38xp4.gif "Virtuální a ne&#45;virtuální součásti třídy") <br/>
Virtuální a nevirtuální součásti stejné třídy

Na obrázku používají třídy `CashierQueue` a `LunchQueue` třídu `Queue` jako virtuální základní třídu. Třída `TakeoutQueue` však třídu `Queue` určuje jako základní třídu, nikoli jako virtuální základní třídu. Proto má třída `LunchTakeoutCashierQueue` dva podobjekty typu `Queue`: jeden z cesty dědičnosti obsahující třídu `LunchCashierQueue` a jeden z cesty obsahující třídu `TakeoutQueue`. To je znázorněno na následujícím obrázku.

![Virtuální & bez&#45;virtuální dědičnosti v rozložení objektu](../cpp/media/vc38xp5.gif "Virtuální & bez&#45;virtuální dědičnosti v rozložení objektu") <br/>
Rozložení objektů s virtuální a nevirtuální dědičností

> [!NOTE]
> Virtuální dědičnost poskytuje v porovnání s nevirtuální dědičností významné výhody ve velikosti. Může však zavést další režii zpracování.

Přepisuje-li odvozená třída virtuální funkci, kterou třída dědí z virtuální základní třídy, a pokud konstruktor nebo destruktor odvozené základní třídy tuto funkci volá pomocí ukazatele na virtuální základní třídu, kompilátor může do tříd s virtuálními základy zavést dodatečná skrytá pole „vtordisp“. Možnost `/vd0` kompilátoru potlačí přidání skrytého vtordisp konstruktoru/destruktoru posunutí člena. Možnost `/vd1` kompilátoru, výchozí, umožňuje jim, kde jsou nezbytné. Členy vtordisp vypněte pouze v případě, že jste si jisti, že všechny konstruktory a destruktory třídy volají virtuální funkce virtuálně.

Možnost `/vd` kompilátoru ovlivňuje celý modul kompilace. Pragma `vtordisp` slouží k potlačení a `vtordisp` opětovnému povolení polí podle třídy:

```cpp
#pragma vtordisp( off )
class GetReal : virtual public { ... };
\#pragma vtordisp( on )
```

## <a name="name-ambiguities"></a>Nejasnosti o názvu

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

1. Pokud přístup k názvu porušuje oprávnění členského přístupu, je vygenerována chybová zpráva. (Další informace naleznete v [tématu Řízení přístupu členů](../cpp/member-access-control-cpp.md).)

Pokud výraz vytvoří nejednoznačnost prostřednictvím dědičnosti, lze tuto nejednoznačnost vyřešit ručním kvalifikováním názvu pomocí názvu třídy. Aby se předchozí příklad zkompiloval správně bez nejednoznačností, použijte kód jako například:

```cpp
C *pc = new C;

pc->B::a();
```

> [!NOTE]
> Když je deklarován typ `C`, má potenciál způsobit chyby, pokud je typ `B` odkazován v rozsahu typu `C`. Avšak žádná chybová zpráva není vygenerována, dokud v rozsahu typu `B` není skutečně proveden nekvalifikovaný odkaz na typ `C`.

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

### <a name="ambiguous-conversions"></a>Nejednoznačné převody

Explicitní a implicitní převody z ukazatelů na typy tříd mohou způsobit nejednoznačnost. Další obrázek – nejednoznačný převod ukazatelů na základní třídy – zobrazuje následující:

- Deklarace objektu typu `D`.

- Účinek použití operátoru address-of (**&**) na tento objekt. Operátor z adresy vždy poskytuje základní adresu objektu.

- Efekt explicitního převodu ukazatele získaného pomocí operátoru adresy z typu základní třídy `A`. Vynucení adresy objektu na typ `A*` vždy neposkytuje kompilátoru dostatek informací o tom, ke kterému podřízenému objektu typu `A` provést výběr. V tomto případě existují dva podřízené objekty.

![Nejednoznačný převod ukazatelů na základní třídy](../cpp/media/vc38xt1.gif "Nejednoznačný převod ukazatelů na základní třídy") <br/>
Nejednoznačný převod ukazatelů na základní třídy

Převod na typ `A*` (ukazatel na `A`) je nejednoznačný, protože neexistuje žádný způsob, jak ověřit, který z podřízených objektů typu `A` je správný. Nejednoznačnosti se lze vyhnout explicitní specifikací podřízeného zamýšleného objektu následujícím způsobem:

```cpp
(A *)(B *)&d       // Use B subobject.
(A *)(C *)&d       // Use C subobject.
```

### <a name="ambiguities-and-virtual-base-classes"></a>Nejasnosti a virtuální základní třídy

Pokud jsou používány virtuální základní třídy, funkce, objekty, typy a výčty lze dosáhnout prostřednictvím cest vícenásobné dědičnosti. Vzhledem k tomu, že existuje pouze jedna instance základní třídy, nedochází k nejednoznačnosti při přístupu k těmto názvům.

Následující obrázek ukazuje, jak jsou objekty složeny pomocí virtuální a nevirtuální dědičnosti.

![Virtuální dekarace a ne&#45;virtuální dekultivace](../cpp/media/vc38xr1.gif "Virtuální dekarace a ne&#45;virtuální dekultivace") <br/>
Virtuální vs. nevirtuální odvození

Na obrázku způsobí přístup k libovolnému členu třídy `A` prostřednictvím nevirtuální základní třídy nejednoznačnost. Kompilátor nemá žádné informace, které vysvětlují použití podobjektu souvisejícího s třídou `B` nebo podobjektu souvisejícího s třídou `C`. Nicméně, když je třída `A` zadána jako virtuální základní třída, je jasné, ke kterému podobjektu je přistupováno.

## <a name="see-also"></a>Viz také

[Dědičnost](../cpp/inheritance-cpp.md)
