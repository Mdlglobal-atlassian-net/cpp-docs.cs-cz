---
title: Kompilátor upozornění (úroveň 4) C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: 0345b730b8fc37329f632bb5d8486c67efd8e3b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400783"
---
# <a name="compiler-warning-level-4-c4471"></a>Kompilátor upozornění (úroveň 4) C4471

"*výčet*': Dopředná deklarace výčtu bez oboru musí mít základní typ (předpokládá se int)

Dopředná deklarace výčtu bez oboru bylo nalezeno bez specifikátoru základního typu. Ve výchozím nastavení, předpokládá Visual C++ `int` je základní typ pro výčet. Pokud jiný typ použít v definici výčtu, například případného různých explicitního typu nebo jiný typ je implicitně nastaven pomocí inicializátoru, může to způsobovat problémy. Také můžete mít problémy s přenositelností; jiné kompilátory Nepředpokládejte `int` je základní typ výčtu.

Toto upozornění je vypnuto ve výchozím nastavení; můžete použít Wall nebo /w*N*4471 ji povolit na příkazovém řádku nebo použijte #pragma [upozornění](../../preprocessor/warning.md) ve zdrojovém souboru.

V některých případech se toto upozornění je nesprávné. Pokud Dopředná deklarace výčtu se zobrazí za definice, toto upozornění může aktivovat. Například tento kód je platný, i když to může způsobit C4471:

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

## <a name="example"></a>Příklad

Obecně je bezpečné používat úplné definici pro místo Dopředná deklarace výčtu bez oboru. Můžete umístit definici v hlavičkovém souboru a zahrnout do zdrojových souborů, které na ni odkazují. Tento postup funguje v kódu napsaného pro C ++ 98 a novější. Doporučujeme, abyste toto řešení pro přenositelnost a snadnost údržby.

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

## <a name="example"></a>Příklad

V C ++ 11 můžete přidat explicitního typu, typu nevymezeného výčtu a k jeho Dopředná deklarace. Toto řešení doporučujeme jenom v případě, že začlenění logiky complex – hlavička brání použití definice místo Dopředná deklarace. Toto řešení může vést k problém s údržbou: změňte základní typ použitý pro definice výčtu, musíte změnit taky všechny deklarace dopředu tak, aby odpovídaly, nebo nemáte tiché chyby v kódu. Dopředná deklarace můžete umístit do souboru hlaviček, chcete-li minimalizovat potíže.

```cpp
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```

```cpp
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```

Pokud chcete zadat explicitní typ pro výčet, doporučujeme také povolit upozornění [C4369](compiler-warning-level-1-C4369.md), na které je ve výchozím nastavení. Určuje, případy, kde položka výčtu vyžaduje jiný typ než explicitně zadaného typu.

## <a name="example"></a>Příklad

Můžete změnit kód Refaktorovat pro použití rozsahu výčtového typu, funkce, která je nového v C ++ 11. Určený rozsah výčtu musíte změnit definici a klientský kód, který používá typ výčtu. Doporučujeme že používat výčtovém Pokud máte problémy s znečištění oboru názvů, protože názvy definované výčet položek jsou omezené na rozsah výčtu. Další funkcí výčtovém je, že její členy nejde implicitně převést na jiný celočíselný nebo Výčtový typ, který může být zdrojem drobné chyby.

```cpp
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```

```cpp
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```

