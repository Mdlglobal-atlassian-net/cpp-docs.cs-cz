---
title: "&lt;náhodné&gt; funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords: std::generate_canonical
caps.latest.revision: "10"
manager: ghogen
ms.openlocfilehash: 0929e7c6749af19065f42f10ee6c15ab4d4a3e88
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltrandomgt-functions"></a>&lt;náhodné&gt; funkce
  
##  <a name="generate_canonical"></a>generate_canonical  
 Vrátí hodnotu s plovoucí desetinnou čárkou z náhodné pořadí.  
  
> [!NOTE]
>  Standardní C++ ISO stavy, že tato funkce by měla vrátit hodnoty v rozsahu [ `0`, `1`). Visual Studio není kompatibilní s tímto omezením. Jako řešení generování hodnot v tomto rozsahu, použijte [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md).  
  
```  
template <class RealType, size_t Bits, class Generator>  
RealType generate_canonical(Generator& Gen);
```  
  
### <a name="parameters"></a>Parametry  
 `RealType`  
 Integrální typu procedura bodu. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).  
  
 `Bits`  
 Generátoru náhodných čísel.  
  
 `Gen`  
 Generátoru náhodných čísel.  
  
### <a name="remarks"></a>Poznámky  
 Volání funkce šablony `operator()` z `Gen` opakovaně a sady vrácené hodnoty na hodnotu s plovoucí desetinnou čárkou `x` typu `RealType` dokud shromáždil zadaný počet bitů mantisa `x`. Zadané číslo je menší z `Bits` (které musí být nenulové hodnoty) a úplné počet bitů mantisa `RealType`. První volání poskytuje nejnižší pořadí bits. Funkce vrátí hodnotu `x`.  
  
## <a name="see-also"></a>Viz také  
 [\<náhodné >](../standard-library/random.md)

