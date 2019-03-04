---
title: Cmfcfontcombobox – třída
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
ms.openlocfilehash: 6d0b2fc22d1d0779db17e970118694270a206439
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272669"
---
# <a name="cmfcfontcombobox-class"></a>Cmfcfontcombobox – třída

`CMFCFontComboBox` Třída vytvoří ovládací prvek pole se seznamem, který obsahuje seznam písem.

## <a name="syntax"></a>Syntaxe

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|Vytvoří `CMFCFontComboBox` objektu.|
|`CMFCFontComboBox::~CMFCFontComboBox`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|Volá se rozhraním, aby určení relativní pozice nové položky v poli seřazený seznam aktuální prvek pole se seznamem písma. (Přepíše [CComboBox::CompareItem](../../mfc/reference/ccombobox-class.md#compareitem).)|
|`CMFCFontComboBox::DrawItem`|Volá se rozhraním, chcete-li nakreslit zadanou položku v aktuální prvek pole se seznamem písma. (Přepíše [CComboBox::DrawItem](../../mfc/reference/ccombobox-class.md#drawitem).)|
|[CMFCFontComboBox::GetSelFont](#getselfont)|Načte informace o aktuálně vybraného písma.|
|`CMFCFontComboBox::MeasureItem`|Volá se rozhraním informovat Windows rozměry pole se seznamem v aktuální prvek pole se seznamem písma. (Přepíše [CComboBox::MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem).)|
|`CMFCFontComboBox::PreTranslateMessage`|Přeloží okno zprávy před odesláním do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkce Windows. (Přepíše [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCFontComboBox::SelectFont](#selectfont)|Vybere písmo, která odpovídá zadaným kritériím v poli se seznamem písma.|
|[CMFCFontComboBox::Setup](#setup)|Inicializuje seznam položek v poli se seznamem písma.|

### <a name="data-members"></a>Datové členy

|Název|Popis|
|----------|-----------------|
|[CMFCFontComboBox::m_bDrawUsingFont](#m_bdrawusingfont)|Určuje rozhraní Framework písma, které slouží k vykreslení položky popisky v aktuální pole se seznamem písma.|

## <a name="remarks"></a>Poznámky

Použití `CMFCFontComboBox` objektu v dialogovém okně, přidejte `CMFCFontComboBox` proměnné třídy dialogového okna. Pak v `OnInitDialog` metodu třídy dialogového okna, volání [CMFCFontComboBox::Setup](#setup) metody k inicializaci seznam položek v ovládacím prvku pole se seznamem.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>Požadavky

**Header:** afxfontcombobox.h

##  <a name="cmfcfontcombobox"></a>  CMFCFontComboBox::CMFCFontComboBox

Vytvoří `CMFCFontComboBox` objektu.

```
CMFCFontComboBox();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getselfont"></a>  CMFCFontComboBox::GetSelFont

Načte informace o aktuálně vybraného písma.

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [cmfcfontinfo – třída](../../mfc/reference/cmfcfontinfo-class.md) objekt, který popisuje písma. To může mít hodnotu NULL, pokud není vybraný žádný font pole se seznamem.

### <a name="remarks"></a>Poznámky

##  <a name="m_bdrawusingfont"></a>  CMFCFontComboBox::m_bDrawUsingFont

Určuje rozhraní Framework písma, které slouží k vykreslení položky popisky v aktuální pole se seznamem písma.

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Poznámky

Tento člen nastavena na hodnotu TRUE pro přesměrování framework použít stejné písmo pro vykreslení každého popisku položky. Tento člen nastavte na hodnotu FALSE pro přímá rozhraní pro vykreslení každého popisku položky s písma, jehož název je stejný jako popisek. Výchozí hodnota tohoto člena je FALSE.

##  <a name="selectfont"></a>  CMFCFontComboBox::SelectFont

Vybere písmo, která odpovídá zadaným kritériím v poli se seznamem písma.

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>Parametry

*pDesc*<br/>
[in] Odkazuje na objekt popisu písma.

*lpszName*<br/>
[in] Určuje název písma.

*nCharSet*<br/>
[in] Určuje znakovou sadu. Výchozí hodnota je DEFAULT_CHARSET. Další informace najdete v tématu `lfCharSet` člena [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktury.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud položka v poli se seznamem písma odpovídá určené písmo popis objektu nebo název písma a charset; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tuto metodu použijte k výběru a přejděte na položku v poli se seznamem písma, která odpovídá zadaným písma.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `SelectFont` metodu `CMFCFontComboBox` třídy. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

##  <a name="setup"></a>  CMFCFontComboBox::Setup

Inicializuje seznam položek v poli se seznamem písma.

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>Parametry

*nFontType*<br/>
[in] Určuje typ písma. Výchozí hodnota je bitová kombinace (nebo) DEVICE_FONTTYPE, RASTER_FONTTYPE a TRUETYPE_FONTTYPE.

*nCharSet*<br/>
[in] Určuje znakovou sadu písma. Výchozí hodnota je DEFAULT_CHARSET.

*nPitchAndFamily*<br/>
[in] Určuje písmo rozteč a rodiny. Výchozí hodnota je DEFAULT_PITCH.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud byl úspěšně; inicializovat pole se seznamem písma v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda inicializuje pole se seznamem písma výčet nainstalovaný písma, které odpovídají zadaným parametrům a vkládání názvy těchto písmo v poli se seznamem písma.

### <a name="example"></a>Příklad

Následující příklad ukazuje způsob použití `Setup` metodu `CMFCFontComboBox` třídy. V tomto příkladu je součástí [nové ovládací prvky ukázka](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox – třída](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo – třída](../../mfc/reference/cmfcfontinfo-class.md)
