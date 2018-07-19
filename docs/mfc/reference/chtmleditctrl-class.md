---
title: Chtmleditctrl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
dev_langs:
- C++
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4cc8cdc389edc8abbc424ec8277f759e7f3d81bb
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338565"
---
# <a name="chtmleditctrl-class"></a>Chtmleditctrl – třída
Poskytuje funkce pro ovládací prvek WebBrowser ActiveX v okně MFC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CHtmlEditCtrl: public CWnd,   
    public CHtmlEditCtrlBase<CHtmlEditCtrl>  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Vytvoří `CHtmlEditCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CHtmlEditCtrl::Create](#create)|Vytvoří ovládací prvek WebBrowser ActiveX a připojí ho k `CHtmlEditCtrl` objektu. Tato funkce automaticky umístí do režimu úprav ovládacího prvku WebBrowser ActiveX.|  
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Načte [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) rozhraní na dokument aktuálně načtené obsažený ovládací prvek WebBrowser.|  
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Načte adresu URL pro výchozí dokument k načtení v obsažený ovládací prvek WebBrowser.|  
  
## <a name="remarks"></a>Poznámky  
 Hostované ovládací prvek WebBrowser, které ovládací prvek automaticky přejde do režimu úprav po jeho vytvoření.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [Chtmleditctrlbase –](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxhtml.h  
  
##  <a name="chtmleditctrl"></a>  CHtmlEditCtrl::CHtmlEditCtrl  
 Vytvoří `CHtmlEditCtrl` objektu.  
  
```  
CHtmlEditCtrl();
```  
  
##  <a name="create"></a>  CHtmlEditCtrl::Create  
 Vytvoří ovládací prvek WebBrowser ActiveX a připojí ho k `CHtmlEditCtrl` objektu. WebBrowser ActiveX ovládací prvek automaticky přejde na výchozí dokument a pak se umístí do režimu úprav touto funkcí.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    int nID,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszWindowName*  
 Tento parametr se nepoužívá.  
  
 *dwStyle*  
 Tento parametr se nepoužívá.  
  
 *Rect*  
 Určuje velikost a umístění ovládacího prvku.  
  
 *pParentWnd*  
 Určuje nadřazené okno ovládacího prvku. Nesmí být NULL.  
  
 *nID*  
 Určuje ID ovládacího prvku.  
  
 *pContext*  
 Tento parametr se nepoužívá.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE v případě úspěchu; při neúspěchu hodnotu FALSE.  
  
##  <a name="getdhtmldocument"></a>  CHtmlEditCtrl::GetDHtmlDocument  
 Načte [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) rozhraní na dokument aktuálně načtené obsažený ovládací prvek WebBrowser  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *ppDocument*  
 Rozhraní dokumentu.  
  
##  <a name="getstartdocument"></a>  CHtmlEditCtrl::GetStartDocument  
 Načte adresu URL pro výchozí dokument k načtení v obsažený ovládací prvek WebBrowser.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

