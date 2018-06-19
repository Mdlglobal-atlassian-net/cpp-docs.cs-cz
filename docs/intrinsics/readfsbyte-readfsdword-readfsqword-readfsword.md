---
title: __readfsbyte, __readfsdword, __readfsqword, __readfsword | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readfsword
- __readfsdword
- __readfsbyte
- __readfsqword
dev_langs:
- C++
helpviewer_keywords:
- __readfsword intrinsic
- readfsword intrinsic
- __readfsdword intrinsic
- readfsbyte intrinsic
- __readfsbyte intrinsic
- readfsdword intrinsic
- readfsqword intrinsic
- __readfsqword intrinsic
ms.assetid: f6ee7203-4179-402c-a464-0746c84ce6ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a2dc016dbd2b17552d50dfdedd1208dcd3e6af22
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333193"
---
# <a name="readfsbyte-readfsdword-readfsqword-readfsword"></a>__readfsbyte, __readfsdword, __readfsqword, __readfsword
**Konkrétní Microsoft**  
  
 Čtení paměti z umístění určeného posun vzhledem k začátku segmentu služby FS.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned char __readfsbyte(   
   unsigned long Offset   
);  
unsigned short __readfsword(   
   unsigned long Offset   
);  
unsigned long __readfsdword(   
   unsigned long Offset  
);  
unsigned __int64 __readfsqword(   
   unsigned long Offset   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `Offset`  
 Posun od začátku `FS` číst z.  
  
## <a name="return-value"></a>Návratová hodnota  
 Obsah paměti bajtů, word, doubleword nebo quadword (označeno název volaná funkce) v umístění `FS:[Offset]`.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__readfsbyte`|x86|  
|`__readfsdword`|x86|  
|`__readfsqword`|x86|  
|`__readfsword`|x86|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tyto rutiny jsou k dispozici pouze jako vnitřní funkce.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)