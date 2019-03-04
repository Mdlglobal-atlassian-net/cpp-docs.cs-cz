---
title: CColorDialog Class
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
ms.openlocfilehash: 39868ed27a0dfb8756b4829ea7c378c798bd2ff3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304207"
---
# <a name="ccolordialog-class"></a>CColorDialog Class

Umožňuje zahrnout do vaší aplikace dialogové okno Výběr barvy.

## <a name="syntax"></a>Syntaxe

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|Vytvoří `CColorDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|Zobrazí dialogové okno barvy a umožňuje uživatelům provést výběr.|
|[CColorDialog::GetColor](#getcolor)|Vrátí `COLORREF` struktury obsahující hodnoty vybrané barvy.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Načte vlastní barvy vytvořený uživatelem.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Vynutí aktuální výběr barvy na zadanou barvu.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Přepsání nastavení za účelem ověření barvu zadaný do dialogového okna.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Struktura používané k úpravám nastavení dialogovém okně.|

## <a name="remarks"></a>Poznámky

A `CColorDialog` objektu je dialogové okno se seznamem barev, které jsou definovány pro systém zobrazení. Uživatele můžete vybrat nebo vytvořit konkrétní barvu ze seznamu, který je pak hlášeny zpět do aplikace při ukončení dialogu.

K vytvoření `CColorDialog` objektu, použijte poskytnutý konstruktor nebo odvozovat nové třídy a použít vlastní vlastního konstruktoru.

Jakmile byl vytvořen dialogových oken, můžete nastavit nebo změnit všechny hodnoty v [m_cc](#m_cc) struktura inicializace hodnot ovládacích prvků v dialogovém okně. *M_cc* struktury je typu [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora).

Po inicializaci ovládací prvky dialogových oken, zavolejte `DoModal` členské funkce k zobrazení dialogového okna a umožnit uživateli vybrat barvu. `DoModal` Vrátí uživatele výběru buď v dialogovém okně tlačítko OK (IDOK) nebo zrušit (IDCANCEL).

Pokud `DoModal` vrátí IDOK, můžete použít jednu z `CColorDialog`pro členské funkce načtete informace o vstup uživatele.

Můžete použít Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkce k určení, zda došlo k chybě při inicializaci dialogového okna a další informace o této chybě.

`CColorDialog` využívá COMMDLG. Soubor knihovny DLL, která se dodává s Windows verze 3.1 nebo novější.

Přizpůsobení dialogových oken, odvoďte třídu z `CColorDialog`zadejte šablonu vlastního dialogu a přidání mapy zpráv pro zpracování zpráv s oznámením z rozšířené ovládací prvky. Všechny nezpracované zprávy by měly být předány základní třídy.

Přizpůsobení funkce háku se nevyžaduje.

> [!NOTE]
>  Na některé zařízení `CColorDialog` objektu nezobrazí na šedém pozadí, pokud používáte rozhraní provádět jiné `CDialog` objekty šedá.

Další informace o používání `CColorDialog`, naleznete v tématu [společné třídy dialogových oken](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

##  <a name="ccolordialog"></a>  CColorDialog::CColorDialog

Vytvoří `CColorDialog` objektu.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*clrInit*<br/>
Výchozí výběr barvy. Pokud není zadána žádná hodnota, výchozí hodnota je RGB(0,0,0) (černá).

*dwFlags*<br/>
Sada příznaků, které funkce a vzhled dialogového okna přizpůsobit. Další informace najdete v tématu [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora) struktura v sadě Windows SDK.

*pParentWnd*<br/>
Ukazatel na okno nadřazené nebo vlastník dialogových oken.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

##  <a name="domodal"></a>  CColorDialog::DoModal

Voláním této funkce dialogového okna Windows běžné barvy a umožní uživateli vybrat barvu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud je vrácena IDCANCEL, zavolejte Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkce k určení, zda došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel vybral tlačítko OK nebo zrušit.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé možnosti dialogového okna barvy tak, že nastavíte členy [m_cc](#m_cc) strukturu, je potřeba to udělat před voláním `DoModal` , ale po vytvoření objektu dialogového okna.

Po volání `DoModal`, můžete volat ostatní členské funkce k načtení nastavení nebo informace o vstup uživatelem do dialogových oken.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CColorDialog::CColorDialog](#ccolordialog).

##  <a name="getcolor"></a>  CColorDialog::GetColor

Voláním této funkce po volání `DoModal` k načtení informací o barvě uživatel vybral.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Návratová hodnota

A [COLORREF](/windows/desktop/gdi/colorref) hodnotu, která obsahuje informace o RGB barva vybraná v dialogovém okně barev.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

##  <a name="getsavedcustomcolors"></a>  CColorDialog::GetSavedCustomColors

`CColorDialog` objekty povolit uživateli, kromě výběr barev, definovat až 16 vlastní barvy.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na pole 16 RGB – hodnoty barev, která ukládá vlastních barev vytvořený uživatelem.

### <a name="remarks"></a>Poznámky

`GetSavedCustomColors` Členskou funkci poskytuje přístup k tyto barvy. Tyto barvy se dá načíst po [DoModal](#domodal) vrátí IDOK.

Všechny 16 hodnoty RGB ve vrácené pole je inicializován na RGB(255,255,255) (bílé). Vlastní barvy uživatelem se uloží pouze mezi vyvolání dialogového okna pole v rámci aplikace. Pokud chcete uložit tyto barvy mezi vyvoláními aplikace, je třeba je uložit jiným způsobem, jako například inicializace (. Soubor INI).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

##  <a name="m_cc"></a>  CColorDialog::m_cc

Strukturu typu [CHOOSECOLOR](/windows/desktop/api/commdlg/ns-commdlg-tagchoosecolora), ukládat obsahující vlastnosti a hodnoty dialogového okna.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Poznámky

Po sestavení `CColorDialog` objektu, můžete použít *m_cc* nastavit různé aspekty dialogového okna před voláním [DoModal](#domodal) členskou funkci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

##  <a name="oncolorok"></a>  CColorDialog::OnColorOK

Přepsání nastavení za účelem ověření barvu zadaný do dialogového okna.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud by neměla zavře dialogové okno; jinak 0 tak, aby přijímal barvy, který jste zadali.

### <a name="remarks"></a>Poznámky

Potlačí tuto funkci pouze v případě, že chcete poskytnout vlastní ověřovací barvu, kterou uživatel vybere v dialogovém okně barev.

Uživatel může vybrat barvu pomocí jedné z těchto dvou metod:

- Kliknutím na barvu na barvu z palety. Vybraná barva RGB hodnoty se projeví pak do příslušných polí RGB upravit.

- Zadávání hodnoty RGB textových polí

Přepsání `OnColorOK` umožňuje odmítnout barvu uživatel zadá do společného dialogové okno barvy z jakéhokoli důvodu specifické pro aplikaci.

Za normálních okolností není nutné tuto funkci použít, protože rozhraní poskytuje výchozí ověřování barev a zobrazí okno se zprávou, pokud je zadán neplatný barvu.

Můžete volat [SetCurrentColor](#setcurrentcolor) v rámci `OnColorOK` vynutit výběr barvy. Jednou `OnColorOK` byla aktivována (to znamená, že uživatel klikne **OK** tak, aby přijímal Změna barvy), můžete volat [getcolor –](#getcolor) k získání hodnoty RGB novou barvu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

##  <a name="setcurrentcolor"></a>  CColorDialog::SetCurrentColor

Voláním této funkce po volání `DoModal` přinutit aktuální výběr barvu na barvu hodnotu zadanou v *clr*.

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Parametry

*CLR*<br/>
Hodnota barvy RGB.

### <a name="remarks"></a>Poznámky

Tato funkce je volána v rámci obslužné rutiny zpráv nebo `OnColorOK`. Dialogové okno automaticky aktualizuje na základě hodnoty z výběru uživatele *clr* parametru.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CColorDialog::OnColorOK](#oncolorok).

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC MDI](../../visual-cpp-samples.md)<br/>
[Ukázky knihovny MFC DRAWCLI](../../visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
