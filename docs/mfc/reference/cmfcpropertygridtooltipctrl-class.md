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
ms.openlocfilehash: f1b6f626b5f9844c73cd2225a7d6311f5b2f7d4f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505095"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl Class

Implementuje ovládací prvek ToolTip, který [Třída CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) používá k zobrazení popisů tlačítek.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name|Popis|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|`CMFCPropertyGridToolTipCtrl` Vytvoří objekt.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name|Popis|
|[CMFCPropertyGridToolTipCtrl::Create](#create)|Vytvoří okno pro ovládací prvek ToolTip.|
|[CMFCPropertyGridToolTipCtrl::Deactivate](#deactivate)|Deaktivuje a skryje ovládací prvek ToolTip.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Vrátí souřadnice poslední pozice ovládacího prvku ToolTip.|
|[CMFCPropertyGridToolTipCtrl::Hide](#hide)|Skryje ovládací prvek ToolTip.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Používá se třídou [CWinApp](../../mfc/reference/cwinapp-class.md) k překladu zpráv oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Potlačení [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Nastaví mezery mezi textem popisu a ohraničením okna s popisem tlačítka.|
|[CMFCPropertyGridToolTipCtrl::Track](#track)|Zobrazí ovládací prvek ToolTip.|

## <a name="remarks"></a>Poznámky

Pokud se ukazatel myši nachází v názvu vlastnosti, zobrazí se popisy tlačítek. Třída [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) zobrazí popis, aby ji uživatel mohl snadno přečíst. Pozice popisu je obvykle dána umístěním ukazatele. Pomocí této třídy se popisek zobrazí nad názvem vlastnosti a podobá se rozšíření přirozených vlastností, aby byl název vlastnosti plně viditelný.

MFC automaticky vytvoří tento ovládací prvek a použije ho ve [třídě CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridToolTipCtrl` třídy a jak zobrazit ovládací prvek ToolTip.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxpropertygridtooltipctrl.h

##  <a name="cmfcpropertygridtooltipctrl"></a>  CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

`CMFCPropertyGridToolTipCtrl` Vytvoří objekt.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

##  <a name="create"></a>  CMFCPropertyGridToolTipCtrl::Create

Vytvoří okno pro ovládací prvek ToolTip.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
pro Ukazatel na nadřazené okno.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud bylo okno úspěšně vytvořeno; v opačném případě FALSE.

##  <a name="deactivate"></a>  CMFCPropertyGridToolTipCtrl::Deactivate

Deaktivuje a skryje ovládací prvek ToolTip.

```
void Deactivate();
```

### <a name="remarks"></a>Poznámky

Tato metoda nastaví poslední pozici a text na prázdné hodnoty, aby budoucí volání [CMFCPropertyGridToolTipCtrl:: Track](#track) zobrazovala popis tlačítka.

##  <a name="getlastrect"></a>  CMFCPropertyGridToolTipCtrl::GetLastRect

Vrátí souřadnice poslední pozice ovládacího prvku ToolTip.

```
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
mimo Obsahuje poslední pozici ovládacího prvku ToolTip.

##  <a name="hide"></a>  CMFCPropertyGridToolTipCtrl::Hide

Skryje ovládací prvek ToolTip.

```
void Hide();
```

##  <a name="settextmargin"></a>  CMFCPropertyGridToolTipCtrl::SetTextMargin

Nastaví mezery mezi textem popisu a ohraničením okna s popisem tlačítka.

```
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Parametry

*nTextMargin*<br/>
pro Určuje mezeru mezi textem ovládacího prvku ToolTip a ohraničením okna s popisem tlačítka. Výchozí hodnota je 10 pixelů.

##  <a name="track"></a>  CMFCPropertyGridToolTipCtrl::Track

Zobrazí ovládací prvek ToolTip.

```
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parametry

*OBD*<br/>
pro Určuje umístění a velikost ovládacího prvku ToolTip.

*strText*<br/>
pro Určuje text zobrazený v popisu tlačítka.

### <a name="remarks"></a>Poznámky

Tato metoda zobrazí ovládací prvek ToolTip na pozici a velikost určenou v *Rect*. Pokud se pozice, velikost a text od posledního volání této metody nezměnily, tato metoda nemá žádný vliv.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
