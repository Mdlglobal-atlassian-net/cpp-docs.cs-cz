---
title: Abcfloat – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5be39336f3da839dc9b1c7be6a64db54b59f99bd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351612"
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

