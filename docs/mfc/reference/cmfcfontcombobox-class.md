---
title: CMFCFontComboBox – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
ms.openlocfilehash: 69e8f81e7e01d0610f3cbf88ac1725a21d59838f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505303"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox – třída

`CMFCFontComboBox` Třída vytvoří ovládací prvek pole se seznamem, který obsahuje seznam písem.

## <a name="syntax"></a>Syntaxe

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|`CMFCFontComboBox` Vytvoří objekt.|
|`CMFCFontComboBox::~CMFCFontComboBox`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|Volá se rozhraním, aby se určila relativní pozice nové položky v poli seřazený seznam pro ovládací prvek pole se seznamem aktuálního písma. (Overrides [CComboBox –:: CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Volá se rozhraním, aby se nakreslila zadaná položka v ovládacím prvku pole se seznamem aktuálního písma. (Overrides [CComboBox –::D rawitem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Načte informace o aktuálně vybraném písmu.|
|`CMFCFontComboBox::MeasureItem`|Volá se rozhraním, aby informovalo okna o dimenzích seznamu v aktuálním ovládacím prvku pole se seznamem písem. (Overrides [CComboBox –:: MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Přeloží zprávy oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Potlačení [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCFontComboBox::SelectFont](#selectfont)|Vybere písmo, které odpovídá zadaným kritériím z pole se seznamem Font.|
|[CMFCFontComboBox:: Setup](#setup)|Inicializuje seznam položek v poli se seznamem písem.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Určuje rozhraní, které má být použito k vykreslení popisků položek v aktuálním písmovém poli se seznamem.|

## <a name="remarks"></a>Poznámky

Chcete-li `CMFCFontComboBox` použít objekt v dialogovém okně, `CMFCFontComboBox` přidejte proměnnou do třídy dialog box. Poté v `OnInitDialog` metodě pro třídu dialogového okna zavolejte metodu [CMFCFontComboBox:: Setup](#setup) pro inicializaci seznamu položek v ovládacím prvku pole se seznamem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxfontcombobox. h

##  <a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox

`CMFCFontComboBox` Vytvoří objekt.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getselfont"></a>CMFCFontComboBox::GetSelFont

Načte informace o aktuálně vybraném písmu.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [třídy CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md) , který popisuje písmo. Může mít hodnotu NULL, pokud není vybráno žádné písmo v poli se seznamem.

### <a name="remarks"></a>Poznámky

##  <a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont

Určuje rozhraní, které má být použito k vykreslení popisků položek v aktuálním písmovém poli se seznamem.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Poznámky

Nastavte tento člen na hodnotu TRUE, chcete-li směrovat rozhraní tak, aby používalo stejné písmo pro vykreslení popisku každé položky. Nastavte tento člen na hodnotu FALSE, chcete-li směrovat rozhraní tak, aby vykreslilo jmenovku každé položky s písmem, jehož název je stejný jako popisek. Výchozí hodnota tohoto člena je FALSE.

##  <a name="selectfont"></a>CMFCFontComboBox::SelectFont

Vybere písmo, které odpovídá zadaným kritériím z pole se seznamem Font.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Parametry

*pDesc*<br/>
pro Odkazuje na objekt popisu písma.

*lpszName*<br/>
pro Určuje název písma.

*nCharSet*<br/>
pro Určuje znakovou sadu. Výchozí hodnota je DEFAULT_CHARSET. Další informace naleznete v tématu `lfCharSet` člen struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud položka v poli se seznamem písem odpovídá zadanému objektu popisu písma nebo názvu písma a znaku charset; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte, chcete-li vybrat položku a přejít k ní v poli se seznamem písem, které odpovídá zadanému písmu.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `SelectFont` metodu `CMFCFontComboBox` ve třídě. Tento příklad je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

##  <a name="setup"></a>CMFCFontComboBox:: Setup

Inicializuje seznam položek v poli se seznamem písem.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Parametry

*nFontType*<br/>
pro Určuje typ písma. Výchozí hodnota je bitová kombinace (nebo) hodnot DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE.

*nCharSet*<br/>
pro Určuje znakovou sadu písma. Výchozí hodnota je DEFAULT_CHARSET.

*nPitchAndFamily*<br/>
pro Určuje rozteč písma a rodinu. Výchozí hodnota je DEFAULT_PITCH.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se pole se seznamem písem úspěšně inicializoval; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda inicializuje pole se seznamem písem vynásobením aktuálně nainstalovaných písem, která odpovídají zadaným parametrům, a vložením těchto názvů písem do pole se seznamem Font.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `Setup` metodu `CMFCFontComboBox` ve třídě. Tento příklad je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo – třída](../../mfc/reference/cmfcfontinfo-class.md)
