---
title: Cmfcribbonseparator – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9112a6790175709a2575319c6f71a55d1303a83
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705312"
---
# <a name="cmfcribbonseparator-class"></a>Cmfcribbonseparator – třída
Implementuje oddělovač pásu karet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonSeparator : public CMFCRibbonBaseElement  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|Vytvoří `CMFCRibbonSeparator` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Oddělovač, který se přidá **příkazy** v seznamu **vlastní** dialogové okno. (Přepíše [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|  
|`CMFCRibbonSeparator::CreateObject`|Rozhraní používá k vytvoření dynamické instance tohoto typu třídy.|  
|`CMFCRibbonSeparator::GetThisClass`|Používá k získání ukazatele na rámec [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený k typu třídy.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Metoda kopírování, která nastaví oddělovač členské proměnné z jiného objektu.|  
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Vrátí velikost položky oddělovače.|  
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Označuje, zda se jedná o oddělovač.|  
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Označuje, zda se jedná o zarážku.|  
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Volá se systémem na oddělovač nakreslit na pásu karet nebo panel nástrojů Rychlý přístup.|  
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Volá se v systému k vykreslení oddělovač **příkazy** seznamu.|  
  
## <a name="remarks"></a>Poznámky  
 Oddělovač pásu karet je svislé nebo vodorovné čáry, logicky odděluje prvky pásu karet. Oddělovačem může vykreslit v ovládacím prvku pás karet, hlavní nabídky, stavový panel pásu karet a panelu nástrojů Rychlý přístup.  
  
 Pokud chcete použít oddělovače ve vaší aplikaci, vytvořit nový objekt a přidat do nabídky hlavní aplikace, jak je znázorněno zde:  
  
```  
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...  
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```  
Volání [CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) přidat oddělovače na panely pásu karet. Oddělovače jsou přiděleny a přidali interně pomocí `AddSeparator` metody.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [Cmfcribbonseparator –](../../mfc/reference/cmfcribbonseparator-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxbaseribbonelement.h  
  
##  <a name="addtolistbox"></a>  CMFCRibbonSeparator::AddToListBox  
 Oddělovač, který se přidá **příkazy** v seznamu **vlastní** dialogové okno.  
  
```  
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,  
    BOOL bDeep);
```  
  
### <a name="parameters"></a>Parametry  
*pWndListBox*<br/>
[in] Ukazatel **příkazy** seznam, kde se přidá oddělovače.  
  
*bDeep*<br/>
[in] Ignorovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule na řetězec v poli určeném *pWndListBox*.  
  
##  <a name="cmfcribbonseparator"></a>  CMFCRibbonSeparator::CMFCRibbonSeparator  
 Vytvoří `CMFCRibbonSeparator` objektu.  
  
```  
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
*bIsHoriz*<br/>
[in] Hodnota TRUE znamená, že oddělovač je vodorovné; Pokud má hodnotu FALSE, oddělovač je svislý.  
  
### <a name="remarks"></a>Poznámky  
 Vodorovné oddělovače jsou použité v nabídkách aplikace. Svislé oddělovače se používají v panelech nástrojů.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonSeparator` třídy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]  
  
##  <a name="copyfrom"></a>  CMFCRibbonSeparator::CopyFrom  
 Metoda kopírování, která nastaví oddělovač členské proměnné z jiného objektu.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parametry  
*src*<br/>
[in] Zdroj pásu karet elementu, který chcete kopírovat.  
  
##  <a name="getregularsize"></a>  CMFCRibbonSeparator::GetRegularSize  
 Vrátí velikost položky oddělovače.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
*primární řadič domény*<br/>
[in] Ukazatel na obsah zařízení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost oddělovač v kontextu daného zařízení.  
  
##  <a name="isseparator"></a>  CMFCRibbonSeparator::IsSeparator  
 Označuje, zda se jedná o oddělovač.  
  
```  
virtual BOOL IsSeparator() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy TRUE pro tuto třídu.  
  
##  <a name="istabstop"></a>  CMFCRibbonSeparator::IsTabStop  
 Označuje, zda se jedná o zarážku.  
  
```  
virtual BOOL IsTabStop() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy hodnotu FALSE pro tuto třídu.  
  
### <a name="remarks"></a>Poznámky  
 Oddělovač pásu karet není konec tabulátoru.  
  
##  <a name="ondraw"></a>  CMFCRibbonSeparator::OnDraw  
 Volá se systémem na oddělovač nakreslit na pásu karet nebo panel nástrojů Rychlý přístup.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
*primární řadič domény*<br/>
[in] Ukazatel na kontext zařízení.  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonSeparator::OnDrawOnList  
 Volá se v systému k vykreslení oddělovač **příkazy** seznamu.  
  
```  
virtual void OnDrawOnList(
    CDC* pDC,  
    CString strText,  
    int nTextOffset,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Popis|  
|*primární řadič domény*|[in] Ukazatel na kontext zařízení.|  
|*strText*|[in] Text zobrazený v seznamu.|  
|*nTextOffset*|[in] Vzdálenost mezi textem a levé straně ohraničující obdélník.|  
|*Rect*|[in] Určuje ohraničující obdélník.|  
|*bIsSelected*|[in] Ignorovat.|  
|*bHighlighted*|[in] Ignorovat.|  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
