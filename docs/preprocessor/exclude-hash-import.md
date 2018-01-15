---
title: "vyloučit (#import) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: exclude
dev_langs: C++
helpviewer_keywords: exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd63eed4eea9404fd0a542c0be20f1770e461508
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)