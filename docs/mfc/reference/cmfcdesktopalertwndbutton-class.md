---
title: CMFCDesktopAlertWndButton – třída
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
ms.openlocfilehash: 5b18a15f8bfd98396acae0558d121b32bc4127c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367630"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton – třída

Umožňuje přidání tlačítek do dialogového okna upozornění na ploše.

## <a name="syntax"></a>Syntaxe

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Name (Název)|Popis|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Výchozí konstruktor.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Name (Název)|Popis|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Určuje, zda se tlačítko zobrazí v oblasti titulků dialogového okna s výstrahou.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Určuje, zda tlačítko zavře dialogové okno výstrahy.|

### <a name="data-members"></a>Členové dat

|||
|-|-|
|Name (Název)|Popis|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Logická hodnota, která určuje, zda je tlačítko zobrazeno v oblasti titulků dialogového okna výstrahy.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Logická hodnota, která určuje, zda tlačítko zavře dialogové okno výstrahy.|

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení nastaví `m_bIsCaptionButton` `m_bIsCloseButton` konstruktor členy a datové členy na NEPRAVDA. Nadřazený `CMFCDesktopAlertDialog` objekt se nastaví `m_bIsCaptionButton` na HODNOTU TRUE, pokud je tlačítko umístěno v oblasti titulků dialogového okna výstrahy. Třída `CMFCDesktopAlertDialog` vytvoří `CMFCDesktopAlertWndButton` objekt, který slouží jako tlačítko, které zavře `m_bIsCloseButton` dialogové okno výstrahy a nastaví na HODNOTU TRUE.

Přidejte `CMFCDesktopAlertWndButton` objekty do objektu stejně `CMFCDesktopAlertDialog` jako libovolné tlačítko. Další informace `CMFCDesktopAlertDialog`naleznete v [tématu CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `SetImage` používat metodu ve `CMFCDesktopAlertWndButton` třídě. Tento fragment kódu je součástí [ukázky ukázky upozornění](../../overview/visual-cpp-samples.md)na ploše .

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CmFCButton](../../mfc/reference/cmfcbutton-class.md)

[CmFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdesktopalertwnd.h

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a>CMFCDesktopAlertWndButton::IsCaptionButton

Určuje, zda se tlačítko zobrazí v oblasti titulků dialogového okna s výstrahou.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je tlačítko zobrazeno v oblasti titulků dialogového okna výstrahy; jinak 0.

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a>CMFCDesktopAlertWndButton::IsCloseButton

Určuje, zda tlačítko zavře dialogové okno výstrahy.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud tlačítko zavře dialogové okno s výstrahou; jinak 0.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)
