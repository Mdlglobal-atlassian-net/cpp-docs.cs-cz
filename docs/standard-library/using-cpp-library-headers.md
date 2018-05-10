---
title: Používání hlaviček knihoven C++ | Microsoft Docs
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
ms.openlocfilehash: 30d31f30971184356374b3991fedda474ca27465
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="using-c-library-headers"></a>Používání hlaviček knihoven C++

Můžete zahrnout obsah standardní hlavičku pojmenováním v direktivu.

```cpp
#include <iostream>// include I/O facilities
```

Můžete zahrnout standardní hlavičky v libovolném pořadí, standardní hlavičku více než jednou nebo dvěma nebo více standardní hlavičky, které definují stejnou makro nebo stejného typu. Nezahrnujte standardní hlavičku v deklaraci. Nedefinují makra, které mají stejné názvy jako klíčová slova před zahrnují standardní hlavičku.

Záhlaví knihovny C++ zahrnuje všechny další hlaviček knihoven C++ je nutné definovat potřebné typy. (Vždy patří explicitně žádné C++ knihovny hlavičky potřebné při překladu jednotky, ale nejméně můžete snadno uhodnout nesprávný o jeho skutečné závislosti.) Standardní C záhlaví nikdy zahrnuje jiné standardní hlavičku. Standardní hlavičku deklaruje nebo definuje jenom entity, které jsou pro něj popsané v tomto dokumentu.

Všechny funkce v knihovně je deklarován v standardní hlavičku. Na rozdíl od ve standardním C standardní hlavičku nikdy poskytuje maskování makro se stejným názvem jako funkce, která zakrývá deklarace funkce a dosáhne stejného efektu. Další informace o maskování makra najdete v tématu [konvence knihovny C++](../standard-library/cpp-library-conventions.md).

Všechny názvy jinak než `operator delete` a `operator new` v knihovně C++ hlavičky jsou definovány v `std` obor názvů, nebo v oboru názvů vnořených ve `std` oboru názvů. Odkaz na název `cin`, například jako `std::cin`. Upozorňujeme však, že – makro názvy nejsou předmětem kvalifikace názvů, vždy zápisu `__STD_COMPLEX` bez kvalifikátor oboru názvů.

V některých prostředích s překlad může včetně hlavičku knihovny C++ Zdvihadlo externí názvy, které jsou deklarované v `std` oboru názvů do globální obor názvů taky u jednotlivých `using` deklarace pro jednotlivé názvy. Jinak hodnota záhlaví nemá *není* zavedení všechny názvy knihoven do oboru názvů aktuální.

Standardní C++ vyžaduje, aby hlavičky C standardních deklarovat všechny externí názvy v oboru názvů `std`, pak je Zdvihadlo do globálního oboru názvů s individuální `using` deklarace pro jednotlivé názvy. Ale v některých prostředích překlad standardní C hlavičky zahrnují žádná deklarace oboru názvů deklarace názvy všech přímo v globálním oboru názvů. Proto je většina přenosných způsob, jak nakládat s obory názvů podle dvě pravidla:

- V oboru názvů assuredly deklarovat `std` externí název, který tradičně deklarovaného v \<stdlib.h >, například obsahovat záhlaví \<cstdlib – >. Vědět, že název může být také deklarovat v globálním oboru názvů.

- V oboru názvů globální assuredly deklarovat externí název deklarované v \<stdlib.h >, zahrnují záhlaví \<stdlib.h > přímo. Vědět, že název může být deklarován také v oboru názvů `std`.

Proto pokud chcete volat `std::abort` způsobí neobvyklé ukončení, by měla obsahovat \<cstdlib – >. Pokud chcete volat `abort`, by měla obsahovat \<stdlib.h >.

Alternativně můžete napsat deklaraci:

```cpp
using namespace std;
```

které všechny názvy knihoven přenese do aktuální obor názvů. Pokud píšete tuto deklaraci okamžitě po všech direktivy začlenění na, Zdvihadlo názvy do globální obor názvů. Následně můžete ignorovat aspekty názvů ve zbývající jednotky překladu. Také se vyhnout většina rozdíly překlad různých prostředích.

Pokud není výslovně uvedeno jinak, nesmí definovat názvy v `std` obor názvů, nebo v oboru názvů vnořených ve `std` oboru názvů, v rámci vašeho programu.

## <a name="see-also"></a>Viz také

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
