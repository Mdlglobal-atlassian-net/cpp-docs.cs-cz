---
title: Nccalcsize_params – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- NCCALCSIZE_PARAMS
dev_langs:
- C++
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 07db612cb6dbde0dd762cf709ac6040bbd836c4b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369720"
---
# <a name="nccalcsizeparams-structure"></a>NCCALCSIZE_PARAMS – struktura
`NCCALCSIZE_PARAMS` Struktura obsahuje informace, které aplikace můžete použít při zpracování `WM_NCCALCSIZE` zpráva k výpočtu velikosti, pozice a platný obsah klientské oblasti časového období.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagNCCALCSIZE_PARAMS {  
    RECT rgrc[3];  
    PWINDOWPOS lppos;  
} NCCALCSIZE_PARAMS;  
```  
  
#### <a name="parameters"></a>Parametry  
 *rgrc*  
 Určuje pole obdélníky. První obsahuje nové souřadnice okno, které byl přesunut nebo změně velikosti. Druhý obsahuje souřadnice okna předtím, než byl přesunut nebo změně velikosti. Třetí obsahuje souřadnice oblasti klienta časového období před byl přesunut nebo změně velikosti. Pokud je okno podřízeného okna, souřadnice jsou relativní vzhledem k klientské oblasti nadřazeného okna. Pokud je okno okno nejvyšší úrovně, souřadnice jsou relativní vzhledem k obrazovce.  
  
 *lppos*  
 Odkazuje na [windowpos –](../../mfc/reference/windowpos-structure1.md) struktura, která obsahuje velikost a umístění hodnoty zadané v operaci, která způsobila okno na přesunutí nebo změně velikosti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

