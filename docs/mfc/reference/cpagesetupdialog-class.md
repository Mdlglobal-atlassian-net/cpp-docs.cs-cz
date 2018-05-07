---
title: Třída CPageSetupDialog | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPageSetupDialog
- AFXDLGS/CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CreatePrinterDC
- AFXDLGS/CPageSetupDialog::DoModal
- AFXDLGS/CPageSetupDialog::GetDeviceName
- AFXDLGS/CPageSetupDialog::GetDevMode
- AFXDLGS/CPageSetupDialog::GetDriverName
- AFXDLGS/CPageSetupDialog::GetMargins
- AFXDLGS/CPageSetupDialog::GetPaperSize
- AFXDLGS/CPageSetupDialog::GetPortName
- AFXDLGS/CPageSetupDialog::OnDrawPage
- AFXDLGS/CPageSetupDialog::PreDrawPage
- AFXDLGS/CPageSetupDialog::m_psd
dev_langs:
- C++
helpviewer_keywords:
- CPageSetupDialog [MFC], CPageSetupDialog
- CPageSetupDialog [MFC], CreatePrinterDC
- CPageSetupDialog [MFC], DoModal
- CPageSetupDialog [MFC], GetDeviceName
- CPageSetupDialog [MFC], GetDevMode
- CPageSetupDialog [MFC], GetDriverName
- CPageSetupDialog [MFC], GetMargins
- CPageSetupDialog [MFC], GetPaperSize
- CPageSetupDialog [MFC], GetPortName
- CPageSetupDialog [MFC], OnDrawPage
- CPageSetupDialog [MFC], PreDrawPage
- CPageSetupDialog [MFC], m_psd
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cffe2d337d611dff0387805c99965c3c2e9ef87
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog – třída
Zapouzdří služeb poskytovaných běžných nastavení stránky OLE dialogové okno s dodatečnou podporou pro nastavení a úprava tisku okraje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CPageSetupDialog : public CCommonDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|Vytvoří `CPageSetupDialog` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Vytvoří kontext zařízení pro tisk.|  
|[CPageSetupDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožňuje vytvořit uživateli výběr.|  
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Vrátí název zařízení tiskárny.|  
|[CPageSetupDialog::GetDevMode](#getdevmode)|Vrátí aktuální `DEVMODE` tiskárny.|  
|[CPageSetupDialog::GetDriverName](#getdrivername)|Vrátí ovladače používané tiskárny.|  
|[CPageSetupDialog::GetMargins](#getmargins)|Vrátí aktuální nastavení okrajů tiskárny.|  
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Vrátí velikost papíru tiskárny.|  
|[CPageSetupDialog::GetPortName](#getportname)|Vrátí název portu výstup.|  
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Voláno rámcem Vykreslit obrázek obrazovky tištěných stránky.|  
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Voláno rámcem před vykreslování snímku obrazovky tištěných stránky.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPageSetupDialog::m_psd](#m_psd)|Struktura sloužící k přizpůsobení `CPageSetupDialog` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je navržené tak, aby na místě v dialogovém okně Nastavení tisku.  
  
 Použít `CPageSetupDialog` objektu, nejprve vytvořit objekt pomocí `CPageSetupDialog` konstruktor. Jakmile dialogové okno byl vytvořený, můžete nastavit nebo změnit všechny hodnoty v `m_psd` – datový člen k chybě při inicializaci hodnoty ovládací prvky dialogových oken. [M_psd](#m_psd) struktura je typu **PAGESETUPDLG**.  
  
 Po inicializaci ovládacím prvkům v dialogovém okně, volání `DoModal` – členská funkce a zobrazit dialogové okno Povolit uživateli vybrat možnosti tisku. `DoModal` Vrátí, zda uživatel vybral OK ( **IDOK**) nebo zrušit ( **IDCANCEL**) tlačítko.  
  
 Pokud `DoModal` vrátí **IDOK**, můžete použít několik `CPageSetupDialog`na členské funkce nebo přístup `m_psd` datový člen načíst informace o vstup uživatele.  
  
> [!NOTE]
>  Po běžných dialogových oken OLE stránky instalace se zruší, veškeré změny provedené uživatelem se neuloží rámcem. Je vlastní aplikace pro uložení všech hodnot z tohoto dialogového okna do trvalé umístění, jako je členem dokument aplikace nebo třídy aplikace.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CCommonDialog](../../mfc/reference/ccommondialog-class.md)  
  
 `CPageSetupDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="cpagesetupdialog"></a>  CPageSetupDialog::CPageSetupDialog  
 Volání této funkce můžete vytvořit `CPageSetupDialog` objektu.  
  
```  
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `dwFlags`  
 Jeden nebo více příznaky, které můžete použít k přizpůsobení nastavení dialogové okno. Hodnoty lze spojovat pomocí operátoru bitové operace OR. Tyto hodnoty mají následující významy:  
  
- **PSD_DEFAULTMINMARGINS** Nastaví minimální povolená šířek pro okraje stránky, aby byla stejná jako minimálních tiskárny. Tento příznak se ignoruje, pokud **PSD_MARGINS** a **PSD_MINMARGINS** příznaky jsou také zadány.  
  
- **PSD_INWININIINTLMEASURE** není implementováno.  
  
- **PSD_MINMARGINS** způsobí, že systém pomocí hodnoty zadané v **rtMinMargin** členem, jako minimální povolená šířek vlevo, horní, pravé a dolní okraj. Systém zabrání uživateli zadat šířku, která je menší než zadaná minimální. Pokud **PSD_MINMARGINS** není zadán, systém Nastaví minimální povolená šířky k těm, jejichž tiskárny.  
  
- **PSD_MARGINS** aktivuje oblast ovládacího prvku okraje.  
  
- **PSD_INTHOUSANDTHSOFINCHES** způsobí, že jednotky dialogu měřenou v 1/1000 palce.  
  
- **PSD_INHUNDREDTHSOFMILLIMETERS** způsobí, že jednotky dialogu měřenou v 1/100 milimetru.  
  
- **PSD_DISABLEMARGINS** zakáže dialogové okno pole okrajů.  
  
- **PSD_DISABLEPRINTER** zakáže tlačítko tiskárny.  
  
- **PSD_NOWARNING** brání upozornění v případě, že neexistuje žádný výchozí tiskárny.  
  
- **PSD_DISABLEORIENTATION** zakáže dialogu řízení orientace stránky.  
  
- **PSD_RETURNDEFAULT** způsobí, že `CPageSetupDialog` vrátit [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) a [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury, které jsou inicializovány tiskárny výchozí systému bez zobrazení dialogového okna. Předpokládá se, že oba **hDevNames je** a **hDevMode** jsou **NULL**, jinak funkce vrátí chybu. Pokud výchozí tiskárna systému je podporovaná staré ovladače tiskárny (starší než Windows verze 3.0), pouze **hDevNames je** je vrácen; **hDevMode** je **NULL**.  
  
- **PSD_DISABLEPAPER** zakáže ovládacího prvku pro výběr dokumentu.  
  
- **PSD_SHOWHELP** způsobí, že dialogovém se zobrazí na tlačítko Nápověda. **HwndOwner** nesmí být člen **NULL** případného tento příznak.  
  
- **PSD_ENABLEPAGESETUPHOOK** umožňuje funkce háku určené v **lpfnSetupHook**.  
  
- **PSD_ENABLEPAGESETUPTEMPLATE** způsobí, že operační systém dialogové okno vytvořit pomocí šablony dialogového identifikovaný **hInstance** a **lpSetupTemplateName**.  
  
- **PSD_ENABLEPAGESETUPTEMPLATEHANDLE** znamená, že **hInstance** identifikuje datový blok, který obsahuje šablony pole předem načtené dialogového okna. Systém ignoruje **lpSetupTemplateName** případného tento příznak.  
  
- **PSD_ENABLEPAGEPAINTHOOK** umožňuje funkce háku určené v **lpfnPagePaintHook**.  
  
- **PSD_DISABLEPAGEPAINTING** zakáže oblasti kreslení dialogového okna.  
  
 `pParentWnd`  
 Ukazatel na nadřazené nebo vlastníka dialogových oken.  
  
### <a name="remarks"></a>Poznámky  
 Použití [DoModal](../../mfc/reference/cdialog-class.md#domodal) funkce, která se zobrazí dialogové okno.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]  
  
##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC  
 Vytvoří z kontextu zařízení tiskárny [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) a [DEVNAMES](../../mfc/reference/devnames-structure.md) struktury.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Zpracování do nově vytvořené tiskárny kontextu zařízení (DC).  
  
##  <a name="domodal"></a>  CPageSetupDialog::DoModal  
 Volání této funkce a zobrazit dialogové okno nastavení stránky OLE Windows běžné uživateli umožní vybrat různé možnosti tisku instalace například tisk okraje, velikosti a orientace papíru a cílové tiskárny.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **IDOK** nebo **IDCANCEL**. Pokud **IDCANCEL** je vrácen, volání Windows [CommDlgExtendedError](http://msdn.microsoft.com/library/windows/desktop/ms646916) funkce k určení, zda došlo k chybě.  
  
 **IDOK** a **IDCANCEL** jsou konstanty, které označuje, zda uživatel vybrané na tlačítko OK nebo Storno.  
  
### <a name="remarks"></a>Poznámky  
 Kromě toho má uživatel přístup možnosti instalace tiskárny, jako je umístění v síti a vlastnosti specifické pro vybrané tiskárny.  
  
 Pokud chcete k chybě při inicializaci různé dialogové okno Možnosti nastavení stránky nastavením členy `m_psd` struktura, měli byste tak učinit před voláním `DoModal`, a poté, co je vytvořený objektu dialogového okna. Po volání `DoModal`, volat jiné členské funkce pro načtení nastavení nebo uživatelský vstup informace do dialogového okna.  
  
 Pokud chcete rozšířit aktuální nastavení zadá uživatel, ujistěte se, volání [CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Tato funkce přebírá informace z `CPageSetupDialog` objektu a inicializuje a vybere nové tiskárny řadič domény s správné atributy.  
  
 [!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).  
  
##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName  
 Volání této funkce po `DoModal` získávání názvu aktuálně vybrané tiskárny.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název zařízení, které jsou používané **CPageSetupDialog** objektu.  
  
##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode  
 Volání této funkce po volání `DoModal` k načtení informací o kontextu zařízení tiskárny `CPageSetupDialog` objektu.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) datová struktura, která obsahuje informace o zařízení inicializace a prostředí ovladače tiskárny. Je třeba odemknout paměť provedenou tuto strukturu s Windows [GlobalUnlock](http://msdn.microsoft.com/library/windows/desktop/aa366595) funkce, která je popsána v sadě Windows SDK.  
  
##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName  
 Volání této funkce po volání [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) načíst název definované systémem ovladače zařízení.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` zadání názvu ovladače definovaná systémem.  
  
### <a name="remarks"></a>Poznámky  
 Použijte odkazy `CString` objekt vrácený `GetDriverName` jako hodnotu `lpszDriverName` ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins  
 Volání této funkce po volání `DoModal` načíst okraje ovladače zařízení.  
  
```  
void GetMargins(
    LPRECT lpRectMargins,  
    LPRECT lpRectMinMargins) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpRectMargins*  
 Ukazatel na [Rect –](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us) struktura nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který popisuje (v palcích 1 nebo 1 000 nebo mm 1/100) okraje tisku pro aktuálně vybrané tiskárny. Předat **NULL** pro tento parametr, pokud vás zajímá není v obdélníku.  
  
 *lpRectMinMargins*  
 Ukazatel na `RECT` struktura nebo `CRect` objekt, který popisuje minimální okraje tisku pro aktuálně vybrané tiskárny (v palcích 1 nebo 1 000 nebo mm 1/100). Předat **NULL** pro tento parametr, pokud vás zajímá není v obdélníku.  
  
##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize  
 Volání této funkce načíst velikost papíru vybrané pro tisk.  
  
```  
CSize GetPaperSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt obsahující velikost papíru (v palcích 1 nebo 1 000 nebo mm 1/100) vybraný pro tisk.  
  
##  <a name="getportname"></a>  CPageSetupDialog::GetPortName  
 Volání této funkce po volání `DoModal` načíst název portu aktuálně vybrané tiskárny.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název portu aktuálně vybrané tiskárny.  
  
##  <a name="m_psd"></a>  CPageSetupDialog::m_psd  
 Struktura typu **PAGESETUPDLG**, jejíž členové uložení charakteristiky objektu dialogového okna.  
  
```  
PAGESETUPDLG m_psd;  
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření `CPageSetupDialog` objekt, můžete použít `m_psd` nastavit různé aspekty dialogu před voláním `DoModal` – členská funkce.  
  
 Pokud změníte `m_psd` – datový člen přímo, přepíše jakékoli výchozí chování.  
  
 Další informace o [PAGESETUPDLG](http://msdn.microsoft.com/library/windows/desktop/ms646842) struktury, najdete v části Windows SDK.  
  
 Podívejte se na příklad pro [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).  
  
##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage  
 Voláno rámcem k vykreslení snímku obrazovky tištěných stránky.  
  
```  
virtual UINT OnDrawPage(
    CDC* pDC,  
    UINT nMessage,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na kontext zařízení tiskárny.  
  
 `nMessage`  
 Určuje zprávu, s upozorněním oblast stránky aktuálně přitahuje. Může být jedna z následujících akcí:  
  
- **WM_PSD_FULLPAGERECT** oblasti celou stránku.  
  
- **WM_PSD_MINMARGINRECT** aktuální minimální okraje.  
  
- **WM_PSD_MARGINRECT** aktuální okraje.  
  
- **WM_PSD_GREEKTEXTRECT** obsah stránky.  
  
- **WM_PSD_ENVSTAMPRECT** oblasti vyhrazené pro znázornění známka.  
  
- **WM_PSD_YAFULLPAGERECT** oblast pro znázornění zpáteční adresu. Tato oblast rozšiřuje s okraji oblasti ukázkové stránky.  
  
 `lpRect`  
 Ukazatel na [CRect](../../atl-mfc-shared/reference/crect-class.md) nebo [Rect –](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us) objekt obsahující souřadnice oblasti výkresu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulovou hodnotu, pokud jsou zpracovávány; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 V rámci běžných dialogových oken OLE stránky instalace se následně zobrazí tuto bitovou kopii. Výchozí implementace nakreslí obrázek stránku textu.  
  
 Přepsání této funkci můžete přizpůsobit kreslení konkrétní oblasti bitovou kopii nebo celého obrázku. Můžete to provést pomocí `switch` příkaz s **případ** příkazy kontrolou hodnoty `nMessage`. Chcete-li přizpůsobit vykreslování obsahu stránce bitové kopie, můžete například použít následující příklad kódu:  
  
 [!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]  
  
 Všimněte si, že není nutné pro zpracování každé malá `nMessage`. Můžete pro zpracování jedna součást bitové kopie, několik součástí bitovou kopii, nebo celou oblast.  
  
##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage  
 Voláno rámcem před kreslení obrazovky bitové kopie na tištěných stránce.  
  
```  
virtual UINT PreDrawPage(
    WORD wPaper,  
    WORD wFlags,  
    LPPAGESETUPDLG pPSD);
```  
  
### <a name="parameters"></a>Parametry  
 *wPaper*  
 Určuje hodnotu, která určuje velikost papíru. Tato hodnota může být jedna z **DMPAPER_** hodnoty uvedené v popis [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) struktura.  
  
 `wFlags`  
 Označuje orientace papíru nebo obálky, a jestli je tiskárna maticové nebo zařízení HPPCL (jazyk pro ovládací prvek Hewlett Packard tiskárny). Tento parametr může mít jednu z následujících hodnot:  
  
-   0x001 papír v režimu na šířku (tečka matice)  
  
-   0x003 papír v režimu na šířku (HPPCL)  
  
-   0x005 papír v režimu na výšku (tečka matice)  
  
-   0x007 papír v režimu na výšku (HPPCL)  
  
-   0x00b obálky v režimu na šířku (HPPCL)  
  
-   0x00d obálky v režimu na výšku (tečka matice)  
  
-   0x019 obálky v režimu na šířku (tečka matice)  
  
-   0x01f obálky v režimu na výšku (tečka matice)  
  
 `pPSD`  
 Ukazatel na **PAGESETUPDLG** struktury. Další informace o [PAGESETUPDLG](http://msdn.microsoft.com/library/windows/desktop/ms646842), najdete v části Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulovou hodnotu, pokud jsou zpracovávány; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkci můžete přizpůsobit kreslení obrázku. Vrátí funkci přepsat a **TRUE**, musí kreslení celého obrázku. Vrátí funkci přepsat a **FALSE**, celý výchozí image vykreslením rámcem.  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC WORDPAD](../../visual-cpp-samples.md)   
 [CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



