---
title: "Třída CHtmlEditCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
dev_langs: C++
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3ea794bfcb3d7e62a53ed8423918e5448990dae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl – třída
Poskytuje funkce ovládacího prvku WebBrowser ActiveX v okně knihovny MFC.  
  
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
|[CHtmlEditCtrl::Create](#create)|Vytvoří ovládacího prvku WebBrowser ActiveX a připojí jej k `CHtmlEditCtrl` objektu. Tato funkce automaticky umístí do ovládacího prvku WebBrowser ActiveX do režimu úprav.|  
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Načte [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) rozhraní na dokument momentálně načtených v ovládacím prvku WebBrowser obsažené.|  
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Načte adresu URL výchozí dokument k načtení v ovládacím prvku WebBrowser obsažené.|  
  
## <a name="remarks"></a>Poznámky  
 Hostované WebBrowser, které řízení automaticky umístí do režimu úprav, po jejím vytvoření.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHtmlEditCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxhtml.h  
  
##  <a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl  
 Vytvoří `CHtmlEditCtrl` objektu.  
  
```  
CHtmlEditCtrl();
```  
  
##  <a name="create"></a>CHtmlEditCtrl::Create  
 Vytvoří ovládacího prvku WebBrowser ActiveX a připojí jej k `CHtmlEditCtrl` objektu. WebBrowser ActiveX řízení automaticky přejde na výchozí dokument a pak je umístěn v režimu úprav pomocí této funkce.  
  
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
 `lpszWindowName`  
 Tento parametr se nepoužívá.  
  
 `dwStyle`  
 Tento parametr se nepoužívá.  
  
 `rect`  
 Určuje velikost a umístění ovládacího prvku.  
  
 `pParentWnd`  
 Určuje ovládacího prvku nadřazeného okna. Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku.  
  
 `pContext`  
 Tento parametr se nepoužívá.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí **TRUE** v případě úspěchu **FALSE** při selhání.  
  
##  <a name="getdhtmldocument"></a>CHtmlEditCtrl::GetDHtmlDocument  
 Načte [IHTMLDocument2](https://msdn.microsoft.com/library/aa752574.aspx) rozhraní na dokument momentálně načtených v obsažené ovládacího prvku WebBrowser  
  
```  
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `ppDocument`  
 Rozhraní dokumentu.  
  
##  <a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument  
 Načte adresu URL výchozí dokument k načtení v ovládacím prvku WebBrowser obsažené.  
  
```  
virtual LPCTSTR GetStartDocument();
```  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)

