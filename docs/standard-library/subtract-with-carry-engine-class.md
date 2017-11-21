---
title: "subtract_with_carry_engine – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
dev_langs: C++
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c1a284af52195db1c25d6175876d732da7255962
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine – třída
Generuje náhodné pořadí algoritmem subtract s carry (tepelně izolováno Fibonacciho).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class UIntType, size_t W, size_t S, size_t R>  
class subtract_with_carry_engine;  
```  
  
#### <a name="parameters"></a>Parametry  
 `UIntType`  
 Výsledný typ celé číslo bez znaménka. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).  
  
 `W`  
 **Aplikace Word velikost**. Velikost jednotlivých slov v bitech, pořadí stavu. **Předběžnou**:`0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `S`  
 **Krátká prodleva**. Počet celočíselné hodnoty. **Předběžnou**:`0 < S < R`  
  
 `R`  
 **Dlouho funkce lag**. Určuje opakování v řadě vygenerovat.  
  
## <a name="members"></a>Členové  
  
||||  
|-|-|-|  
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|  
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|  
|`default_seed`je členem konstantní, definované jako `19780503u`, použít jako výchozí hodnota parametru pro `subtract_with_carry_engine::seed` a konstruktor jednu hodnotu.|||  
  
 Další informace o modulu členy najdete v tématu [ \<náhodných >](../standard-library/random.md).  
  
## <a name="remarks"></a>Poznámky  
 `substract_with_carry_engine` Šablony třídy představuje vylepšení [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md). Ani jeden z nich pro tyto moduly se tak rychle, nebo s jako vysoce kvalitního výsledky jako [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).  
  
 Tento modul vytváří hodnoty typu zadán uživatel nepodepsaných integrálních pomocí vztahu opakování ( *období*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, kde `cy(i)` má hodnotu `1` Pokud `x(i - S) - x(i - R) - cy(i - 1) < 0`, jinak hodnota `0`, a `M` má hodnotu `2` <sup>W</sup>. Stav stroje je carry indikátor plus `R` hodnoty. Tyto hodnoty se skládají z posledních `R` hodnoty vrácené v případě `operator()` byla volána alespoň `R` krát jinak `N` hodnoty, které byly vráceny a poslední `R - N` hodnoty počáteční hodnoty.  
  
 Argument šablony `UIntType` musí být dostatečně velký pro uložení hodnoty až `M - 1`.  
  
 Přestože generátor z tento modul můžete vytvořit přímo, můžete také použít jednu z těchto předdefinovaných definice TypeDef:  
  
 `ranlux24_base`: Použít jako základ pro `ranlux24`.                   
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`  
  
 `ranlux48_base`: Použít jako základ pro `ranlux48`.                   
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`  
  
 Podrobné informace o subract s algoritmem modulu carry, najdete v článku Wikipedia [generátor tepelně izolováno Fibonacciho](http://go.microsoft.com/fwlink/LinkId=402445).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<náhodných >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [\<náhodné >](../standard-library/random.md)

