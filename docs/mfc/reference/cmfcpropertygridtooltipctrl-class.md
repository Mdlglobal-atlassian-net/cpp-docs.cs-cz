---
title: CMFCPropertyGridToolTipCtrl – třída
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
ms.openlocfilehash: fc5d6d99c326fba7020e8c5040c3bf28d09f8f0a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754113"
---
# <a name="cmfcpropertygridtooltipctrl-class"></a>CMFCPropertyGridToolTipCtrl – třída

Implementuje ovládací prvek popisku, který [třída CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md) používá k zobrazení popisků.

## <a name="syntax"></a>Syntaxe

```
class CMFCPropertyGridToolTipCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](#cmfcpropertygridtooltipctrl)|Vytvoří `CMFCPropertyGridToolTipCtrl` objekt.|
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCPropertyGridToolTipCtrl::Vytvořit](#create)|Vytvoří okno pro ovládací prvek popisek.|
|[CMFCPropertyGridToolTipCtrl::Deaktivovat](#deactivate)|Deaktivuje a skryje ovládací prvek popisku.|
|[CMFCPropertyGridToolTipCtrl::GetLastRect](#getlastrect)|Vrátí souřadnice poslední pozice ovládacího prvku popisku.|
|[CMFCPropertyGridToolTipCtrl::Skrýt](#hide)|Skryje ovládací prvek popisek.|
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Používá třídy [CWinApp](../../mfc/reference/cwinapp-class.md) přeložit okno zprávy před jejich odesláním do [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows funkce. (Přepíše [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](#settextmargin)|Nastaví mezery mezi textem popisu a ohraničením okna popisku.|
|[CMFCPropertyGridToolTipCtrl::Sledovat](#track)|Zobrazí ovládací prvek popisku.|

## <a name="remarks"></a>Poznámky

Popisky jsou zobrazeny, když ukazatel spočívá na názvu vlastnosti. Třída [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) zobrazí popisek, který je uživatelsnadno čitelný. Obvykle je poloha popisku určena polohou ukazatele. Pomocí této třídy se popisek zobrazí nad názvem vlastnosti a podobá se rozšíření přirozené vlastnosti, takže název vlastnosti je plně viditelný.

Knihovna MFC automaticky vytvoří tento ovládací prvek a použije jej ve [třídě CMFCPropertyGridCtrl](../../mfc/reference/cmfcpropertygridctrl-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit objekt `CMFCPropertyGridToolTipCtrl` třídy a jak zobrazit ovládací prvek popisku.

[!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/cpp/cmfcpropertygridtooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxpropertygridtooltipctrl.h

## <a name="cmfcpropertygridtooltipctrlcmfcpropertygridtooltipctrl"></a><a name="cmfcpropertygridtooltipctrl"></a>CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl

Vytvoří `CMFCPropertyGridToolTipCtrl` objekt.

```
CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl();
```

## <a name="cmfcpropertygridtooltipctrlcreate"></a><a name="create"></a>CMFCPropertyGridToolTipCtrl::Vytvořit

Vytvoří okno pro ovládací prvek popisek.

```
BOOL Create(CWnd* pWndParent);
```

### <a name="parameters"></a>Parametry

*pWndParent*<br/>
[v] Ukazatel na nadřazené okno.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo okno úspěšně vytvořeno; jinak NEPRAVDA.

## <a name="cmfcpropertygridtooltipctrldeactivate"></a><a name="deactivate"></a>CMFCPropertyGridToolTipCtrl::Deaktivovat

Deaktivuje a skryje ovládací prvek popisku.

```cpp
void Deactivate();
```

### <a name="remarks"></a>Poznámky

Tato metoda nastaví poslední pozici a text na prázdné hodnoty, takže budoucí volání [CMFCPropertyGridToolTipCtrl::Track](#track) zobrazí popisek.

## <a name="cmfcpropertygridtooltipctrlgetlastrect"></a><a name="getlastrect"></a>CMFCPropertyGridToolTipCtrl::GetLastRect

Vrátí souřadnice poslední pozice ovládacího prvku popisku.

```cpp
void GetLastRect(CRect& rect) const;
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[out] Obsahuje poslední pozici ovládacího prvku popisku.

## <a name="cmfcpropertygridtooltipctrlhide"></a><a name="hide"></a>CMFCPropertyGridToolTipCtrl::Skrýt

Skryje ovládací prvek popisek.

```cpp
void Hide();
```

## <a name="cmfcpropertygridtooltipctrlsettextmargin"></a><a name="settextmargin"></a>CMFCPropertyGridToolTipCtrl::SetTextMargin

Nastaví mezery mezi textem popisu a ohraničením okna popisku.

```cpp
void SetTextMargin(int nTextMargin);
```

### <a name="parameters"></a>Parametry

*nTextMargin*<br/>
[v] Určuje mezery mezi textem ovládacího prvku popisu a ohraničením okna popisku. Výchozí hodnota je 10 pixelů.

## <a name="cmfcpropertygridtooltipctrltrack"></a><a name="track"></a>CMFCPropertyGridToolTipCtrl::Sledovat

Zobrazí ovládací prvek popisku.

```cpp
void Track(
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>Parametry

*Rect*<br/>
[v] Určuje umístění a velikost ovládacího prvku popisku.

*strText*<br/>
[v] Určuje text, který se má zobrazit v popisku.

### <a name="remarks"></a>Poznámky

Tato metoda zobrazí ovládací prvek popisku v pozici a velikosti určené *rect*. Pokud se pozice, velikost a text od posledního volání této metody nezměnily, nemá tato metoda žádný vliv.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
