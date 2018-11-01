---
title: Cmfcspinbuttonctrl – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: ecc8a010b534515850752f7d83c9a9976f14ddfc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50567515"
---
# <a name="cmfcspinbuttonctrl-class"></a>Cmfcspinbuttonctrl – třída

`CMFCSpinButtonCtrl` Třída podporuje vizuálního správce, který vykreslí ovládací prvek číselníku.

## <a name="syntax"></a>Syntaxe

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Výchozí konstruktor.|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Překreslí aktuální ovládací prvek typu číselník tlačítko.|

## <a name="remarks"></a>Poznámky

Nakreslete ovládací prvek číselníku ve vaší aplikaci pomocí Správce vzhledu, nahraďte všechny výskyty `CSpinButtonCtrl` třídy s `CMFCSpinButtonCtrl` třídy.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCSpinButtonCtrl` třídy a použít jeho `Create` metoda.

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Cspinbuttonctrl –](../../mfc/reference/cspinbuttonctrl-class.md)

[Cmfcspinbuttonctrl –](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxspinbuttonctrl.h

##  <a name="ondraw"></a>  CMFCSpinButtonCtrl::OnDraw

Překreslí aktuální ovládací prvek typu číselník tlačítko.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*primární řadič domény*<br/>
[in] Ukazatel na kontext zařízení.

### <a name="remarks"></a>Poznámky

Rámec volá `CMFCSpinButtonCtrl::OnPaint` metodu ke zpracování [CWnd::OnPaint](../../mfc/reference/cwnd-class.md#onpaint) zprávu, a že metoda volá to `CMFCSpinButtonCtrl::OnDraw` metody. Přepsáním této metody můžete přizpůsobit tak, jak rozhraní nakreslí otočný ovládací prvek tlačítko.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager – třída](../../mfc/reference/cmfcvisualmanager-class.md)
