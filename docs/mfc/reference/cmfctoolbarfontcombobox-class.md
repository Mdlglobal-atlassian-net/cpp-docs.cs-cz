---
title: Cmfctoolbarfontcombobox – třída
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
ms.openlocfilehash: 4ab4eece67406b1c5a52669beafc9bfd8acd32e6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283719"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Cmfctoolbarfontcombobox – třída

Tlačítka panelu nástrojů obsahující ovládací prvek pole se seznamem, který umožňuje uživateli vybrat písmo ze seznamu systémových písem.

## <a name="syntax"></a>Syntaxe

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Vytvoří `CMFCToolBarFontComboBox` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Vrací ukazatel `CMFCFontInfo` objekt pro zadaný index v poli se seznamem.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Vybere písmo v poli se seznamem písma podle buď název písma nebo předpona a znaková sada písmo.|

### <a name="data-members"></a>Datové členy

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
Výška znaky v poli se seznamem písma.

## <a name="remarks"></a>Poznámky

Chcete-li na panel nástrojů přidat tlačítko pole se seznamem písma, postupujte takto:

1. Zarezervujte si pro tlačítko zástupný identifikátor ID prostředku v nadřazeném prostředku panelu nástrojů.

1. Vytvoření `CMFCToolBarFontComboBox` objektu.

1. V popisovači zpráv, která zpracovává zprávu AFX_WM_RESETTOOLBAR, nahraďte původní tlačítko Nová tlačítka pole se seznamem pomocí [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Synchronizovat vybrané v poli se seznamem písma v dokumentu s použitím písmo [CMFCToolBarFontComboBox::SetFont](#setfont) metody.

Chcete-li synchronizovat s písmo vybrané v poli se seznamem písma dokumentu, použijte [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) má metoda načíst atributy vybraného písma a použít tyto atributy k vytvoření [ Cfont – třída](../../mfc/reference/cfont-class.md) objektu.

Tlačítko pole se seznamem písma volá funkci Win32 [EnumFontFamiliesEx](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesexa) určit písma obrazovky a tiskárny, které jsou k dispozici v systému.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Vytvoří [cmfctoolbarfontcombobox –](../../mfc/reference/cmfctoolbarfontcombobox-class.md) objektu.

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
[in] ID příkazu pole se seznamem.

*iImage*<br/>
[in] Index založený na nule Obrázek panelu nástrojů. Na obrázku se nachází v [cmfctoolbarimages – třída](../../mfc/reference/cmfctoolbarimages-class.md) objekt, který [cmfctoolbar – třída](../../mfc/reference/cmfctoolbar-class.md) třída udržuje.

*nFontType*<br/>
[in] Typy písem, které obsahuje pole se seznamem. Tento parametr může být kombinací (logický OR) následující hodnoty:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
[in] Pokud je nastaveno na DEFAULT_CHARSET, pole se seznamem obsahuje všechny jednoznačně názvem písma ve všech sadách znaků. (Pokud existují dvě písma se stejným názvem, pole se seznamem obsahuje jeden z nich). Pokud je nastaveno na hodnotu set platný znak pole se seznamem obsahuje pouze písma v zadanou znakovou sadu. Zobrazit [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) nastavuje pro výpis znaku je to možné.

*dwStyle*<br/>
[in] Styl pole se seznamem. (viz [pole se seznamem stylů](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
[in] Šířka v pixelech ovládacích prvků pro úpravy.

*nPitchAndFamily*<br/>
[in] Je-li nastaveno na DEFAULT_PITCH, pole se seznamem obsahuje písma, bez ohledu na výšku. Pokud sada FIXED_PITCH nebo VARIABLE_PITCH, pole se seznamem obsahuje pouze písma s tímto typem rozteč. Filtrování podle rodinu písem se momentálně nepodporuje.

*pLstFontsExternal*<br/>
[out] Ukazatel [coblist – třída](../../mfc/reference/coblist-class.md) objekt, který uchovává dostupná písma.

### <a name="remarks"></a>Poznámky

Obvykle `CMFCToolBarFontComboBox` objekty uložení seznamu dostupných písem v jedné sdílené `CObList` objektu. Pokud používáte druhé přetížení konstruktoru a poskytnout platný ukazatel na *pLstFontsExternal*, který `CMFCToolBarFontComboBox` objektu se místo toho vyplnit `CObList` , který *pLstFontsExternal* odkazuje na dostupné písma.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCToolBarFontComboBox` objektu. Tento fragment kódu je součástí [slovo panel vzorku](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc

Vrací ukazatel `CMFCFontInfo` objekt pro zadaný index v poli se seznamem.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
[in] Určuje index založený na nule položky pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Ukazatel `CMFCFontInfo` objektu. Pokud *iIndex* neurčuje platnou položkou index, vrácená hodnota je NULL.

##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight

Určuje výšku v pixelech, znaků v poli se seznamem písma, pokud má pole se seznamem styl kreslení vlastníka.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Poznámky

Pokud `m_nFontHeight` proměnná je 0, výška se vypočítá automaticky podle výchozí písmo pole se seznamem. Výška zahrnuje ascent znaky nad směrný plán i sestup znaků pod směrného plánu.

##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont

Vybere písmo v poli se seznamem písma podle znaků a název písma nastavit, které jsou zadány v parametrech.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Parametry

*lpszName*<br/>
[in] Určuje název písma nebo předponu.

*nCharSet*<br/>
[in] Určuje znakovou sadu.

*bExact*<br/>
[in] Určuje, zda *lpszName* obsahuje název písma nebo předpona písma.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl úspěšně; vybrán písma jinak 0.

### <a name="remarks"></a>Poznámky

Pokud *bExact* má hodnotu TRUE, tato metoda vybere písmo, který přesně odpovídá názvu, který jste zadali jako *lpszName*. Pokud *bExact* má hodnotu FALSE, tato metoda vybere písma, která začíná textem zadaný jako *lpszName* a, která používá znakovou sadu, která jste zadali jako *nCharSet*. Pokud *nCharSet* nastavený pro DEFAULT_CHARSET, znakové sady bude ignorována a pouze *lpszName* se použije k vyberte písmo.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton – třída](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo – třída](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Návod: Vkládání ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)
