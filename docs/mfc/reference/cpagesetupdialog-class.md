---
title: Cpagesetupdialog – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: c134d2e1dc6f3782446afc57b8384279a615e86f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197454"
---
# <a name="cpagesetupdialog-class"></a>Cpagesetupdialog – třída
Zapouzdřuje služby poskytované dialogovým oknem běžných nastavení stránky OLE Windows s další podporou nastavení a úprav okrajů tisku.  
  
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
|[CPageSetupDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožňuje vytvořit uživatele s výběrem.|  
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Vrátí název zařízení tiskárny.|  
|[CPageSetupDialog::GetDevMode](#getdevmode)|Vrátí aktuální DEVMODE tiskárny.|  
|[CPageSetupDialog::GetDriverName](#getdrivername)|Vrátí bude ovladač používaný tiskárny.|  
|[CPageSetupDialog::GetMargins](#getmargins)|Vrátí aktuální nastavení okrajů tiskárny.|  
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Vrátí velikost papíru tiskárny.|  
|[CPageSetupDialog::GetPortName](#getportname)|Vrátí název výstupního portu.|  
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Volá se rozhraním, aby se vykreslil obraz tištěné stránky.|  
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Volá se rozhraním, před vykreslením obraz tištěné stránky.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CPageSetupDialog::m_psd](#m_psd)|Struktura používané k úpravám `CPageSetupDialog` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída je navržené tak, aby místo dialogovém okně Nastavení tisku.  
  
 Použití `CPageSetupDialog` objektu, musíte nejprve vytvořit objekt pomocí `CPageSetupDialog` konstruktoru. Jakmile byl vytvořen dialogových oken, můžete nastavit nebo změnit všechny hodnoty v `m_psd` datový člen inicializace hodnot ovládacích prvků v dialogovém okně. [M_psd](#m_psd) struktury je typu PAGESETUPDLG.  
  
 Po inicializaci ovládací prvky dialogového okna, zavolejte `DoModal` členské funkce k zobrazení dialogového okna a umožnit uživateli vybrat možnosti tisku. `DoModal` Vrátí, zda uživatel vybral tlačítko OK (IDOK) nebo zrušit (IDCANCEL).  
  
 Pokud `DoModal` vrátí IDOK, můžete použít několik `CPageSetupDialog`pro členské funkce nebo přístup `m_psd` datový člen načíst informace o vstup uživatele.  
  
> [!NOTE]
>  Po běžných dialogových oken OLE stránky instalace je zrušená, neuloží se rozhraním, všechny změny provedené uživatelem. Je až po samotné aplikace chcete-li uložit všechny hodnoty z tohoto dialogového okna do trvalého umístění, jako je například člen třídy aplikace nebo aplikace dokument.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [Ccommondialog –](../../mfc/reference/ccommondialog-class.md)  
  
 `CPageSetupDialog`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdlgs.h  
  
##  <a name="cpagesetupdialog"></a>  CPageSetupDialog::CPageSetupDialog  
 Voláním této funkce k vytvoření `CPageSetupDialog` objektu.  
  
```  
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,  
    CWnd* pParentWnd = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *dwFlags*  
 Jeden nebo více příznaků, které vám umožní přizpůsobit nastavení dialogového okna. Hodnoty lze spojovat pomocí operátoru bitového operátoru OR. Tyto hodnoty mají následující význam:  
  
- PSD_DEFAULTMINMARGINS Nastaví minimální šířku povolená pro okraje stránky patřit tiskárny minima. Tento příznak se ignoruje, pokud jsou také uvedeny příznaky PSD_MARGINS a PSD_MINMARGINS.  
  
- PSD_INWININIINTLMEASURE není implementována.  
  
- PSD_MINMARGINS způsobí, že systém použít hodnoty uvedené v `rtMinMargin` člena jako minimální povolená šířku doleva, horní, pravé a dolní okraj. Systém znemožní uživateli zadat šířku, která je nižší než zadané minimum. Pokud není zadán PSD_MINMARGINS, systém Nastaví minimální šířka povolená těm tiskárna.  
  
- PSD_MARGINS aktivuje oblast okraje ovládacího prvku.  
  
- PSD_INTHOUSANDTHSOFINCHES způsobí, že jednotky dialogu měřený v 1/1 000 palce.  
  
- PSD_INHUNDREDTHSOFMILLIMETERS způsobí, že jednotky dialogu měřený v 1/100 milimetru.  
  
- PSD_DISABLEMARGINS zakáže ovládací prvky dialogového okna pole okraj.  
  
- PSD_DISABLEPRINTER zakáže tlačítko tiskárna.  
  
- PSD_NOWARNING zabraňuje upozornění se zobrazí, když není žádná výchozí tiskárna.  
  
- PSD_DISABLEORIENTATION zakáže ovládací prvek dialogového okna orientace stránky.  
  
- Způsobí, že PSD_RETURNDEFAULT `CPageSetupDialog` vrátit [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) a [DEVNAMES –](../../mfc/reference/devnames-structure.md) struktury, které jsou inicializovány pro výchozí tiskárna systému bez zobrazení dialogového okna. Předpokládá se, jak `hDevNames` a `hDevMode` hodnotu Null; v opačném případě vrátí chybu. Pokud se výchozí tiskárna systému je podporována staré ovladače tiskárny (dřívější než Windows verze 3.0), pouze `hDevNames` je vrácena. `hDevMode` má hodnotu NULL.  
  
- PSD_DISABLEPAPER zakáže ovládacího prvku pro výběr dokumentu.  
  
- PSD_SHOWHELP způsobí, že dialogovém okně zobrazeno tlačítko Nápověda. `hwndOwner` Člen nesmí mít hodnotu NULL, pokud je tento příznak zadán.  
  
- PSD_ENABLEPAGESETUPHOOK umožňuje funkci připojení zadaný v `lpfnSetupHook`.  
  
- PSD_ENABLEPAGESETUPTEMPLATE způsobí, že operační systém dialogové okno vytvořit pomocí šablony dialogového identifikovaný `hInstance` a `lpSetupTemplateName`.  
  
- PSD_ENABLEPAGESETUPTEMPLATEHANDLE znamená, že `hInstance` identifikuje blok dat, který obsahuje šablony předem dialogového okna. Systém ignoruje `lpSetupTemplateName` Pokud je tento příznak zadán.  
  
- PSD_ENABLEPAGEPAINTHOOK umožňuje funkci připojení zadaný v `lpfnPagePaintHook`.  
  
- PSD_DISABLEPAGEPAINTING zakáže vystavení oblasti dialogového okna.  
  
 *pParentWnd*  
 Ukazatel na nadřazenou nebo vlastník dialogových oken.  
  
### <a name="remarks"></a>Poznámky  
 Použití [DoModal](../../mfc/reference/cdialog-class.md#domodal) funkce k zobrazení dialogového okna.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]  
  
##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC  
 Vytvoří kontext zařízení tiskárny ze [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) a [DEVNAMES –](../../mfc/reference/devnames-structure.md) struktury.  
  
```  
HDC CreatePrinterDC();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kontextu zařízení nově vytvořené tiskárny (DC).  
  
##  <a name="domodal"></a>  CPageSetupDialog::DoModal  
 Voláním této funkce Zobrazit dialogové okno nastavení stránky OLE Windows běžné a umožnit uživateli vybrat různé možnosti nastavení tisku, jako je například okraje pro tisk, velikosti a orientace papíru a cílovou tiskárnu.  
  
```  
virtual INT_PTR DoModal();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 IDOK nebo IDCANCEL. Pokud je vrácena IDCANCEL, zavolejte Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) funkce k určení, zda došlo k chybě.  
  
 IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel vybral tlačítko OK nebo zrušit.  
  
### <a name="remarks"></a>Poznámky  
 Kromě toho má uživatel přístup možnosti nastavení tiskárny, jako je umístění v síti a vlastnosti specifické pro vybrané tiskárny.  
  
 Pokud chcete inicializovat různé možnosti nastavení stránky dialogového okna tak, že nastavíte členy `m_psd` strukturu, měli byste tak činit před voláním `DoModal`, a po vytvoření objektu dialogového okna. Po volání `DoModal`, volat ostatní členské funkce k načtení nastavení nebo informace o vstup uživatelem do dialogových oken.  
  
 Pokud chcete rozšířit aktuální nastavení zadá uživatel, proveďte volání [CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Tato funkce přebírá informace z `CPageSetupDialog` objektu a inicializuje a vybere nové tiskárny řadič domény pomocí vlastních atributech.  
  
 [!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).  
  
##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName  
 Voláním této funkce po `DoModal` načíst název aktuálně vybrané tiskárny.  
  
```  
CString GetDeviceName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název zařízení, které se používají `CPageSetupDialog` objektu.  
  
##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode  
 Voláním této funkce po volání `DoModal` k načtení informací o kontextu zařízení tiskárny `CPageSetupDialog` objektu.  
  
```  
LPDEVMODE GetDevMode() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) datová struktura, která obsahuje informace o inicializaci zařízení a prostředí, které ovladače tiskárny. Musíte odemknout paměť provedenou tato struktura se Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) funkce, která je popsána v sadě Windows SDK.  
  
##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName  
 Voláním této funkce po volání [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) načíst název definovaných systémem ovladače zařízení.  
  
```  
CString GetDriverName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` určující název ovladače definovaná systémem.  
  
### <a name="remarks"></a>Poznámky  
 Použít ukazatel `CString` vrácený `GetDriverName` jako hodnotu `lpszDriverName` ve volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).  
  
##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins  
 Voláním této funkce po volání `DoModal` načíst okraje ovladač zařízení.  
  
```  
void GetMargins(
    LPRECT lpRectMargins,  
    LPRECT lpRectMinMargins) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpRectMargins*  
 Ukazatel [RECT](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us) struktury nebo [crect –](../../atl-mfc-shared/reference/crect-class.md) objekt, který popisuje (v palcích 1/1 000 nebo 1/100 mm) okrajů tisku pro aktuálně vybrané tiskárny. Pro tento parametr předejte hodnotu NULL, pokud vás nezajímají v obdélníku.  
  
 *lpRectMinMargins*  
 Ukazatel `RECT` struktury nebo `CRect` objekt, který popisuje (v palcích 1/1 000 nebo 1/100 mm) minimální okrajů tisku pro aktuálně vybrané tiskárny. Pro tento parametr předejte hodnotu NULL, pokud vás nezajímají v obdélníku.  
  
##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize  
 Voláním této funkce načtete velikosti papíru vybraná pro tisk.  
  
```  
CSize GetPaperSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) objekt, který obsahuje formát papíru (v palcích 1/1 000 nebo 1/100 mm) vybraný pro tisk.  
  
##  <a name="getportname"></a>  CPageSetupDialog::GetPortName  
 Voláním této funkce po volání `DoModal` načíst název portu aktuálně vybrané tiskárny.  
  
```  
CString GetPortName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název portu aktuálně vybrané tiskárny.  
  
##  <a name="m_psd"></a>  CPageSetupDialog::m_psd  
 Struktura typu PAGESETUPDLG, jejíž členové uložení vlastnosti z objektu dialogového okna.  
  
```  
PAGESETUPDLG m_psd;  
```  
  
### <a name="remarks"></a>Poznámky  
 Po sestavení `CPageSetupDialog` objektu, můžete použít `m_psd` nastavit různé aspekty dialogového okna před voláním `DoModal` členskou funkci.  
  
 Pokud změníte `m_psd` datový člen přímo, budou všechny výchozí chování přepsat.  
  
 Další informace o [PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda) struktury, naleznete v sadě Windows SDK.  
  
 Podívejte se na příklad pro [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).  
  
##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage  
 Volá se rozhraním, chcete-li nakreslit obraz tištěné stránky.  
  
```  
virtual UINT OnDrawPage(
    CDC* pDC,  
    UINT nMessage,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 *primární řadič domény*  
 Ukazatel na kontext zařízení tiskárny.  
  
 *nZpráva*  
 Určuje zprávu, s upozorněním oblasti na stránce se vykreslí. Může být jedna z následujících akcí:  
  
- WM_PSD_FULLPAGERECT oblasti celou stránku.  
  
- WM_PSD_MINMARGINRECT aktuální minimální okraje.  
  
- Aktuální WM_PSD_MARGINRECT okraje.  
  
- WM_PSD_GREEKTEXTRECT obsah stránky.  
  
- WM_PSD_ENVSTAMPRECT oblasti vyhrazené pro reprezentaci známka.  
  
- WM_PSD_YAFULLPAGERECT oblast pro reprezentaci návratovou hodnotu. Tato oblast se rozšiřuje na okraji oblasti ukázkové stránky.  
  
 *lprect –*  
 Ukazatel [crect –](../../atl-mfc-shared/reference/crect-class.md) nebo [RECT](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us) objekt, který obsahuje souřadnice oblasti pro kreslení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulová hodnota, pokud zpracovává; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato image se následně zobrazí jako součást běžné dialogových oken OLE stránku nastavení. Výchozí implementace nakreslí obrázek stránky textu.  
  
 Přepsání této funkce můžete přizpůsobit kreslení určitou oblast obrázku nebo celého obrázku. Můžete to provést pomocí **přepnout** příkazem **případ** příkazy kontrolou hodnoty *nZpráva*. Například pro přizpůsobení vykreslování obsahu stránky image, můžete použít následující příklad kódu:  
  
 [!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]  
  
 Všimněte si, že není potřeba zpracovávat každý případ *nZpráva*. Můžete pro zpracování jedné ze součástí bitové kopie, několik součástí image nebo celou oblast.  
  
##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage  
 Volá se rozhraním před kreslením obraz tištěné stránky.  
  
```  
virtual UINT PreDrawPage(
    WORD wPaper,  
    WORD wFlags,  
    LPPAGESETUPDLG pPSD);
```  
  
### <a name="parameters"></a>Parametry  
 *wPaper*  
 Určuje hodnotu, která určuje velikost papíru. Tato hodnota může být jedna z **DMPAPER_** hodnoty uvedené v popisu [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) struktury.  
  
 *wFlags*  
 Určuje orientaci ovládacího prvku dokument nebo obálky, a jestli je tiskárna jehličkové nebo zařízení HPPCL (jazyk pro ovládací prvek Hewlett Packard tiskárny). Tento parametr může mít jednu z následujících hodnot:  
  
-   0x001 papír v režimu na šířku (jehličkové tiskárny)  
  
-   0x003 papír v režimu na šířku (HPPCL)  
  
-   0x005 papír v režimu na výšku (jehličkové tiskárny)  
  
-   0x007 papír v režimu na výšku (HPPCL)  
  
-   0x00b Obálka v režimu na šířku (HPPCL)  
  
-   0x00d Obálka v režimu na výšku (jehličkové tiskárny)  
  
-   0x019 Obálka v režimu na šířku (jehličkové tiskárny)  
  
-   0x01f Obálka v režimu na výšku (jehličkové tiskárny)  
  
 *pPSD*  
 Ukazatel `PAGESETUPDLG` struktury. Další informace o [PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda), naleznete v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulová hodnota, pokud zpracovává; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkce můžete přizpůsobit kreslení obrázku. Je-li přepsat tuto funkci a vrátí hodnotu TRUE, musí vykreslení celého obrázku. Je-li přepsat tuto funkci a vrátí hodnotu FALSE, je celý výchozí image vykreslené rozhraní framework.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky knihovny MFC WORDPAD](../../visual-cpp-samples.md)   
 [Ccommondialog – třída](../../mfc/reference/ccommondialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



