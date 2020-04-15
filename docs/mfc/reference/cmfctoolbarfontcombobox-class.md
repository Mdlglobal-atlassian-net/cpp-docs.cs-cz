---
title: CMFCToolBarFontComboBox – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
ms.openlocfilehash: 7b31f4b725a6983171162d9805d08224ad787808
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360468"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox – třída

Tlačítko panelu nástrojů, které obsahuje ovládací prvek pole se seznamem, který umožňuje uživateli vybrat písmo ze seznamu systémových písem.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Vytvoří `CMFCToolBarFontComboBox` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Vrátí ukazatel na `CMFCFontInfo` objekt pro zadaný index v poli se seznamem.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Vybere písmo v poli se seznamem písem podle názvu písma nebo podle předpony a znakové sady písma.|

### <a name="data-members"></a>Členové dat

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
Výška znaků v poli se seznamem písem.

## <a name="remarks"></a>Poznámky

Chcete-li na panel nástrojů přidat tlačítko pole se seznamem písem, postupujte takto:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.

1. Vytvořte `CMFCToolBarFontComboBox` objekt.

1. V obslužné rutině zprávy, která zpracovává zprávu AFX_WM_RESETTOOLBAR, nahraďte původní tlačítko novým tlačítkem pole se seznamem pomocí [cmfctoolbar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Synchronizujte písmo vybrané v poli se seznamem s písmem v dokumentu pomocí metody [CMFCToolBarFontComboBox::SetFont.](#setfont)

Chcete-li synchronizovat písmo dokumentu s písmem vybraným v poli se seznamem, použijte metodu [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) k načtení atributů vybraného písma a pomocí těchto atributů vytvořte objekt [Třídy CFont.](../../mfc/reference/cfont-class.md)

Tlačítko pole se seznamem písem volá funkci Win32 [EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) k určení písma obrazovky a tiskárny, která jsou v systému k dispozici.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CmFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CmFCToolBarComboBoxTlačítko](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarfontcombobox.h

## <a name="cmfctoolbarfontcomboboxcmfctoolbarfontcombobox"></a><a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Vytvoří objekt [CMFCToolBarFontComboBox.](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

```
public:
CMFCToolBarFontComboBox(
    UINT uiID,
    int iImage,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    DWORD dwStyle = CBS_DROPDOWN,
    int iWidth = 0,
    BYTE nPitchAndFamily = DEFAULT_PITCH);

protected:
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,
    int nFontType,
    BYTE nCharSet,
    BYTE nPitchAndFamily);

CMFCToolBarFontComboBox();
```

### <a name="parameters"></a>Parametry

*uiID*<br/>
[v] ID příkazu pole se seznamem.

*iImage*<br/>
[v] Nulový index obrazu panelu nástrojů. Obraz je umístěn v objektu [třídy CMFCToolBarImages,](../../mfc/reference/cmfctoolbarimages-class.md) který udržuje [třídu TŘÍDY CMFCToolBar.](../../mfc/reference/cmfctoolbar-class.md)

*nTyp písma*<br/>
[v] Typy písem, které pole se seznamem obsahuje. Tento parametr může být kombinací (logická hodnota OR) následujících hodnot:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nSada char*<br/>
[v] Pokud je nastavena na DEFAULT_CHARSET, pole se seznamem obsahuje všechna jedinečně pojmenované písma ve všech znakových sadách. (Pokud existují dvě písma se stejným názvem, pole se seznamem obsahuje jedno z nich.) Pokud je nastavena na platnou hodnotu znakové sady, pole se seznamem obsahuje pouze písma v zadané znakové sadě. Seznam možných znakových sad naleznete v tématu [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

*dwStyl*<br/>
[v] Styl pole se seznamem. (viz [Styly v kombinaci s rámečkem](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iŠířka*<br/>
[v] Šířka ovládacího prvku úprav v obrazových bodech.

*nPitchAndFamily*<br/>
[v] Pokud je nastavena na DEFAULT_PITCH, pole se seznamem obsahuje písma bez ohledu na výšku. Pokud je nastavena na FIXED_PITCH nebo VARIABLE_PITCH, pole se seznamem obsahuje pouze písma s tímto typem rozteče. Filtrování na základě rodiny písem není aktuálně podporováno.

*pLstFontsExterní*<br/>
[out] Ukazatel na [coblistý objekt třídy,](../../mfc/reference/coblist-class.md) který ukládá dostupná písma.

### <a name="remarks"></a>Poznámky

`CMFCToolBarFontComboBox` Objekty obvykle ukládají seznam dostupných písem `CObList` do jednoho sdíleného objektu. Pokud použijete druhé přetížení konstruktoru a poskytnete platný ukazatel *pLstFontsExternal*, tento `CMFCToolBarFontComboBox` objekt místo toho vyplní `CObList` *tento pLstFontsExternal* points s dostupnými písmy.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCToolBarFontComboBox` vytvořit objekt. Tento fragment kódu je součástí [ukázky aplikace Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

## <a name="cmfctoolbarfontcomboboxgetfontdesc"></a><a name="getfontdesc"></a>CMFCToolBarFontComboBox::GetFontDesc

Vrátí ukazatel na `CMFCFontInfo` objekt pro zadaný index v poli se seznamem.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[v] Určuje nulový index položky pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CMFCFontInfo` objekt. Pokud *iIndex* nezadává platný index položky, vrácená hodnota je NULL.

## <a name="cmfctoolbarfontcomboboxm_nfontheight"></a><a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight

Určuje výšku znaků v obrazových bodech v poli se seznamem písem, pokud má pole se seznamem styl kreslení vlastníka.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Poznámky

Pokud `m_nFontHeight` je proměnná 0, výška se vypočítá automaticky podle výchozího písma pole se seznamem. Výška zahrnuje jak stoupání znaků nad účaří, tak sestup znaků pod účaří.

## <a name="cmfctoolbarfontcomboboxsetfont"></a><a name="setfont"></a>CMFCToolBarFontComboBox::SetFont

Vybere písmo v poli se seznamem písem podle názvu písma a znakové sady, které jsou zadány v parametrech.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Parametry

*název lpsz*<br/>
[v] Určuje název písma nebo předponu.

*nSada char*<br/>
[v] Určuje znakovou sadu.

*bPřesné*<br/>
[v] Určuje, zda *lpszName* obsahuje název písma nebo předponu písma.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud bylo písmo vybráno úspěšně; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *je hodnota bExact* true, vybere tato metoda písmo, které přesně odpovídá názvu, který jste zadali jako *lpszName*. Pokud *je bExact* FALSE, vybere tato metoda písmo, které začíná textem určeným jako *lpszName* a které používá znakovou sadu, kterou jste zadali jako *nCharSet*. Pokud je *hodnota nCharSet* nastavena na DEFAULT_CHARSET, znaková sada bude ignorována a k výběru písma bude použit pouze *lpszName.*

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Třída CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Třída CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[Třída CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
