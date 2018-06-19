---
title: __readcr3 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readcr3
dev_langs:
- C++
helpviewer_keywords:
- __readcr3 intrinsic
ms.assetid: e24392c3-cad7-4788-8f31-94bf2e9e0053
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a632199dcc3318109a6b95f82d718ac3f26fa23
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328380"
---
# <a name="readcr3"></a>__readcr3
**Konkrétní Microsoft**  
  
 Přečte CR3 registrace a vrátí jeho hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned __int64 __readcr3(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Hodnota v CR3 registrace.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__readcr3`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tento vnitřní je k dispozici pouze v režimu jádra a rutiny je k dispozici jako vnitřní pouze.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)