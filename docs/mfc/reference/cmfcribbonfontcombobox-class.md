---
title: CMFCRibbonFontComboBox – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 822f4f6fe76bb5b82b455daec54ed96568ea6ba7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375170"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox – třída

Implementuje pole se seznamem, které obsahuje seznam písem. Pole se seznamem umístíte na panel pásky.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destruktor.|

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonRibbonFontcomboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Vytvoří a inicializuje `CMFCRibbonFontComboBox` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCRibbonRibbonFontoBox::BuildFonts](#buildfonts)|Naplní pole se seznamem písma pásu karet písmy zadaného typu písma, znakové sady a rozteče a rodiny.|
|`CMFCRibbonFontComboBox::CreateObject`|Používá rámci k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCRibbonRibbonFontcomboBox::GetCharSet](#getcharset)|Vrátí zadanou znakovou sadu.|
|[CMFCRibbonRibbonFontcomboBox::GetFontDesc](#getfontdesc)||
|[CMFCRIBBONRibbonFontComboBox::Typ getfontu](#getfonttype)|Vrátí typy písem, které se mají zobrazit v poli se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jejich bitové kombinace.|
|[CMFCRibbonRibbonFontcomboBox::GetPitchAndFamily](#getpitchandfamily)|Vrátí výšku a rodinu písem, které jsou zobrazeny v poli se seznamem.|
|`CMFCRibbonFontComboBox::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objektu, který je přidružen k tomuto typu třídy.|
|[CMFCRibbonRibbonFontoBox::Znovu vytvořit písma](#rebuildfonts)|Naplní pole se seznamem písma pásu karet písmy dříve určeného typu písma, znakové sady a rozteče a rodiny.|
|[CMFCRibbonRibbonFontComboBox::SetFont](#setfont)|Vybere zadané písmo v poli se seznamem.|

## <a name="remarks"></a>Poznámky

Po vytvoření `CMFCRibbonFontComboBox` objektu jej přidejte do panelu pásu karet voláním [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CMFC4RibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CmFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbon](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonRibbonFontcomboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonComboBox.h

## <a name="cmfcribbonfontcomboboxbuildfonts"></a><a name="buildfonts"></a>CMFCRibbonRibbonFontoBox::BuildFonts

Naplní pole se seznamem na pásu karet písmy.

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Parametry

*nTyp písma*<br/>
[v] Určuje typ písma písem, která chcete přidat.

*nSada char*<br/>
[v] Určuje znakovou sadu písem, která chcete přidat.

*nPitchAndFamily*<br/>
[v] Určuje výšku a rodinu písem, která chcete přidat.

## <a name="cmfcribbonfontcomboboxcmfcribbonfontcombobox"></a><a name="cmfcribbonfontcombobox"></a>CMFCRibbonRibbonFontcomboBox::CMFCRibbonFontComboBox

Vytvoří a inicializuje objekt [CMFCRibbonFontComboBox.](../../mfc/reference/cmfcribbonfontcombobox-class.md)

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
[v] ID příkazu, který se provede, když uživatel vybere položku z pole se seznamem.

*nTyp písma*<br/>
[v] Určuje, které typy písem se mají zobrazit v poli se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jejich bitové kombinace.

*nSada char*<br/>
[v] Filtruje písma v poli se seznamem na písma, která patří do zadané znakové sady.

*nPitchAndFamily*<br/>
[v] Určuje výšku a rodinu písem, které jsou zobrazeny v poli se seznamem.

*nŠířka*<br/>
[v] Určuje šířku pole se seznamem v obrazových bodech.

### <a name="remarks"></a>Poznámky

Další informace o možných hodnotách parametrů *nFontType* naleznete v tématu [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) v dokumentaci k sada Windows SDK.

Další informace o platných znakových sadách, které lze přiřadit *k nCharSet*, a platných hodnotách, které lze přiřadit *k nPitchAndFamily*, naleznete v [tématu LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) v dokumentaci k sadě Windows SDK.

## <a name="cmfcribbonfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCRibbonRibbonFontcomboBox::GetFontDesc

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Parametry

[v] *iIndex*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonfontcomboboxrebuildfonts"></a><a name="rebuildfonts"></a>CMFCRibbonRibbonFontoBox::Znovu vytvořit písma

Naplní pole se seznamem na pásu karet písmy dříve určeného typu písma, znakové sady a rozteče a rodiny.

```
void RebuildFonts();
```

### <a name="remarks"></a>Poznámky

Můžete určit typ písma, znakovou sadu a výšku a rodinu písem, které mají být zahrnuty do pole se seznamem písma na pásu karet v [konstruktoru](#cmfcribbonfontcombobox) pro tuto třídu, nebo voláním [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).

## <a name="cmfcribbonfontcomboboxsetfont"></a><a name="setfont"></a>CMFCRibbonRibbonFontComboBox::SetFont

Vybere zadané písmo v poli se seznamem.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Parametry

'lpszName* Určuje název písma, které chcete vybrat.

*nSada char*<br/>
Určuje znakovou sadu vybraného písma.

*bPřesné*<br/>
TRUE, chcete-li určit, že znaková sada se musí shodovat při výběru písma; FALSE určit, že znaková sada může být ignorována při výběru písma.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo zadané písmo nalezeno a vybráno; jinak nula.

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonfontcomboboxgetcharset"></a><a name="getcharset"></a>CMFCRibbonRibbonFontcomboBox::GetCharSet

Vrátí zadanou znakovou sadu.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Návratová hodnota

Znaková sada (viz LOGFONT v dokumentaci k sadě Windows SDK).

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonfontcomboboxgetfonttype"></a><a name="getfonttype"></a>CMFCRIBBONRibbonFontComboBox::Typ getfontu

Vrátí typy písem, které se mají zobrazit v poli se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jejich bitové kombinace.

```
int GetFontType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typy písem (viz EnumFontFamProc v dokumentaci k sada Windows SDK).

### <a name="remarks"></a>Poznámky

## <a name="cmfcribbonfontcomboboxgetpitchandfamily"></a><a name="getpitchandfamily"></a>CMFCRibbonRibbonFontcomboBox::GetPitchAndFamily

Vrátí výšku a rodinu písem, které jsou zobrazeny v poli se seznamem.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Návratová hodnota

Pitch a rodiny (viz LOGFONT v dokumentaci sady Windows SDK).

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)
