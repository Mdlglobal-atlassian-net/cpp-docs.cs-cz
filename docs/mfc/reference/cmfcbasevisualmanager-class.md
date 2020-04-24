---
title: CMFCBaseVisualManager – třída
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
ms.openlocfilehash: ac64a3feac5d124c2bfa67fc857dad5045c2dd28
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754885"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager – třída

Vrstva mezi odvozenými vizuálními manažery a rozhraním API motivu systému Windows.

`CMFCBaseVisualManager`načte soubor UxTheme.dll, pokud je k dispozici, a spravuje přístup k metodám rozhraní API motivů systému Windows.

Tato třída je pouze pro interní použití.

## <a name="syntax"></a>Syntaxe

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|||
|-|-|
|Název|Popis|
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|Vytvoří a inicializuje `CMFCBaseVisualManager` objekt.|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|Název|Popis|
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Nakreslí ovládací prvek zaškrtávacího políčka pomocí aktuálního motivu systému Windows.|
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Nakreslí ohraničení pole se seznamem pomocí aktuálního motivu systému Windows.|
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Nakreslí rozevírací tlačítko pole se seznamem pomocí aktuálního motivu systému Windows.|
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Nakreslí tlačítko pomocí aktuálního motivu systému Windows.|
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Nakreslí ovládací prvek přepínacího tlačítka pomocí aktuálního motivu systému Windows.|
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Nakreslí indikátor průběhu ovládacího prvku stavového řádku [(třída CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)) pomocí aktuálního motivu systému Windows.|
|[CMFCBaseVisualManager::FillRebarpane](#fillrebarpane)|Vyplní pozadí ovládacího prvku výztuže pomocí aktuálního motivu systému Windows.|
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Získá aktuální motiv systému Windows.|

### <a name="protected-methods"></a>Chráněné metody

|||
|-|-|
|Název|Popis|
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Vyžaduje `CloseThemeData` všechny popisovače `UpdateSystemColors`získané v .|
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Volání `OpenThemeData` získat popisovače pro kreslení různých ovládacích prvků: okna, panely nástrojů, tlačítka a tak dále.|

## <a name="remarks"></a>Poznámky

Není třeba vytvořit instanci objektů této třídy přímo.

Vzhledem k tomu, že se jedná o základní třídu pro všechny vizuální manažery, stačí zavolat [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), získat ukazatel na aktuální Visual Manager a získat přístup k metodám pro `CMFCBaseVisualManager` použití tohoto ukazatele. Pokud však máte zobrazit ovládací prvek pomocí aktuálního motivu systému `CMFCVisualManagerWindows` Windows, je lepší použít rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxvisualmanager.h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a>CMFCBaseVisualManager::CleanUpThemes

Vyžaduje `CloseThemeData` všechny popisovače `UpdateSystemColors`získané v .

```cpp
void CleanUpThemes();
```

### <a name="remarks"></a>Poznámky

Pouze pro interní použití.

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a>CMFCBaseVisualManager::CMFCBaseVisualManager

Vytvoří a inicializuje `CMFCBaseVisualManager` objekt.

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a>CMFCBaseVisualManager::DrawCheckBox

Nakreslí ovládací prvek zaškrtávacího políčka pomocí aktuálního motivu systému Windows.

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

*Pdc*<br/>
[v] Ukazatel na kontext zařízení

*Rect*<br/>
[v] Ohraničovací obdélník zaškrtávacího políčka.

*bZvýrazněno*<br/>
[v] Určuje, zda je zaškrtávací políčko zvýrazněno.

*nStát*<br/>
[v] 0 pro nekontrolované, 1 pro kontrolované normální,

2 pro smíšené normální.

*bPovoleno*<br/>
[v] Určuje, zda je toto políčko povoleno.

*bLisované*<br/>
[v] Určuje, zda je zaškrtávací políčko stisknuto.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je povoleno rozhraní API motivu; jinak FALSE.

### <a name="remarks"></a>Poznámky

Hodnoty *nState* odpovídají následujícím stylům zaškrtávacích pokresl.

|nStát|Styl zaškrtávacího políčka|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a>CMFCBaseVisualManager::DrawComboBorder

Nakreslí ohraničení pole se seznamem pomocí aktuálního motivu systému Windows.

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Ohraničující obdélník ohraničení pole se seznamem.

*bZakázáno.*<br/>
[v] Určuje, zda je ohraničení pole se seznamem zakázáno.

*bIsDropped*<br/>
[v] Určuje, zda je ohraničení pole se seznamem vynecháno.

*bIsZvýrazněno*<br/>
[v] Určuje, zda je zvýrazněno ohraničení pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je povoleno rozhraní API motivu; jinak FALSE.

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a>CMFCBaseVisualManager::DrawComboDropButton

Nakreslí rozevírací tlačítko pole se seznamem pomocí aktuálního motivu systému Windows.

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
|*Pdc*|[v] Ukazatel na kontext zařízení.|
|*Rect*|[v] Ohraničovací obdélník rozbalovacího tlačítka pole se seznamem.|
|*bZakázáno.*|[v] Určuje, zda je rozbalovací tlačítko pole se seznamem zakázáno.|
|*bIsDropped*|[v] Určuje, zda je rozbalovací tlačítko pole se seznamem vynecháno.|
|*bIsZvýrazněno*|[v] Určuje, zda je zvýrazněno rozbalovací tlačítko pole se seznamem.|

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je povoleno rozhraní API motivu; jinak FALSE.

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a>CMFCBaseVisualManager::DrawPushButton

Nakreslí tlačítko pomocí aktuálního motivu systému Windows.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Ohraničovací obdélník tlačítka.

*pTlačítko*<br/>
[v] Ukazatel na objekt [třídy CMFCButton](../../mfc/reference/cmfcbutton-class.md) k nakreslení.

*uiState*<br/>
[v] Ignorovány. Stav je převzat z *pButton*.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je povoleno rozhraní API motivu; jinak FALSE.

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a>CMFCBaseVisualManager::DrawRadioButton

Nakreslí ovládací prvek přepínacího tlačítka pomocí aktuálního motivu systému Windows.

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

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*Rect*<br/>
[v] Ohraničovací obdélník přepínacího tlačítka.

*bZvýrazněno*<br/>
[v] Určuje, zda je přepínací tlačítko zvýrazněno.

*bZaškrtnuto*<br/>
[v] Určuje, zda je přepínací tlačítko zaškrtnuto.

*bPovoleno*<br/>
[v] Určuje, zda je přepínací tlačítko povoleno.

*bLisované*<br/>
[v] Určuje, zda je stisknuto přepínací tlačítko.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je povoleno rozhraní API motivu; jinak FALSE.

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a>CMFCBaseVisualManager::DrawStatusBarProgress

Nakreslí indikátor průběhu ovládacího prvku stavového řádku [(třída CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)) pomocí aktuálního motivu systému Windows.

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

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*pStavový pruh*<br/>
[v] Ukazatel na stavový řádek. Tato hodnota je ignorována.

*rectProgress*<br/>
[v] Ohraničující obdélník indikátoru průběhu v souřadnicích *primárního řadiče domény.*

*nProgressTotal*<br/>
[v] Celková hodnota průběhu.

*nProgressCurr*<br/>
[v] Aktuální hodnota průběhu.

*clrBar*<br/>
[v] Počáteční barva. `CMFCBaseVisualManager`ignoruje to. Odvozené třídy jej mohou použít pro barevné přechody.

*clrProgressBarDest*<br/>
[v] Koncová barva. `CMFCBaseVisualManager`ignoruje to. Odvozené třídy jej mohou použít pro barevné přechody.

*clrProgressText*<br/>
[v] Průběh textu barva. `CMFCBaseVisualManager`ignoruje to. Barva textu je `afxGlobalData.clrBtnText`definována .

*bProgressText*<br/>
[v] Určuje, zda se má zobrazit text průběhu.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je povoleno rozhraní API motivu; jinak FALSE.

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a>CMFCBaseVisualManager::FillRebarpane

Vyplní pozadí ovládacího prvku výztuže pomocí aktuálního motivu systému Windows.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*pBar*<br/>
[v] Ukazatel na podokno, jehož pozadí by mělo být nakresleno.

*rectClient*<br/>
[v] Ohraničující obdélník oblasti, která má být vyplněna.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je povoleno rozhraní API motivu; jinak FALSE.

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a>CMFCBaseVisualManager::GetStandardWindowsTheme

Získá aktuální motiv systému Windows.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>Návratová hodnota

Aktuálně vybraná barva motivu systému Windows. Může se na pokládá některá z následujících výčtových hodnot.

- `WinXpTheme_None`- není povoleno žádné téma.

- `WinXpTheme_NonStandard`- je vybrán nestandardní motiv (což znamená, že je vybrán otemněr, ale žádný z níže uvedeného seznamu).

- `WinXpTheme_Blue`- modré téma (Luna).

- `WinXpTheme_Olive`- olivové téma.

- `WinXpTheme_Silver`- stříbrné téma.

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a>CMFCBaseVisualManager::UpdateSystemColors

Volání `OpenThemeData` získat popisovače pro kreslení různých ovládacích prvků: okna, panely nástrojů, tlačítka a tak dále.

```cpp
void UpdateSystemColors();
```

### <a name="remarks"></a>Poznámky

Pouze pro interní použití.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)
