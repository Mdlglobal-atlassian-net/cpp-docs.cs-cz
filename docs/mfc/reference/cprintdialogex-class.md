---
title: Cprintdialogex – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 45975354305323f2a3a4d4f8916b901110d91441
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37849581"
---
# <a name="cprintdialogex-class"></a>Cprintdialogex – třída
Zapouzdřuje služby poskytované seznamem vlastností tisku Windows.  
  
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
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Vytvoří kontext zařízení tiskárny bez zobrazení dialogového okna Tisk.|  
|[CPrintDialogEx::DoModal](#domodal)|Zobrazí dialogové okno a umožňuje uživateli vybrat.|  
|[CPrintDialogEx::GetCopies](#getcopies)|Získá počet kopií požadovaný.|  
|[CPrintDialogEx::GetDefaults](#getdefaults)|Načte výchozí nastavení zařízení bez zobrazení dialogového okna.|  
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Načte název zařízení aktuálně vybrané tiskárny.|  
|[CPrintDialogEx::GetDevMode](#getdevmode)|Načte `DEVMODE` struktury.|  
|[CPrintDialogEx::GetDriverName](#getdrivername)|Načte název definovaných systémem ovladače zařízení.|  
|[CPrintDialogEx::GetPortName](#getportname)|Načte název portu aktuálně vybrané tiskárny.|  
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Načte popisovač kontextu zařízení tiskárny.|  
|[CPrintDialogEx::PrintAll](#printall)|Určuje, jestli se má vytisknout všechny stránky dokumentu.|  
|[CPrintDialogEx::PrintCollate](#printcollate)|Určuje, zda porovnávány kopie jsou požadovány.|  
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Určuje, jestli se má vytisknout aktuální stránku z dokumentu.|  
|[CPrintDialogEx::PrintRange](#printrange)|Určuje, jestli se má vytisknout zadaného rozsahu stránek.|  
|[CPrintDialogEx::PrintSelection](#printselection)|Určuje, jestli se má tisknout jen aktuálně vybrané položky.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPrintDialogEx::m_pdex](#m_pdex)|Struktura používané k úpravám `CPrintDialogEx` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete se spolehnout na rozhraní .NET framework pro zpracování mnoho aspektů proces tisku pro vaši aplikaci. Další informace o použití rozhraní pro zpracování tiskové úlohy, najdete v článku [tisk](../../mfc/printing.md).  
  
 Pokud chcete, aby aplikace zpracovávala tisk bez zapojení rozhraní framework, můžete použít `CPrintDialogEx` třídy pomocí konstruktoru určených "tak jak jsou", nebo lze odvodit vlastní třídy dialogového okna z `CPrintDialogEx` a zápis konstruktoru tak, aby odpovídala vašim potřebám. V obou případech se tyto dialogy se chovají jako standardní dialogová okna MFC vzhledem k tomu, že jsou odvozeny z třídy `CCommonDialog`.  
  
 Použití `CPrintDialogEx` objektu, musíte nejprve vytvořit objekt pomocí `CPrintDialogEx` konstruktoru. Jakmile byl vytvořen dialogových oken, můžete nastavit nebo změnit všechny hodnoty v [m_pdex](#m_pdex) struktura inicializace hodnot ovládacích prvků v dialogovém okně. `m_pdex` Struktury je typu [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844). Další informace o této struktuře naleznete v tématu Windows SDK.  
  
 Pokud nezadáte vlastní obslužných rutin v `m_pdex` pro `hDevMode` a `hDevNames` členy, nezapomeňte volat funkci Windows `GlobalFree` pro tyto manipulační body, jakmile budete hotovi s dialogovým oknem.  
  
 Po inicializaci ovládací prvky dialogového okna, zavolejte `DoModal` členské funkce k zobrazení dialogového okna a umožnit uživateli vybrat možnosti tisku. Když `DoModal` vrátí, můžete určit, zda uživatel vybral tlačítko OK, použít nebo zrušit.  
  
 Pokud uživatel stiskl OK, můžete použít `CPrintDialogEx`pro členské funkce načtete informace o vstup uživatele.  
  
 `CPrintDialogEx::GetDefaults` Členská funkce je užitečná pro získání aktuální výchozí nastavení tiskárny bez zobrazení dialogového okna. Tato metoda nevyžaduje žádný zásah uživatele.  
  
 Můžete použít Windows `CommDlgExtendedError` funkce k určení, zda došlo k chybě při inicializaci dialogového okna a další informace o této chybě. Další informace o této funkci najdete v tématu Windows SDK.  
  
 Další informace o používání `CPrintDialogEx`, naleznete v tématu [společné třídy dialogových oken](../../mfc/common-dialog-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `IObjectWithSite`  
  
 `IPrintDialogCallback`  
  
 [Ccommondialog –](../../mfc/reference/ccommondialog-class.md)  
  
 `CPrintDialogEx`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx  
 Sestaví seznam vlastností tisku Windows.  
  
```  
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *dwFlags*  
 Jeden nebo více příznaků, které vám umožní přizpůsobit nastavení dialogovém okně kombinované pomocí bitového operátoru OR. Například PD_ALLPAGES příznak nastaví výchozí rozsah tisku na všechny stránky dokumentu. Zobrazit [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) struktura v sadě Windows SDK pro další informace o těchto příznacích.  
  
 *pParentWnd*  
 Ukazatel na okno nadřazené nebo vlastník dialogových oken.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce pouze vytvoří objekt. Použití `DoModal` členské funkce k zobrazení dialogového okna.  
  
##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC  
 Vytvoří kontext zařízení tiskárny (DC) z [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) a [DEVNAMES –](../../mfc/reference/devnames-structure.md) struktury.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kontextu zařízení nově vytvořené tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Vrácený řadič domény je také uložena v `hDC` členem [m_pdex](#m_pdex).  
  
 Tento řadič domény je považován za aktuální tiskárny řadiče domény a jakýkoli jiný dříve získány tiskárny, řadiče domény musí být odstraněny. Tuto funkci lze volat a výsledné řadič domény používá bez někdy zobrazení dialogového okna Tisk.  
  
##  <a name="domodal"></a>  CPrintDialogEx::DoModal  
 Voláním této funkce zobrazí seznamem vlastností tisku Windows a umožní uživateli vybrat různé možnosti tisku, jako je například počet kopií, stránka rozsahu, a určuje, zda mají být kopie tříděny.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 INT_PTR návratové hodnoty je ve skutečnosti HRESULT. V části vrátit hodnoty v [PrintDlgEx](http://msdn.microsoft.com/library/windows/desktop/ms646942) v sadě Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete inicializovat různé možnosti dialogového okna Tisk nastavením členy `m_pdex` strukturu, je potřeba to udělat před voláním `DoModal`, ale po vytvoření objektu dialogového okna.  
  
 Po volání `DoModal`, můžete volat ostatní členské funkce k načtení nastavení nebo informace o vstup uživatelem do dialogových oken.  
  
 Pokud je příznak PD_RETURNDC použitá při volání metody `DoModal`, tiskárnu řadiče domény, vrátí se `hDC` členem [m_pdex](#m_pdex). Tento řadič domény musí být uvolněna voláním [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) volajícím funkce `CPrintDialogEx`.  
  
##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies  
 Voláním této funkce po volání `DoModal` načíst počet kopií požadovaný.  
  
```  
int GetCopies() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet kopií požadovaný.  
  
##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults  
 Voláním této funkce načtete výchozí tiskárny výchozí nastavení zařízení bez zobrazení dialogového okna.  
  
```  
BOOL GetDefaults();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 TRUE, pokud je úspěšná, jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoří kontext zařízení tiskárny (DC) z [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) a [DEVNAMES –](../../mfc/reference/devnames-structure.md) struktury.  
  
 `GetDefaults` nezobrazuje seznamem vlastností tisku. Místo toho se nastaví `hDevNames` a `hDevMode` členy [m_pdex](#m_pdex) do popisovače [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) a [DEVNAMES –](../../mfc/reference/devnames-structure.md) struktury, které jsou inicializovány pro výchozí tiskárna systému. Obě `hDevNames` a `hDevMode` musí mít hodnotu NULL, nebo `GetDefaults` selže.  
  
 Pokud je nastavený příznak PD_RETURNDC, tato funkce nebude vrátit pouze `hDevNames` a `hDevMode` (umístěné v `m_pdex.hDevNames` a `m_pdex.hDevMode`) volajícímu, ale také vrátí tiskárnu řadiče domény v `m_pdex.hDC`. Je odpovědností volajícího k odstranění tiskárny řadiče domény a volat Windows [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579) funkce s popisovači po dokončení se `CPrintDialogEx` objektu.  
  
##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName  
 Voláním této funkce po volání [DoModal](#domodal) načíst název aktuálně vybrané tiskárny, nebo po volání [GetDefaults](#getdefaults) načíst název výchozí tiskárna.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název vybrané tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Použít ukazatel `CString` vrácený `GetDeviceName` jako hodnotu `lpszDeviceName` ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode  
 Voláním této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) k načtení informací o tiskové zařízení.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) datová struktura, která obsahuje informace o inicializaci zařízení a prostředí, které ovladače tiskárny. Musíte odemknout paměť provedenou tato struktura se Windows [GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595) funkce, která je popsána v sadě Windows SDK.  
  
##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName  
 Voláním této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název definovaných systémem ovladače zařízení.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` určující název ovladače definovaná systémem.  
  
### <a name="remarks"></a>Poznámky  
 Použít ukazatel `CString` vrácený `GetDriverName` jako hodnotu *lpszDriverName* ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getportname"></a>  CPrintDialogEx::GetPortName  
 Voláním této funkce po volání [DoModal](#domodal) nebo [GetDefaults](#getdefaults) načíst název portu aktuálně vybrané tiskárny.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název portu aktuálně vybrané tiskárny.  
  
##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC  
 Vrátí popisovač do kontextu zařízení tiskárny.  
  
```  
HDC GetPrinterDC() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kontextu zařízení tiskárny.  
  
### <a name="remarks"></a>Poznámky  
 Je třeba zavolat Windows [DeleteDC](http://msdn.microsoft.com/library/windows/desktop/dd183533) funkce kontextu zařízení odstranit, po dokončení jeho použití.  
  
##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex  
 PRINTDLGEX struktura, jejíž členové uložení vlastnosti z objektu dialogového okna.  
  
```  
PRINTDLGEX m_pdex;  
```  
  
### <a name="remarks"></a>Poznámky  
 Po sestavení `CPrintDialogEx` objektu, můžete použít `m_pdex` nastavit různé aspekty dialogového okna před voláním [DoModal](#domodal) členskou funkci. Další informace o `m_pdex` struktury, přečtěte si téma [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) v sadě Windows SDK.  
  
 Pokud změníte `m_pdex` datový člen přímo, budou všechny výchozí chování přepsat.  
  
##  <a name="printall"></a>  CPrintDialogEx::PrintAll  
 Voláním této funkce po volání `DoModal` k určení, jestli se má vytisknout všechny stránky v dokumentu.  
  
```  
BOOL PrintAll() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 TRUE, pokud jsou všechny stránky v dokumentu, které se mají vytisknout; v opačném případě FALSE.  
  
##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate  
 Voláním této funkce po volání `DoModal` k určení, zda by měl tiskárny collate všechny vytištěných kopií dokumentu.  
  
```  
BOOL PrintCollate() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud uživatel vybere toto políčko, pokud v dialogovém okně. v opačném případě FALSE.  
  
##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage  
 Voláním této funkce po volání `DoModal` k určení, jestli se má vytisknout aktuální stránku v dokumentu.  
  
```  
BOOL PrintCurrentPage() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě **vytisknout aktuální stránku** je vybrané v dialogovém okně tisku; jinak hodnota FALSE.  
  
##  <a name="printrange"></a>  CPrintDialogEx::PrintRange  
 Voláním této funkce po volání `DoModal` k určení, jestli se má vytisknout pouze rozsah stránek v dokumentu.  
  
```  
BOOL PrintRange() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud pouze rozsahu stránek v dokumentu se mají vytisknout; v opačném případě FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Lze určit rozsahy zadanou stránku [m_pdex](#m_pdex) (naleznete v tématu `nPageRanges`, `nMaxPageRanges`, a `lpPageRanges` v [PRINTDLGEX](http://msdn.microsoft.com/library/windows/desktop/ms646844) struktura v sadě Windows SDK).  
  
##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection  
 Voláním této funkce po volání `DoModal` k určení, jestli se má tisknout jen aktuálně vybrané položky.  
  
```  
BOOL PrintSelection() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud pouze vybrané položky se mají vytisknout; v opačném případě FALSE.  
  
## <a name="see-also"></a>Viz také  
 [Ccommondialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CPrintInfo – struktura](../../mfc/reference/cprintinfo-structure.md)
