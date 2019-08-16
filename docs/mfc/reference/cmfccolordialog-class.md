---
title: CMFCColorDialog – třída
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
ms.openlocfilehash: 9e018c122cded09e5366c3b349525fa7cc004897
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505344"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog – třída

`CMFCColorDialog` Třída představuje dialogové okno Výběr barvy.

## <a name="syntax"></a>Syntaxe

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|`CMFCColorDialog` Vytvoří objekt.|
|`CMFCColorDialog::~CMFCColorDialog`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|Vrátí aktuální vybranou barvu.|
|[CMFCColorDialog::GetPalette](#getpalette)|Vrátí paletu barvy.|
|`CMFCColorDialog::PreTranslateMessage`|Přeloží zprávy oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Syntaxi a další informace naleznete v tématu [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Overrides `CDialogEx::PreTranslateMessage`.)|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Odvodí paletu z palety systému.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Nastaví aktuální vybranou barvu.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Nastaví barvu, která je shodná s zadanou hodnotou RGB.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Vybere hodnotu RGB pro první stránku vlastností.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Vybere hodnotu RGB pro druhou stránku vlastností.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|`m_bIsMyPalette`|TRUE, pokud dialogové okno Výběr barvy používá vlastní paletu barev, nebo NEPRAVDA, pokud dialogové okno používá paletu, která je určena `CMFCColorDialog` v konstruktoru.|
|`m_bPickerMode`|TRUE, když uživatel vybere barvu z dialogového okna Výběr; v opačném případě FALSE.|
|`m_btnColorSelect`|Tlačítko barvy, které uživatel vybral.|
|`m_CurrentColor`|Aktuálně vybraná barva.|
|`m_hcurPicker`|Kurzor, který se používá k výběru barvy.|
|`m_NewColor`|Potenciální vybraná barva, kterou lze trvale vybrat nebo vrátit do původní barvy.|
|`m_pColourSheetOne`|Ukazatel na první stránku vlastností seznamu vlastností výběru barvy.|
|`m_pColourSheetTwo`|Ukazatel na druhou stránku vlastností seznamu vlastností výběru barvy.|
|`m_pPalette`|Aktuální logická paleta|
|`m_pPropSheet`|Ukazatel na seznam vlastností dialogového okna Výběr barvy.|
|`m_wndColors`|Objekt ovládacího prvku pro výběr barvy|
|`m_wndStaticPlaceHolder`|Statický ovládací prvek, který je zástupným symbolem pro výběr barvy seznamu vlastností.|

## <a name="remarks"></a>Poznámky

Dialogové okno Výběr barvy se zobrazí jako seznam vlastností se dvěma stránkami. Na první stránce vyberete ze systémové palety standardní barvu. na druhé stránce vyberte vlastní barvu.

Můžete vytvořit `CMFCColorDialog` objekt v zásobníku a pak zavolat `DoModal`a předat počáteční barvu `CMFCColorDialog` jako parametr konstruktoru. Dialogové okno Výběr barvy pak vytvoří několik objektů [třídy CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) pro zpracování každé palety barev.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat dialog barvy pomocí různých metod ve `CMFCColorDialog` třídě. Tento příklad ukazuje, jak nastavit aktuální a nové barvy dialogového okna a jak nastavit červené, zelené a modré komponenty vybrané barvy na dvou stránkách vlastností dialogového okna barva. Tento příklad je součástí [ukázky nové ovládací prvky](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcolordialog. h

##  <a name="cmfccolordialog"></a>CMFCColorDialog::CMFCColorDialog

`CMFCColorDialog` Vytvoří objekt.

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>Parametry

*clrInit*<br/>
pro Výchozí výběr barvy Pokud není zadána žádná hodnota, výchozí hodnota je RGB (0, 0, 0) (černá).

*dwFlags*<br/>
pro Rezervovaný.

*pParentWnd*<br/>
pro Ukazatel na nadřazené nebo vlastní okno dialogového okna.

*hPal*<br/>
pro Popisovač palety barev.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="getcolor"></a>CMFCColorDialog:: GetColor

Načte barvu, kterou uživatel vybere z dialogového okna barvy.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) , která obsahuje informace RGB barvy vybrané v dialogovém okně Barva.

### <a name="remarks"></a>Poznámky

Tuto funkci zavolejte po volání `DoModal` metody.

##  <a name="getpalette"></a>CMFCColorDialog:: getpaleta

Načte paletu barev, která je k dispozici v dialogovém okně aktuální barva.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CPalette` objekt, který byl zadán `CMFCColorDialog` v konstruktoru.

### <a name="remarks"></a>Poznámky

Barevná paleta určuje barvy, které může uživatel zvolit.

##  <a name="rebuildpalette"></a>CMFCColorDialog::RebuildPalette

Odvodí paletu z palety systému.

```
void RebuildPalette();
```

##  <a name="setcurrentcolor"></a>CMFCColorDialog::SetCurrentColor

Nastaví aktuální barvu dialogového okna.

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>Parametry

*režimu*<br/>
pro Hodnota barvy RGB

### <a name="remarks"></a>Poznámky

##  <a name="setnewcolor"></a>CMFCColorDialog::SetNewColor

Nastaví aktuální barvu na barvu v aktuální paletě, která je nejvíce podobná.

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Parametry

*režimu*<br/>
pro [COLORREF](/windows/win32/gdi/colorref) , který určuje barvu RGB.

### <a name="remarks"></a>Poznámky

##  <a name="setpageone"></a>CMFCColorDialog::SetPageOne

Explicitně určuje červené, zelené a modré komponenty vybrané barvy na první stránce vlastností dialogového okna barvy.

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

*R*<br/>
pro Určuje červenou komponentu hodnoty RGB.

*G*<br/>
pro Určuje zelenou součást hodnoty RGB.

*B*<br/>
pro Určuje modrou komponentu hodnoty RGB.

### <a name="remarks"></a>Poznámky

##  <a name="setpagetwo"></a>CMFCColorDialog::SetPageTwo

Explicitně určuje červené, zelené a modré komponenty vybrané barvy na druhé stránce vlastností dialogového okna barvy.

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Parametry

*R*<br/>
pro Určuje červenou komponentu hodnoty RGB.

*G*<br/>
pro Určuje zelenou komponentu hodnoty RGB.

*B*<br/>
pro Určuje modrou komponentu hodnoty RGB.

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl – třída](../../mfc/reference/cmfccolorpickerctrl-class.md)
