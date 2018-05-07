---
title: Minmaxinfo – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MINMAXINFO
dev_langs:
- C++
helpviewer_keywords:
- MINMAXINFO structure [MFC]
ms.assetid: be6fb578-f98a-4581-9ada-be9df308ed2f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12161938f96e5044ae48f9eb5cf380fbc3840d3f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="minmaxinfo-structure"></a>MINMAXINFO – struktura
`MINMAXINFO` Struktura obsahuje informace o maximalizovaném okně velikost okna a pozice a jeho sledování minimální a maximální velikost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagMINMAXINFO {  
    POINT ptReserved;  
    POINT ptMaxSize;  
    POINT ptMaxPosition;  
    POINT ptMinTrackSize;  
    POINT ptMaxTrackSize;  
} MINMAXINFO;  
```  
  
#### <a name="parameters"></a>Parametry  
 *ptReserved*  
 Vyhrazeno pro interní použití.  
  
 *ptMaxSize*  
 Určuje šířku maximalizovaném okně (point.x) a maximalizovaném okně výšku okna (point.y).  
  
 `ptMaxPosition`  
 Určuje pozici na levé straně maximalizovaném okně (point.x) a pozice horní části okna maximalizovaném okně (point.y).  
  
 *ptMinTrackSize*  
 Určuje minimální šířku (point.x) pro sledování a minimální výška (point.y) okna pro sledování.  
  
 *ptMaxTrackSize*  
 Určuje maximální počet sledování šířka (point.x) a maximální výšku (point.y) okna pro sledování.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

