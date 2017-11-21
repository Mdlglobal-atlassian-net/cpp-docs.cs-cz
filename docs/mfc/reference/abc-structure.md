---
title: "ABC – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ABC
dev_langs: C++
helpviewer_keywords: ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7cc04527e5fc70feffd5a5fa81dc5149a5ecc130
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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


