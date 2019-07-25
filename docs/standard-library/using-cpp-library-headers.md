---
title: Používání hlaviček knihoven C++
ms.date: 11/04/2016
helpviewer_keywords:
- headers, naming in C++ include directive
- standard header in C++
- headers
- INCLUDE directive
- headers, C++ Standard Library
- library headers
- C++ Standard Library, headers
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
ms.openlocfilehash: 9cc0bb51b159f6668adad05ebd2d386364ae2f81
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450065"
---
# <a name="using-c-library-headers"></a>Používání hlaviček knihoven C++

Obsah standardní hlavičky zahrnete pojmenováním do direktivy include.

```cpp
#include <iostream>// include I/O facilities
```

Standardní hlavičky můžete zahrnout v libovolném pořadí, standardní záhlaví více než jednou nebo dvě nebo více standardních hlaviček, které definují stejné makro nebo stejný typ. Nezahrnovat standardní hlavičku v rámci deklarace. Nedefinujte makra, která mají stejné názvy jako klíčová slova předtím, než zahrnete standardní hlavičku.

Hlavička C++ knihovny zahrnuje všechny další C++ hlavičky knihoven, které potřebuje k definování potřebných typů. (Vždy zahrňte explicitně C++ všechna záhlaví knihoven potřebná v jednotce překladu, ale lesti špatného odhadu jeho skutečných závislostí.) Standardní hlavička jazyka C nikdy neobsahuje další standardní hlavičku. Standardní hlavička deklaruje nebo definuje pouze ty entity, které jsou pro něj popsány v tomto dokumentu.

Každá funkce v knihovně je deklarována ve standardním záhlaví. Na rozdíl od standardu C, standardní hlavička nikdy neposkytuje maskující makro se stejným názvem jako funkce, která maskuje deklaraci funkce a dosahuje stejného efektu. Další informace o maskování maker naleznete v tématu [ C++ konvence knihovny](../standard-library/cpp-library-conventions.md).

Všechny názvy jiné než **operátor delete** a **operator new** v `std` hlavičce C++ knihovny jsou definovány v oboru názvů nebo v oboru názvů vnořeném v rámci `std` oboru názvů. Odkaz na název `cin`, například jako `std::cin`. Všimněte si však, že názvy maker nejsou předmětem kvalifikace oboru názvů, takže můžete vždy zapisovat `__STD_COMPLEX` bez kvalifikátoru oboru názvů.

V některých převodových prostředích, C++ včetně hlavičky knihovny, může být také možné použít `std` externí názvy deklarované v oboru názvů do globálního oboru názvů, přičemž jednotlivec **používá** deklarace pro každý z názvů. Jinak hlavička v aktuálním oboru názvů *nezavádí žádné* názvy knihoven.

C++ Standard vyžaduje, aby standardní hlavičky jazyka C deklarovaly všechny externí názvy v `std`oboru názvů a pak je nahlásily do globálního oboru názvů s individuálním **použitím** deklarace pro každý název. Ale v některých prostředích překladu standardní hlavičky jazyka C neobsahují deklarace oboru názvů a deklaruje všechny názvy přímo v globálním oboru názvů. Nejspolehlivějším způsobem, jak se vypořádat s obory názvů, je tedy postupovat podle dvou pravidel:

- Pro zaručenou deklaraci v `std` oboru názvů externí název, který je tradičně \<deklarovaný v Stdlib. h > například zahrnout hlavičku \<cstdlib >. Víte, že název může být také deklarován v globálním oboru názvů.

- Pro zaručenou deklaraci v globálním oboru názvů externí název deklarovaný v \<Stdlib. h >, zahrňte > \<záhlaví Stdlib. h. Víte, že název může být také deklarován v oboru `std`názvů.

Proto pokud chcete zavolat `std::abort` , aby způsobila abnormální ukončení, měli byste zahrnout \<cstdlib >. Pokud chcete volat `abort`, měli byste zahrnout \<Stdlib. h >.

Alternativně můžete zapsat deklaraci:

```cpp
using namespace std;
```

který do aktuálního oboru názvů převede všechny názvy knihoven. Pokud zapíšete tuto deklaraci hned po všech direktivách include, získáte názvy v globálním oboru názvů. Následně můžete ignorovat požadavky oboru názvů ve zbývající části jednotky překladu. Vyhnete se také většině rozdílů v různých prostředích překladu.

Pokud není výslovně uvedeno jinak, nesmíte v rámci programu definovat názvy `std` v oboru názvů nebo v oboru názvů vnořeném `std` v rámci oboru názvů.

## <a name="see-also"></a>Viz také:

[C++Přehled standardní knihovny](../standard-library/cpp-standard-library-overview.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
