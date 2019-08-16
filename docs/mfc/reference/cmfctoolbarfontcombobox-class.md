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
ms.openlocfilehash: 7e19fc9257c1fe986ff09a8bbc86bf2fb55af7ee
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504735"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox – třída

Tlačítko panelu nástrojů, které obsahuje ovládací prvek pole se seznamem, který uživateli umožňuje vybrat písmo ze seznamu systémových písem.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|`CMFCToolBarFontComboBox` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Vrátí ukazatel na `CMFCFontInfo` objekt pro zadaný index v poli se seznamem.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Vybere písmo v poli se seznamem písem podle názvu písma nebo předpony a znakové sady písma.|

### <a name="data-members"></a>Datové členy

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
Výška znaků v poli se seznamem písem

## <a name="remarks"></a>Poznámky

Chcete-li přidat tlačítko pole se seznamem písma na panel nástrojů, postupujte takto:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.

1. Sestavte `CMFCToolBarFontComboBox` objekt.

1. V obslužné rutině zprávy, která zpracovává zprávu AFX_WM_RESETTOOLBAR, nahraďte původní tlačítko novým polem se seznamem pomocí tlačítka [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Synchronizuje písmo, které je vybráno v poli se seznamem, s písmem v dokumentu pomocí metody [CMFCToolBarFontComboBox:: SetFont](#setfont) .

Chcete-li synchronizovat písmo dokumentu se zvoleným písmem v poli se seznamem, použijte metodu [CMFCToolBarFontComboBox:: GetFontDesc](#getfontdesc) k načtení atributů vybraného písma a použijte tyto atributy k vytvoření objektu [třídy CFont –](../../mfc/reference/cfont-class.md) .

Tlačítko pole se seznamem fontu zavolá funkci Win32 [EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw) k určení písma obrazovky a tiskárny, která jsou k dispozici pro systém.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarfontcombobox. h

##  <a name="cmfctoolbarfontcombobox"></a>CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Vytvoří objekt [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) .

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
pro ID příkazu pole se seznamem

*iImage*<br/>
pro Index obrázku panelu nástrojů založený na nule. Obrázek se nachází v objektu [třídy CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) , který udržuje třída [třídy CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) .

*nFontType*<br/>
pro Typy písem, které pole se seznamem obsahuje. Tento parametr může být kombinací (Boolean nebo) následujících hodnot:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
pro Pokud je nastavena na DEFAULT_CHARSET, pole se seznamem obsahuje všechna jedinečně pojmenovaná písma ve všech znakových sadách. (Pokud jsou k dispozici dvě písma se stejným názvem, pole se seznamem obsahuje jednu z nich.) Pokud je nastaveno na platnou hodnotu znakové sady, pole se seznamem obsahuje pouze písma v zadané znakové sadě. Seznam možných znakových sad naleznete v tématu [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*dwStyle*<br/>
pro Styl pole se seznamem (viz [styly polí se seznamem](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
pro Šířka ovládacího prvku pro úpravy v pixelech

*nPitchAndFamily*<br/>
pro Pokud je nastavená na DEFAULT_PITCH, pole se seznamem obsahuje písma bez ohledu na rozteč. Pokud je nastavené na FIXED_PITCH nebo VARIABLE_PITCH, pole se seznamem obsahuje jenom písma s tímto typem sklonu. Filtrování založené na rodině písem není aktuálně podporováno.

*pLstFontsExternal*<br/>
mimo Ukazatel na objekt [třídy CObList](../../mfc/reference/coblist-class.md) , ve kterém jsou uložena dostupná písma.

### <a name="remarks"></a>Poznámky

Objekty obvykle ukládají seznam dostupných písem v jednom sdíleném `CObList` objektu. `CMFCToolBarFontComboBox` Použijete-li druhé přetížení konstruktoru a zadáte platný ukazatel na *pLstFontsExternal*, `CMFCToolBarFontComboBox` `CObList` bude tento objekt místo toho naplnit *pLstFontsExternal* body na s dostupnými písmy.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCToolBarFontComboBox` objekt. Tento fragment kódu je součástí ukázky panelu [aplikace Word](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>CMFCToolBarFontComboBox::GetFontDesc

Vrátí ukazatel na `CMFCFontInfo` objekt pro zadaný index v poli se seznamem.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
pro Určuje index založený na nule položky pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CMFCFontInfo` objekt. Pokud *iIndex* neurčuje platný index položky, vrácená hodnota je null.

##  <a name="m_nfontheight"></a>CMFCToolBarFontComboBox::m_nFontHeight

Určuje výšku znaků v pixelech v poli se seznamem písem, pokud má pole se seznamem styl vykreslování vlastníka.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Poznámky

Pokud je `m_nFontHeight` proměnná 0, vypočítává se výška automaticky podle výchozího písma v poli se seznamem. Výška zahrnuje stoupání znaků nad účaří a klesání znaků pod základnu.

##  <a name="setfont"></a>CMFCToolBarFontComboBox::SetFont

Vybere písmo v poli se seznamem písem podle názvu písma a sady znaků, které jsou zadány v parametrech.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
pro Určuje název nebo předponu písma.

*nCharSet*<br/>
pro Určuje znakovou sadu.

*bExact*<br/>
pro Určuje, zda *lpszName* obsahuje název písma nebo předponu písma.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo písmo vybráno úspěšně; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud má *bExact* hodnotu true, tato metoda vybere písmo, které přesně odpovídá názvu, který jste zadali jako *lpszName*. Pokud je *BEXACT* false, tato metoda vybere písmo, které začíná textem zadaným jako *lpszName* a který používá znakovou sadu, kterou jste zadali jako *nCharSet*. Pokud je *nCharSet* nastaveno na DEFAULT_CHARSET, bude znaková sada ignorována a k výběru písma bude použita pouze *lpszName* .

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton – třída](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo – třída](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
