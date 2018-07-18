---
title: Používání hlaviček knihoven C++ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- headers, naming in C++ include directive
- standard header in C++
- headers
- INCLUDE directive
- headers, C++ Standard Library
- library headers
- C++ Standard Library, headers
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2283e74c00867e373d2ba117fd5dfbf70f137c75
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966004"
---
# <a name="using-c-library-headers"></a>Používání hlaviček knihoven C++

Zahrnout obsah standardní hlavičku pojmenováním v direktivě include.

```cpp
#include <iostream>// include I/O facilities
```

Můžete zahrnout standardní záhlaví v libovolném pořadí, standardní hlavičku více než jednou nebo dvěma nebo více standardními záhlavími, které definují stejné – makro nebo stejného typu. Standardní hlavička v rámci deklarace nezahrnují. Nedefinujte makra, která mají stejné názvy jako klíčová slova před zahrnout standardní hlavička.

Záhlaví knihovny C++ obsahuje všechny ostatní hlaviček knihoven C++ je potřeba definovat potřebné typy. (Vždy zahrnovat explicitně C++ knihovny záhlaví v jednotce překladu, ale potřeba, přidejte odhad nesprávné informace o jeho skutečné závislosti.) Záhlaví Standard C nikdy obsahuje jiné standardní hlavičku. Standardní hlavičku deklaruje a definuje pouze entity pro něj popsané v tomto dokumentu.

Každá funkce v knihovně je deklarován ve standardní hlavičku. Na rozdíl od ve standardním C standardní hlavičku nikdy poskytuje maskování makro se stejným názvem jako funkce, která skrývá deklaraci funkce a dosáhne stejného výsledku. Další informace o maskování makra, naleznete v tématu [konvence knihovny C++](../standard-library/cpp-library-conventions.md).

Všechny názvy jiných než **operátor delete** a **operátor new** v knihovně C++ hlavičky jsou definovány v `std` obor názvů, nebo v oboru vnořené `std` oboru názvů. Odkaz na název `cin`, například jako `std::cin`. Pamatujte však, že názvy maker se nevztahují kvalifikace názvů, takže vždy psát `__STD_COMPLEX` bez kvalifikátoru oboru názvů.

V některých prostředích překladu, včetně hlaviček knihoven C++ může zahrnul externí názvy deklarované v `std` oboru názvů do globálního oboru názvů, u jednotlivých **pomocí** deklarace pro jednotlivé názvy. V opačném případě nemá hlavičku *není* představovat všechny názvy knihoven na aktuální obor názvů.

Standard jazyka C++ vyžaduje, aby C standardními záhlavími deklarovat všechny externí názvy v oboru názvů `std`, pak je zahrnul do globální obor názvů u jednotlivých **pomocí** deklarace pro jednotlivé názvy. Ale v některých prostředích překlad standardní knihovnou jazyka c. hlavičky zahrnují žádné deklarace oboru názvů deklarovat všechny názvy přímo v globálním oboru názvů. Díky tomu se nejvíce přenosný způsob, jak zacházet s obory názvů má následovat dvě pravidla:

- Chcete-li assuredly deklarovat v oboru názvů `std` externí název, který je obvykle deklarované v \<stdlib.h >, například zahrnout hlavičku \<cstdlib – >. Vědět, že název může být také deklarovány v globálním oboru názvů.

- Chcete-li assuredly deklarovat v globálním oboru názvů deklarovaný v externí název \<stdlib.h >, zahrnout hlavičku \<stdlib.h > přímo. Vědět, že název může být také deklarovány v oboru názvů `std`.

Proto pokud chcete volat `std::abort` způsobit neobvyklé ukončení, měli byste zahrnout \<cstdlib – >. Pokud chcete volat `abort`, měli byste zahrnout \<stdlib.h >.

Alternativně můžete napsat deklarace:

```cpp
using namespace std;
```

všechny názvy knihoven což přináší do aktuální obor názvů. Při zápisu této deklarace okamžitě direktivy přece zahrnout, zahrnul názvy do globálního oboru názvů. Následně můžete ignorovat aspekty oboru názvů ve zbývající jednotky překladu. Také vyhnout většina rozdílů mezi prostředími různých překladu.

Pokud není výslovně uvedeno jinak, nesmí definovat názvy v `std` obor názvů, nebo v oboru vnořené `std` oboru názvů, v rámci programu.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
