---
title: Minmaxinfo – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: cf9a6e6a1397b9361df5372af09be8e61d997e62
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37337811"
---
# <a name="minmaxinfo-structure"></a>MINMAXINFO – struktura
`MINMAXINFO` Struktura obsahuje informace o maximální velikosti okna a pozice a jeho sledování minimální a maximální velikost.  
  
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
 Určuje maximální šířku (point.x) a maximální výšku okna (point.y).  
  
 *ptMaxPosition*  
 Určuje pozici levé straně maximalizované okno (point.x) a pozice horní části okna maximalizované (point.y).  
  
 *ptMinTrackSize*  
 Určuje minimální šířku (point.x) pro sledování a minimální výšku (point.y) okna pro sledování.  
  
 *ptMaxTrackSize*  
 Určuje maximální šířku (point.x) pro sledování a maximální výška (point.y) v okně pro sledování.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)

