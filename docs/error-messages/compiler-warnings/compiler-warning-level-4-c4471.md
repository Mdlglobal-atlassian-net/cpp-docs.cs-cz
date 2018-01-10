---
title: "Kompilátoru (úroveň 4) upozornění C4471 | Microsoft Docs"
ms.custom: 
ms.date: 04/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4471
dev_langs: C++
helpviewer_keywords: C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5e7429a458c90c30fdf57b985cda88ca85c6d29c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4471"></a>C4471 kompilátoru upozornění (úroveň 4)
'*výčtu*': deklaraci předat dál bez ohledu na obor výčtu musí mít základní typ (int předpokládá, že)  
  
Bez specifikátorem pro základní typ nebyl nalezen deklaraci předat dál bez ohledu na obor výčtu. Ve výchozím nastavení, předpokládá Visual C++ `int` je základní typ pro výčet. Pokud jiný typ použitými v definici – výčet, například pokud je zadán jiný explicitní typ, nebo pokud jiný atribut type je implicitně nastavit pomocí inicializátoru to může způsobit problémy. Můžete mít problémy s přenositelností; Další kompilátory Nepředpokládejte `int` je základní typ výčtu.  
  
Toto upozornění je vypnuto ve výchozím nastavení; můžete použít /Wall nebo /w*N*4471 ji povolit na příkazovém řádku nebo použijte #pragma [upozornění](../../preprocessor/warning.md) ve zdrojovém souboru.  
  
V některých případech toto upozornění je nesprávné. Pokud se po definice se objeví dopředného deklarace pro výčet, může aktivovat toto upozornění. Například tento kód je platný, i když může to způsobit C4471:  
  
```cpp  
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```  
  
## <a name="example"></a>Příklad  
Obecně je bezpečné použít úplnou definici pro bez ohledu na obor výčet místo deklaraci předat dál. Můžete uvést definici v záhlaví souboru a její zahrnutí do zdrojových souborů, které na ni odkazuje. Toto funguje ve kódu napsaného pro C ++ 98 a novější. Doporučujeme, abyste toto řešení pro přenositelnost a snadné údržby.  
  
```cpp  
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```  
  
## <a name="example"></a>Příklad  
Ve C ++ 11 můžete přidat explicitní typ výčtu bez ohledu na obor a jeho dopředného deklaraci. Doporučujeme, abyste toto řešení pouze v případě, že complex – hlavička zahrnutí logiku brání použití definici místo deklaraci předat dál. Toto řešení může vést k problém údržby: Pokud změníte základní typ použitý pro definice výčtu, musíte změnit taky všechny dopředného deklarací tak, aby odpovídaly nebo tichou chyby může mít v kódu. Předat dál deklaraci můžete umístit do souboru záhlaví pro tento problém minimalizoval.  
  
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
  
Pokud zadáte explicitního typu pro výčet, doporučujeme také povolit upozornění [C4369](compiler-warning-level-1-C4369.md), který se ve výchozím nastavení zapnutý. Ten identifikuje případech, kde položka výčtu vyžaduje jiného typu než explicitně zadaného typu.
  
## <a name="example"></a>Příklad  
Můžete změnit svůj kód použít vymezenou výčtu, funkce, která je nové v C ++ 11. Definice a kód klienta, který používá typ výčtu musí být změněn na použít vymezenou výčtu. Doporučujeme že používat vymezenou výčtu Pokud máte problémy s znečištění oboru názvů, protože názvy definované výčtu položky jsou omezeny na rozsahu výčtového typu. Jiné funkce vymezená výčtu je, že její členy nelze implicitně převést na jiný typ celočíselný nebo výčet, který může být zdrojem jemně chyby.

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
  
