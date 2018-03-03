---
title: "Třída COleIPFrameWnd | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleIPFrameWnd
- AFXOLE/COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::COleIPFrameWnd
- AFXOLE/COleIPFrameWnd::OnCreateControlBars
- AFXOLE/COleIPFrameWnd::RepositionFrame
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWnd [MFC], COleIPFrameWnd
- COleIPFrameWnd [MFC], OnCreateControlBars
- COleIPFrameWnd [MFC], RepositionFrame
ms.assetid: 24abb2cb-826c-4dda-a287-d8a8900a5763
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f1833cbbbfb6706cffe73770bcd9b61ff755a645
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="coleipframewnd-class"></a>COleIPFrameWnd – třída
Základ pro úpravy okna aplikace na místě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleIPFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleIPFrameWnd::COleIPFrameWnd](#coleipframewnd)|Vytvoří `COleIPFrameWnd` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleIPFrameWnd::OnCreateControlBars](#oncreatecontrolbars)|Voláno rámcem, pokud je aktivován položku pro úpravy na místě.|  
|[COleIPFrameWnd::RepositionFrame](#repositionframe)|Voláno rámcem aby přemístil okno úprav na místě.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída se vytvoří a pozice řídit řádky v rámci okna dokumentu aplikace typu kontejner. Také obstará oznámení vygenerovaná embedded [COleResizeBar](../../mfc/reference/coleresizebar-class.md) objektu, když uživatel změní velikost okna pro úpravy na místě.  
  
 Další informace o používání `COleIPFrameWnd`, najdete v článku [aktivace](../../mfc/activation-cpp.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `COleIPFrameWnd`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="coleipframewnd"></a>COleIPFrameWnd::COleIPFrameWnd  
 Vytvoří `COleIPFrameWnd` objektu a inicializuje informace o jeho stavu na místě, který je uložený ve struktuře typu **OLEINPLACEFRAMEINFO**.  
  
```  
COleIPFrameWnd();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [OLEINPLACEFRAMEINFO](http://msdn.microsoft.com/library/windows/desktop/ms693737) ve Windows SDK.  
  
##  <a name="oncreatecontrolbars"></a>COleIPFrameWnd::OnCreateControlBars  
 Volání framework `OnCreateControlBars` fungovat, pokud je aktivován položku pro úpravy na místě.  
  
```  
virtual BOOL OnCreateControlBars(
    CWnd* pWndFrame,  
    CWnd* pWndDoc);

 
virtual BOOL OnCreateControlBars(
    CFrameWnd* pWndFrame,  
    CFrameWnd* pWndDoc);
```  
  
### <a name="parameters"></a>Parametry  
 *pWndFrame*  
 Ukazatel na oken s rámečkem kontejnerové aplikace.  
  
 *pWndDoc*  
 Ukazatel na úrovni dokumentu okno kontejneru. Může být **NULL** Pokud je aplikace SDI kontejneru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace neprovede žádnou akci. Funkci provést žádné speciální zpracování požadováno, když jsou vytvořeny ovládací pruhy přepište.  
  
##  <a name="repositionframe"></a>COleIPFrameWnd::RepositionFrame  
 Volání framework `RepositionFrame` – členská funkce Rozvrhněte ovládací pruhy a změnit umístění okna pro úpravy v místě, tak, aby všechny viditelné.  
  
```  
virtual void RepositionFrame(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Parametry  
 `lpPosRect`  
 Ukazatel na `RECT` struktura nebo `CRect` objekt obsahující na místě rámce okna na aktuální pozici souřadnice, v pixelech, relativně k klientské oblasti.  
  
 `lpClipRect`  
 Ukazatel na `RECT` struktura nebo `CRect` objekt obsahující na místě rámce okna aktuální výstřižek obdélníku souřadnice, v pixelech, relativně k klientské oblasti.  
  
### <a name="remarks"></a>Poznámky  
 Rozložení ovládací pruhy v okně kontejner se liší od které provádí pomocí jiných než OLE rámce okna. Okně s rámečkem jiných než OLE vypočítá pozice ovládací pruhy a dalších objektů z daného oken s rámečkem velikost, stejně jako volání [CFrameWnd::RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout). Klientské oblasti je co zůstává poté, co je odečten místa pro ovládací pruhy a dalších objektů. A `COleIPFrameWnd` okně na druhé straně umisťuje panely nástrojů v souladu s danou klientské oblasti. Jinými slovy `CFrameWnd::RecalcLayout` funguje "zvenku,", zatímco `COleIPFrameWnd::RepositionFrame` funguje "od zevnitř ven.."  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC HIERSVR](../../visual-cpp-samples.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CFrameWnd – třída](../../mfc/reference/cframewnd-class.md)
