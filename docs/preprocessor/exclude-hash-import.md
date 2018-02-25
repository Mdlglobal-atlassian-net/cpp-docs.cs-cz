---
title: "vyloučit (#import) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- exclude
dev_langs:
- C++
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d553b706d4a2c21aacf23ef5ee17cca372b9c89
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="exclude-import"></a>exclude (#import)
**Konkrétní C++**  
  
 Vyloučí položky z generovaných souborů hlaviček knihoven typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
#### <a name="parameters"></a>Parametry  
 `Name1`  
 První položka, která má být vyloučena.  
  
 `Name2`  
 Druhá položka, která má být vyloučena (je-li zapotřebí).  
  
## <a name="remarks"></a>Poznámky  
 Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. Tento atribut může přijmout libovolný počet argumentů, přičemž každý z nich je položkou knihovny typů nejvyšší úrovně, která má být vyloučena.  
  
 Konkrétní END C++  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)