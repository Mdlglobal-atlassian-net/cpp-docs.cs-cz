---
title: Paintstruct – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- PAINTSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75a3db6c6beb18afe2303b464fcab290b2e132fc
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338207"
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT – struktura
`PAINTSTRUCT` Struktura obsahuje informace, které slouží k vykreslení klientské oblasti okna.  
  
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
 Určuje kontext zobrazení má být použit pro kreslení.  
  
 *fErase*  
 Určuje, jestli potřebuje překreslit na pozadí. Není 0, pokud aplikace byste ho překreslit na pozadí. Aplikace je zodpovědné za vykreslování na pozadí, pokud se vytvoří okno Windows-třídy bez štětec pozadí (viz popis `hbrBackground` člen [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) struktura v sadě Windows SDK).  
  
 *rcPaint*  
 Určuje horní vlevo a pravém dolním rohu obdélníku, ve které je požadováno pro malování.  
  
 *fRestore*  
 Vyhrazeným členem. Používá se interně ve Windows.  
  
 *fIncUpdate*  
 Vyhrazeným členem. Používá se interně ve Windows.  
  
 *rgbReserved [16]*  
 Vyhrazeným členem. Vyhrazeným blokem paměť používaná interně ve Windows.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** winuser  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

