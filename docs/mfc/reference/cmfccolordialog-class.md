---
title: Třída CMFCColorDialog
ms.date: 11/04/2016
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
ms.openlocfilehash: 987e4f1e5e89c3c56b58adaad76cfd23d5e26c52
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367721"
---
# <a name="cmfccolordialog-class"></a>Třída CMFCColorDialog

Třída `CMFCColorDialog` představuje dialogové okno výběru barev.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCColorDialog::DIALOGOVÉ OKNO CMFCColorDialog](#cmfccolordialog)|Vytvoří `CMFCColorDialog` objekt.|
|`CMFCColorDialog::~CMFCColorDialog`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|Vrátí aktuální vybranou barvu.|
|[CMFCColorDialog::GetPalette](#getpalette)|Vrátí paletu barvy.|
|`CMFCColorDialog::PreTranslateMessage`|Přeloží zprávy okna před jejich odesláním do funkcí [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systému Windows. Syntaxe a další informace naleznete [v tématu CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Přepíše `CDialogEx::PreTranslateMessage`.)|
|[CMFCColorDialog::Znovusestavitpaletu](#rebuildpalette)|Odvozuje paletu ze systémové palety.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Nastaví aktuální vybranou barvu.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Nastaví barvu nejvíce ekvivalentní zadané hodnotě RGB.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Vybere hodnotu RGB pro první stránku vlastností.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Vybere hodnotu RGB pro druhou stránku vlastností.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|`m_bIsMyPalette`|PRAVDA, pokud dialogové okno výběru barev používá vlastní paletu barev, nebo NEPRAVDA, pokud dialogové okno používá paletu určenou v konstruktoru. `CMFCColorDialog`|
|`m_bPickerMode`|TRUE, když uživatel vybírá barvu z dialogového okna výběru; jinak NEPRAVDA.|
|`m_btnColorSelect`|Tlačítko barva, které uživatel vybral.|
|`m_CurrentColor`|Aktuálně vybraná barva.|
|`m_hcurPicker`|Kurzor, který se používá k výběru barvy.|
|`m_NewColor`|Perspektivní vybraná barva, která může být trvale vybrána nebo vrácena do původní barvy.|
|`m_pColourSheetOne`|Ukazatel na první stránku vlastností listu vlastností výběru barev.|
|`m_pColourSheetTwo`|Ukazatel na druhou stránku vlastností listu vlastností výběru barev.|
|`m_pPalette`|Aktuální logická paleta.|
|`m_pPropSheet`|Ukazatel na seznam vlastností dialogového okna výběru barev|
|`m_wndColors`|Objekt ovládacího prvku pro výběr barvy.|
|`m_wndStaticPlaceHolder`|Statický ovládací prvek, který je zástupným symbolem pro seznam vlastností výběru barev.|

## <a name="remarks"></a>Poznámky

Dialogové okno výběru barev se zobrazí jako seznam vlastností se dvěma stránkami. Na první stránce vyberete standardní barvu ze systémové palety; na druhé stránce vyberete vlastní barvu.

Můžete vytvořit `CMFCColorDialog` objekt v zásobníku `DoModal`a pak volání , předání `CMFCColorDialog` počáteční barvu jako parametr konstruktoru. Dialogové okno výběru barev pak vytvoří několik objektů [třídy CMFCColorPickerCtrl třídy](../../mfc/reference/cmfccolorpickerctrl-class.md) pro zpracování každé palety barev.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CmFCDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat dialog barev pomocí `CMFCColorDialog` různých metod ve třídě. Příklad ukazuje, jak nastavit aktuální a nové barvy dialogového okna a jak nastavit červenou, zelenou a modrou složku vybrané barvy na dvou stránkách vlastností dialogového okna barev. Tento příklad je součástí [ukázky Nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolordialog.h

## <a name="cmfccolordialogcmfccolordialog"></a><a name="cmfccolordialog"></a>CMFCColorDialog::DIALOGOVÉ OKNO CMFCColorDialog

Vytvoří `CMFCColorDialog` objekt.

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>Parametry

*clrInit*<br/>
[v] Výchozí výběr barev. Pokud není zadána žádná hodnota, výchozí hodnota je RGB(0,0,0) (černá).

*dwFlags*<br/>
[v] Vyhrazena.

*pParentWnd*<br/>
[v] Ukazatel na nadřazené nebo vlastníjméno okna dialogového okna.

*hPal*<br/>
[v] Úchyt palety barev.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfccolordialoggetcolor"></a><a name="getcolor"></a>CMFCColorDialog::GetColor

Načte barvu, kterou uživatel vybere z dialogového okna barev.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF,](/windows/win32/gdi/colorref) která obsahuje informace rgb pro barvu vybranou v dialogovém okně barva.

### <a name="remarks"></a>Poznámky

Volání této funkce po `DoModal` volání metody.

## <a name="cmfccolordialoggetpalette"></a><a name="getpalette"></a>CMFCColorDialog::GetPalette

Načte paletu barev, která je k dispozici v aktuálním dialogu barev.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CPalette` objekt, který byl `CMFCColorDialog` zadán v konstruktoru.

### <a name="remarks"></a>Poznámky

Paleta barev určuje barvy, které si uživatel může vybrat.

## <a name="cmfccolordialogrebuildpalette"></a><a name="rebuildpalette"></a>CMFCColorDialog::Znovusestavitpaletu

Odvozuje paletu ze systémové palety.

```
void RebuildPalette();
```

## <a name="cmfccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor

Nastaví aktuální barvu dialogového okna.

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>Parametry

*Rgb*<br/>
[v] Hodnota barvy RGB

### <a name="remarks"></a>Poznámky

## <a name="cmfccolordialogsetnewcolor"></a><a name="setnewcolor"></a>CMFCColorDialog::SetNewColor

Nastaví aktuální barvu na barvu v aktuální paletě, která je nejvíce podobná.

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Parametry

*Rgb*<br/>
[v] [Colorref,](/windows/win32/gdi/colorref) který určuje barvu RGB.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolordialogsetpageone"></a><a name="setpageone"></a>CMFCColorDialog::SetPageOne

Explicitně určuje červenou, zelenou a modrou složku vybrané barvy na první stránce vlastností barevného dialogu.

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

*R*<br/>
[v] Určuje červenou součást hodnoty RGB.

*G*<br/>
[v] Určuje zelenou součást hodnoty RGB.

*B*<br/>
[v] Určuje modrou součást hodnoty RGB.

### <a name="remarks"></a>Poznámky

## <a name="cmfccolordialogsetpagetwo"></a><a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo

Explicitně určuje červenou, zelenou a modrou složku vybrané barvy na druhé stránce vlastností barevného dialogu.

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

*R*<br/>
[v] Určuje červenou součást hodnoty RGB.

*G*<br/>
[v] Určuje zelenou součást hodnoty RGB.

*B*<br/>
[v] Určuje modrou součást hodnoty RGB.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)
