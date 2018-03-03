---
title: "RECT – Struktura1 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LPRECT
- RECT
dev_langs:
- C++
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f4e56c78e717b24390a82e7cbb55670f36369044
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
