---
title: Třída CColorDialog
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
ms.openlocfilehash: 99b4ff27a7686972bcbc85478998b52ed713ab5b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754260"
---
# <a name="ccolordialog-class"></a>Třída CColorDialog

Umožňuje začlenit dialogové okno pro výběr barev do aplikace.

## <a name="syntax"></a>Syntaxe

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CColorDialog:dialog CColor](#ccolordialog)|Vytvoří `CColorDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CColorDialog::DoModální](#domodal)|Zobrazí dialogové okno barev a umožní uživateli provést výběr.|
|[CColorDialog::GetColor](#getcolor)|Vrátí `COLORREF` strukturu obsahující hodnoty vybrané barvy.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Načte vlastní barvy vytvořené uživatelem.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Vynutí, aby se aktuální výběr barvy vytábyl na určenou barvu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CcolorDialog::OnColorOK](#oncolorok)|Přepsáním ověřte barvu zadanou do dialogového okna.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Struktura používaná k přizpůsobení nastavení dialogového okna.|

## <a name="remarks"></a>Poznámky

Objekt `CColorDialog` je dialogové okno se seznamem barev, které jsou definovány pro systém zobrazení. Uživatel může vybrat nebo vytvořit určitou barvu ze seznamu, která je pak hlášena zpět do aplikace při ukončení dialogového okna.

Chcete-li `CColorDialog` vytvořit objekt, použijte zadaný konstruktor nebo odvodit novou třídu a použijte vlastní konstruktor.

Po vytvoření dialogového okna můžete nastavit nebo upravit libovolné hodnoty ve struktuře [m_cc](#m_cc) a inicializovat hodnoty ovládacích prvků dialogového okna. Struktura *m_cc* je typu [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1).

Po inicializaci ovládacích prvků `DoModal` dialogového okna zavolejte členské funkce, aby zobrazila dialogové okno a umožnila uživateli vybrat barvu. `DoModal`vrátí výběr tlačítka OK (IDOK) dialogového okna nebo zrušit (IDCANCEL) uživatele.

Pokud `DoModal` vrátí IDOK, můžete `CColorDialog`použít jednu z 's členské funkce načíst informace vstup uživatelem.

Pomocí funkce Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) můžete určit, zda došlo k chybě během inicializace dialogového okna a získat další informace o chybě.

`CColorDialog`spoléhá na COMMDLG. Soubor DLL, který je dodáván se systémem Windows verze 3.1 a novější.

Chcete-li dialogové okno přizpůsobit, `CColorDialog`odvoděte třídu z aplikace , zadejte vlastní šablonu dialogového okna a přidejte mapu zpráv pro zpracování zpráv s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měly být předány základní třídě.

Přizpůsobení funkce háku není nutné.

> [!NOTE]
> U některých `CColorDialog` instalací se objekt nezobrazí s šedým pozadím, `CDialog` pokud jste pomocí rozhraní frameworku zmedaly.

Další informace o `CColorDialog`použití najdete [v tématu Společné třídy dialogů](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

## <a name="ccolordialogccolordialog"></a><a name="ccolordialog"></a>CColorDialog:dialog CColor

Vytvoří `CColorDialog` objekt.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*clrInit*<br/>
Výchozí výběr barev. Pokud není zadána žádná hodnota, výchozí hodnota je RGB(0,0,0) (černá).

*dwFlags*<br/>
Sada příznaků, které přizpůsobují funkci a vzhled dialogového okna. Další informace naleznete v [choosecolor](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1) struktury v sadě Windows SDK.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastníjméno okna dialogového okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

## <a name="ccolordialogdomodal"></a><a name="domodal"></a>CColorDialog::DoModální

Voláním této funkce zobrazíte dialogové okno Se obecné barvy systému Windows a umožníte uživateli vybrat barvu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud je vrácena funkce IDCANCEL, zavolejte funkci Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) a zjistěte, zda došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel zvolil tlačítko OK nebo Cancel.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé volby dialogového okna barev nastavením členů [m_cc](#m_cc) `DoModal` struktury, měli byste to provést před voláním, ale po vytvoření objektu dialogového okna.

Po `DoModal`volání můžete volat další členské funkce a načíst nastavení nebo informace vstupující uživatelem do dialogového okna.

### <a name="example"></a>Příklad

  Viz příklad [ccolordialog::CColorDialog](#ccolordialog).

## <a name="ccolordialoggetcolor"></a><a name="getcolor"></a>CColorDialog::GetColor

Volání této funkce `DoModal` po volání načíst informace o barvu, kterou uživatel vybral.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota [COLORREF,](/windows/win32/gdi/colorref) která obsahuje informace rgb pro barvu vybranou v dialogovém okně barva.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

## <a name="ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors

`CColorDialog`objekty umožňují uživateli, kromě výběru barev, definovat až 16 vlastních barev.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole 16 hodnot barev RGB, které ukládá vlastní barvy vytvořené uživatelem.

### <a name="remarks"></a>Poznámky

Členská `GetSavedCustomColors` funkce poskytuje přístup k těmto barvám. Tyto barvy lze načíst po [DoModal](#domodal) vrátí IDOK.

Každá z 16 hodnot RGB ve vráceném poli je inicializována na RGB (255 255 255) (bílá). Vlastní barvy zvolené uživatelem jsou uloženy pouze mezi vyvolání dialogového okna v rámci aplikace. Pokud chcete uložit tyto barvy mezi vyvolání aplikace, je nutné je uložit jiným způsobem, například v inicializaci (. INI).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

## <a name="ccolordialogm_cc"></a><a name="m_cc"></a>CColorDialog::m_cc

Struktura typu [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1), jejíž členové ukládají charakteristiky a hodnoty dialogového okna.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Poznámky

Po vytvoření `CColorDialog` objektu můžete použít *m_cc* nastavení různých aspektů dialogového okna před voláním členské funkce [DoModal.](#domodal)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

## <a name="ccolordialogoncolorok"></a><a name="oncolorok"></a>CcolorDialog::OnColorOK

Přepsáním ověřte barvu zadanou do dialogového okna.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud by dialogové okno nemělo být odmítnuto; jinak 0 přijmout barvu, která byla zadána.

### <a name="remarks"></a>Poznámky

Tuto funkci přepište pouze v případě, že chcete zadat vlastní ověření barvy, kterou uživatel vybere v dialogovém okně barva.

Uživatel může vybrat barvu jedním z následujících dvou způsobů:

- Klepnutí na barvu palety barev. Hodnoty RGB vybrané barvy se pak projeví v příslušných polích pro úpravy RGB.

- Zadávání hodnot do polí pro úpravy RGB

Přepsání `OnColorOK` umožňuje odmítnout barvu, kterou uživatel zadá do společného dialogového okna barev z jakéhokoli důvodu specifického pro aplikaci.

Za normálních okolností není nutné používat tuto funkci, protože rozhraní framework poskytuje výchozí ověření barev a zobrazí okno se zprávou, pokud je zadána neplatná barva.

Chcete-li vynutit `OnColorOK` výběr barvy, můžete volat [SetCurrentColor](#setcurrentcolor) zevnitř. Po `OnColorOK` vypálení (to znamená, že uživatel klepne na **tlačítko OK,** aby přijal změnu barvy), můžete volat [GetColor,](#getcolor) abyste získali hodnotu RGB nové barvy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

## <a name="ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor

Volání této funkce `DoModal` po volání vynutit aktuální výběr barvy na hodnotu barvy zadanou v *clr*.

```cpp
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*Clr*<br/>
Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

Tato funkce je volána z `OnColorOK`obslužné rutiny zprávy nebo . Dialogové okno automaticky aktualizuje výběr uživatele na základě hodnoty parametru *clr.*

### <a name="example"></a>Příklad

  Viz příklad pro [CColorDialog::OnColorOK](#oncolorok).

## <a name="see-also"></a>Viz také

[MDI vzorku knihovny MFc](../../overview/visual-cpp-samples.md)<br/>
[Vzorek mfc DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
