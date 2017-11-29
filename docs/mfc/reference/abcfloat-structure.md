---
title: "Abcfloat – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ABCFLOAT
dev_langs: C++
helpviewer_keywords: ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 983439d773a7ded59e09c1385bce4febc9979ef6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="abcfloat-structure"></a>ABCFLOAT – struktura
`ABCFLOAT` Struktura obsahuje A, B a C šířky písma znaku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _ABCFLOAT { /* abcf */  
    FLOAT abcfA;  
    FLOAT abcfB;  
    FLOAT abcfC;  
} ABCFLOAT;  
```  
  
#### <a name="parameters"></a>Parametry  
 *abcfA*  
 Určuje mezery A znaku. Mezery A je vzdálenost přidat na aktuální pozici před kreslení glyf znaku.  
  
 *abcfB*  
 Určuje mezery B znaku. Mezery B je šířka vykresleného část glyf znaku.  
  
 *abcfC*  
 Určuje mezery C znaku. Mezery C je vzdálenost přidat na aktuální pozici zajistit mezera vpravo od glyf znaku.  
  
## <a name="remarks"></a>Poznámky  
 Šířky A, B a C se měří podél řádku základní písma. Znak přírůstku (celková šířka) znaku je součet hodnot mezery A, B a C. A nebo C prostor může být záporná indikující underhangs nebo přesahu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h systému  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)
