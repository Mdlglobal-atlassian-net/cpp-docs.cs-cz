---
title: "Paintstruct – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PAINTSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92583bba3dca60caa2895966a87571dc60805475
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT – struktura
`PAINTSTRUCT` Struktura obsahuje informace, které lze použít k vyplnění klientské oblasti časového období.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagPAINTSTRUCT {  
    HDC hdc;  
    BOOL fErase;  
    RECT rcPaint;  
    BOOL fRestore;  
    BOOL fIncUpdate;  
    BYTE rgbReserved[16];  
} PAINTSTRUCT;  
```  
  
#### <a name="parameters"></a>Parametry  
 *hDC*  
 Identifikuje kontext zobrazení má být použit pro vykreslování.  
  
 *fErase*  
 Určuje, zda musí být překreslen na pozadí. Není 0, pokud aplikace by ho překreslit na pozadí. Aplikace je zodpovědná za kreslení na pozadí, pokud třídy okna Windows je vytvořen bez štětec pozadí plochy (viz popis **hbrBackground** členem [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktura v systému Windows SDK).  
  
 *rcPaint*  
 Určuje horní vlevo a pravém dolním rohu obdélníku, ve kterém se požaduje pro malování.  
  
 *fRestore*  
 Vyhrazené člen. Používá se interně v systému Windows.  
  
 *fIncUpdate*  
 Vyhrazené člen. Používá se interně v systému Windows.  
  
 *rgbReserved [16]*  
 Vyhrazené člen. Blok vyhrazené paměti používaná interně k systému Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

