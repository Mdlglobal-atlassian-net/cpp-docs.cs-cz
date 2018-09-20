---
title: Cmfcribbonlinkctrl – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 24dc82015e003b3a2ddbbd202dd6cba9176154eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440079"
---
# <a name="cmfcribbonlinkctrl-class"></a>Cmfcribbonlinkctrl – třída

Implementuje hypertextový odkaz, který je umístěn na pásu karet. Hypertextový odkaz otevře webovou stránku, po kliknutí.
Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.

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
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(Přepíše `CMFCRibbonButton::CopyFrom`.)|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(Přepíše [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|Vrátí hodnotu hypertextový odkaz.|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(Přepíše [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(Přepíše [CMFCRibbonButton::GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(Přepíše `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(Přepíše [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(Přepíše [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(Přepíše `CMFCRibbonButton::OnMouseMove`.)|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|Otevře webovou stránku podle hypertextový odkaz.|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|Nastaví hodnotu hypertextový odkaz.|

## <a name="remarks"></a>Poznámky

Po vytvoření hypertextového odkazu, přidejte ho do panelu voláním [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject –](../../mfc/reference/cobject-class.md) [cmfcribbonbaseelement –](../../mfc/reference/cmfcribbonbaseelement-class.md)

[Cmfcribbonbutton –](../../mfc/reference/cmfcribbonbutton-class.md) [cmfcribbonlinkctrl –](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonLinkCtrl.h

##  <a name="cmfcribbonlinkctrl"></a>  CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

Vytvoří a inicializuje [cmfcribbonlinkctrl –](../../mfc/reference/cmfcribbonlinkctrl-class.md) objektu.

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
[in] Určuje ID příkazu, který se spustí po kliknutí na ovládací prvek odkazu příkazu.

*lpszText*<br/>
[in] Určuje popisek se zobrazí na ovládací prvek odkazu.

*lpszLink*<br/>
[in] Určuje hypertextový odkaz přidružený k ovládacímu prvku odkaz.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití konstruktoru `CMFCRibbonLinkCtrl` třídy. Tento fragment kódu je součástí [miniaplikace na pásu karet ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCRibbonLinkCtrl::CopyFrom


```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

[in] *src*

### <a name="remarks"></a>Poznámky

##  <a name="getcompactsize"></a>  CMFCRibbonLinkCtrl::GetCompactSize


```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[in] *primárního řadiče domény*

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

[in] *primárního řadiče domény*

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

[in] *CDC** [in] *crect –*

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

[in] *primárního řadiče domény*

### <a name="remarks"></a>Poznámky

##  <a name="onmousemove"></a>  CMFCRibbonLinkCtrl::OnMouseMove


```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>Parametry

[in] *bodu*

### <a name="remarks"></a>Poznámky

##  <a name="onseticon"></a>  CMFCRibbonLinkCtrl::OnSetIcon


```
virtual void OnSetIcon();
```

### <a name="remarks"></a>Poznámky

##  <a name="openlink"></a>  CMFCRibbonLinkCtrl::OpenLink

Otevře webovou stránku podle hypertextový odkaz.

```
BOOL OpenLink();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud přidružené webové stránce byl otevřen úspěšně; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Otevře webovou stránku pomocí přidruženého hypertextového odkazu `CMFCRibbonLinkCtrl` objektu.

##  <a name="setlink"></a>  CMFCRibbonLinkCtrl::SetLink

Nastaví hodnotu hypertextový odkaz.

```
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parametry

*lpszLink*<br/>
[in] Určuje text, hypertextový odkaz.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
