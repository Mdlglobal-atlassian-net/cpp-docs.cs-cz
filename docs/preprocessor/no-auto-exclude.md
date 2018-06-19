---
title: no_auto_exclude – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_auto_exclude
dev_langs:
- C++
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b0c8d28e1e9c7306c1a74db90177caf76ca95b0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839519"
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
  
 **Konkrétní END C++**  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)