---
title: Třída CPrintDialogEx | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPrintDialogEx
- AFXDLGS/CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CreatePrinterDC
- AFXDLGS/CPrintDialogEx::DoModal
- AFXDLGS/CPrintDialogEx::GetCopies
- AFXDLGS/CPrintDialogEx::GetDefaults
- AFXDLGS/CPrintDialogEx::GetDeviceName
- AFXDLGS/CPrintDialogEx::GetDevMode
- AFXDLGS/CPrintDialogEx::GetDriverName
- AFXDLGS/CPrintDialogEx::GetPortName
- AFXDLGS/CPrintDialogEx::GetPrinterDC
- AFXDLGS/CPrintDialogEx::PrintAll
- AFXDLGS/CPrintDialogEx::PrintCollate
- AFXDLGS/CPrintDialogEx::PrintCurrentPage
- AFXDLGS/CPrintDialogEx::PrintRange
- AFXDLGS/CPrintDialogEx::PrintSelection
- AFXDLGS/CPrintDialogEx::m_pdex
dev_langs:
- C++
helpviewer_keywords:
- CPrintDialogEx [MFC], CPrintDialogEx
- CPrintDialogEx [MFC], CreatePrinterDC
- CPrintDialogEx [MFC], DoModal
- CPrintDialogEx [MFC], GetCopies
- CPrintDialogEx [MFC], GetDefaults
- CPrintDialogEx [MFC], GetDeviceName
- CPrintDialogEx [MFC], GetDevMode
- CPrintDialogEx [MFC], GetDriverName
- CPrintDialogEx [MFC], GetPortName
- CPrintDialogEx [MFC], GetPrinterDC
- CPrintDialogEx [MFC], PrintAll
- CPrintDialogEx [MFC], PrintCollate
- CPrintDialogEx [MFC], PrintCurrentPage
- CPrintDialogEx [MFC], PrintRange
- CPrintDialogEx [MFC], PrintSelection
- CPrintDialogEx [MFC], m_pdex
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f511eb1414a5cd5e22b9a3e05f81caef15b908e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx – třída
Zapouzdří služeb poskytovaných vlastností Tisk systému Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPrintDialogEx : public CCommonDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|Vytvoří `CPrintDialogEx` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Bez zobrazení dialogového okna Tisk vytvoří kontextu zařízení tiskárny.|  
|[CPrintDialogEx::DoModal](#domodal)|Zobrazí dialogové okno a umožňuje uživateli možnosti.|  
|[CPrintDialogEx::GetCopies](#getcopies)|Načte počtu kopií požadovaný.|  
|[CPrintDialogEx::GetDefaults](#getdefaults)|Načte výchozí nastavení zařízení bez zobrazení dialogového okna.|  
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Načte název zařízení aktuálně vybrané tiskárny.|  
|[CPrintDialogEx::GetDevMode](#getdevmode)|Načte `DEVMODE` struktura.|  
|[CPrintDialogEx::GetDriverName](#getdrivername)|Načte název definované systémem ovladače zařízení.|  
|[CPrintDialogEx::GetPortName](#getportname)|Načte název portu aktuálně vybrané tiskárny.|  
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Načte popisovač pro kontext zařízení tiskárny.|  
|[CPrintDialogEx::PrintAll](#printall)|Určuje, zda všechny stránky z dokumentu.|  
|[CPrintDialogEx::PrintCollate](#printcollate)|Určuje, zda kompletován, že jsou požadovány kopie.|  
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Určuje, zda se aktuální stránku dokumentu vytisknout.|  
|[CPrintDialogEx::PrintRange](#printrange)|Určuje, zda zadaný rozsah stránek vytisknout.|  
|[CPrintDialogEx::PrintSelection](#printselection)|Určuje, jestli se mají vytisknout pouze aktuálně vybrané položky.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPrintDialogEx::m_pdex](#m_pdex)|Struktura sloužící k přizpůsobení `CPrintDialogEx` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete spolehnout na rozhraní pro zpracování mnoho aspektů proces tisku pro vaši aplikaci. Další informace o používání rozhraní k zpracovávat tiskové úlohy, najdete v článku [tisk](../../mfc/printing.md).  
  
 Pokud chcete, aby aplikace pro zpracování tisk bez zapojení rozhraní framework, můžete použít `CPrintDialogEx` třídy s konstruktorem poskytuje "tak, jak je, nebo odvozujete vlastní třídy dialogového okna z `CPrintDialogEx` a zápis konstruktoru tak, aby vyhovovala vašim potřebám. V obou případech tyto dialogy budou chovat jako standardní dialogová okna MFC vzhledem k tomu, že jsou odvozeny od třídy `CCommonDialog`.  
  
 Použít `CPrintDialogEx` objektu, nejprve vytvořit objekt pomocí `CPrintDialogEx` konstruktor. Jakmile dialogové okno byl vytvořený, můžete nastavit nebo změnit všechny hodnoty v [m_pdex](#m_pdex) struktura k chybě při inicializaci hodnoty ovládací prvky dialogových oken. `m_pdex` Struktura je typu [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844). Další informace o tuto strukturu najdete v části Windows SDK.  
  
 Pokud nezadáte vlastní obslužných rutin v `m_pdex` pro **hDevMode** a **hDevNames je** členy, nezapomeňte volání funkce systému Windows **GlobalFree** pro tyto obslužné rutiny Jakmile jste hotovi s dialogové okno.  
  
 Po inicializaci ovládacím prvkům v dialogovém okně, volání `DoModal` – členská funkce a zobrazit dialogové okno Povolit uživateli vybrat možnosti tisku. Když `DoModal` vrátí, můžete určit, zda uživatel vybral na tlačítko OK, použít nebo Storno.  
  
 Pokud uživatel klepl na tlačítko OK, můžete použít `CPrintDialogEx`na členské funkce načíst informace o zadaný uživatelem.  
  
 `CPrintDialogEx::GetDefaults` – Členská funkce je užitečná pro načítání aktuální výchozí nastavení tiskárny bez zobrazení dialogového okna. Tato metoda vyžaduje zásah uživatele.  
  
 Můžete použít Windows **CommDlgExtendedError** funkce k určení, zda došlo k chybě během inicializace dialogových oken a další informace o této chybě. Další informace o této funkci najdete v části Windows SDK.  
  
 Další informace o používání `CPrintDialogEx`, najdete v části [třídy společných dialogů](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `IObjectWithSite`  
  
 `IPrintDialogCallback`  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialogEx`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx  
 Vytvoří seznam vlastností Tisk systému Windows.  
  
```  
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Jeden nebo více příznaky, které můžete použít k přizpůsobení nastavení dialogovém okně spojovat pomocí bitový operátor OR. Například **PD_ALLPAGES** příznak nastaví výchozí rozsah tisku na všechny stránky z dokumentu. Najdete v článku [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) struktura ve Windows SDK pro další informace o tyto příznaky.  
  
 `pParentWnd`  
 Ukazatele v dialogovém okně nadřazené nebo vlastníka.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen pouze vytvoří objekt. Použití `DoModal` členské funkce k zobrazení dialogového okna.  
  
##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC  
 Vytvoří z kontextu zařízení tiskárny (DC) [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) a [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kontextu zařízení nově vytvořené tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Vrácený řadič domény je také uložen v **hDC** členem [m_pdex](#m_pdex).  
  
 Tento řadič domény předpokládá se, že aktuální tiskárny řadiče domény a všechny další dříve získány tiskárny, řadiče domény musí být odstraněny. Tato funkce se dá volat a výsledný řadič domény použít bez někdy zobrazení dialogového okna Tisk.  
  
##  <a name="domodal"></a>  CPrintDialogEx::DoModal  
 Volání této funkce můžete zobrazit seznam vlastností Tisk systému Windows a umožní uživateli vybrat různé možnosti tisku, jako je například počet kopií, rozsahu stránek, a zda mají být tříděny kopie.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 INT_PTR vrátit, že hodnota je ve skutečnosti HRESULT. Najdete v části vrátit hodnoty v [PrintDlgEx](http://msdn.microsoft.com/library/windows/desktop/ms646942) ve Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete k chybě při inicializaci různé tiskové dialogové okno Možnosti nastavením členy `m_pdex` struktura, bude třeba provést před voláním `DoModal`, ale po objektu dialogového okna je vytvořený.  
  
 Po volání `DoModal`, můžete volat jiné členské funkce načíst nastavení nebo uživatelský vstup informace do dialogových oken.  
  
 Pokud **PD_RETURNDC** příznak se používá při volání metody `DoModal`, tiskárny řadič domény, vrátí se **hDC** členem [m_pdex](#m_pdex). Tento řadič domény musí být uvolněno pomocí volání [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) volající z `CPrintDialogEx`.  
  
##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies  
 Volání této funkce po volání `DoModal` načíst počet kopií požadovaný.  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet kopií požadovaný.  
  
##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults  
 Volání této funkce se načíst výchozí nastavení zařízení výchozí tiskárny bez zobrazení dialogového okna.  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud bylo úspěšné, jinak **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří z kontextu zařízení tiskárny (DC) [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) a [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.  
  
 `GetDefaults` nezobrazuje vlastností tisku. Místo toho nastaví **hDevNames je** a **hDevMode** členy [m_pdex](#m_pdex) ke zpracování na [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) a [DEVNAMES ](../../mfc/reference/devnames-structure.md) struktury, které jsou inicializovány tiskárny výchozí systému. Obě **hDevNames je** a **hDevMode** musí mít hodnotu NULL, nebo `GetDefaults` selže.  
  
 Pokud **PD_RETURNDC** nastavený příznak, tato funkce nebude vrátit pouze **hDevNames je** a **hDevMode** (umístěné v **m_pdex.hDevNames** a **m_pdex.hDevMode**) volajícího, ale také vrátí tiskárnu řadiče domény v **m_pdex.hDC**. Zodpovídá volající odstranit tiskárny řadiče domény a volání Windows [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) funkce na obslužné rutiny pro zpracování po dokončení se `CPrintDialogEx` objektu.  
  
##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName  
 Volání této funkce po volání [DoModal](#domodal) získávání názvu aktuálně vybrané tiskárny, nebo po volání [GetDefaults](#getdefaults) načíst název výchozí tiskárny.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název aktuálně vybrané tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Použijte odkazy `CString` objekt vrácený `GetDeviceName` jako hodnotu `lpszDeviceName` ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode  
 Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) k načtení informací o tisk zařízení.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) datová struktura, která obsahuje informace o zařízení inicializace a prostředí ovladače tiskárny. Je třeba odemknout paměť provedenou tuto strukturu s Windows [GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595) funkce, která je popsána v sadě Windows SDK.  
  
##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName  
 Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název definované systémem ovladače zařízení.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` zadání názvu ovladače definovaná systémem.  
  
### <a name="remarks"></a>Poznámky  
 Použijte odkazy `CString` objekt vrácený `GetDriverName` jako hodnotu `lpszDriverName` ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getportname"></a>  CPrintDialogEx::GetPortName  
 Volání této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název portu aktuálně vybrané tiskárny.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název portu aktuálně vybrané tiskárny.  
  
##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC  
 Vrátí popisovač kontextu zařízení tiskárny.  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro kontext zařízení tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) funkce můžete odstranit kontextu zařízení, když jste hotovi jeho použití.  
  
##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex  
 Struktura PRINTDLGEX, jejíž členové uložení charakteristiky objektu dialogového okna.  
  
```  
PRINTDLGEX m_pdex;  
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření `CPrintDialogEx` objekt, můžete použít `m_pdex` nastavit různé aspekty dialogu před voláním [DoModal](#domodal) – členská funkce. Další informace o `m_pdex` struktury najdete v tématu [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) ve Windows SDK.  
  
 Pokud změníte `m_pdex` – datový člen přímo, přepíše jakékoli výchozí chování.  
  
##  <a name="printall"></a>  CPrintDialogEx::PrintAll  
 Volání této funkce po volání `DoModal` a určí, jestli všechny stránky v dokumentu.  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud jsou všechny stránky v dokumentu na tištěných; jinak hodnota **FALSE**.  
  
##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate  
 Volání této funkce po volání `DoModal` k určení, zda by měl tiskárny collate všechny na tištěných kopií dokumentu.  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud uživatel vybere toto políčko, pokud v dialogovém okně; v opačném případě **FALSE**.  
  
##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage  
 Volání této funkce po volání `DoModal` a určí, jestli tisk aktuální stránky v dokumentu.  
  
```  
BOOL PrintCurrentPage() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud **tisk aktuální stránky** je vybraný v dialogovém okně tisku; jinak hodnota **FALSE**.  
  
##  <a name="printrange"></a>  CPrintDialogEx::PrintRange  
 Volání této funkce po volání `DoModal` a určí, jestli chcete vytisknout pouze rozsahu stránek v dokumentu.  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** -li jen rozsahu stránek v dokumentu jsou na tištěných; jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Lze určit rozsahy Zadaná stránka [m_pdex](#m_pdex) (viz **nPageRanges**, **nMaxPageRanges**, a **lpPageRanges** v [ PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) struktura ve Windows SDK).  
  
##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection  
 Volání této funkce po volání `DoModal` a určí, jestli chcete vytisknout pouze aktuálně vybrané položky.  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud pouze vybrané položky se na tištěných; jinak hodnota **FALSE**.  
  
## <a name="see-also"></a>Viz také  
 [CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CPrintInfo – struktura](../../mfc/reference/cprintinfo-structure.md)
