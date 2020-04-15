---
title: Třída CMFCSpinButtonCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: 445b857400d8c82109ca7220b84bac692a2abf89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376180"
---
# <a name="cmfcspinbuttonctrl-class"></a>Třída CMFCSpinButtonCtrl

Třída `CMFCSpinButtonCtrl` podporuje vizuální manažer, který kreslí ovládací prvek číselníku.

## <a name="syntax"></a>Syntaxe

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Výchozí konstruktor.|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCSpinButtonCtrl::Ondraw](#ondraw)|Překreslí aktuální ovládací prvek číselníku.|

## <a name="remarks"></a>Poznámky

Chcete-li použít vizuální manažer k nakreslení ovládacího prvku číselníku ve vaší aplikaci, nahraďte všechny instance `CSpinButtonCtrl` třídy třídou. `CMFCSpinButtonCtrl`

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCSpinButtonCtrl` třídy `Create` a použít jeho metodu.

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxspinbuttonctrl.h

## <a name="cmfcspinbuttonctrlondraw"></a><a name="ondraw"></a>CMFCSpinButtonCtrl::Ondraw

Překreslí aktuální ovládací prvek číselníku.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

### <a name="remarks"></a>Poznámky

Framework volá `CMFCSpinButtonCtrl::OnPaint` metodu pro zpracování [cWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) zprávy a tato `CMFCSpinButtonCtrl::OnDraw` metoda zase volá tuto metodu. Přepsat tuto metodu přizpůsobit způsob, jakým rámec kreslí ovládací prvek číselníku.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager – třída](../../mfc/reference/cmfcvisualmanager-class.md)
