---
title: "RECT – Struktura1 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPRECT
- RECT
dev_langs: C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9d3a33330ace97db19521362384356b58a6c8dca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="rect-structure1"></a>RECT – Struktura1
`RECT` Struktura definuje souřadnice levého a pravého dolního rozích obdélníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagRECT {  
    LONG left;  
    LONG top;  
    LONG right;  
    LONG bottom;  
} RECT;  
```  
  
## <a name="members"></a>Členové  
 `left`  
 Určuje souřadnici x levého horního rohu obdélníku.  
  
 `top`  
 Určuje souřadnici y levého horního rohu obdélníku.  
  
 `right`  
 Určuje souřadnici x v pravém dolním rohu obdélníku.  
  
 `bottom`  
 Určuje souřadnici y pravém dolním rohu obdélníku.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** windef.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CRect – třída](../../atl-mfc-shared/reference/crect-class.md)
