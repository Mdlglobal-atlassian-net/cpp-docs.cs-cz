---
title: Definice makra NMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5997eee052ebba198e1fb52da35322c65a32627b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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
 [Makra a příkaz NMAKE](../build/macros-and-nmake.md)