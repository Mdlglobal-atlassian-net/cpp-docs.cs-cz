---
title: Definice makra NMAKE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b355431576a4662062a00ce2c4e44f3a0a52ffdc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="defining-an-nmake-macro"></a>Definice makra NMAKE
## <a name="syntax"></a>Syntaxe  
  
```  
  
macroname=string  
```  
  
## <a name="remarks"></a>Poznámky  
 *Makro* je kombinací písmena, číslice a podtržítka (_), maximálně 1 024 znaků, a je případ citlivé. *Makro* může obsahovat vyvolaná makro. Pokud *makro* se skládá pouze z vyvolané makro, makro volané nemůže být null nebo definován.  
  
 `string` Může být jakékoli pořadí nula nebo více znaků. Řetězec null obsahuje nulový počet znaků nebo pouze mezery ani karty. `string` Může obsahovat makro volání.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
 [Speciální znaky v makrech](../build/special-characters-in-macros.md)  
  
 [Hodnota Null a Nedefinovaná makra](../build/null-and-undefined-macros.md)  
  
 [Místo definice maker](../build/where-to-define-macros.md)  
  
 [Priority v definicích maker](../build/precedence-in-macro-definitions.md)  
  
## <a name="see-also"></a>Viz také  
 [Makra a NMAKE](../build/macros-and-nmake.md)