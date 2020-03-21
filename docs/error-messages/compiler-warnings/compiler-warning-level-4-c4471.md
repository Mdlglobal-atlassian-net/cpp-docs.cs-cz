---
title: Upozornění kompilátoru (úroveň 4) C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: 5d7ed7dc84c0ef61c7789deeb128b99977fa6028
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076945"
---
# <a name="compiler-warning-level-4-c4471"></a>Upozornění kompilátoru (úroveň 4) C4471

'*Enumeration*': Dopředná deklarace výčtu bez oboru musí mít podkladový typ (předpokládá se int).

Byla nalezena Dopředná deklarace výčtu bez oboru bez specifikátoru základního typu. Ve výchozím nastavení předpokládá C++ Visual `int` základní typ pro výčet. To může způsobit problémy, pokud je v definici výčtu použit jiný typ, například, pokud je zadán jiný explicitní typ nebo pokud je jiný typ implicitně nastaven pomocí inicializátoru. Možná máte také problémy s přenositelností. jiné kompilátory nepředpokládají `int` je základní typ výčtu.

Toto upozornění je ve výchozím nastavení vypnuté. k povolení na příkazovém řádku můžete použít/Wall nebo/w*N*4471 nebo použít [Upozornění](../../preprocessor/warning.md) #pragma ve zdrojovém souboru.

V některých případech je toto upozornění spurious. Pokud se po definici zobrazí Dopředná deklarace pro výčet, může se toto upozornění aktivovat. Například tento kód je platný, i když může způsobit C4471:

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

## <a name="example"></a>Příklad

Obecně je bezpečné použít úplnou definici pro nevymezený výčet namísto dopředné deklarace. Definici můžete vložit do souboru hlaviček a zahrnout ho do zdrojových souborů, které na něj odkazují. To funguje v kódu napsaném pro C++ 98 a novějším. Toto řešení doporučujeme pro přenositelnost a snadné udržování.

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

## <a name="example"></a>Příklad

V jazyce C++ 11 můžete přidat explicitní typ do výčtu bez oboru a do jeho dopředné deklarace. Toto řešení doporučujeme jenom v případě, že komplexní logika zahrnutí hlaviček brání použití definice namísto dopředné deklarace. Toto řešení může vést k potížím s údržbou: Pokud změníte podkladový typ použitý pro definici výčtu, musíte také změnit všechny dopředné deklarace, aby odpovídaly, nebo můžete mít v kódu tiché chyby. K minimalizaci tohoto problému můžete umístit dopřednou deklaraci do souboru hlaviček.

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

Pokud pro výčet zadáte explicitní typ, doporučujeme také povolit upozornění [C4369](compiler-warning-level-1-C4369.md), které je ve výchozím nastavení zapnuté. To identifikuje případy, kde položka výčtu vyžaduje jiný typ než explicitně určený typ.

## <a name="example"></a>Příklad

Můžete změnit kód na použití oboru výčtu, funkce, která je novinkou v C++ 11. Definice i jakýkoli klientský kód, který používá typ výčtu, musí být změněn, aby používaly vymezený výčet. Pokud máte problémy s znečišťováním oboru názvů, doporučujeme použít vymezený výčet, protože názvy definovaných položek výčtu jsou omezeny na rozsah výčtu. Další funkcí výčtu s vymezeným oborem je, že jeho členové nelze implicitně převést na jiný integrální nebo Výčtový typ, což může být zdrojem drobných chyb.

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
