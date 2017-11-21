---
title: "&lt;číselné&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <numeric>
dev_langs: C++
helpviewer_keywords: <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 1a4ffc7ad1e7fa512a51169e4155b54b7eca3194
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltnumericgt"></a>&lt;číselné&gt;
Definuje funkce šablony kontejneru, které provádějí algoritmy numerického zpracování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <numeric>  
```  
  
## <a name="remarks"></a>Poznámky  
Číselné algoritmy vypadat algoritmy standardní knihovna C++ v [ \<algoritmus >](algorithm.md)a můžete pracovat s řadou datové struktury. Patří mezi ně třídy kontejnerů standardní knihovna – například [vektoru](../standard-library/vector-class.md) a [seznamu](../standard-library/list-class.md)a program definované datové struktury a pole elementů, které splňují požadavky na konkrétní algoritmem. Algoritmy této úrovně obecnosti dosahují přístupem k prvkům kontejneru a jejich přecházením nepřímo prostřednictvím iterátorů. Algoritmy zpracovávají rozsahy iterátoru, které jsou obvykle určeny počáteční a koncovou pozicí. Tyto rozsahy musí být platné v tom smyslu, že na všechny ukazatele v rozsazích musí být možné nepřímo odkazovat a v rámci sekvencí každého rozsahu musí být poslední pozice dosažitelná z první pomocí přírůstku.  
  
 Algoritmy rozšířit akce, které jsou podporovány v operations a členské funkce jednotlivých kontejnery standardní knihovna C++ a povolit komunikaci s různých typů objektů kontejneru ve stejnou dobu.  
  
### <a name="functions"></a>Funkce  
  
|||  
|-|-|  
|[accumulate](../standard-library/numeric-functions.md#accumulate)|Vypočítá součet všech prvků v určeném rozsahu, včetně některých počátečních hodnot, podle výpočtu po sobě jdoucích částečných součtů nebo vypočítá výsledek po sobě jdoucích částečných výsledků, které jsou získány pomocí zadané binární operace místo operace součtu.|  
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|Vypočítá po sobě následující rozdíly mezi každým prvkem a jeho předchůdcem ve vstupním rozsahu a vydá výsledky do cílového rozsahu nebo vypočte výsledek zobecněné procedury, kde je operace rozdílu nahrazena jinou zadanou binární operací.|  
|[inner_product –](../standard-library/numeric-functions.md#inner_product)|Vypočítá součet prvků produktu ve dvou rozsazích a přidá jej k zadané počáteční hodnotě nebo vypočítá výsledek zobecněné procedury, kde jsou operace součtu a produktu nahrazeny jinými zadanými binárními operacemi.|  
|[iota](../standard-library/numeric-functions.md#iota)|Ukládá počáteční hodnotu, počínaje prvním elementem a vyplnění pomocí následných přírůstcích hodnoty (`value++`) v jednotlivých prvků v intervalu `[first, last)`.|  
|[partial_sum –](../standard-library/numeric-functions.md#partial_sum)|Vypočítá řadu součtů ve vstupní oblasti z první prvek prostřednictvím *i*element TD a ukládá výsledek každé součet v *i*element TD cílového rozsahu, nebo vypočítá výsledek zobecněný postup, kde je součet operaci nahrazen jiným zadat binární operace.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)

