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
ms.openlocfilehash: 60b4b7cdfdace2332de35dd93c43eacf592e99e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367490"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox – třída

Třída `CMFCFontComboBox` vytvoří ovládací prvek pole se seznamem, který obsahuje seznam písem.

## <a name="syntax"></a>Syntaxe

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Vytvoří `CMFCFontComboBox` objekt.|
|`CMFCFontComboBox::~CMFCFontComboBox`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|Volat rámci k určení relativní pozice nové položky v seznamu seřazené aktuální ovládací prvek pole se seznamem písma. (Přepíše [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Volat rámci nakreslit zadanou položku v aktuální ovládací prvek pole se seznamem písma. (Přepíše [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Načte informace o aktuálně vybraném písmu.|
|`CMFCFontComboBox::MeasureItem`|Volat rámci informovat Windows o rozměrech seznamu v aktuálním ovládacím prvku pole se seznamem písma. (Přepíše [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Přeloží zprávy okna před jejich odesláním do funkcí [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systému Windows. (Přepíše [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCFontComboBox::SelectFont](#selectfont)|Vybere písmo, které odpovídá zadaným kritériím z pole se seznamem písem.|
|[CMFCFontComboBox::Nastavení](#setup)|Inicializuje seznam položek v poli se seznamem písem.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Označuje rámci, které písmo použít k nakreslení popisky položek v aktuálním poli se seznamem písma.|

## <a name="remarks"></a>Poznámky

Chcete-li `CMFCFontComboBox` použít objekt v dialogovém okně, přidejte proměnnou `CMFCFontComboBox` do třídy dialogového okna. Potom v `OnInitDialog` metodě třídy dialogového okna volejte [metodu CMFCFontComboBox::Setup](#setup) metodu pro inicializaci seznamu položek v ovládacím prvku pole se seznamem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxfontcombobox.h

## <a name="cmfcfontcomboboxcmfcfontcombobox"></a><a name="cmfcfontcombobox"></a>CMFCFontComboBox::CMFCFontComboBox

Vytvoří `CMFCFontComboBox` objekt.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcfontcomboboxgetselfont"></a><a name="getselfont"></a>CMFCFontComboBox::GetSelFont

Načte informace o aktuálně vybraném písmu.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [třídy CMFCFontInfo,](../../mfc/reference/cmfcfontinfo-class.md) který popisuje písmo. Může být null, pokud není vybráno žádné písmo v poli se seznamem.

### <a name="remarks"></a>Poznámky

## <a name="cmfcfontcomboboxm_bdrawusingfont"></a><a name="m_bdrawusingfont"></a>CMFCFontComboBox::m_bDrawUsingFont

Označuje rámci, které písmo použít k nakreslení popisky položek v aktuálním poli se seznamem písma.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Poznámky

Nastavte tento člen na TRUE na přímé rozhraní použít stejné písmo k nakreslení každého popisku položky. Nastavte tento člen na FALSE na přímé rozhraní k tomu každý popisek položky s písmem, jehož název je stejný jako popisek. Výchozí hodnota tohoto člena je FALSE.

## <a name="cmfcfontcomboboxselectfont"></a><a name="selectfont"></a>CMFCFontComboBox::SelectFont

Vybere písmo, které odpovídá zadaným kritériím z pole se seznamem písem.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Parametry

*pDesc*<br/>
[v] Odkazuje na objekt popisu písma.

*název lpsz*<br/>
[v] Určuje název písma.

*nSada char*<br/>
[v] Určuje znakovou sadu. Výchozí hodnota je DEFAULT_CHARSET. Další informace naleznete `lfCharSet` v člen [logfont](/windows/win32/api/wingdi/ns-wingdi-logfontw) struktury.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud položka v poli se seznamem písem odpovídá zadanému objektu popisu písma nebo názvu písma a znakové sadě; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete vybrat položku a přejít na ni v poli se seznamem písem, které odpovídá zadanému písmu.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `SelectFont` používat metodu ve `CMFCFontComboBox` třídě. Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

## <a name="cmfcfontcomboboxsetup"></a><a name="setup"></a>CMFCFontComboBox::Nastavení

Inicializuje seznam položek v poli se seznamem písem.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Parametry

*nTyp písma*<br/>
[v] Určuje typ písma. Výchozí hodnota je bitová kombinace (OR) DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE.

*nSada char*<br/>
[v] Určuje znakovou sadu písma. Výchozí hodnota je DEFAULT_CHARSET.

*nPitchAndFamily*<br/>
[v] Určuje výšku písma a rodinu. Výchozí hodnota je DEFAULT_PITCH.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud bylo pole se seznamem písem úspěšně inicializováno; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda inicializuje pole se seznamem písem výčetem aktuálně nainstalovaných písem, která odpovídají zadaným parametrům, a vložením těchto názvů písem do pole se seznamem písem.

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak `Setup` používat metodu ve `CMFCFontComboBox` třídě. Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[Třída CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)
