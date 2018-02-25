---
title: "independent_bits_engine – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::independent_bits_engine
dev_langs:
- C++
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d2f5b064b91aa6df766ff4ca460a6096f984ab8b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="independentbitsengine-class"></a>independent_bits_engine – třída
Generuje náhodné pořadí čísel s zadaný počet bitů podle počtu bitů opětovné z hodnot vrácených jeho základní modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class Engine, size_t W, class UIntType>  
class independent_bits_engine;  
```  
  
### <a name="parameters"></a>Parametry  
 `Engine`  
 Typ základního modulu.  
  
 `W`  
 **Aplikace Word velikost**. Velikost v bitech, každé číslo vygenerovat. **Předběžnou**: `0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `UIntType`  
 Výsledný typ celé číslo bez znaménka. Možné typy, najdete v části [ \<náhodných >](../standard-library/random.md).  
  
## <a name="members"></a>Členové  
  
||||  
|-|-|-|  
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|  
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|  
  
 Další informace o modulu členy najdete v tématu [ \<náhodných >](../standard-library/random.md).  
  
## <a name="remarks"></a>Poznámky  
 Tato třída šablony popisuje *modul adaptéru* , která vyvolává hodnoty podle opětovném zabalení bits z hodnot vrácených jeho základní modul, výsledkem `W`-bit hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<náhodných >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [\<random>](../standard-library/random.md)

