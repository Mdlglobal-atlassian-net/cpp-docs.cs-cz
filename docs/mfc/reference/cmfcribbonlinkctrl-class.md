---
title: CMFCRibbonLinkCtrl – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 3c0cbe843aac172464683288d61e2aec2af60b68
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753566"
---
# <a name="cmfcribbonlinkctrl-class"></a>CMFCRibbonLinkCtrl – třída

Implementuje hypertextový odkaz, který je umístěn na pásu karet. Hypertextový odkaz otevře webovou stránku po klepnutí na ni.
Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonLinkCtrl : public CMFCRibbonButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](#cmfcribbonlinkctrl)|Vytvoří a inicializuje `CMFCRibbonLinkCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonLinkCtrl::CopyFrom](#copyfrom)|(Přepíše `CMFCRibbonButton::CopyFrom`.)|
|[CMFCRibbonLinkCtrl::GetCompactSize](#getcompactsize)|(Přepíše [CMFCRibbonButton::GetCompactSize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize).)|
|[CMFCRibbonLinkCtrl::GetLink](#getlink)|Vrátí hodnotu hypertextového odkazu.|
|[CMFCRibbonLinkCtrl::GetRegularSize](#getregularsize)|(Přepíše [CMFCRibbonButton::GetRegularSize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize).)|
|[CMFCRibbonLinkCtrl::GetToolTipText](#gettooltiptext)|(Přepíše [CMFCRibbonButton::GetToolTipText](../../mfc/reference/cmfcribbonbutton-class.md#gettooltiptext).)|
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](#isdrawtooltipimage)|(Přepíše `CMFCRibbonButton::IsDrawTooltipImage`.)|
|[CMFCRibbonLinkCtrl::OnDraw](#ondraw)|(Přepíše [CMFCRibbonButton::OnDraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw).)|
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](#ondrawmenuimage)|(Přepíše [CMFCRibbonBaseElement::OnDrawMenuImage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage).)|
|[CMFCRibbonLinkCtrl::OnMouseMove](#onmousemove)|(Přepíše `CMFCRibbonButton::OnMouseMove`.)|
|[CMFCRibbonLinkCtrl::OnSetIcon](#onseticon)||
|[CMFCRibbonLinkCtrl::OpenLink](#openlink)|Otevře webovou stránku zadanou v hypertextovém odkazu.|
|[CMFCRibbonLinkCtrl::SetLink](#setlink)|Nastaví hodnotu hypertextového odkazu.|

## <a name="remarks"></a>Poznámky

Po vytvoření hypertextového odkazu jej přidejte do panelu voláním [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)\
啦&nbsp;[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;啦&nbsp;[CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonLinkCtrl.h

## <a name="cmfcribbonlinkctrlcmfcribbonlinkctrl"></a><a name="cmfcribbonlinkctrl"></a>CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl

Vytvoří a inicializuje objekt [CMFCRibbonLinkCtrl.](../../mfc/reference/cmfcribbonlinkctrl-class.md)

```
CMFCRibbonLinkCtrl(
    UINT nID,
    LPCTSTR lpszText,
    LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] Určuje ID příkazu, který se provede po klepnutí na ovládací prvek propojení.

*lpszText*<br/>
[v] Určuje popisek, který se má zobrazit v ovládacím prvku propojení.

*lpszLink*<br/>
[v] Určuje hypertextový odkaz přidružený k ovládacímu prvku propojení.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat konstruktor `CMFCRibbonLinkCtrl` třídy. Tento fragment kódu je součástí [ukázky miniaplikací na pásu karet](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_RibbonGadgets#1](../../mfc/reference/codesnippet/cpp/cmfcribbonlinkctrl-class_1.cpp)]

## <a name="cmfcribbonlinkctrlcopyfrom"></a><a name="copyfrom"></a>CMFCRibbonLinkCtrl::CopyFrom

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>Parametry

[v] *src*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonlinkctrlgetcompactsize"></a><a name="getcompactsize"></a>CMFCRibbonLinkCtrl::GetCompactSize

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[v] *pDC*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonlinkctrlgetlink"></a><a name="getlink"></a>CMFCRibbonLinkCtrl::GetLink

Vrátí hodnotu hypertextového odkazu.

```
LPCTSTR GetLink() const;
```

### <a name="return-value"></a>Návratová hodnota

Aktuální hodnota hypertextového odkazu.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonlinkctrlgetregularsize"></a><a name="getregularsize"></a>CMFCRibbonLinkCtrl::GetRegularSize

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[v] *pDC*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonlinkctrlgettooltiptext"></a><a name="gettooltiptext"></a>CMFCRibbonLinkCtrl::GetToolTipText

```
virtual CString GetToolTipText() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonlinkctrlondrawmenuimage"></a><a name="ondrawmenuimage"></a>CMFCRibbonLinkCtrl::OnDrawMenuImage

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>Parametry

[v] *CDC&#42;*<br/>
[v] *CRect*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonlinkctrlisdrawtooltipimage"></a><a name="isdrawtooltipimage"></a>CMFCRibbonLinkCtrl::IsDrawTooltipImage

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonlinkctrlondraw"></a><a name="ondraw"></a>CMFCRibbonLinkCtrl::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

[v] *pDC*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonlinkctrlonmousemove"></a><a name="onmousemove"></a>CMFCRibbonLinkCtrl::OnMouseMove

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>Parametry

[v] *bod*<br/>

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonlinkctrlonseticon"></a><a name="onseticon"></a>CMFCRibbonLinkCtrl::OnSetIcon

```
virtual void OnSetIcon();
```

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonlinkctrlopenlink"></a><a name="openlink"></a>CMFCRibbonLinkCtrl::OpenLink

Otevře webovou stránku zadanou v hypertextovém odkazu.

```
BOOL OpenLink();
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla přidružená webová stránka úspěšně otevřena; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Otevře webovou stránku pomocí hypertextového odkazu přidruženého k objektu. `CMFCRibbonLinkCtrl`

## <a name="cmfcribbonlinkctrlsetlink"></a><a name="setlink"></a>CMFCRibbonLinkCtrl::SetLink

Nastaví hodnotu hypertextového odkazu.

```cpp
void SetLink(LPCTSTR lpszLink);
```

### <a name="parameters"></a>Parametry

*lpszLink*<br/>
[v] Určuje text hypertextového odkazu.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton – třída](../../mfc/reference/cmfcribbonbutton-class.md)
