---
title: Třída CMFCRibbonSeparator | Microsoft Docs
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
ms.openlocfilehash: bed63f6752f0335e3c1917e6597e7f8b096c8df6
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37039792"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator – třída
Implementuje oddělovače pásu karet.  
  
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
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|Přidá oddělovač, který má **příkazy** v seznamu **přizpůsobit** dialogové okno. (Přepisuje [CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox).)|  
|`CMFCRibbonSeparator::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|`CMFCRibbonSeparator::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|||  
|-|-|  
|Název|Popis|  
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|Metoda kopírování, která nastaví proměnné oddělovače člena z jiného objektu.|  
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|Vrátí velikost oddělovač.|  
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|Určuje, zda se jedná o oddělovač.|  
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|Určuje, zda se jedná o zarážku.|  
|[CMFCRibbonSeparator::OnDraw](#ondraw)|Volá se v systému k vykreslení oddělovače na pásu karet nebo panel nástrojů Rychlý přístup.|  
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|Volá kreslení oddělovače v systému **příkazy** seznamu.|  
  
## <a name="remarks"></a>Poznámky  
 Oddělovač pásu karet je svislé nebo vodorovné čáry, logicky odděluje pásu karet elementy. Oddělovač, mohou být založeny na řízení pásu karet, v nabídce hlavní aplikace, stavového řádku pásu karet a panelu nástrojů Rychlý přístup.  
  
 Chcete-li použít oddělovače v aplikaci, vytvořit nový objekt a přidejte ho do hlavní aplikace nabídky, jak je vidět tady:  
  
```  
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...  
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```  
Volání [CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator) Přidání oddělovačů do panelů pásu karet. Oddělovače se přidělené a přidají se interně pomocí `AddSeparator` metoda.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxbaseribbonelement.h  
  
##  <a name="addtolistbox"></a>  CMFCRibbonSeparator::AddToListBox  
 Přidá oddělovač, který má **příkazy** v seznamu **přizpůsobit** dialogové okno.  
  
```  
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,  
    BOOL bDeep);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pWndListBox*  
 Ukazatel **příkazy** seznamu, kde se přidá oddělovače.  
  
 [v] *bDeep*  
 Ignorovat.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index počítaný od nuly na řetězec v seznamu určeného *pWndListBox*.  
  
##  <a name="cmfcribbonseparator"></a>  CMFCRibbonSeparator::CMFCRibbonSeparator  
 Vytvoří `CMFCRibbonSeparator` objektu.  
  
```  
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *bIsHoriz*  
 Pokud `TRUE`, oddělovače je vodorovný; Pokud `FALSE`, oddělovače je svislý.  
  
### <a name="remarks"></a>Poznámky  
 Vodorovné oddělovače jsou použité v nabídkách aplikace. Svislé oddělovačů se používají v panelech nástrojů.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCRibbonSeparator` třídy.  
  
 [!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]  
  
##  <a name="copyfrom"></a>  CMFCRibbonSeparator::CopyFrom  
 Metoda kopírování, která nastaví proměnné oddělovače člena z jiného objektu.  
  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *Src*  
 Element source pásu karet pro kopírování z.  
  
##  <a name="getregularsize"></a>  CMFCRibbonSeparator::GetRegularSize  
 Vrátí velikost oddělovač.  
  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na obsah zařízení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost oddělovače v kontextu daného zařízení.  
  
##  <a name="isseparator"></a>  CMFCRibbonSeparator::IsSeparator  
 Určuje, zda se jedná o oddělovač.  
  
```  
virtual BOOL IsSeparator() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `TRUE` pro tuto třídu.  
  
##  <a name="istabstop"></a>  CMFCRibbonSeparator::IsTabStop  
 Určuje, zda se jedná o zarážku.  
  
```  
virtual BOOL IsTabStop() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vždy `FALSE` pro tuto třídu.  
  
### <a name="remarks"></a>Poznámky  
 Oddělovač pásu karet není zarážku.  
  
##  <a name="ondraw"></a>  CMFCRibbonSeparator::OnDraw  
 Volá se v systému k vykreslení oddělovače na pásu karet nebo panel nástrojů Rychlý přístup.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *primárního řadiče domény*  
 Ukazatel na kontextu zařízení.  
  
##  <a name="ondrawonlist"></a>  CMFCRibbonSeparator::OnDrawOnList  
 Volá kreslení oddělovače v systému **příkazy** seznamu.  
  
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
|[v] *primárního řadiče domény*|Ukazatel na kontextu zařízení.|  
|[v] *strText*|Text zobrazovaný v seznamu.|  
|[v] *nTextOffset*|Mezera mezi textem a levé straně ohraničující obdélník.|  
|[v] *Rect –*|Určuje ohraničující obdélník.|  
|[v] *bIsSelected*|Ignorovat.|  
|[v] *bHighlighted*|Ignorovat.|  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)
