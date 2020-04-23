---
title: Třída CMFCRibbonRibbonColorButton
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
ms.openlocfilehash: 528b883d75889589c7021f462324dd9dcb71be25
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754853"
---
# <a name="cmfcribboncolorbutton-class"></a>Třída CMFCRibbonRibbonColorButton

Třída `CMFCRibbonColorButton` implementuje barevné tlačítko, které můžete přidat na pruh pásu karet. Tlačítko barva pásu karet zobrazí rozevírací nabídku, která obsahuje jednu nebo více palet barev.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonColorButton : public CMFCRibbonGallery
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|Přidá skupinu barev do oblasti běžných barev.|
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|Určuje, zda je povoleno tlačítko **Automaticky.**|
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|Povolí tlačítko **Další.**|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[CMFCRibbonColorButton::GetColor](#getcolor)|Vrátí aktuálně vybranou barvu.|
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|Vrátí velikost barevných prvků, které se objeví na panelu barev.|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|Vrátí barvu aktuálně vybraného prvku na paletě barev automaticky otevíraných vyskakovacích okno.|
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|Odstraní všechny skupiny barev z oblasti běžných barev.|
|[CMFCRibbonColorButton::SetColor](#setcolor)|Vybere barvu z oblasti běžné barvy.|
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|Nastaví velikost všech barevných prvků, které se objeví na pruhu barev.|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|Určuje seznam hodnot RGB, které se mají zobrazit v oblasti barev dokumentu.|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>Poznámky

Tlačítko barva pásu karet zobrazí barevný pruh, když ho uživatel stiskne. Ve výchozím nastavení obsahuje tento barevný pruh paletu výběru barev nazývanou normální oblast barev. Volitelně může barevný pruh zobrazit tlačítko **Automaticky,** které uživateli umožňuje vybrat výchozí barvu, a tlačítko **Další,** které zobrazuje vyskakovací paletu barev, která obsahuje další barvy.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat různé `CMFCRibbonColorButton` metody ve třídě. Příklad ukazuje, jak `CMFCRibbonColorButton` vytvořit objekt, nastavit velký obraz, povolit tlačítko **Automaticky,** povolit tlačítko **Další,** nastavit počet sloupců, nastavit velikost všech barevných prvků, které se objeví na barevném pruhu, přidat skupinu barev do normální oblasti barev a určit seznam hodnot RGB, které se mají zobrazit v oblasti barev dokumentu. Tento fragment kódu je součástí [ukázky klienta Draw](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CmFCRibbonGalerie](../../mfc/reference/cmfcribbongallery-class.md)

[CmFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxribboncolorbutton.h

## <a name="cmfcribboncolorbuttonaddcolorsgroup"></a><a name="addcolorsgroup"></a>CMFCRibbonColorButton::AddColorsGroup

Přidá skupinu barev do oblasti běžných barev.

```cpp
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
[v] Název skupiny.

*lstBarvy*<br/>
[v] Seznam barev.

*bSouvislé sloupce*<br/>
[v] Určuje způsob zobrazení barevných položek ve skupině. Pokud true, barevné položky jsou kresleny bez svislé mezery. Pokud false, barevné položky jsou kresleny s svislým rozestupem.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k tomu, aby se v rozbalovacím okno barvy zobrazilo několik skupin barev. Můžete určit, jak budou barvy zobrazeny ve skupině.

## <a name="cmfcribboncolorbuttoncmfcribboncolorbutton"></a><a name="cmfcribboncolorbutton"></a>CMFCRibbonColorButton::CMFCRibbonColorButton

Vytvoří `CMFCRibbonColorButton` objekt.

```
CMFCRibbonColorButton();

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex,
    COLORREF color = RGB(0, 0, 0));

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    BOOL bSimpleButtonLook,
    int nSmallImageIndex,
    int nLargeImageIndex,
    COLORREF color = RGB(0, 0, 0));
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] Určuje ID příkazu, který má být proveden, když uživatel klepne na tlačítko.

*lpszText*<br/>
[v] Určuje text, který se má zobrazit na tlačítku.

*nSmallImageIndex*<br/>
[v] Nulový index malého obrázku, který se zobrazí na tlačítku.

*color*<br/>
[v] Barva tlačítka (výchozí černá).

*bSimpleButtonLook*<br/>
[v] Pokud TRUE, tlačítko je nakreslena jako jednoduchý obdélník.

*nLargeImageIndex*<br/>
[v] Nulový index velkého obrázku, který se zobrazí na tlačítku.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncolorbuttonenableautomaticbutton"></a><a name="enableautomaticbutton"></a>CMFCRibbonColorButton::EnableAutomaticButton

Určuje, zda je povoleno tlačítko **Automaticky.**

```cpp
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE,
    LPCTSTR lpszToolTip=NULL,
    BOOL bOnTop=TRUE,
    BOOL bDrawBorder=FALSE);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Popisek tlačítka **Automaticky.**

*colorAutomaticky*<br/>
[v] Hodnota RGB, která určuje výchozí barvu tlačítka **Automaticky.**

*bEnable*<br/>
[v] PRAVDA, pokud je povoleno tlačítko **Automaticky;** FALSE, pokud je zakázán.

*lpszToolTip*<br/>
[v] Popis tlačítka **Automaticky.**

*bOnTop*<br/>
[v] Určuje, zda je tlačítko **Automaticky** v horní části před paletou barev.

*bDrawBorder*<br/>
[v] PRAVDA, pokud aplikace nakreslí ohraničení kolem pruhu barev na tlačítku barvy pásu karet. Pruh barev zobrazuje aktuálně vybranou barvu. FALSE, pokud aplikace nenakreslí ohraničení

## <a name="cmfcribboncolorbuttonenableotherbutton"></a><a name="enableotherbutton"></a>CMFCRibbonColorButton::EnableOtherButton

Povolí tlačítko **Další.**

```cpp
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
Štítek tlačítka.

*lpszToolTip*<br/>
Text popisku tlačítka **Další.**

### <a name="remarks"></a>Poznámky

Tlačítko **Další** je tlačítko, které se zobrazí pod skupinou barev. Když uživatel klepne na tlačítko **Další,** zobrazí se dialog barev.

## <a name="cmfcribboncolorbuttongetautomaticcolor"></a><a name="getautomaticcolor"></a>CMFCRibbonColorButton::GetAutomaticColor

Načte aktuální barvu automatického tlačítka.

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB, která představuje aktuální barvu automatického tlačítka.

### <a name="remarks"></a>Poznámky

Barva automatického tlačítka je `colorAutomatic` nastavena parametrem předanou metodě. `CMFCRibbonColorButton::EnableAutomaticButton`

## <a name="cmfcribboncolorbuttongetcolor"></a><a name="getcolor"></a>CMFCRibbonColorButton::GetColor

Vrátí aktuálně vybranou barvu.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva vybraná klepnutím na tlačítko.

## <a name="cmfcribboncolorbuttongetcolorboxsize"></a><a name="getcolorboxsize"></a>CMFCRibbonColorButton::GetColorBoxSize

Vrátí velikost barevných prvků, které se objeví na panelu barev.

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost barevných tlačítek v rozevírací paletě barev.

## <a name="cmfcribboncolorbuttongetcolumns"></a><a name="getcolumns"></a>CMFCRibbonColorButton::GetColumns

Získá počet položek v řádku zobrazení galerie tlačítka barvy pásu karet.

```
int GetColumns() const;
```

### <a name="return-value"></a>Návratová hodnota

Vrátí počet ikon v každém řádku.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncolorbuttongethighlightedcolor"></a><a name="gethighlightedcolor"></a>CMFCRibbonColorButton::GetHighlightedColor

Vrátí barvu aktuálně vybraného prvku na rozbalovací paletě barev.

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva aktuálně vybraného prvku na rozbalovací paletě barev.

## <a name="cmfcribboncolorbuttonremoveallcolorgroups"></a><a name="removeallcolorgroups"></a>CMFCRibbonColorButton::RemoveAllColorGroups

Odstraní všechny skupiny barev z oblasti běžných barev.

```cpp
void RemoveAllColorGroups();
```

## <a name="cmfcribboncolorbuttonsetcolor"></a><a name="setcolor"></a>CMFCRibbonColorButton::SetColor

Vybere barvu z oblasti běžné barvy.

```cpp
void SetColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Barva, která má být nastavena.

## <a name="cmfcribboncolorbuttonsetcolorboxsize"></a><a name="setcolorboxsize"></a>CMFCRibbonColorButton::SetColorBoxSize

Nastaví velikost všech barevných prvků, které se objeví na pruhu barev.

```cpp
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>Parametry

*sizeBox*<br/>
[v] Nová velikost barevných tlačítek v paletě barev.

## <a name="cmfcribboncolorbuttonsetcolorname"></a><a name="setcolorname"></a>CMFCRibbonColorButton::SetColorName

Nastaví nový název pro zadanou barvu.

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Hodnota RGB barvy.

*strName*<br/>
[v] Nový název pro zadanou barvu.

### <a name="remarks"></a>Poznámky

Vzhledem `CMFCColorBar::SetColorName`k tomu, že volá , tato `CMFCColorBar` metoda změní název zadané barvy ve všech objektech v aplikaci.

## <a name="cmfcribboncolorbuttonsetcolumns"></a><a name="setcolumns"></a>CMFCRibbonColorButton::SetColumns

Nastaví počet sloupců zobrazených v tabulce barev, která je uživateli zobrazena během procesu výběru barev uživatele.

```cpp
void SetColumns(int nColumns);
```

### <a name="parameters"></a>Parametry

*nSloupce*<br/>
[v] Počet ikon barev, které se mají zobrazit v každém řádku.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncolorbuttonsetdocumentcolors"></a><a name="setdocumentcolors"></a>CMFCRibbonColorButton::SetDocumentColors

Určuje seznam hodnot RGB, které se mají zobrazit v oblasti barev dokumentu.

```cpp
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>Parametry

*popisek lpsz*<br/>
[v] Text, který se má zobrazit s barvami dokumentu.

*lstBarvy*<br/>
[v] Odkaz na seznam hodnot RGB.

## <a name="cmfcribboncolorbuttonsetpalette"></a><a name="setpalette"></a>CMFCRibbonColorButton::SetPalette

Určuje standardní barvy, které se mají zobrazit v tabulce barev, kterou zobrazí tlačítko barva.

```cpp
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>Parametry

*pPaleta*<br/>
[v] Ukazatel na paletu barev.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribboncolorbuttonupdatecolor"></a><a name="updatecolor"></a>CMFCRibbonColorButton::UpdateColor

Volat rámci, když uživatel vybere barvu z tabulky barev zobrazí, když uživatel klepne na tlačítko barva.

```cpp
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>Parametry

*color*<br/>
[v] Barva vybraná uživatelem.

### <a name="remarks"></a>Poznámky

Metoda `CMFCRibbonColorButton::UpdateColor` změní barvu aktuálně vybraného tlačítka a upozorní nadřazenou položku odesláním WM_COMMAND zprávy se standardním oznámením BN_CLICKED. K načtení vybrané barvy použijte metodu [CMFCRibbonColorButton:::GetColor.](#getcolor)

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery – třída](../../mfc/reference/cmfcribbongallery-class.md)
