---
title: CMFCBaseVisualManager Class
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
ms.openlocfilehash: 0c26c0c9c9026f8312218b2ac15f83a50a67be79
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292208"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager Class

Vrstva mezi odvozené vizuální vedoucí a rozhraní API Windows motiv.

`CMFCBaseVisualManager` načte UxTheme.dll, pokud je k dispozici a spravuje přístup k rozhraní API Windows motiv metody.

Tato třída je jen pro interní použití.

## <a name="syntax"></a>Syntaxe

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|Vytvoří a inicializuje `CMFCBaseVisualManager` objektu.|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Vykreslí ovládací prvek zaškrtávací políčko pomocí aktuálního motivu Windows.|
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Kreslení pomocí aktuálního motivu Windows ohraničení pole se seznamem.|
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Nakreslí tlačítko rozevíracího pole se seznamem pomocí aktuálního motivu Windows.|
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Kreslení pomocí aktuálního motivu Windows příkazové tlačítko.|
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Nakreslí ovládací prvek přepínač pomocí aktuálního motivu Windows.|
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Nakreslí indikátor průběhu na ovládacím panelu stavu ( [CMFCStatusBar – třída](../../mfc/reference/cmfcstatusbar-class.md)) použitím aktuální motiv Windows.|
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Pomocí aktuální motiv Windows vyplní celé pozadí ovládacího prvku rebar.|
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Získá aktuální motiv Windows.|

### <a name="protected-methods"></a>Chráněné metody

|||
|-|-|
|Název|Popis|
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Volání `CloseThemeData` pro všechny popisovače, kterou jste získali v `UpdateSystemColors`.|
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Volání `OpenThemeData` získání popisovačů pro kreslení různých ovládacích prvků: windows, panely nástrojů, tlačítka a tak dále.|

## <a name="remarks"></a>Poznámky

Není nutné k vytvoření objektů této třídy přímo.

Protože je základní třída pro všechny vizuální vedoucí, ho prostě zavoláte [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), ukazatel na aktuální Visual Manager a přístup k metodám pro `CMFCBaseVisualManager` pomocí tento ukazatel. Pokud máte k zobrazení ovládacího prvku pomocí aktuálního motivu Windows, je ale vhodnější použít `CMFCVisualManagerWindows` rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxvisualmanager.h

##  <a name="cleanupthemes"></a>  CMFCBaseVisualManager::CleanUpThemes

Volání `CloseThemeData` pro všechny popisovače, kterou jste získali v `UpdateSystemColors`.

```
void CleanUpThemes();
```

### <a name="remarks"></a>Poznámky

Pouze pro interní použití.

##  <a name="cmfcbasevisualmanager"></a>  CMFCBaseVisualManager::CMFCBaseVisualManager

Vytvoří a inicializuje `CMFCBaseVisualManager` objektu.

```
CMFCBaseVisualManager();
```

##  <a name="drawcheckbox"></a>  CMFCBaseVisualManager::DrawCheckBox

Vykreslí ovládací prvek zaškrtávací políčko pomocí aktuálního motivu Windows.

```
virtual BOOL DrawCheckBox(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    int nState,
    BOOL bEnabled,
    BOOL bPressed);

);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení

*Rect*<br/>
[in] Ohraničující obdélník zaškrtávací políčko.

*bHighlighted*<br/>
[in] Určuje, zda je zvýrazněn zaškrtávací políčko.

*nState*<br/>
[in], 0 pro není zaškrtnuto, 1 pro normální zaškrtnuté,

2 pro smíšený normální.

*bEnabled*<br/>
[in] Určuje, zda zaškrtávací políčko je dostupné.

*bPressed*<br/>
[in] Určuje, zda se stiskne zaškrtávací políčko.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je povolená rozhraní API motiv; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Hodnoty *nInformace* odpovídají na následující styly zaškrtávací políčko.

|nInformace|Styl zaškrtávacího políčka|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

##  <a name="drawcomboborder"></a>  CMFCBaseVisualManager::DrawComboBorder

Kreslení pomocí aktuálního motivu Windows ohraničení pole se seznamem.

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*Rect*<br/>
[in] Ohraničující obdélník hranice pole se seznamem.

*bDisabled*<br/>
[in] Určuje, zda je zakázaný ohraničení pole se seznamem.

*bIsDropped*<br/>
[in] Určuje, zda se rozbalil ohraničení pole se seznamem.

*bIsHighlighted*<br/>
[in] Určuje, zda je zvýrazněn ohraničení pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je povolená rozhraní API motiv; v opačném případě FALSE.

##  <a name="drawcombodropbutton"></a>  CMFCBaseVisualManager::DrawComboDropButton

Nakreslí tlačítko rozevíracího pole se seznamem pomocí aktuálního motivu Windows.

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pDC*|[in] Ukazatel na kontext zařízení.|
|*Rect*|[in] Ohraničující obdélník tlačítko rozevíracího pole se seznamem.|
|*bDisabled*|[in] Určuje, zda je zakázaný tlačítko rozevíracího pole se seznamem.|
|*bIsDropped*|[in] Určuje, zda se rozbalil tlačítko rozevíracího pole se seznamem.|
|*bIsHighlighted*|[in] Určuje, zda se zvýrazní tlačítko rozevíracího pole se seznamem.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je povolená rozhraní API motiv; v opačném případě FALSE.

##  <a name="drawpushbutton"></a>  CMFCBaseVisualManager::DrawPushButton

Kreslení pomocí aktuálního motivu Windows příkazové tlačítko.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*Rect*<br/>
[in] Ohraničující obdélník příkazové tlačítko.

*pButton*<br/>
[in] Ukazatel [cmfcbutton – třída](../../mfc/reference/cmfcbutton-class.md) objektů pro kreslení.

*uiState*<br/>
[in] Ignorovat. Stav je převzata z *pButton*.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je povolená rozhraní API motiv; v opačném případě FALSE.

##  <a name="drawradiobutton"></a>  CMFCBaseVisualManager::DrawRadioButton

Nakreslí ovládací prvek přepínač pomocí aktuálního motivu Windows.

```
virtual BOOL DrawRadioButton(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    BOOL bChecked,
    BOOL bEnabled,
    BOOL bPressed);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*Rect*<br/>
[in] Ohraničující obdélník přepínač.

*bHighlighted*<br/>
[in] Určuje, zda přepínač je zvýrazněn.

*bChecked*<br/>
[in] Určuje, jestli je zaškrtnuté políčko přepínač.

*bEnabled*<br/>
[in] Určuje, zda je povoleno přepínač.

*bPressed*<br/>
[in] Určuje, zda se stiskne tlačítko přepínače.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je povolená rozhraní API motiv; v opačném případě FALSE.

##  <a name="drawstatusbarprogress"></a>  CMFCBaseVisualManager::DrawStatusBarProgress

Nakreslí indikátor průběhu na ovládací prvek panelu stavu ( [CMFCStatusBar – třída](../../mfc/reference/cmfcstatusbar-class.md)) použitím aktuální motiv Windows.

```
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,
    CMFCStatusBar* pStatusBar,
    CRect rectProgress,
    int nProgressTotal,
    int nProgressCurr,
    COLORREF clrBar,
    COLORREF clrProgressBarDest,
    COLORREF clrProgressText,
    BOOL bProgressText);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*pStatusBar*<br/>
[in] Ukazatel na stavovém řádku. Tato hodnota je ignorována.

*rectProgress*<br/>
[in] Ohraničující obdélník indikátor průběhu v *primárního řadiče domény* souřadnice.

*nProgressTotal*<br/>
[in] Celkový průběh hodnotu.

*nProgressCurr*<br/>
[in] Aktuální hodnota průběhu.

*clrBar*<br/>
[in] Počáteční barvu. `CMFCBaseVisualManager` to bude ignorovat. Odvozené třídy lze použít pro barevné přechody.

*clrProgressBarDest*<br/>
[in] Koncová barva. `CMFCBaseVisualManager` to bude ignorovat. Odvozené třídy lze použít pro barevné přechody.

*clrProgressText*<br/>
[in] Barva textu průběh. `CMFCBaseVisualManager` to bude ignorovat. Barva textu je definován `afxGlobalData.clrBtnText`.

*bProgressText*<br/>
[in] Určuje, jestli se mají zobrazovat text průběhu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je povolená rozhraní API motiv; v opačném případě FALSE.

##  <a name="fillrebarpane"></a>  CMFCBaseVisualManager::FillReBarPane

Pomocí aktuální motiv Windows vyplní celé pozadí ovládacího prvku rebar.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
[in] Ukazatel na kontext zařízení.

*pBar*<br/>
[in] Ukazatel na podokno má být vykreslena jehož pozadí.

*rectClient*<br/>
[in] Ohraničující obdélník oblasti pro vyplnění.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud je povolená rozhraní API motiv; v opačném případě FALSE.

##  <a name="getstandardwindowstheme"></a>  CMFCBaseVisualManager::GetStandardWindowsTheme

Získá aktuální motiv Windows.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>Návratová hodnota

Aktuálně vybraná barva motivu Windows. Může být jedna z následujících hodnot výčtu:

- `WinXpTheme_None` – neexistuje žádná motiv povolena.

- `WinXpTheme_NonStandard` -nestandardním motivu je vybraná (tj. vybraný motiv, ale žádné ze seznamu níže).

- `WinXpTheme_Blue` -modrý motiv (Luna).

- `WinXpTheme_Olive` -oliv motiv.

- `WinXpTheme_Silver` -stříbrné motiv.

##  <a name="updatesystemcolors"></a>  CMFCBaseVisualManager::UpdateSystemColors

Volání `OpenThemeData` získání popisovačů pro kreslení různých ovládacích prvků: windows, panely nástrojů, tlačítka a tak dále.

```
void UpdateSystemColors();
```

### <a name="remarks"></a>Poznámky

Pouze pro interní použití.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
