---
title: Cmfcdesktopalertwndbutton – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
ms.openlocfilehash: 639342e0a09a6e970478fce1b5aac629f03c2015
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776944"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>Cmfcdesktopalertwndbutton – třída

Umožňuje tlačítka pro přidání do klasické pracovní plochy dialogového okna výstrah.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name|Popis|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Výchozí konstruktor.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name|Popis|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Určuje, zda je zobrazeno tlačítko v oblasti Titulek dialogového okna Výstraha.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Určuje, zda tlačítko zavře dialogové okno upozornění.|

### <a name="data-members"></a>Datové členy

|||
|-|-|
|Name|Popis|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Logická hodnota určující, zda je zobrazeno tlačítko v oblasti Titulek dialogového okna Výstraha.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Logická hodnota určující, zda tlačítko zavře dialogové okno upozornění.|

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, konstruktor nastaví `m_bIsCaptionButton` a `m_bIsCloseButton` datové členy na hodnotu FALSE. Nadřazené `CMFCDesktopAlertDialog` objektu sady `m_bIsCaptionButton` na hodnotu TRUE, pokud tlačítko je umístěný v oblasti Titulek dialogového okna Výstraha. `CMFCDesktopAlertDialog` Vytvoří třídu `CMFCDesktopAlertWndButton` objekt, který slouží jako tlačítko, které zavření dialogového okna výstrah pole a nastaví `m_bIsCloseButton` na hodnotu TRUE.

Přidat `CMFCDesktopAlertWndButton` objektů do `CMFCDesktopAlertDialog` jak by jakékoli tlačítko Přidat. Další informace o `CMFCDesktopAlertDialog`, naleznete v tématu [cmfcdesktopalertdialog – třída](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `SetImage` metodu `CMFCDesktopAlertWndButton` třídy. Tento fragment kódu je součástí [Desktopu výstrah demonstrační ukázka](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdesktopalertwnd.h

##  <a name="iscaptionbutton"></a>  CMFCDesktopAlertWndButton::IsCaptionButton

Určuje, zda je zobrazeno tlačítko v oblasti Titulek dialogového okna Výstraha.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud na tlačítko se zobrazí v oblasti popisek pole dialogového okna výstrah. jinak 0.

##  <a name="isclosebutton"></a>  CMFCDesktopAlertWndButton::IsCloseButton

Určuje, zda tlačítko zavře dialogové okno upozornění.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud tlačítko zavření dialogového okna Výstraha; jinak 0.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertDialog – třída](../../mfc/reference/cmfcdesktopalertdialog-class.md)
