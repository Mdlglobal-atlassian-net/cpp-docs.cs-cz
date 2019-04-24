---
title: CMFCPropertyGridToolTipCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Create
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Deactivate
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::GetLastRect
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Hide
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::SetTextMargin
- AFXPROPERTYGRIDTOOLTIPCTRL/CMFCPropertyGridToolTipCtrl::Track
helpviewer_keywords:
- CMFCPropertyGridToolTipCtrl [MFC], CMFCPropertyGridToolTipCtrl
- CMFCPropertyGridToolTipCtrl [MFC], Create
- CMFCPropertyGridToolTipCtrl [MFC], Deactivate
- CMFCPropertyGridToolTipCtrl [MFC], GetLastRect
- CMFCPropertyGridToolTipCtrl [MFC], Hide
- CMFCPropertyGridToolTipCtrl [MFC], SetTextMargin
- CMFCPropertyGridToolTipCtrl [MFC], Track
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
ms.openlocfilehash: 6c14ed1f11a7a414332b34566a314459d76b911b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62310471"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl Class

Ovládací prvek implementuje popisek, který [cmfcpropertygridctrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md) používá k zobrazení popisů tlačítek.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Vytvoří `CMFCPropertyGridToolTipCtrl` objektu.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Vytvoří okno pro ovládací prvek tooltip.|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Deaktivuje a skryje ovládací prvek tooltip.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Vrátí souřadnice poslední pozice ovládacího prvku tooltip.|
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|ToolTip – ovládací prvek skryje.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Používá třída [CWinApp](../../mfc/reference/cwinapp-class.md) přeložit okno zprávy před odesláním do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkce Windows. (Přepíše [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Nastaví mezery mezi text popisku a ohraničení okna popisu.|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Zobrazí ovládací prvek tooltip.|

## <a name="remarks"></a>Poznámky

Popisy tlačítek se zobrazí při umístění ukazatele myši na název vlastnosti. [Cmfcpropertygridtooltipctrl –](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) třída zobrazí popis tlačítka tak, aby se snadno čitelné uživatelem. Pozici popisku je obvykle určeno pozici ukazatele. Pomocí této třídy, popisek se zobrazí nad název vlastnosti a podobá rozšíření fyzické vlastnosti tak, aby název vlastnosti není plně viditelný.

Automaticky vytvoří tento ovládací prvek MFC a používá ho v [cmfcpropertygridctrl – třída](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridToolTipCtrl` třídy a jak zobrazit ovládací prvek tooltip.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxpropertygridtooltipctrl.h

##  <a name="cmfcpropertygridtooltipctrl"></a>  CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Vytvoří `CMFCPropertyGridToolTipCtrl` objektu.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

##  <a name="create"></a>  CMFCPropertyGridToolTipCtrl::Create

Vytvoří okno pro ovládací prvek tooltip.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[in] Ukazatel do nadřazeného okna.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud v okně se úspěšně vytvořil; v opačném případě hodnota FALSE.

##  <a name="deactivate"></a>  CMFCPropertyGridToolTipCtrl::Deactivate

Deaktivuje a skryje ovládací prvek tooltip.

```
void Deactivate();
```

### <a name="remarks"></a>Poznámky

Tato metoda nastaví poslední pozice a text na prázdné hodnoty, tak, že budoucí volání [CMFCPropertyGridToolTipCtrl::Track](#track) zobrazit v popisu.

##  <a name="getlastrect"></a>  CMFCPropertyGridToolTipCtrl::GetLastRect

Vrátí souřadnice poslední pozice ovládacího prvku tooltip.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[out] Obsahuje poslední pozice ovládacího prvku tooltip.

##  <a name="hide"></a>  CMFCPropertyGridToolTipCtrl::Hide

ToolTip – ovládací prvek skryje.

```
void Hide();
```

##  <a name="settextmargin"></a>  CMFCPropertyGridToolTipCtrl::SetTextMargin

Nastaví mezery mezi text popisku a ohraničení okna popisu.

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Parametry

*nTextMargin*<br/>
[in] Určuje mezery mezi text ovládacího prvku popisku a ohraničení okna popisu. Výchozí hodnota je 10 pixelů.

##  <a name="track"></a>  CMFCPropertyGridToolTipCtrl::Track

Zobrazí ovládací prvek tooltip.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[in] Určuje umístění a velikost ovládacího prvku tooltip.

*strText*<br/>
[in] Určuje text zobrazený v popisku.

### <a name="remarks"></a>Poznámky

Tato metoda zobrazí ToolTip – ovládací prvek na pozici a velikost určená *rect*. Pokud umístění, velikost a text nebyly změněny od poslední chvíle, kdy byla tato metoda volána, tato metoda nemá žádný vliv.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
