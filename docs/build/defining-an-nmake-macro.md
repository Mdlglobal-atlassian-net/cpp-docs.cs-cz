---
title: Definice makra NMAKE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96799bbd10d442c50d66ac4e84169864b9b989ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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