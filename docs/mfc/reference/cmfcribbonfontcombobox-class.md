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
ms.openlocfilehash: 186c4bc3e1b26529ed0e000d2893e1b2d81c4304
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504958"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox – třída

Implementuje pole se seznamem, které obsahuje seznam písem. Pole se seznamem umístěte na panel pásu karet.

## <a name="syntax"></a>Syntaxe

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Destruktor.|

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Vytvoří a inicializuje `CMFCRibbonFontComboBox` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Naplní pole se seznamem fontu na pásu karet písmy zadaného typu písma, znakové sady a sklonu a rodiny.|
|`CMFCRibbonFontComboBox::CreateObject`|Používá se rozhraním k vytvoření dynamické instance tohoto typu třídy.|
|[CMFCRibbonFontComboBox:: getcharset](#getcharset)|Vrátí zadanou znakovou sadu.|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Vrátí typy písem, které se mají zobrazit v poli se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jakékoli bitové kombinace.|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Vrátí rozteč a rodinu písem, která jsou zobrazena v poli se seznamem.|
|`CMFCRibbonFontComboBox::GetThisClass`|Používá se rozhraním, aby se získal ukazatel na objekt [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , který je přidružený k tomuto typu třídy.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Naplní pole se seznamem fontu na pásu karet písmy dříve zadaného typu písma, znakové sady a sklonu a rodiny.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Vybere zadané písmo v poli se seznamem.|

## <a name="remarks"></a>Poznámky

Po vytvoření `CMFCRibbonFontComboBox` objektu jej přidejte na panel pásu karet voláním [CMFCRibbonPanel:: Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxRibbonComboBox. h

##  <a name="buildfonts"></a>CMFCRibbonFontComboBox::BuildFonts

Naplní pole se seznamem na pásu karet písmy.

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Parametry

*nFontType*<br/>
pro Určuje typ písma, který se má přidat.

*nCharSet*<br/>
pro Určuje znakovou sadu písem, která se má přidat.

*nPitchAndFamily*<br/>
pro Určuje rozteč a rodinu přidaných písem.

##  <a name="cmfcribbonfontcombobox"></a>CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

Vytvoří a inicializuje objekt [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) .

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
pro ID příkazu, který se spustí, když uživatel vybere položku z pole se seznamem.

*nFontType*<br/>
pro Určuje typy písem, které se mají zobrazit v poli se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jakékoli bitové kombinace.

*nCharSet*<br/>
pro Filtruje písma v poli se seznamem na ty, které patří do zadané znakové sady.

*nPitchAndFamily*<br/>
pro Určuje rozteč a rodinu písem, která jsou zobrazena v poli se seznamem.

*nWidth*<br/>
pro Určuje šířku pole se seznamem (v pixelech).

### <a name="remarks"></a>Poznámky

Další informace o možných hodnotách parametrů *nFontType* naleznete v tématu [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) v dokumentaci k Windows SDK.

Další informace o platných znakových sadách, které mohou být přiřazeny *nCharSet*a platné hodnoty, které lze přiřadit k *nPitchAndFamily*, naleznete v tématu [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) v dokumentaci Windows SDK.

##  <a name="getfontdesc"></a>CMFCRibbonFontComboBox::GetFontDesc

Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Parametry

pro *iIndex*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="rebuildfonts"></a>CMFCRibbonFontComboBox::RebuildFonts

Naplní pole se seznamem na pásu karet písmy dříve zadaného typu písma, znakové sady a sklonu a rodiny.

```
void RebuildFonts();
```

### <a name="remarks"></a>Poznámky

Můžete zadat typ písma, znakovou sadu a rozteč a rodinu písem, které mají být zahrnuty do pole se seznamem písem pásu karet v [konstruktoru](#cmfcribbonfontcombobox) pro tuto třídu, nebo voláním [CMFCRibbonFontComboBox:: BuildFonts](#buildfonts).

##  <a name="setfont"></a>CMFCRibbonFontComboBox::SetFont

Vybere zadané písmo v poli se seznamem.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Parametry

' lpszName * Určuje název písma, které chcete vybrat.

*nCharSet*<br/>
Určuje znakovou sadu vybraného písma.

*bExact*<br/>
Hodnota TRUE určuje, že znaková sada musí při výběru písma odpovídat. FALSE pro určení, že znaková sada může být při výběru písma ignorována.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zadané písmo bylo nalezeno a vybráno; v opačném případě nula.

### <a name="remarks"></a>Poznámky

##  <a name="getcharset"></a>CMFCRibbonFontComboBox:: getcharset

Vrátí zadanou znakovou sadu.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Návratová hodnota

Znaková sada (viz LOGFONT v dokumentaci k Windows SDK).

### <a name="remarks"></a>Poznámky

##  <a name="getfonttype"></a>CMFCRibbonFontComboBox::GetFontType

Vrátí typy písem, které se mají zobrazit v poli se seznamem. Platné možnosti jsou DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE nebo jakékoli bitové kombinace.

```
int GetFontType() const;
```

### <a name="return-value"></a>Návratová hodnota

Typy písem (viz EnumFontFamProc v dokumentaci k Windows SDK).

### <a name="remarks"></a>Poznámky

##  <a name="getpitchandfamily"></a>CMFCRibbonFontComboBox::GetPitchAndFamily

Vrátí rozteč a rodinu písem, která jsou zobrazena v poli se seznamem.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Návratová hodnota

Rozteč a rodina (viz LOGFONT v dokumentaci k Windows SDK).

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox – třída](../../mfc/reference/cmfcribboncombobox-class.md)
