---
title: "Třída CPrintDialog | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d7834351533cac7f518f5ce5f5558a6be2da34be
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="cprintdialog-class"></a>CPrintDialog – třída
Zapouzdří služeb poskytovaných běžné dialogové okno pro tisk.  
  
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
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Bez zobrazení dialogového okna Tisk vytvoří kontextu zařízení tiskárny.|  
|[CPrintDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožňuje uživateli proveďte výběr.|  
|[CPrintDialog::GetCopies](#getcopies)|Načte počtu kopií požadovaný.|  
|[CPrintDialog::GetDefaults](#getdefaults)|Načte výchozí nastavení zařízení bez zobrazení dialogového okna.|  
|[CPrintDialog::GetDeviceName](#getdevicename)|Načte název zařízení aktuálně vybrané tiskárny.|  
|[CPrintDialog::GetDevMode](#getdevmode)|Načte `DEVMODE` struktura.|  
|[CPrintDialog::GetDriverName](#getdrivername)|Načte název aktuálně vybraného ovladače tiskárny.|  
|[CPrintDialog::GetFromPage](#getfrompage)|Načte výchozí stránka rozsah tisku.|  
|[CPrintDialog::GetPortName](#getportname)|Načte název portu aktuálně vybrané tiskárny.|  
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Načte popisovač pro kontext zařízení tiskárny.|  
|[CPrintDialog::GetToPage](#gettopage)|Načte koncové stránky rozsah tisku.|  
|[CPrintDialog::PrintAll](#printall)|Určuje, zda všechny stránky z dokumentu.|  
|[CPrintDialog::PrintCollate](#printcollate)|Určuje, zda kompletován, že jsou požadovány kopie.|  
|[CPrintDialog::PrintRange](#printrange)|Určuje, zda zadaný rozsah stránek vytisknout.|  
|[CPrintDialog::PrintSelection](#printselection)|Určuje, jestli se mají vytisknout pouze aktuálně vybrané položky.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPrintDialog::m_pd](#m_pd)|Struktura sloužící k přizpůsobení `CPrintDialog` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Společná dialogová tiskové poskytují snadný způsob, jak implementovat dialogová okna Nastavení tisku a tisk v souladu s normami systému Windows.  
  
> [!NOTE]
>  `CPrintDialogEx` Třída zapouzdří služeb poskytovaných vlastností Tisk systému Windows. Další informace najdete v článku [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) Přehled.  
  
 `CPrintDialog`pro funkci oprávněni u [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), který slouží k poskytnout běžné dialogové okno pro obě tisku nastavení a nastavení stránky.  
  
 Můžete spolehnout na rozhraní pro zpracování mnoho aspektů proces tisku pro vaši aplikaci. V takovém případě rozhraní automaticky zobrazí běžné dialogové okno pro tisk. Můžete také mít framework popisovač tisk pro vaši aplikaci, ale přepsání běžné tiskových dialogové okno s vlastní tiskové dialogové okno. Další informace o používání rozhraní k zpracovávat tiskové úlohy, najdete v článku [tisk](../../mfc/printing.md).  
  
 Pokud chcete, aby aplikace pro zpracování tisk bez zapojení rozhraní framework, můžete použít `CPrintDialog` třídy s konstruktorem poskytuje "tak, jak je, nebo odvozujete vlastní třídy dialogového okna z `CPrintDialog` a zápis konstruktoru tak, aby vyhovovala vašim potřebám. V obou případech tyto dialogy budou chovat jako standardní dialogová okna MFC vzhledem k tomu, že jsou odvozeny od třídy `CCommonDialog`.  
  
 Použít `CPrintDialog` objektu, nejprve vytvořit objekt pomocí `CPrintDialog` konstruktor. Jakmile dialogové okno byl vytvořený, můžete nastavit nebo změnit všechny hodnoty v [m_pd](#m_pd) struktura k chybě při inicializaci hodnoty ovládací prvky dialogových oken. `m_pd` Struktura je typu [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843). Další informace o tuto strukturu najdete v části Windows SDK.  
  
 Pokud nezadáte vlastní obslužných rutin v `m_pd` pro **hDevMode** a **hDevNames je** členy, nezapomeňte volání funkce systému Windows **GlobalFree** pro tyto obslužné rutiny Jakmile jste hotovi s dialogové okno. Při použití v rámci nastavení tisku implementace poskytovaná `CWinApp::OnFilePrintSetup`, není nutné bez těchto obslužných rutin. Obslužné rutiny pro zpracování se spravuje pomocí `CWinApp` a jsou uvolněny v `CWinApp`na destruktor. Je nutné uvolnit těchto obslužných rutin, při použití pouze `CPrintDialog` samostatné.  
  
 Po inicializaci ovládacím prvkům v dialogovém okně, volání `DoModal` – členská funkce a zobrazit dialogové okno Povolit uživateli vybrat možnosti tisku. `DoModal`Vrátí, zda uživatel vybral OK ( **IDOK**) nebo zrušit ( **IDCANCEL**) tlačítko.  
  
 Pokud `DoModal` vrátí **IDOK**, můžete použít jednu z `CPrintDialog`na členské funkce načíst informace o zadaný uživatelem.  
  
 `CPrintDialog::GetDefaults` – Členská funkce je užitečná pro načítání aktuální výchozí nastavení tiskárny bez zobrazení dialogového okna. Tato funkce člen nevyžaduje zásah uživatele.  
  
 Můžete použít Windows **CommDlgExtendedError** funkce k určení, zda došlo k chybě během inicializace dialogových oken a další informace o této chybě. Další informace o této funkci najdete v části Windows SDK.  
  
 `CPrintDialog`spoléhá na COMMDLG. Soubor knihovny DLL, která se dodává s verzí systému Windows verze 3.1 nebo novější.  
  
 Chcete-li přizpůsobit dialogové okno, odvození třídy z `CPrintDialog`zadejte dialogové okno vlastní šablony a přidat mapy zpráv pro zpracování zprávy s oznámením z rozšířených ovládacích prvků. Všechny nezpracované zprávy by měla být předána základní třídy. Přizpůsobení funkce háku se nevyžaduje.  
  
 Při zpracování stejnou zprávu odlišně v závislosti na tom, jestli je dialogové okno tisku nebo nastavení tisku, musí být odvozeny třídu, pro každý dialogové okno. Také je nutné přepsat Windows **AttachOnSetup** funkce, která zpracovává vytvoření nového dialogového okna, pokud je vybrána tlačítko Nastavení tisku v dialogovém okně tisku.  
  
 Další informace o používání `CPrintDialog`, najdete v části [třídy společných dialogů](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="cprintdialog"></a>CPrintDialog::CPrintDialog  
 Vytvoří Tisk systému Windows nebo nastavení tisku objektu dialogového okna.  
  
```  
CPrintDialog(
    BOOL bPrintSetupOnly,  
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `bPrintSetupOnly`  
 Určuje, zda se zobrazí dialogové okno standardní tisk systému Windows nebo dialogové okno Nastavení tisku. Tento parametr nastavte na **TRUE** zobrazíte standardní dialogové okno Nastavení tisku systému Windows. Nastavte ji na **FALSE** k zobrazení dialogového okna Tisk systému Windows. Pokud `bPrintSetupOnly` je **FALSE**, tlačítko možnost nastavení tisku se pořád zobrazí v dialogovém okně tisku.  
  
 `dwFlags`  
 Jeden nebo více příznaky, které můžete použít k přizpůsobení nastavení dialogovém okně spojovat pomocí bitový operátor OR. Například **PD_ALLPAGES** příznak nastaví výchozí rozsah tisku na všechny stránky z dokumentu. Najdete v článku [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) struktura ve Windows SDK pro další informace o tyto příznaky.  
  
 `pParentWnd`  
 Ukazatele v dialogovém okně nadřazené nebo vlastníka.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen pouze vytvoří objekt. Použití `DoModal` členské funkce k zobrazení dialogového okna.  
  
 Upozorňujeme, že pokud volat konstruktor s `bPrintSetupOnly` nastavena na **FALSE**, **PD_RETURNDC** příznak se používá automaticky. Po volání `DoModal`, `GetDefaults`, nebo `GetPrinterDC`, tiskárny řadič domény bude vrácen v `m_pd.hDC`. Tento řadič domény musí být uvolněno pomocí volání [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) volající z `CPrintDialog`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]  
  
##  <a name="createprinterdc"></a>CPrintDialog::CreatePrinterDC  
 Vytvoří z kontextu zařízení tiskárny (DC) [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) a [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kontextu zařízení nově vytvořené tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Tento řadič domény předpokládá se, že aktuální tiskárny řadiče domény a všechny další dříve získány tiskárny, které řadiče domény musí být odstraněno uživatelem. Tato funkce se dá volat a výsledný řadič domény použít bez někdy zobrazení dialogového okna Tisk.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]  
  
##  <a name="domodal"></a>CPrintDialog::DoModal  
 Zobrazí běžné tiskové dialogové okno a umožňuje uživateli vybrat různé možnosti tisku, jako je například počet kopií, rozsahu stránek, a zda mají být tříděny kopie.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **IDOK** nebo **IDCANCEL**. Pokud **IDCANCEL** je vrácen, volání Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkce k určení, zda došlo k chybě.  
  
 **IDOK** a **IDCANCEL** jsou konstanty, které označuje, zda uživatel vybrané na tlačítko OK nebo Storno.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různé tiskové dialogové okno Možnosti nastavením členy `m_pd` struktura, bude třeba provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
 Po volání `DoModal`, můžete volat jiné členské funkce načíst nastavení nebo uživatelský vstup informace do dialogových oken.  
  
 Upozorňujeme, že pokud volat konstruktor s `bPrintSetupOnly` nastavena na **FALSE**, **PD_RETURNDC** příznak se používá automaticky. Po volání `DoModal`, `GetDefaults`, nebo `GetPrinterDC`, tiskárny řadič domény bude vrácen v `m_pd.hDC`. Tento řadič domény musí být uvolněno pomocí volání [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) volající z `CPrintDialog`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPrintDialog::CreatePrinterDC](#createprinterdc).  
  
##  <a name="getcopies"></a>CPrintDialog::GetCopies  
 Načte počtu kopií požadovaný.  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet kopií požadovaný.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání `DoModal` načíst počet kopií požadovaný.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPrintDialog::PrintCollate](#printcollate).  
  
##  <a name="getdefaults"></a>CPrintDialog::GetDefaults  
 Načte výchozí nastavení zařízení výchozí tiskárny bez zobrazení dialogového okna.  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud funkci byla úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Načtené hodnoty jsou umístěny v `m_pd` struktura.  
  
 V některých případech bude volat volání této funkce [konstruktor](#cprintdialog) pro `CPrintDialog` s `bPrintSetupOnly` nastavena na **FALSE**. V těchto případech tiskárny řadiče domény a **hDevNames je** a **hDevMode** (dvě obslužné rutiny umístěný v `m_pd` – datový člen) jsou automaticky přiděleny.  
  
 Pokud v konstruktoru pro `CPrintDialog` byla volána s `bPrintSetupOnly` nastavena na **FALSE**, tato funkce nebude vrátit pouze **hDevNames je** a **hDevMode** (nachází se ve **m_pd.hDevNames** a **m_pd.hDevMode**) volajícího, ale také vrátí tiskárnu řadiče domény v **m_pd.hDC**. Zodpovídá volající odstranit tiskárny řadiče domény a volání Windows [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) funkce na obslužné rutiny pro zpracování po dokončení se `CPrintDialog` objektu.  
  
### <a name="example"></a>Příklad  
 Tento fragment kódu získá kontext zařízení výchozí tiskárny a oznámí uživateli rozlišení tiskárny v bodů na palec. (Tento atribut vlastnosti tiskárny se často označuje jako DPI.)  
  
 [!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]  
  
##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName  
 Načte název zařízení aktuálně vybrané tiskárny.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název aktuálně vybrané tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání [DoModal](#domodal) získávání názvu aktuálně vybrané tiskárny, nebo po volání [GetDefaults](#getdefaults) načíst aktuální výchozí nastavení zařízení výchozí tiskárny. Použijte odkazy `CString` objekt vrácený `GetDeviceName` jako hodnotu `lpszDeviceName` ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
### <a name="example"></a>Příklad  
 Tento fragment kódu ukazuje název tiskárny výchozí uživatele a port, který je připojený k, společně s zařazování název, který používá tiskárny. Kód může zobrazit okno se zprávou, která uvádí, "je tiskárna výchozí HP LaserJet IIIP na \\\server\share pomocí winspool.", např.  
  
 [!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]  
  
##  <a name="getdevmode"></a>CPrintDialog::GetDevMode  
 Načte `DEVMODE` struktura.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) datová struktura, která obsahuje informace o zařízení inicializace a prostředí ovladače tiskárny. Je třeba odemknout paměť provedenou tuto strukturu s Windows [GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595) funkce, která je popsána v sadě Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) k načtení informací o tisk zařízení.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPrintDialog::PrintCollate](#printcollate).  
  
##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName  
 Načte název aktuálně vybraného ovladače tiskárny.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` zadání názvu ovladače definovaná systémem.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název definované systémem ovladače zařízení. Použijte odkazy `CString` objekt vrácený `GetDriverName` jako hodnotu `lpszDriverName` ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPrintDialog::GetDeviceName](#getdevicename).  
  
##  <a name="getfrompage"></a>CPrintDialog::GetFromPage  
 Načte výchozí stránka rozsah tisku.  
  
```  
int GetFromPage() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počáteční stránka číslo v rozsahu stránek k tisku.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání `DoModal` načíst první stránka číslo v rozsahu stránek k tisku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="getportname"></a>CPrintDialog::GetPortName  
 Načte název portu aktuálně vybrané tiskárny.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název portu aktuálně vybrané tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název portu aktuálně vybrané tiskárny.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPrintDialog::GetDeviceName](#getdevicename).  
  
##  <a name="getprinterdc"></a>CPrintDialog::GetPrinterDC  
 Načte popisovač pro kontext zařízení tiskárny.  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro kontext tiskárny zařízení v případě úspěšného; v opačném případě **NULL**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `bPrintSetupOnly` parametr `CPrintDialog` konstruktor byl **FALSE** (což znamená, že se zobrazí dialogové okno tisku), pak `GetPrinterDC` vrátí popisovač do kontextu zařízení tiskárny. Je třeba volat Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) funkce můžete odstranit kontextu zařízení, když jste hotovi jeho použití.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]  
  
##  <a name="gettopage"></a>CPrintDialog::GetToPage  
 Načte koncové stránky rozsah tisku.  
  
```  
int GetToPage() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Koncová stránka číslo v rozsahu stránek k tisku.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání `DoModal` načíst koncová číslo stránky v rozsahu stránek k tisku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="m_pd"></a>  CPrintDialog::m_pd  
 Struktura, jejíž členové uložení charakteristiky objektu dialogového okna.  
  
```  
PRINTDLG& m_pd;  
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření `CPrintDialog` objekt, můžete použít `m_pd` nastavit různé aspekty dialogu před voláním [DoModal](#domodal) – členská funkce. Další informace o `m_pd` struktury najdete v tématu [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) ve Windows SDK.  
  
 Pokud změníte `m_pd` – datový člen přímo, přepíše jakékoli výchozí chování.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]  
  
##  <a name="printall"></a>CPrintDialog::PrintAll  
 Určuje, zda všechny stránky z dokumentu.  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud všechny stránky v dokumentu se mají vytisknout; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání `DoModal` a určí, jestli všechny stránky v dokumentu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="printcollate"></a>CPrintDialog::PrintCollate  
 Určuje, zda kompletován, že jsou požadovány kopie.  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud uživatel vybere toto políčko, pokud v dialogovém okně. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání `DoModal` k určení, zda by měl tiskárny collate všechny na tištěných kopií dokumentu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]  
  
##  <a name="printrange"></a>CPrintDialog::PrintRange  
 Určuje, zda zadaný rozsah stránek vytisknout.  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud jenom rozsahu stránek v dokumentu se mají vytisknout; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání `DoModal` a určí, jestli chcete vytisknout pouze rozsahu stránek v dokumentu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPrintDialog::m_pd](#m_pd).  
  
##  <a name="printselection"></a>CPrintDialog::PrintSelection  
 Určuje, jestli se mají vytisknout pouze aktuálně vybrané položky.  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud pouze vybrané položky se mají vytisknout; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce po volání `DoModal` a určí, jestli chcete vytisknout pouze aktuálně vybrané položky.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPrintDialog::m_pd](#m_pd).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC DIBLOOK](../../visual-cpp-samples.md)   
 [CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CPrintInfo – struktura](../../mfc/reference/cprintinfo-structure.md)
