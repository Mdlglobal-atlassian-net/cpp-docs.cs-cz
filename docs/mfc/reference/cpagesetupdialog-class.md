---
title: CPageSetupDialog – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 3664149ef0d7476b460ef06cddaf2b8145ade701
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753684"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog – třída

Zapouzdřuje služby poskytované běžným oknem Nastavení stránky OLE v systému Windows s další podporou nastavení a úpravtiskových okrajů.

## <a name="syntax"></a>Syntaxe

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|Vytvoří `CPageSetupDialog` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Vytvoří kontext zařízení pro tisk.|
|[CPageSetupDialog::DoModální](#domodal)|Zobrazí dialogové okno a umožní uživateli provést výběr.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Vrátí název zařízení tiskárny.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Vrátí aktuální funkce DEVMODE tiskárny.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Vrátí ovladač používaný tiskárnou.|
|[CPageSetupDialog::GetMargins](#getmargins)|Vrátí aktuální nastavení okrajů tiskárny.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Vrátí velikost papíru tiskárny.|
|[CPageSetupDialog::GetPortName](#getportname)|Vrátí název výstupního portu.|
|[cPageSetupDialog::OndrawPage](#ondrawpage)|Volat rámci k vykreslení obraz obrazovky tištěné stránky.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Volat rámci před vykreslením obraz obrazovky tištěné stránky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Struktura slouží k `CPageSetupDialog` přizpůsobení objektu.|

## <a name="remarks"></a>Poznámky

Tato třída je navržena tak, aby převzala místo dialogového okna Nastavení tisku.

Chcete-li `CPageSetupDialog` použít objekt, nejprve `CPageSetupDialog` vytvořte objekt pomocí konstruktoru. Po vytvoření dialogového okna můžete nastavit nebo upravit libovolné `m_psd` hodnoty v datovém členu tak, aby inicializovaly hodnoty ovládacích prvků dialogového okna. Struktura [m_psd](#m_psd) je typu PAGESETUPDLG.

Po inicializaci ovládacích `DoModal` prvků dialogového okna zavolejte členské funkce, aby zobrazila dialogové okno a umožnila uživateli vybrat možnosti tisku. `DoModal`vrátí, zda uživatel zvolil tlačítko OK (IDOK) nebo Cancel (IDCANCEL).

Pokud `DoModal` vrátí Hodnotu IDOK, `CPageSetupDialog`můžete k načtení `m_psd` informací vstupů uživatele použít několik členských funkcí společnosti nebo získat přístup k datovému členu.

> [!NOTE]
> Po zavření společného dialogového okna Nastavení stránky OLE nebudou všechny změny provedené uživatelem v rámci uloženy. Je na samotné aplikaci uložit všechny hodnoty z tohoto dialogového okna do trvalého umístění, jako je například člen dokumentu aplikace nebo třídy aplikace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

## <a name="cpagesetupdialogcpagesetupdialog"></a><a name="cpagesetupdialog"></a>CPageSetupDialog::CPageSetupDialog

Volání této funkce `CPageSetupDialog` k vytvoření objektu.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Jeden nebo více příznaků, které můžete použít k přizpůsobení nastavení dialogového okna. Hodnoty lze kombinovat pomocí operátoru Bitwise-OR. Tyto hodnoty mají následující význam:

- PSD_DEFAULTMINMARGINS Nastaví minimální přípustné šířky okrajů stránky tak, aby byly stejné jako minima tiskárny. Tento příznak je ignorován, pokud jsou také zadány příznaky PSD_MARGINS a PSD_MINMARGINS.

- PSD_INWININIINTLMEASURE není implementováno.

- PSD_MINMARGINS Způsobí, že systém použít `rtMinMargin` hodnoty zadané v členu jako minimální přípustné šířky pro levé, horní, pravé a dolní okraje. Systém zabrání uživateli zadat šířku, která je menší než zadané minimum. Pokud není zadán PSD_MINMARGINS, systém nastaví minimální přípustné šířky na šířku povolenou tiskárnou.

- PSD_MARGINS Aktivuje oblast kontroly okrajů.

- PSD_INTHOUSANDTHSOFINCHES Způsobí, že jednotky dialogového okna, které mají být měřeny v 1/1000 palce.

- PSD_INHUNDREDTHSOFMILLIMETERS Způsobí, že jednotky dialogového okna budou měřeny v 1/100 milimetru.

- PSD_DISABLEMARGINS Zakáže ovládací prvky dialogového okna okraje.

- PSD_DISABLEPRINTER Zakáže tlačítko Tiskárna.

- PSD_NOWARNING Zabrání zobrazení varovné zprávy, pokud neexistuje žádná výchozí tiskárna.

- PSD_DISABLEORIENTATION Zakáže ovládací prvek dialogového okna orientace stránky.

- PSD_RETURNDEFAULT `CPageSetupDialog` Způsobí, že vrátí [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) struktury, které jsou inicializovány pro výchozí tiskárnu systému bez zobrazení dialogového okna. Předpokládá se, `hDevNames` že `hDevMode` oba a jsou NULL; v opačném případě vrátí funkce chybu. Pokud je výchozí systémová tiskárna podporována starým ovladačem tiskárny (starší než Windows verze 3.0), je vrácena pouze `hDevNames` možnost. `hDevMode` je null.

- PSD_DISABLEPAPER Zakáže ovládací prvek výběru papíru.

- PSD_SHOWHELP Způsobí, že se v dialogovém okně zobrazí tlačítko Nápověda. Člen `hwndOwner` nesmí být NULL, pokud je zadán tento příznak.

- PSD_ENABLEPAGESETUPHOOK Povolí funkci háku určenou v aplikaci `lpfnSetupHook`.

- PSD_ENABLEPAGESETUPTEMPLATE Způsobí, že operační systém vytvoří dialogové okno pomocí `hInstance` `lpSetupTemplateName`dialogového okna šablony určeného písmenem a .

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE Označuje, že `hInstance` identifikuje datový blok, který obsahuje přednastavenou šablonu dialogového okna. Systém ignoruje, `lpSetupTemplateName` pokud je tento příznak zadán.

- PSD_ENABLEPAGEPAINTHOOK Povolí funkci háku určenou v aplikaci `lpfnPagePaintHook`.

- PSD_DISABLEPAGEPAINTING Zakáže oblast kreslení v dialogovém okně.

*pParentWnd*<br/>
Ukazatel na nadřazeného nebo vlastníka dialogového okna.

### <a name="remarks"></a>Poznámky

Dialogové okno se zobrazí pomocí funkce [DoModal.](../../mfc/reference/cdialog-class.md#domodal)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

## <a name="cpagesetupdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPageSetupDialog::CreatePrinterDC

Vytvoří kontext zařízení tiskárny ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Návratová hodnota

Zpracovat nově vytvořený kontext zařízení tiskárny (DC).

## <a name="cpagesetupdialogdomodal"></a><a name="domodal"></a>CPageSetupDialog::DoModální

Voláním této funkce zobrazíte dialogové okno Nastavení společné ho prostředí OLE v systému Windows a umožníte uživateli vybrat různé možnosti nastavení tisku, jako jsou okraje tisku, velikost a orientace papíru a cílová tiskárna.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud je vrácena funkce IDCANCEL, zavolejte funkci Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) a zjistěte, zda došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel zvolil tlačítko OK nebo Cancel.

### <a name="remarks"></a>Poznámky

Kromě toho má uživatel přístup k možnostem nastavení tiskárny, jako je umístění v síti a vlastnosti specifické pro vybranou tiskárnu.

Chcete-li inicializovat různé možnosti dialogového okna `m_psd` Vzhled stránky nastavením `DoModal`členů struktury, měli byste tak učinit před voláním a po vytvoření objektu dialogového okna. Po `DoModal`volání volejte další členské funkce a načtěte nastavení nebo informace vstupující uživatelem do dialogového okna.

Chcete-li šířit aktuální nastavení zadaná uživatelem, zavolejte na [CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Tato funkce přebírá informace `CPageSetupDialog` z objektu a inicializuje a vybere novou tiskárnu DC se správnými atributy.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Příklad

  Viz příklad [cPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

## <a name="cpagesetupdialoggetdevicename"></a><a name="getdevicename"></a>CPageSetupDialog::GetDeviceName

Volání této `DoModal` funkce po načíst název aktuálně vybrané tiskárny.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název zařízení používaný `CPageSetupDialog` objektem.

## <a name="cpagesetupdialoggetdevmode"></a><a name="getdevmode"></a>CPageSetupDialog::GetDevMode

Volání této funkce `DoModal` po volání načíst informace `CPageSetupDialog` o kontextu zařízení tiskárny objektu.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Datová struktura [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) která obsahuje informace o inicializaci zařízení a prostředí tiskového ovladače. Je nutné odemknout paměť převzatou touto strukturou pomocí funkce Windows [GlobalUnlock,](/windows/win32/api/winbase/nf-winbase-globalunlock) která je popsána v sadě Windows SDK.

## <a name="cpagesetupdialoggetdrivername"></a><a name="getdrivername"></a>CPageSetupDialog::GetDriverName

Volání této funkce po volání [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) načíst název systémově definované ovladače tiskárny zařízení.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Návratová hodnota

A `CString` zadání systémově definovaného názvu ovladače.

### <a name="remarks"></a>Poznámky

Použijte ukazatel na `CString` objekt `GetDriverName` vrácený jako `lpszDriverName` hodnotu volání [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cpagesetupdialoggetmargins"></a><a name="getmargins"></a>CPageSetupDialog::GetMargins

Volání této funkce po `DoModal` volání načíst okraje ovladače zařízení tiskárny.

```cpp
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Parametry

*lpRectOkraje*<br/>
Ukazatel na strukturu [RECT](/windows/win32/api/windef/ns-windef-rect) nebo [crect](../../atl-mfc-shared/reference/crect-class.md) objekt, který popisuje (v 1/1000 palců nebo 1/100 mm) tiskové okraje pro aktuálně vybrané tiskárny. Pokud vás tento obdélník nezajímá, předajte hodnotu NULL pro tento parametr.

*lpRectMinOkraje*<br/>
Ukazatel na `RECT` strukturu `CRect` nebo objekt, který popisuje (v 1/1000 palců nebo 1/100 mm) minimální tiskové okraje pro aktuálně vybranou tiskárnu. Pokud vás tento obdélník nezajímá, předajte hodnotu NULL pro tento parametr.

## <a name="cpagesetupdialoggetpapersize"></a><a name="getpapersize"></a>CPageSetupDialog::GetPaperSize

Voláním této funkce načtěte velikost papíru vybraného pro tisk.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Pro tisk byl vybrán objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) obsahující velikost papíru (v 1/1000 palců nebo 1/100 mm).

## <a name="cpagesetupdialoggetportname"></a><a name="getportname"></a>CPageSetupDialog::GetPortName

Volání této funkce `DoModal` po volání načíst název aktuálně vybraného portu tiskárny.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název aktuálně vybraného portu tiskárny.

## <a name="cpagesetupdialogm_psd"></a><a name="m_psd"></a>CPageSetupDialog::m_psd

Struktura typu PAGESETUPDLG, jejíž členové ukládají charakteristiky objektu dialogového okna.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Poznámky

Po vytvoření `CPageSetupDialog` objektu můžete `m_psd` před voláním `DoModal` členské funkce nastavit různé aspekty dialogového okna.

Pokud změníte `m_psd` datový člen přímo, přepíšete jakékoli výchozí chování.

Další informace o struktuře [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw) naleznete v souboru Windows SDK.

Viz příklad [cPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

## <a name="cpagesetupdialogondrawpage"></a><a name="ondrawpage"></a>cPageSetupDialog::OndrawPage

Volat rámci nakreslit obraz obrazovky tištěné stránky.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení tiskárny.

*nZpráva*<br/>
Určuje zprávu označující oblast aktuálně vykreslované stránky. Může to být jedna z následujících možností:

- WM_PSD_FULLPAGERECT Celá oblast stránky.

- WM_PSD_MINMARGINRECT Aktuální minimální marže.

- WM_PSD_MARGINRECT Aktuální marže.

- WM_PSD_GREEKTEXTRECT obsah stránky.

- WM_PSD_ENVSTAMPRECT oblast vyhrazena pro reprezentaci poštovní známky.

- WM_PSD_YAFULLPAGERECT oblast pro reprezentaci zpáteční adresy. Tato oblast se rozprostírá k okrajům oblasti ukázkové stránky.

*lpRect*<br/>
Ukazatel na objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) nebo [RECT](/windows/win32/api/windef/ns-windef-rect) obsahující souřadnice kreslicí oblasti.

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota, pokud je zpracována; jinak 0.

### <a name="remarks"></a>Poznámky

Tento obrázek je pak zobrazen jako součást společného dialogového okna Nastavení stránky OLE. Výchozí implementace nakreslí obrázek stránky textu.

Přepsáním této funkce přizpůsobíte výkres určité oblasti obrazu nebo celého obrazu. Můžete to provést pomocí **příkazu switch** s **příkazy case,** které kontrolují hodnotu *nMessage*. Chcete-li například přizpůsobit vykreslování obsahu obrázku stránky, můžete použít následující ukázkový kód:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Všimněte si, že není nutné zpracovávat každý případ *nMessage*. Můžete zvolit zpracování jedné součásti obrazu, několika součástí obrazu nebo celé oblasti.

## <a name="cpagesetupdialogpredrawpage"></a><a name="predrawpage"></a>CPageSetupDialog::PreDrawPage

Volat rámci před kreslením obraz obrazovky tištěné stránky.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Parametry

*wPapír*<br/>
Určuje hodnotu, která označuje velikost papíru. Tato hodnota může být jednou z **DMPAPER_** hodnot uvedených v popisu struktury [DEVMODE.](/windows/win32/api/wingdi/ns-wingdi-devmodea)

*wPříznaky*<br/>
Označuje orientaci papíru nebo obálky a to, zda je tiskárna je jehličkovým nebo HPPCL (Hewlett Packard Printer Control Language). Tento parametr může mít jednu z následujících hodnot:

- 0x001 Papír v režimu na šířku (jehličková matice)

- 0x003 Papír v režimu na šířku (HPPCL)

- 0x005 Papír v režimu na výšku (jehličková matice)

- 0x007 Papír v režimu na výšku (HPPCL)

- 0x00b Obálka v režimu na šířku (HPPCL)

- 0x00d Obálka v režimu na výšku (jehličková matice)

- 0x019 Obálka v režimu na šířku (jehličková matice)

- 0x01f Obálka v režimu na výšku (jehličková matice)

*pPSD*<br/>
Ukazatel na `PAGESETUPDLG` strukturu. Další informace o [službě PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw)naleznete v souboru Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota, pokud je zpracována; jinak 0.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce přizpůsobíte výkres obrazu. Pokud tuto funkci přepíšete a vrátíte hodnotu TRUE, musíte nakreslit celý obraz. Pokud tuto funkci přepíšete a vrátíte hodnotu NEPRAVDA, bude celý výchozí obrázek nakreslen rámcem.

## <a name="see-also"></a>Viz také

[MFC Ukázka WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
