---
title: ABC – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 2c9aac181edb12df8904a2bc6d891d59c0067ecc
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339316"
---
# <a name="abc-structure"></a>ABC – struktura
`ABC` Struktura obsahuje Šířka znaku v písma TrueType.  
  
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
 Určuje mezery A znaku. Mezery A je vzdálenost k přidání do aktuální pozici před kreslením glyf znaku.  
  
 *abcB*  
 Určuje mezery B znaku. Mezery B je šířku části vykresleného glyf znaku.  
  
 *abcC*  
 Určuje mezery C znaku. Mezery C je vzdálenost k přidání do aktuální pozici, aby poskytují napravo od glyf znaku prázdný znak.  
  
## <a name="remarks"></a>Poznámky  
 Celková šířka znaku je součtem mezery A, B a C. A nebo pole jazyka C může být záporná hodnota, při označení underhangs nebo přesahu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


