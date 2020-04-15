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
ms.openlocfilehash: 6ece239496def9fd65a95a622ac3c475fe5becea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373824"
---
# <a name="cfontdialog-class"></a>CFontDialog – třída

Umožňuje začlenit dialogové okno pro výběr písma do aplikace.

## <a name="syntax"></a>Syntaxe

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|Vytvoří `CFontDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFontDialog::DoModální](#domodal)|Zobrazí dialogové okno a umožní uživateli provést výběr.|
|[CFontDialog::GetCharFormat](#getcharformat)|Načte formátování znaků vybraného písma.|
|[CFontDialog::GetColor](#getcolor)|Vrátí barvu vybraného písma.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Přiřadí vlastnosti aktuálně vybraného písma `LOGFONT` ke struktuře.|
|[CFontDialog::GetFaceName](#getfacename)|Vrátí název tváře vybraného písma.|
|[CFontDialog::GetSize](#getsize)|Vrátí velikost bodu vybraného písma.|
|[CFontDialog::GetStyleName](#getstylename)|Vrátí název stylu vybraného písma.|
|[CFontDialog::GetWeight](#getweight)|Vrátí tloušťku vybraného písma.|
|[CFontDialog::IsBold](#isbold)|Určuje, zda je písmo tučné.|
|[CFontDialog::IsItalic](#isitalic)|Určuje, zda je písmo kurzívou.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Určuje, zda je písmo zobrazeno s přeškrtáním.|
|[cfontdialog::podtržení](#isunderline)|Určuje, zda je písmo podtrženo.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Struktura slouží k `CFontDialog` přizpůsobení objektu.|

## <a name="remarks"></a>Poznámky

Objekt `CFontDialog` je dialogové okno se seznamem písem, která jsou aktuálně nainstalována v systému. Uživatel může vybrat konkrétní písmo ze seznamu a tento výběr je pak hlášen zpět do aplikace.

Chcete-li `CFontDialog` vytvořit objekt, použijte zadaný konstruktor nebo odvodte novou podtřídu a použijte vlastní konstruktor.

Po `CFontDialog` vytvoření objektu můžete pomocí `m_cf` struktury inicializovat hodnoty nebo stavy ovládacích prvků v dialogovém okně. Struktura [m_cf](#m_cf) je typu [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw). Další informace o této struktuře naleznete v souboru Windows SDK.

Po inicializaci ovládacích prvků `DoModal` objektu dialogového okna zavolejte členské funkce, aby zobrazila dialogové okno a umožnila uživateli vybrat písmo. `DoModal`vrátí, zda uživatel zvolil tlačítko OK (IDOK) nebo Cancel (IDCANCEL).

Pokud `DoModal` vrátí IDOK, můžete `CFontDialog`použít jednu z 's členské funkce načíst informace vstup uživatelem.

Pomocí funkce Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) můžete určit, zda došlo k chybě během inicializace dialogového okna a získat další informace o chybě. Další informace o této funkci naleznete v souboru Windows SDK.

`CFontDialog`spoléhá na COMMDLG. Soubor DLL, který je dodáván se systémem Windows verze 3.1 a novější.

Chcete-li dialogové okno přizpůsobit, `CFontDialog`odvoděte třídu z aplikace , zadejte vlastní šablonu dialogového okna a přidejte mapu zpráv pro zpracování zpráv s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měly být předány základní třídě.

Přizpůsobení funkce háku není nutné.

Další informace o `CFontDialog`použití naleznete v [tématu Common Dialog Classes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

## <a name="cfontdialogcfontdialog"></a><a name="cfontdialog"></a>CFontDialog::CFontDialog

Vytvoří `CFontDialog` objekt.

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

*plfPočáteční*<br/>
Ukazatel na datovou strukturu [LOGFONT,](/windows/win32/api/wingdi/ns-wingdi-logfontw) která umožňuje nastavit některé vlastnosti písma.

*charFormat*<br/>
Ukazatel na datovou strukturu [CHARFORMAT,](/windows/win32/api/richedit/ns-richedit-charformata) která umožňuje nastavit některé charakteristiky písma v ovládacím prvku rich edit.

*dwFlags*<br/>
Určuje jeden nebo více příznaků choose-font. Jednu nebo více přednastavených hodnot lze kombinovat pomocí bitového operátoru OR. Pokud změníte `m_cf.Flag`člen struktury s, ujistěte se, že ve změnách použijete bitový operátor OR, aby výchozí chování zůstalo beze změny. Podrobnosti o každém z těchto příznaků naleznete v popisu struktury [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) v sadě Windows SDK.

*pdcPrinter*<br/>
Ukazatel na kontext tiskárny zařízení. Pokud je zadán, tento parametr odkazuje na kontext tiskárny, na které mají být vybrána písma.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastní iložské okno dialogového okna písma.

### <a name="remarks"></a>Poznámky

Všimněte si, že konstruktor automaticky `CHOOSEFONT` vyplní členy struktury. Tyto možnosti byste měli změnit pouze v případě, že chcete, aby se dialogové okno písem lišilo od výchozího nastavení.

> [!NOTE]
> První verze této funkce existuje pouze v případě, že neexistuje žádná podpora ovládacího prvku rich edit.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

## <a name="cfontdialogdomodal"></a><a name="domodal"></a>CFontDialog::DoModální

Voláním této funkce zobrazíte dialogové okno s běžným písmem systému Windows a umožníte uživateli vybrat písmo.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud je vrácena funkce IDCANCEL, zavolejte funkci Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) a zjistěte, zda došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel zvolil tlačítko OK nebo Cancel.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky dialogového okna písma nastavením `DoModal`členů [m_cf](#m_cf) struktury, měli byste to provést před voláním , ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí hodnotu IDOK, můžete volat další členské funkce a načíst nastavení nebo informace vstupující uživatelem do dialogového okna.

### <a name="example"></a>Příklad

  Podívejte se na příklady pro [CFontDialog::CFontDialog](#cfontdialog) a [CFontDialog::GetColor](#getcolor).

## <a name="cfontdialoggetcharformat"></a><a name="getcharformat"></a>CFontDialog::GetCharFormat

Načte formátování znaků vybraného písma.

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Parametry

*Viz*<br/>
Struktura [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) obsahující informace o formátování znaků vybraného písma.

## <a name="cfontdialoggetcolor"></a><a name="getcolor"></a>CFontDialog::GetColor

Voláním této funkce načtěte vybranou barvu písma.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva vybraného písma.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

## <a name="cfontdialoggetcurrentfont"></a><a name="getcurrentfont"></a>CFontDialog::GetCurrentFont

Volání této funkce přiřadit vlastnosti aktuálně vybrané písmo členům struktury [LOGFONT.](/windows/win32/api/wingdi/ns-wingdi-logfontw)

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Parametry

*lplf*<br/>
Ukazatel na `LOGFONT` strukturu.

### <a name="remarks"></a>Poznámky

Další `CFontDialog` členské funkce jsou k dispozici pro přístup k individuálním charakteristikám aktuálního písma.

Pokud je tato funkce volána během volání [DoModal](#domodal), vrátí aktuální výběr v době (co uživatel vidí nebo změnil v dialogovém okně). Pokud tato funkce je volána po volání `DoModal` (pouze pokud `DoModal` vrátí IDOK), vrátí, co uživatel skutečně vybrané.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

## <a name="cfontdialoggetfacename"></a><a name="getfacename"></a>CFontDialog::GetFaceName

Voláním této funkce načtěte název tváře vybraného písma.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název tváře písma vybraného `CFontDialog` v dialogovém okně.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

## <a name="cfontdialoggetsize"></a><a name="getsize"></a>CFontDialog::GetSize

Voláním této funkce načtěte velikost vybraného písma.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost písma v desetinách bodu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

## <a name="cfontdialoggetstylename"></a><a name="getstylename"></a>CFontDialog::GetStyleName

Voláním této funkce načtěte název stylu vybraného písma.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název stylu písma.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

## <a name="cfontdialoggetweight"></a><a name="getweight"></a>CFontDialog::GetWeight

Voláním této funkce načtěte tloušťku vybraného písma.

```
int GetWeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Tloušťka vybraného písma.

### <a name="remarks"></a>Poznámky

Další informace o hmotnosti písma naleznete v tématu [CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

## <a name="cfontdialogisbold"></a><a name="isbold"></a>CFontDialog::IsBold

Volánítéto funkce k určení, zda je vybrané písmo tučné.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má vybrané písmo povolenou charakteristiku Tučné; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

## <a name="cfontdialogisitalic"></a><a name="isitalic"></a>CFontDialog::IsItalic

Volání této funkce k určení, zda je vybrané písmo kurzívou.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má vybrané písmo povolenou charakteristiku kurzívy; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

## <a name="cfontdialogisstrikeout"></a><a name="isstrikeout"></a>CFontDialog::IsStrikeOut

Volání této funkce k určení, zda je vybrané písmo zobrazeno s přeškrtnutou.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má vybrané písmo zapnutou charakteristiku Strikeout; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

## <a name="cfontdialogisunderline"></a><a name="isunderline"></a>cfontdialog::podtržení

Voláním této funkce můžete určit, zda je vybrané písmo podtržené.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má vybrané písmo zapnutou charakteristiku Podtržení; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

## <a name="cfontdialogm_cf"></a><a name="m_cf"></a>CFontDialog::m_cf

Struktura, jejíž členové ukládají vlastnosti objektu dialogového okna.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Poznámky

Po vytvoření `CFontDialog` objektu můžete `m_cf` před voláním `DoModal` členské funkce upravit různé aspekty dialogového okna. Další informace o této struktuře naleznete v tématu [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
