---
title: Cprintdialog – třída
ms.date: 11/04/2016
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
ms.openlocfilehash: 3e86ce3e0179ff7c7a47a7083b6c168fea91ccbc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50662433"
---
# <a name="cprintdialog-class"></a>Cprintdialog – třída

Zapouzdřuje služby poskytované běžným dialogovým oknem Windows pro tisk.

## <a name="syntax"></a>Syntaxe

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|Vytvoří `CPrintDialog` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Vytvoří kontext zařízení tiskárny bez zobrazení dialogového okna Tisk.|
|[CPrintDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožňuje uživatelům provést výběr.|
|[CPrintDialog::GetCopies](#getcopies)|Získá počet kopií požadovaný.|
|[CPrintDialog::GetDefaults](#getdefaults)|Načte výchozí nastavení zařízení bez zobrazení dialogového okna.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Načte název zařízení aktuálně vybrané tiskárny.|
|[CPrintDialog::GetDevMode](#getdevmode)|Načte `DEVMODE` struktury.|
|[CPrintDialog::GetDriverName](#getdrivername)|Získá název aktuálně vybraného ovladače tiskárny.|
|[CPrintDialog::GetFromPage](#getfrompage)|Získá počáteční stránky rozsah tisku.|
|[CPrintDialog::GetPortName](#getportname)|Načte název portu aktuálně vybrané tiskárny.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Načte popisovač kontextu zařízení tiskárny.|
|[CPrintDialog::GetToPage](#gettopage)|Načte poslední stránky rozsah tisku.|
|[CPrintDialog::PrintAll](#printall)|Určuje, jestli se má vytisknout všechny stránky dokumentu.|
|[CPrintDialog::PrintCollate](#printcollate)|Určuje, zda porovnávány kopie jsou požadovány.|
|[CPrintDialog::PrintRange](#printrange)|Určuje, jestli se má vytisknout zadaného rozsahu stránek.|
|[CPrintDialog::PrintSelection](#printselection)|Určuje, jestli se má tisknout jen aktuálně vybrané položky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Struktura používané k úpravám `CPrintDialog` objektu.|

## <a name="remarks"></a>Poznámky

Společná dialogová tisku poskytují snadný způsob, jak implementovat dialogová okna tisku a nastavení tisku v souladu se standardy Windows.

> [!NOTE]
>  `CPrintDialogEx` Třídy zapouzdřuje služby poskytované seznamem vlastností tisku Windows. Další informace najdete v článku [cprintdialogex –](../../mfc/reference/cprintdialogex-class.md) Přehled.

`CPrintDialog`pro funkce se nahradí u [cpagesetupdialog –](../../mfc/reference/cpagesetupdialog-class.md), který slouží k poskytování běžným dialogovým oknem pro obě vytisknout, instalace a nastavení stránky.

Můžete se spolehnout na rozhraní .NET framework pro zpracování mnoho aspektů proces tisku pro vaši aplikaci. V tomto případě rozhraní automaticky zobrazí Windows běžných dialogových oken pro tisk. Můžete také mít popisovač framework tisku pro vaši aplikaci, ale přepsat běžné dialogového okna Tisk s vlastními poli dialogového okna Tisk. Další informace o použití rozhraní pro zpracování tiskové úlohy, najdete v článku [tisk](../../mfc/printing.md).

Pokud chcete, aby aplikace zpracovávala tisk bez zapojení rozhraní framework, můžete použít `CPrintDialog` třídy pomocí konstruktoru určených "tak jak jsou", nebo lze odvodit vlastní třídy dialogového okna z `CPrintDialog` a zápis konstruktoru tak, aby odpovídala vašim potřebám. V obou případech se tyto dialogy se chovají jako standardní dialogová okna MFC vzhledem k tomu, že jsou odvozeny z třídy `CCommonDialog`.

Použití `CPrintDialog` objektu, musíte nejprve vytvořit objekt pomocí `CPrintDialog` konstruktoru. Jakmile byl vytvořen dialogových oken, můžete nastavit nebo změnit všechny hodnoty v [m_pd](#m_pd) struktura inicializace hodnot ovládacích prvků v dialogovém okně. `m_pd` Struktury je typu [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda). Další informace o této struktuře naleznete v tématu Windows SDK.

Pokud nezadáte vlastní obslužných rutin v `m_pd` pro `hDevMode` a `hDevNames` členy, nezapomeňte volat funkci Windows `GlobalFree` pro tyto manipulační body, jakmile budete hotovi s dialogovým oknem. Při použití nastavení tisku implementace poskytované `CWinApp::OnFilePrintSetup`, není nutné uvolnit tyto manipulační body. Úchyty jsou udržovány `CWinApp` a jsou uvolněny v `CWinApp`jeho destruktor. Je nutné uvolnit tyto manipulační body při použití pouze `CPrintDialog` samostatné.

Po inicializaci ovládací prvky dialogového okna, zavolejte `DoModal` členské funkce k zobrazení dialogového okna a umožnit uživateli vybrat možnosti tisku. `DoModal` Vrátí, zda uživatel vybral tlačítko OK (IDOK) nebo zrušit (IDCANCEL).

Pokud `DoModal` vrátí IDOK, můžete použít jednu z `CPrintDialog`pro členské funkce načtete informace o vstup uživatele.

`CPrintDialog::GetDefaults` Členská funkce je užitečná pro získání aktuální výchozí nastavení tiskárny bez zobrazení dialogového okna. Tato členská funkce nevyžaduje žádný zásah uživatele.

Můžete použít Windows `CommDlgExtendedError` funkce k určení, zda došlo k chybě při inicializaci dialogového okna a další informace o této chybě. Další informace o této funkci najdete v tématu Windows SDK.

`CPrintDialog` využívá COMMDLG. Soubor knihovny DLL, která se dodává s Windows verze 3.1 nebo novější.

Přizpůsobení dialogových oken, odvoďte třídu z `CPrintDialog`zadejte šablonu vlastního dialogu a přidání mapy zpráv pro zpracování zpráv s oznámením z rozšířené ovládací prvky. Všechny nezpracované zprávy by měly být předány základní třídu. Přizpůsobení funkce háku se nevyžaduje.

Ke zpracování stejné zprávy odlišně v závislosti na tom, zda je dialogové okno Tisk nebo nastavení tisku, musí být odvozena třída pro každou dialogové okno. Musí také přepsat Windows `AttachOnSetup` funkce, která zpracovává vytvoření nového dialogového okna při výběru tlačítka nastavení tisku v dialogovém okně tisku.

Další informace o používání `CPrintDialog`, naleznete v tématu [společné třídy dialogových oken](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[Ccommondialog –](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

##  <a name="cprintdialog"></a>  CPrintDialog::CPrintDialog

Vytvoří objekt dialogové okno Tisk Windows nebo nastavení tisku.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*bPrintSetupOnly*<br/>
Určuje, zda se zobrazí standardní dialogové okno Tisk Windows nebo dialogové okno Nastavení tisku. Nastavte tento parametr na hodnotu PRAVDA, zobrazení standardní dialogové okno Nastavení tisku Windows. Nastavte na hodnotu FALSE pro zobrazení dialogového okna Tisk Windows. Pokud *bPrintSetupOnly* má hodnotu FALSE, nastavení tisku přepínač se stále zobrazí v dialogovém okně tisku.

*dwFlags*<br/>
Jeden nebo více příznaků, které vám umožní přizpůsobit nastavení dialogovém okně kombinované pomocí bitového operátoru OR. Například PD_ALLPAGES příznak nastaví výchozí rozsah tisku na všechny stránky dokumentu. Zobrazit [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) struktura v sadě Windows SDK pro další informace o těchto příznacích.

*pParentWnd*<br/>
Ukazatel na okno nadřazené nebo vlastník dialogových oken.

### <a name="remarks"></a>Poznámky

Tato členská funkce pouze vytvoří objekt. Použití `DoModal` členské funkce k zobrazení dialogového okna.

Všimněte si, že při volání konstruktoru s *bPrintSetupOnly* nastavena na hodnotu FALSE, příznak PD_RETURNDC se automaticky použije. Po volání `DoModal`, `GetDefaults`, nebo `GetPrinterDC`, tiskárnu řadiče domény, vrátí se `m_pd.hDC`. Tento řadič domény musí být uvolněna voláním [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) volajícím funkce `CPrintDialog`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC

Vytvoří kontext zařízení tiskárny (DC) z [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) a [DEVNAMES –](../../mfc/reference/devnames-structure.md) struktury.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač kontextu zařízení nově vytvořené tiskárny.

### <a name="remarks"></a>Poznámky

Tento řadič domény je považován za aktuální tiskárny řadiče domény a jakýkoli jiný dříve získány tiskárny, které řadiče domény musí být odstraněno uživatelem. Tuto funkci lze volat a výsledné řadič domény používá bez někdy zobrazení dialogového okna Tisk.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>  CPrintDialog::DoModal

Zobrazí okno Windows běžné dialogového okna Tisk a umožňuje uživateli vybrat různé možnosti tisku, jako je například počet kopií, stránka rozsahu, a určuje, zda mají být kopie tříděny.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud je vrácena IDCANCEL, zavolejte Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkce k určení, zda došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel vybral tlačítko OK nebo zrušit.

### <a name="remarks"></a>Poznámky

Pokud chcete inicializovat různé možnosti dialogového okna Tisk nastavením členy `m_pd` strukturu, je potřeba to udělat před voláním `DoModal`, ale po vytvoření objektu dialogového okna.

Po volání `DoModal`, můžete volat ostatní členské funkce k načtení nastavení nebo informace o vstup uživatelem do dialogových oken.

Všimněte si, že při volání konstruktoru s *bPrintSetupOnly* nastavena na hodnotu FALSE, příznak PD_RETURNDC se automaticky použije. Po volání `DoModal`, `GetDefaults`, nebo `GetPrinterDC`, tiskárnu řadiče domény, vrátí se `m_pd.hDC`. Tento řadič domény musí být uvolněna voláním [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) volajícím funkce `CPrintDialog`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::CreatePrinterDC](#createprinterdc).

##  <a name="getcopies"></a>  CPrintDialog::GetCopies

Získá počet kopií požadovaný.

```
int GetCopies() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet kopií požadovaný.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání `DoModal` načíst počet kopií požadovaný.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::PrintCollate](#printcollate).

##  <a name="getdefaults"></a>  CPrintDialog::GetDefaults

Načte výchozí tiskárny výchozí nastavení zařízení bez zobrazení dialogového okna.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud funkce byla úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Načtené hodnoty jsou umístěny v `m_pd` struktury.

V některých případech bude volat volání této funkce [konstruktor](#cprintdialog) pro `CPrintDialog` s *bPrintSetupOnly* nastavena na hodnotu FALSE. V těchto případech tiskárny řadiče domény a `hDevNames` a `hDevMode` (dva popisovače umístěný v `m_pd` datový člen) alokováno automaticky.

Pokud konstruktor pro `CPrintDialog` byla volána s *bPrintSetupOnly* nastavena na hodnotu FALSE, tato funkce nebude vrátit pouze `hDevNames` a `hDevMode` umístěné v `m_pd.hDevNames` a `m_pd.hDevMode`) volajícímu, ale také vrátí tiskárnu řadiče domény v `m_pd.hDC`. Je odpovědností volajícího k odstranění tiskárny řadiče domény a volat Windows [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree) funkce s popisovači po dokončení se `CPrintDialog` objektu.

### <a name="example"></a>Příklad

Tento fragment kódu získá kontext zařízení na výchozí tiskárně a oznámí uživateli rozlišení tiskárny v bodů na palec. (Tento atribut vlastnosti tiskárny se často označuje jako DPI.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName

Načte název zařízení aktuálně vybrané tiskárny.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název vybrané tiskárny.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání [DoModal](#domodal) načíst název aktuálně vybrané tiskárny, nebo po volání [GetDefaults](#getdefaults) načíst aktuální výchozí nastavení zařízení z výchozí tiskárna. Použít ukazatel `CString` vrácený `GetDeviceName` jako hodnotu `lpszDeviceName` ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Příklad

Tento fragment kódu ukazuje uživatele výchozí název tiskárny a port, který je připojený, spolu s názvem zařazování, který tiskárnu používá. Kód může zobrazit okno se zprávou, že "výchozí tiskárna je HP LaserJet IIIP na \\\server\share pomocí winspool.", např.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>  CPrintDialog::GetDevMode

Načte `DEVMODE` struktury.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Návratová hodnota

[DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) datová struktura, která obsahuje informace o inicializaci zařízení a prostředí, které ovladače tiskárny. Musíte odemknout paměť provedenou tato struktura se Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) funkce, která je popsána v sadě Windows SDK.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) k načtení informací o tiskové zařízení.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::PrintCollate](#printcollate).

##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName

Získá název aktuálně vybraného ovladače tiskárny.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CString` určující název ovladače definovaná systémem.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název definovaných systémem ovladače zařízení. Použít ukazatel `CString` vrácený `GetDriverName` jako hodnotu `lpszDriverName` ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::GetDeviceName](#getdevicename).

##  <a name="getfrompage"></a>  CPrintDialog::GetFromPage

Získá počáteční stránky rozsah tisku.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Počáteční stránka číslo v rozsahu stránek, které se mají vytisknout.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání `DoModal` načíst počáteční stránky číslo v rozsahu stránek, které se mají vytisknout.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::m_pd](#m_pd).

##  <a name="getportname"></a>  CPrintDialog::GetPortName

Načte název portu aktuálně vybrané tiskárny.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název portu aktuálně vybrané tiskárny.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název portu aktuálně vybrané tiskárny.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::GetDeviceName](#getdevicename).

##  <a name="getprinterdc"></a>  CPrintDialog::GetPrinterDC

Načte popisovač kontextu zařízení tiskárny.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač kontextu zařízení tiskárny v případě úspěchu; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Pokud *bPrintSetupOnly* parametr `CPrintDialog` konstruktor byl NEPRAVDA (Určuje, že se zobrazí dialogové okno Tisk), pak `GetPrinterDC` vrací popisovač do kontextu zařízení tiskárny. Je třeba zavolat Windows [DeleteDC](/windows/desktop/api/wingdi/nf-wingdi-deletedc) funkce kontextu zařízení odstranit, po dokončení jeho použití.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>  CPrintDialog::GetToPage

Načte poslední stránky rozsah tisku.

```
int GetToPage() const;
```

### <a name="return-value"></a>Návratová hodnota

Koncové číslo stránky v rozsahu stránek, které se mají vytisknout.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání `DoModal` k načtení poslední stránky číslo v rozsahu stránek, které se mají vytisknout.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::m_pd](#m_pd).

##  <a name="m_pd"></a>  CPrintDialog::m_pd

Struktura, jejíž členové uložení vlastnosti z objektu dialogového okna.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Poznámky

Po sestavení `CPrintDialog` objektu, můžete použít `m_pd` nastavit různé aspekty dialogového okna před voláním [DoModal](#domodal) členskou funkci. Další informace o `m_pd` struktury, přečtěte si téma [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) v sadě Windows SDK.

Pokud změníte `m_pd` datový člen přímo, budou všechny výchozí chování přepsat.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>  CPrintDialog::PrintAll

Určuje, jestli se má vytisknout všechny stránky dokumentu.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud všechny stránky v dokumentu se mají vytisknout; jinak 0.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání `DoModal` k určení, jestli se má vytisknout všechny stránky v dokumentu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::m_pd](#m_pd).

##  <a name="printcollate"></a>  CPrintDialog::PrintCollate

Určuje, zda porovnávány kopie jsou požadovány.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud uživatel vybere toto políčko, pokud v dialogovém okně. jinak 0.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání `DoModal` k určení, zda by měl tiskárny collate všechny vytištěných kopií dokumentu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>  CPrintDialog::PrintRange

Určuje, jestli se má vytisknout zadaného rozsahu stránek.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud pouze rozsahu stránek v dokumentu se mají vytisknout; jinak 0.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání `DoModal` k určení, jestli se má vytisknout pouze rozsah stránek v dokumentu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::m_pd](#m_pd).

##  <a name="printselection"></a>  CPrintDialog::PrintSelection

Určuje, jestli se má tisknout jen aktuálně vybrané položky.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud pouze vybrané položky se mají vytisknout; jinak 0.

### <a name="remarks"></a>Poznámky

Voláním této funkce po volání `DoModal` k určení, jestli se má tisknout jen aktuálně vybrané položky.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPrintDialog::m_pd](#m_pd).

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC DIBLOOK](../../visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo – struktura](../../mfc/reference/cprintinfo-structure.md)
