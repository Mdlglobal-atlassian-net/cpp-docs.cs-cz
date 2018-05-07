---
title: ABC – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61b5f67247b556b37cdf934f94c30947675533e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="abc-structure"></a>ABC – struktura
**ABC** struktura obsahuje šířku znaku v písmo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _ABC { /* abc */  
    int abcA;  
    UINT abcB;  
    int abcC;  
} ABC;  
```  
  
#### <a name="parameters"></a>Parametry  
 *abcA*  
 Určuje mezery A znaku. Mezery A je vzdálenost přidat na aktuální pozici před kreslení glyf znaku.  
  
 *abcB*  
 Určuje mezery B znaku. Mezery B je šířka vykresleného část glyf znaku.  
  
 *abcC*  
 Určuje mezery C znaku. Mezery C je vzdálenost přidat na aktuální pozici zajistit mezera vpravo od glyf znaku.  
  
## <a name="remarks"></a>Poznámky  
 Celková šířka znaku je součtem mezery A, B a C. A nebo C prostor může být záporná indikující underhangs nebo přesahu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h systému  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


