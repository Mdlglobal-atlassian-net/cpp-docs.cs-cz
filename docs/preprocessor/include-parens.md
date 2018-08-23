---
title: include() | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- include()
dev_langs:
- C++
helpviewer_keywords:
- include() attribute
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ebadd9e453e8a34e92acee363d0dd6b6ff765910
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42464802"
---
# <a name="include"></a>include()
**Specifické pro C++**  
  
Zakáže automatické vyloučení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
### <a name="parameters"></a>Parametry  
*Name1*  
První položky mají být nuceně zahrnuty.  
  
*Name2*  
Druhá položka mají být nuceně zahrnuty (v případě potřeby).  
  
## <a name="remarks"></a>Poznámky  
 
Knihovny typů mohou obsahovat definice položek definovaných v systémových hlavičkách nebo jiných knihovnách typů. `#import` se pokouší vyhnout několik chyb definice tak, že tyto položky automaticky vyloučí. Pokud byly vyloučeny položky, jak je uvedeno ve [upozornění kompilátoru (úroveň 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md), a neměl by mít byl tento atribut je možné zakázat automatické vyloučení. Tento atribut může přijmout libovolný počet argumentů, každý se název knihovny typů položky mají být zahrnuty.  
  
**Specifické pro END C++**  
  
## <a name="see-also"></a>Viz také  
 
[atributů #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import – direktiva](../preprocessor/hash-import-directive-cpp.md)