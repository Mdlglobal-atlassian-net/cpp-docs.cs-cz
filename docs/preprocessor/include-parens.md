---
title: include() | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- include()
dev_langs:
- C++
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da6a8bfc67f63caa8ee1f2699c8bb8675dbae775
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="include"></a>include()
**Konkrétní C++**  
  
 Zakáže automatické vyloučení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### <a name="parameters"></a>Parametry  
 `Name1`  
 První položka vynuceně zahrnuty.  
  
 `Name2`  
 Druhá položka bude nuceně zahrnuta (v případě potřeby).  
  
## <a name="remarks"></a>Poznámky  
 Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. `#import` pokusí se vyhnout se tak, že tyto položky automaticky vyloučíte více chybám definice. Pokud byly vyloučeny položky, jako je indikován [upozornění kompilátoru (úroveň 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), a neměl by mít byl tento atribut slouží k zakázání automatické vyloučení. Tento atribut může trvat libovolný počet argumentů, každý se název položky knihovny typů, které mají být zahrnuty.  
  
 Konkrétní END C++  
  
## <a name="see-also"></a>Viz také  
 [#import – atributy](../preprocessor/hash-import-attributes-cpp.md)   
 [#import – direktiva](../preprocessor/hash-import-directive-cpp.md)