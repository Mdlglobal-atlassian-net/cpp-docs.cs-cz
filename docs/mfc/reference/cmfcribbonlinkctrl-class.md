---
title: Třída CMFCRibbonLinkCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::CopyFrom
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetCompactSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetRegularSize
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::GetToolTipText
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::IsDrawTooltipImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDraw
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnDrawMenuImage
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnMouseMove
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OnSetIcon
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::OpenLink
- AFXRIBBONLINKCTRL/CMFCRibbonLinkCtrl::SetLink
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonLinkCtrl [MFC], CMFCRibbonLinkCtrl
- CMFCRibbonLinkCtrl [MFC], CopyFrom
- CMFCRibbonLinkCtrl [MFC], GetCompactSize
- CMFCRibbonLinkCtrl [MFC], GetLink
- CMFCRibbonLinkCtrl [MFC], GetRegularSize
- CMFCRibbonLinkCtrl [MFC], GetToolTipText
- CMFCRibbonLinkCtrl [MFC], IsDrawTooltipImage
- CMFCRibbonLinkCtrl [MFC], OnDraw
- CMFCRibbonLinkCtrl [MFC], OnDrawMenuImage
- CMFCRibbonLinkCtrl [MFC], OnMouseMove
- CMFCRibbonLinkCtrl [MFC], OnSetIcon
- CMFCRibbonLinkCtrl [MFC], OpenLink
- CMFCRibbonLinkCtrl [MFC], SetLink
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9267dd6ab89871bcf8058529f32eb3686be937df
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33368433"
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl – třída
Implementuje hypertextový odkaz, který je umístěn na pásu karet. Po kliknutí na tlačítko se otevře hypertextový odkaz na webové stránce.  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCRibbonLinkCtrl : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|Vytvoří a inicializuje `CMFCRibbonLinkCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(Přepisuje `CMFCRibbonButton::CopyFrom`.)|  
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(Přepisuje [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|  
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|Vrátí hodnotu hypertextový odkaz.|  
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(Přepisuje [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|  
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(Přepisuje [CMFCRibbonButton::GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).)|  
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(Přepisuje `CMFCRibbonButton::IsDrawTooltipImage`.)|  
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(Přepisuje [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|  
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(Přepisuje [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|  
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(Přepisuje `CMFCRibbonButton::OnMouseMove`.)|  
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||  
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|Otevře se webová stránka zadaný v hypertextový odkaz.|  
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|Nastaví hodnotu hypertextový odkaz.|  
  
## <a name="remarks"></a>Poznámky  
 Jakmile vytvoříte hypertextový odkaz, přidat do panelu voláním [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxRibbonLinkCtrl.h  
  
##  <a name="cmfcribbonlinkctrl"></a>  CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl  
 Vytvoří a inicializuje [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md) objektu.  
  
```  
CMFCRibbonLinkCtrl(
    UINT nID,  
    LPCTSTR lpszText,  
    LPCTSTR lpszLink);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `nID`  
 Určuje příkaz ID příkazu, který provede, když se po kliknutí na ovládací prvek odkazu.  
  
 [v] `lpszText`  
 Určuje popisek zobrazíte na ovládací prvek odkazu.  
  
 [v] `lpszLink`  
 Určuje hypertextový odkaz přidružený k ovládacímu prvku odkazu.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí konstruktoru `CMFCRibbonLinkCtrl` třídy. Tento fragment kódu je součástí [pásu karet miniaplikacemi ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]  
  
##  <a name="copyfrom"></a>  CMFCRibbonLinkCtrl::CopyFrom  

  
```  
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `src`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getcompactsize"></a>  CMFCRibbonLinkCtrl::GetCompactSize  

  
```  
virtual CSize GetCompactSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getlink"></a>  CMFCRibbonLinkCtrl::GetLink  
 Vrátí hodnotu hypertextový odkaz.  
  
```  
LPCTSTR GetLink() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota hypertextový odkaz.  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="getregularsize"></a>  CMFCRibbonLinkCtrl::GetRegularSize  

  
```  
virtual CSize GetRegularSize(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettooltiptext"></a>  CMFCRibbonLinkCtrl::GetToolTipText  

  
```  
virtual CString GetToolTipText() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondrawmenuimage"></a>  CMFCRibbonLinkCtrl::OnDrawMenuImage  

  
```  
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `CDC*`  
 [v] `CRect`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="isdrawtooltipimage"></a>  CMFCRibbonLinkCtrl::IsDrawTooltipImage  

  
```  
virtual BOOL IsDrawTooltipImage() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="ondraw"></a>  CMFCRibbonLinkCtrl::OnDraw  

  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `pDC`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onmousemove"></a>  CMFCRibbonLinkCtrl::OnMouseMove  

  
```  
virtual void OnMouseMove(CPoint point);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `point`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="onseticon"></a>  CMFCRibbonLinkCtrl::OnSetIcon  

  
```  
virtual void OnSetIcon();
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="openlink"></a>  CMFCRibbonLinkCtrl::OpenLink  
 Otevře se webová stránka zadaný v hypertextový odkaz.  
  
```  
BOOL OpenLink();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud byl úspěšně; otevřít související webové stránky v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Otevře na webové stránce pomocí přidruženého hypertextového odkazu `CMFCRibbonLinkCtrl` objektu.  
  
##  <a name="setlink"></a>  CMFCRibbonLinkCtrl::SetLink  
 Nastaví hodnotu hypertextový odkaz.  
  
```  
void SetLink(LPCTSTR lpszLink);
```  
  
### <a name="parameters"></a>Parametry  
 [v] `lpszLink`  
 Určuje text hypertextového odkazu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
