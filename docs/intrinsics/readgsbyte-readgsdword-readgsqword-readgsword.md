---
title: __readgsbyte __readgsdword, __readgsqword __readgsword | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
dev_langs:
- C++
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cc4c44807a40425d4531c747526148837e0a25c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711155"
---
# <a name="readgsbyte-readgsdword-readgsqword-readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword
**Specifické pro Microsoft**  
  
 Čtení paměti z umístění, které určuje posun vzhledem k začátku segmentu GS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __readgsbyte(   
   unsigned long Offset   
);  
unsigned short __readgsword(   
   unsigned long Offset   
);  
unsigned long __readgsdword(   
   unsigned long Offset  
);  
unsigned __int64 __readgsqword(   
   unsigned long Offset   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Posun*<br/>
[in] Posun od začátku `GS` ke čtení z.  
  
## <a name="return-value"></a>Návratová hodnota  
 Obsah paměti byte, word, slovo double nebo quadword (jak je uvedeno podle názvu funkce volaná) v umístění `GS:[Offset]`.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__readgsbyte`|x64|  
|`__readgsdword`|x64|  
|`__readgsqword`|x64|  
|`__readgsword`|x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tyto vnitřní objekty jsou dostupné jenom v režimu jádra a rutiny jsou dostupné jenom jako vnitřní funkce.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)