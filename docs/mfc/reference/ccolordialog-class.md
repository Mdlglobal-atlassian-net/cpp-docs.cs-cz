---
title: CColorDialog – třída
ms.date: 11/04/2016
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
ms.openlocfilehash: f5c235008b72996424e01ee912ca78ecffab450a
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741580"
---
# <a name="ccolordialog-class"></a>CColorDialog – třída

Umožňuje začlenit do aplikace dialogové okno Výběr barvy.

## <a name="syntax"></a>Syntaxe

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|`CColorDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|Zobrazí dialogové okno barvy a umožní uživateli provést výběr.|
|[CColorDialog:: GetColor](#getcolor)|`COLORREF` Vrátí strukturu obsahující hodnoty vybrané barvy.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Načte vlastní barvy vytvořené uživatelem.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Vynutí aktuální výběr barvy určenou barvou.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Přepsáním ověříte barvu zadanou v dialogovém okně.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Struktura používaná k přizpůsobení nastavení dialogového okna.|

## <a name="remarks"></a>Poznámky

`CColorDialog` Objekt je dialogové okno se seznamem barev, které jsou definovány pro zobrazovací systém. Uživatel může vybrat nebo vytvořit určitou barvu ze seznamu, která je pak při ukončení dialogového okna nahlášena zpět do aplikace.

Chcete-li `CColorDialog` vytvořit objekt, použijte poskytnutý konstruktor nebo odvodit novou třídu a použijte vlastní konstruktor.

Po vytvoření dialogového okna můžete nastavit nebo změnit libovolné hodnoty ve struktuře [m_cc](#m_cc) a inicializovat tak hodnoty ovládacích prvků dialogového okna. Struktura *m_cc* je typu [chooseColor](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1).

Po inicializaci ovládacích prvků dialogového okna zavolejte `DoModal` členskou funkci pro zobrazení dialogového okna a umožněte uživateli vybrat barvu. `DoModal`Vrátí výběr uživatele dialogového okna pro tlačítko OK (IDOK) nebo zrušit (IDCANCEL).

Pokud `DoModal` vrátí IDOK, můžete použít jednu z `CColorDialog`členských funkcí k načtení informací o vstupu uživatele.

Pomocí funkce Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) můžete zjistit, jestli při inicializaci dialogového okna došlo k chybě, a získat další informace o chybě.

`CColorDialog`spoléhá na COMMDLG. Soubor DLL dodávaný se systémem Windows verze 3,1 nebo novějším.

Chcete-li přizpůsobit dialogové okno, odvodit třídu `CColorDialog`z, zadat vlastní šablonu dialogového okna a přidat mapu zpráv pro zpracování zpráv s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měly být předány základní třídě.

Přizpůsobení funkce zavěšení není vyžadováno.

> [!NOTE]
>  V některých instalacích `CColorDialog` se objekt nezobrazí se šedým pozadím, pokud jste použili rozhraní k nastavení jiných `CDialog` objektů šedě.

Další informace o použití nástroje `CColorDialog`najdete v tématu [společné třídy dialogových oken](../../mfc/common-dialog-classes.md) .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs. h

##  <a name="ccolordialog"></a>CColorDialog::CColorDialog

`CColorDialog` Vytvoří objekt.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*clrInit*<br/>
Výchozí výběr barvy Pokud není zadána žádná hodnota, výchozí hodnota je RGB (0, 0, 0) (černá).

*dwFlags*<br/>
Sada příznaků, které přizpůsobují funkce a vzhled dialogového okna. Další informace najdete v tématu struktura [chooseColor](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1) v Windows SDK.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastní okno dialogového okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

##  <a name="domodal"></a>CColorDialog::D oModal

Voláním této funkce zobrazíte dialogové okno společná barva systému Windows a povolíte uživateli vybrat barvu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud se vrátí IDCANCEL, zavolejte funkci Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) a určete, jestli došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel vybral tlačítko OK nebo Storno.

### <a name="remarks"></a>Poznámky

Chcete-li inicializovat různé možnosti dialogového okna barev nastavením členů struktury [m_cc](#m_cc) , měli byste to provést před voláním `DoModal` , ale po sestavení objektu dialogového okna.

Po volání `DoModal`můžete zavolat jiné členské funkce a načíst nastavení nebo zadání informací uživatelem do dialogového okna.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CColorDialog:: CColorDialog](#ccolordialog).

##  <a name="getcolor"></a>CColorDialog:: GetColor

Tuto funkci zavolejte po volání `DoModal` , aby se načetly informace o barvě, kterou uživatel vybral.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF](/windows/win32/gdi/colorref) , která obsahuje informace RGB barvy vybrané v dialogovém okně Barva.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

##  <a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors

`CColorDialog`objekty umožňují uživateli kromě výběru barev definovat až 16 vlastních barev.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole s hodnotami 16 barev RGB, ve kterých jsou uloženy vlastní barvy vytvořené uživatelem.

### <a name="remarks"></a>Poznámky

`GetSavedCustomColors` Členské funkce poskytují přístup k těmto barvám. Tyto barvy lze načíst po [DoModal](#domodal) vrátí IDOK.

Každý z 16 hodnot RGB ve vráceném poli se inicializuje na RGB (255255255) (bílá). Vlastní barvy zvolené uživatelem jsou uloženy pouze mezi voláními dialogového okna v rámci aplikace. Chcete-li uložit tyto barvy mezi voláními aplikace, je nutné je uložit jiným způsobem, například při inicializaci (. Souboru INI).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

##  <a name="m_cc"></a>  CColorDialog::m_cc

Struktura typu [chooseColor](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1), jejíž členové ukládají charakteristiky a hodnoty dialogového okna.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Poznámky

Po sestavení `CColorDialog` objektu můžete použít *m_cc* k nastavení různých aspektů dialogového okna před voláním členské funkce [DoModal](#domodal) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

##  <a name="oncolorok"></a>CColorDialog::OnColorOK

Přepsáním ověříte barvu zadanou v dialogovém okně.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud by dialogové okno nemělo být zavřeno. jinak 0 potvrďte zadanou barvu.

### <a name="remarks"></a>Poznámky

Tuto funkci můžete přepsat pouze v případě, že chcete zadat vlastní ověření barvy, kterou uživatel vybere v dialogovém okně Barva.

Uživatel může vybrat barvu pomocí jedné z následujících dvou metod:

- Kliknutím na barvu na paletě barev. Hodnoty RGB vybrané barvy se pak projeví v příslušných textových polích RGB.

- Zadávání hodnot do textových polí RGB

Přepsání `OnColorOK` umožňuje odmítat barvu, kterou uživatel zadá do dialogového okna společná barva pro libovolný důvod specifický pro danou aplikaci.

Obvykle tuto funkci nemusíte používat, protože rozhraní poskytuje výchozí ověřování barev a zobrazí okno se zprávou, pokud je zadána neplatná barva.

Můžete volat [SetCurrentColor](#setcurrentcolor) z v rámci `OnColorOK` vynucení výběru barvy. Po `OnColorOK` vyvolání (to znamená, že uživatel klikne na **tlačítko OK** , aby se změnila Změna barvy), můžete volat metodu [GetColor](#getcolor) pro získání hodnoty RGB nové barvy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

##  <a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor

Po volání `DoModal` vyvolejte tuto funkci pro vynucení současného výběru barvy s hodnotou barvy zadanou v *modulu CLR*.

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*CLR*<br/>
Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

Tato funkce je volána v rámci obslužné rutiny zprávy `OnColorOK`nebo. Dialogové okno automaticky aktualizuje výběr uživatele na základě hodnoty parametru *CLR* .

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CColorDialog:: OnColorOK](#oncolorok).

## <a name="see-also"></a>Viz také:

[Ukázka MDI MFC](../../overview/visual-cpp-samples.md)<br/>
[DRAWCLI Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
