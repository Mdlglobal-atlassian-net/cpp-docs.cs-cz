---
title: "no_auto_exclude – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- no_auto_exclude
dev_langs:
- C++
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 492e906b542ee8f378a350b04abfb1ec2e738801
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="noautoexclude"></a>no_auto_exclude
**Konkrétní C++**  
  
 Zakáže automatické vyloučení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
no_auto_exclude  
```  
  
## <a name="remarks"></a>Poznámky  
 Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. `#import` pokusí se vyhnout se tak, že tyto položky automaticky vyloučíte více chybám definice. Když to uděláte, [upozornění kompilátoru (úroveň 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) dojde u jednotlivých položek, které se mají vyloučit. Toto automatické vyloučení můžete zakázat pomocí tohoto atributu.  
  
 Konkrétní END C++  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)