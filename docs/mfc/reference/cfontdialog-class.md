---
title: Cfontdialog – třída
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
ms.openlocfilehash: b711ca65e552d495e466ea2e46a6779cf43ecbe3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767741"
---
# <a name="cfontdialog-class"></a>Cfontdialog – třída

Umožňuje zahrnout do vaší aplikace dialogové okno Výběr písma.

## <a name="syntax"></a>Syntaxe

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|Vytvoří `CFontDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožňuje uživatelům provést výběr.|
|[CFontDialog::GetCharFormat](#getcharformat)|Načte formátování vybraného písma.|
|[CFontDialog::GetColor](#getcolor)|Vrátí barvu vybraného písma.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Přiřadí vlastnosti aktuálně zvoleného písma, `LOGFONT` struktury.|
|[CFontDialog::GetFaceName](#getfacename)|Vrátí název vybraného písma pro rozpoznávání tváře.|
|[CFontDialog::GetSize](#getsize)|Vrátí velikost vybraného písma.|
|[CFontDialog::GetStyleName](#getstylename)|Vrátí název stylu vybraného písma.|
|[CFontDialog::GetWeight](#getweight)|Vrací váhu vybraného písma.|
|[CFontDialog::IsBold](#isbold)|Určuje, zda je písmo tučné.|
|[CFontDialog::IsItalic](#isitalic)|Určuje, zda je písmo kurzíva.|
|[CFontDialog::IsStrikeOut](#isstrikeout)|Určuje, zda se u přeškrtnutí zobrazí písma.|
|[CFontDialog::IsUnderline](#isunderline)|Určuje, zda je písmo podtržené.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Struktura používané k úpravám `CFontDialog` objektu.|

## <a name="remarks"></a>Poznámky

A `CFontDialog` objekt je dialogové okno se seznamem písma, které jsou nainstalovány v systému. Uživatel může vybrat zvolené písmo ze seznamu a tento výběr je pak hlášeny zpět do aplikace.

K vytvoření `CFontDialog` objektu, použijte poskytnutý konstruktor nebo odvodit novou podtřídu a použít vlastní vlastního konstruktoru.

Jednou `CFontDialog` objekt byl vytvořen, můžete použít `m_cf` struktury k inicializaci hodnoty nebo stavy ovládacích prvků v dialogovém okně. [M_cf](#m_cf) struktury je typu [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta). Další informace o této struktuře naleznete v tématu Windows SDK.

Po inicializaci objektu dialogového okna ovládacích prvků, volání `DoModal` členské funkce a zobrazte dialogové okno Povolit uživatelům výběr písma. `DoModal` Vrátí, zda uživatel vybral tlačítko OK (IDOK) nebo zrušit (IDCANCEL).

Pokud `DoModal` vrátí IDOK, můžete použít jednu z `CFontDialog`pro členské funkce načtete informace o vstup uživatele.

Můžete použít Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkce k určení, zda došlo k chybě při inicializaci dialogového okna a další informace o této chybě. Další informace o této funkci najdete v tématu Windows SDK.

`CFontDialog` využívá COMMDLG. Soubor knihovny DLL, která se dodává s Windows verze 3.1 nebo novější.

Přizpůsobení dialogových oken, odvoďte třídu z `CFontDialog`zadejte šablonu vlastního dialogu a přidání mapy zpráv pro zpracování zpráv s oznámením z rozšířené ovládací prvky. Všechny nezpracované zprávy by měly být předány základní třídy.

Přizpůsobení funkce háku se nevyžaduje.

Další informace o používání `CFontDialog`, naleznete v tématu [společné třídy dialogových oken](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

##  <a name="cfontdialog"></a>  CFontDialog::CFontDialog

Vytvoří `CFontDialog` objektu.

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
Ukazatel [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) datová struktura, která vám umožní nastavit některé z vlastností písma.

*charFormat*<br/>
Ukazatel [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) datová struktura, která vám umožní nastavit některé z vlastností písma v bohaté ovládací prvek textové pole.

*dwFlags*<br/>
Určuje jeden nebo více příznaků zvolit písmo. Jeden nebo více přednastavené hodnoty lze spojovat pomocí bitového operátoru OR. Pokud změníte `m_cf.Flag`člen struktury s, nezapomeňte použít bitový operátor OR své změny zachovat výchozí chování beze změny. Podrobnosti o každé z těchto příznaků, viz popis [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta) struktura v sadě Windows SDK.

*pdcPrinter*<br/>
Ukazatel na kontext zařízení tiskárny. Pokud je zadané, tento parametr odkazuje na kontext zařízení tiskárny pro tiskárny, na kterém mají být vybrán písma.

*pParentWnd*<br/>
Ukazatel na písmo dialogové okno nadřazené nebo vlastníka.

### <a name="remarks"></a>Poznámky

Všimněte si, že konstruktor automaticky vyplní členů `CHOOSEFONT` struktury. By měl změnit pouze ty Pokud chcete dialogové okno písmo jiné než výchozí.

> [!NOTE]
>  První verze této funkce existuje pouze v případě, že podpora ovládacího prvku pro úpravy s formátováním žádné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

##  <a name="domodal"></a>  CFontDialog::DoModal

Voláním této funkce a zobrazte dialogové okno Písmo Windows běžné povolit uživateli, aby zvolil písmo.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud je vrácena IDCANCEL, zavolejte Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkce k určení, zda došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel vybral tlačítko OK nebo zrušit.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé ovládací prvky písma dialogového okna tak, že nastavíte členy [m_cf](#m_cf) strukturu, je potřeba to udělat před voláním `DoModal`, ale po vytvoření objektu dialogového okna.

Pokud `DoModal` vrátí IDOK, můžete volat ostatní členské funkce k načtení nastavení nebo informace o vstup uživatelem do dialogových oken.

### <a name="example"></a>Příklad

  Podívejte se na příklady pro [CFontDialog::CFontDialog](#cfontdialog) a [CFontDialog::GetColor](#getcolor).

##  <a name="getcharformat"></a>  CFontDialog::GetCharFormat

Načte formátování vybraného písma.

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Parametry

*cf*<br/>
A [CHARFORMAT](/windows/desktop/api/richedit/ns-richedit-_charformat) struktura obsahující informace o formátování vybraného písma.

##  <a name="getcolor"></a>  CFontDialog::GetColor

Volání této funkce načtete barvu vybraného písma.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Barva vybraného písma.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

##  <a name="getcurrentfont"></a>  CFontDialog::GetCurrentFont

Voláním této funkce k přiřazení vlastnosti aktuálně vybraného písma k členům [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) struktury.

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Parametry

*lplf*<br/>
Ukazatel `LOGFONT` struktury.

### <a name="remarks"></a>Poznámky

Další `CFontDialog` členské funkce jsou k dispozici pro přístup k individuální vlastnosti aktuálním písmem.

Pokud tato funkce je volána při volání [DoModal](#domodal), vrátí aktuální výběr v době (co uživatel uvidí, nebo je změnit v dialogovém okně). Pokud tato funkce je volána po volání `DoModal` (pouze tehdy, pokud `DoModal` vrátí IDOK), vrátí co uživatel skutečně vybrali.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

##  <a name="getfacename"></a>  CFontDialog::GetFaceName

Volání této funkce načtete pro rozpoznávání tváře název vybraného písma.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název pro rozpoznávání tváře písmo vybrané v `CFontDialog` dialogové okno.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

##  <a name="getsize"></a>  CFontDialog::GetSize

Voláním této funkce, aby se načetla velikost vybraného písma.

```
int GetSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Velikost písma v desetiny bod.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

##  <a name="getstylename"></a>  CFontDialog::GetStyleName

Volání této funkce načtete název stylu vybraného písma.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Návratová hodnota

Styl písma.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

##  <a name="getweight"></a>  CFontDialog::GetWeight

Volání této funkce načtete váhu vybraného písma.

```
int GetWeight() const;
```

### <a name="return-value"></a>Návratová hodnota

Váha vybraného písma.

### <a name="remarks"></a>Poznámky

Další informace o váze písma, naleznete v tématu [CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

##  <a name="isbold"></a>  CFontDialog::IsBold

Voláním této funkce k určení, zda je vybrané písmo tučné.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud vybrané písmo má tučné charakteristiku povolené; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

##  <a name="isitalic"></a>  CFontDialog::IsItalic

Voláním této funkce k určení, zda je vybrané písmo kurzíva.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud vybrané písmo kurzíva charakteristiku povolené; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

##  <a name="isstrikeout"></a>  CFontDialog::IsStrikeOut

Voláním této funkce k určení, pokud vybrané písmo se zobrazí u přeškrtnutí.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud vybrané písmo má charakteristiku přeškrtnutí povolené; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

##  <a name="isunderline"></a>  CFontDialog::IsUnderline

Voláním této funkce k určení, pokud je vybrané písmo podtržené.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud vybrané písmo má charakteristiku podtržení povolené; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

##  <a name="m_cf"></a>  CFontDialog::m_cf

Struktura, jejíž členové uložení vlastnosti z objektu dialogového okna.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Poznámky

Po sestavení `CFontDialog` objektu, můžete použít `m_cf` upravit různé aspekty dialogového okna před voláním `DoModal` členskou funkci. Další informace o této struktuře naleznete v tématu [CHOOSEFONT](/windows/desktop/api/commdlg/ns-commdlg-tagchoosefonta) v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
