---
title: "Třída CSplitterWndEx | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
dev_langs:
- C++
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94ec633718dda81a5183a59eb46387b361d0f004
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx – třída



Představuje vlastní rozděleném okně.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CSplitterWndEx : public CSplitterWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CSplitterWndEx::CSplitterWndEx`|Výchozí konstruktor.|  
|`CSplitterWndEx::~CSplitterWndEx`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|Voláno rámcem k vykreslení rozděleném okně. (Přepisuje [CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter).)|  
  
## <a name="remarks"></a>Poznámky  
 Přepsání `OnDrawSplitter` metodu za účelem přizpůsobení vzhledu součásti grafické rozděleném okně.  
  
 `CSplitterWndEx` Třída se používá spolu s [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder), [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox), a [OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground) metody, které jsou implementováno modulem visual správce. Aby visual manager k vykreslení rozdělovače oken v aplikaci, nahraďte prohlášení o `CSplitterWnd` třídy s `CSplitterWndEx` třídy. Pro aplikace rámce okna je v CMainFrame – třída, která se nachází v mainfrm.h deklarována třídu rozdělovače oken. Příklad, naleznete v části `OutlookDemo` ukázku v adresáři ukázky.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 [CSplitterWnd](csplitterwnd-class.md)  
   
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxsplitterwndex.h  
  
##  <a name="ondrawsplitter"></a>CSplitterWndEx::OnDrawSplitter  
 Voláno rámcem k vykreslení rozděleném okně.  
  
```  
virtual void OnDrawSplitter(  
   CDC* pDC,  
   ESplitType nType,  
   const CRect& rect   
);  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Ukazatel na kontext zařízení. Pokud tento parametr je `NULL`, rozhraní ho překreslí aktivní okno.  
  
 [v]`nType`  
 Jeden z `CSplitterWnd::ESplitType` hodnot výčtu, která určuje prvku rozdělovač okno k vykreslení. Platné hodnoty jsou `splitBox`, `splitBar`, `splitIntersection`, a `splitBorder`.  
  
 [v]`rect`  
 Ohraničující obdélník, který určuje rozměry a umístění k vykreslení elementu zadané rozdělovací okno.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../hierarchy-chart.md)   
 [Třídy](mfc-classes.md)   
 [CSplitterWnd – třída](csplitterwnd-class.md)   
 [CMFCVisualManager – třída](cmfcvisualmanager-class.md)