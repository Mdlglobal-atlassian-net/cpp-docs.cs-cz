---
title: CFontDialog – třída
ms.date: 11/04/2016
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
ms.openlocfilehash: b538acd564402459a05cc96303b63a35a99ba243
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506473"
---
# <a name="cfontdialog-class"></a>CFontDialog – třída

Umožňuje začlenit dialogové okno výběru písma do aplikace.

## <a name="syntax"></a>Syntaxe

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|`CFontDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožní uživateli provést výběr.|
|[CFontDialog::GetCharFormat](#getcharformat)|Načte formátování znaků vybraného písma.|
|[CFontDialog:: GetColor](#getcolor)|Vrátí barvu vybraného písma.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Přiřadí charakteristiky aktuálně vybraného písma ke `LOGFONT` struktuře.|
|[CFontDialog::GetFaceName](#getfacename)|Vrátí název obličeje vybraného písma.|
|[CFontDialog:: GetSize](#getsize)|Vrátí velikost bodu vybraného písma.|
|[CFontDialog:: GetStyle](#getstylename)|Vrátí název stylu vybraného písma.|
|[CFontDialog:: getweight](#getweight)|Vrátí váhu vybraného písma.|
|[CFontDialog::IsBold](#isbold)|Určuje, zda je písmo tučné.|
|[CFontDialog::IsItalic](#isitalic)|Určuje, zda je písmo kurzívou.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Určuje, zda je písmo zobrazeno přeškrtnutím.|
|[CFontDialog::IsUnderline](#isunderline)|Určuje, zda je písmo podtržené.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Struktura používaná k přizpůsobení `CFontDialog` objektu.|

## <a name="remarks"></a>Poznámky

`CFontDialog` Objekt je dialogové okno se seznamem písem, která jsou aktuálně nainstalována v systému. Uživatel může ze seznamu vybrat konkrétní písmo a tento výběr se pak nahlásí zpátky do aplikace.

Chcete-li `CFontDialog` vytvořit objekt, použijte poskytnutý konstruktor nebo odvodit novou podtřídu a použijte vlastní konstruktor.

`m_cf` Jakmile je `CFontDialog` objekt vytvořen, můžete použít strukturu pro inicializaci hodnot nebo stavů ovládacích prvků v dialogovém okně. Struktura [m_cf](#m_cf) je typu [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw). Další informace o této struktuře naleznete v Windows SDK.

Po inicializaci ovládacích prvků objektu dialogového okna zavolejte `DoModal` členskou funkci pro zobrazení dialogového okna a umožněte uživateli vybrat písmo. `DoModal`Vrátí, zda uživatel vybral tlačítko OK (IDOK) nebo zrušit (IDCANCEL).

Pokud `DoModal` vrátí IDOK, můžete použít jednu z `CFontDialog`členských funkcí k načtení informací o vstupu uživatele.

Pomocí funkce Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) můžete zjistit, jestli při inicializaci dialogového okna došlo k chybě, a získat další informace o chybě. Další informace o této funkci naleznete v Windows SDK.

`CFontDialog`spoléhá na COMMDLG. Soubor DLL dodávaný se systémem Windows verze 3,1 nebo novějším.

Chcete-li přizpůsobit dialogové okno, odvodit třídu `CFontDialog`z, zadat vlastní šablonu dialogového okna a přidat mapu zpráv pro zpracování zpráv s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měly být předány základní třídě.

Přizpůsobení funkce zavěšení není vyžadováno.

Další informace o použití `CFontDialog`naleznete v tématu [Common dialoging Class](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs. h

##  <a name="cfontdialog"></a>CFontDialog::CFontDialog

`CFontDialog` Vytvoří objekt.

```
CFontDialog(
    LPLOGFONT lplfInitial = NULL,
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,
    DWORD dwFlags = CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*plfInitial*<br/>
Ukazatel na strukturu dat [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) , která umožňuje nastavit některé charakteristiky písma.

*charFormat*<br/>
Ukazatel na strukturu dat [Charformat](/windows/win32/api/richedit/ns-richedit-_charformat) , která umožňuje nastavit některé charakteristiky písma v ovládacím prvku pro úpravy s formátováním.

*dwFlags*<br/>
Určuje jeden nebo více příznaků výběru písma. Jednu nebo více přednastavených hodnot lze kombinovat pomocí bitového operátoru OR. Pokud upravíte `m_cf.Flag`člena struktury s, nezapomeňte ve svých změnách použít bitový operátor OR, abyste zachovali výchozí chování beze změny. Podrobnosti o každém z těchto příznaků naleznete v popisu struktury [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) v Windows SDK.

*pdcPrinter*<br/>
Ukazatel na kontext zařízení tiskárny. Pokud je tento parametr zadán, odkazuje na kontext zařízení tiskárny pro tiskárnu, na které mají být písma vybrána.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastní okno dialogového okna písma.

### <a name="remarks"></a>Poznámky

Všimněte si, že konstruktor automaticky vyplní členy `CHOOSEFONT` struktury. Ty byste měli změnit, jenom pokud chcete, aby se dialogové okno písma lišilo od výchozího.

> [!NOTE]
>  První verze této funkce existuje pouze v případě, že není k dispozici žádná podpora bohatě s ovládacími prvky pro úpravy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

##  <a name="domodal"></a>CFontDialog::D oModal

Voláním této funkce zobrazíte dialogové okno běžné písmo Windows a umožníte uživateli zvolit písmo.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud se vrátí IDCANCEL, zavolejte funkci Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) a určete, jestli došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel vybral tlačítko OK nebo Storno.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogu písma nastavením členů struktury [m_cf](#m_cf) , měli byste to provést před voláním `DoModal`, ale po sestavení objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete zavolat jiné členské funkce pro načtení nastavení nebo zadání informací uživatelem do dialogového okna.

### <a name="example"></a>Příklad

  Podívejte se na příklady pro [CFontDialog:: CFontDialog](#cfontdialog) a [CFontDialog:: GetColor](#getcolor).

##  <a name="getcharformat"></a>CFontDialog::GetCharFormat

Načte formátování znaků vybraného písma.

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Parametry

*cf*<br/>
Struktura [Charformat](/windows/win32/api/richedit/ns-richedit-_charformat) obsahující informace o formátování znaku vybraného písma.

##  <a name="getcolor"></a>CFontDialog:: GetColor

Voláním této funkce načtete vybranou barvu písma.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva vybraného písma

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

##  <a name="getcurrentfont"></a>CFontDialog::GetCurrentFont

Voláním této funkce přiřadíte vlastnosti aktuálně vybraného písma k členům struktury [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Parametry

*lplf*<br/>
Ukazatel na `LOGFONT` strukturu.

### <a name="remarks"></a>Poznámky

Pro `CFontDialog` přístup k jednotlivým vlastnostem aktuálního písma jsou k dispozici jiné členské funkce.

Pokud je tato funkce volána během volání [DoModal](#domodal), vrátí aktuální výběr v čase (co uživatel uvidí nebo se v dialogovém okně změnil). Pokud je tato funkce volána po volání `DoModal` (pouze pokud `DoModal` vrátí IDOK), vrátí, co uživatel skutečně vybral.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>CFontDialog:: getface

Voláním této funkce načtete název obličeje vybraného písma.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název obličeje písma vybraného v `CFontDialog` dialogovém okně

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>CFontDialog:: GetSize

Voláním této funkce načtete velikost vybraného písma.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost písma v desetinách bodu

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>CFontDialog:: GetStyle

Voláním této funkce načtete název stylu vybraného písma.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Návratová hodnota

Styl názvu písma

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

##  <a name="getweight"></a>CFontDialog:: getweight

Voláním této funkce načtete váhu vybraného písma.

```
int GetWeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Tloušťka vybraného písma

### <a name="remarks"></a>Poznámky

Další informace o váhy písma naleznete v tématu [CFont –:: CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>CFontDialog:: Bold

Voláním této funkce určíte, zda je vybrané písmo tučné.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud má vybrané písmo tučnou charakteristiku povoleno; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>CFontDialog::-kurzíva

Voláním této funkce určíte, zda je zvolený Font kurzívou.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud má vybrané písmo kurzívu povoleno; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>CFontDialog::-přeškrtnutí

Voláním této funkce určíte, zda se vybrané písmo zobrazí s přeškrtnutím.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud má vybrané písmo Přeškrtnutéelné charakteristiky; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>CFontDialog:: depodtrhávat

Voláním této funkce určíte, zda je vybrané písmo podtržené.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud vybrané písmo má vlastnost podtržení povoleno; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>  CFontDialog::m_cf

Struktura, jejíž členové ukládají charakteristiky objektu dialogového okna.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Poznámky

Po sestavení `CFontDialog` objektu lze použít `m_cf` k úpravě různých aspektů `DoModal` dialogového okna před voláním členské funkce. Další informace o této struktuře naleznete v tématu [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Viz také:

[HIERSVR Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
