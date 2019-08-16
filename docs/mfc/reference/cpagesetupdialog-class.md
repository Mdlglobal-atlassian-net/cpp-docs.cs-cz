---
title: CPageSetupDialog Class
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
ms.openlocfilehash: 18b17d0f40aaab6ba2a018a568950549eda23016
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503015"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog Class

Zapouzdřuje služby poskytované dialogovým oknem nastavení běžné stránky OLE systému Windows s další podporou pro nastavení a úpravy okrajů tisku.

## <a name="syntax"></a>Syntaxe

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|`CPageSetupDialog` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Vytvoří kontext zařízení pro tisk.|
|[CPageSetupDialog::DoModal](#domodal)|Zobrazí dialogové okno a umožní uživateli vybrat výběr.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Vrátí název zařízení tiskárny.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Vrátí aktuální režim DEVMODE tiskárny.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Vrátí ovladač používaný tiskárnou.|
|[CPageSetupDialog::GetMargins](#getmargins)|Vrátí aktuální nastavení okrajů tiskárny.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Vrátí velikost papíru tiskárny.|
|[CPageSetupDialog:: GetPort](#getportname)|Vrátí název výstupního portu.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Volá se rozhraním, aby se vygenerovala obrazová obrazovka tištěné stránky.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Volá se rozhraním před vykreslením obrázku na obrazovce tištěné stránky.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Struktura používaná k přizpůsobení `CPageSetupDialog` objektu.|

## <a name="remarks"></a>Poznámky

Tato třída je navržena tak, aby vybrala místo v dialogovém okně nastavení tisku.

Chcete-li `CPageSetupDialog` použít objekt, nejprve vytvořte objekt `CPageSetupDialog` pomocí konstruktoru. Po vytvoření dialogového okna můžete nastavit nebo upravit jakékoli hodnoty v `m_psd` datovém členu pro inicializaci hodnot ovládacích prvků dialogového okna. Struktura [m_psd](#m_psd) je typu PAGESETUPDLG.

Po inicializaci ovládacích prvků dialogového okna zavolejte `DoModal` členskou funkci pro zobrazení dialogového okna a umožněte uživateli vybrat možnosti tisku. `DoModal`Vrátí, zda uživatel vybral tlačítko OK (IDOK) nebo zrušit (IDCANCEL).

Pokud `DoModal` vrátí IDOK, můžete použít `CPageSetupDialog`několik členských `m_psd` funkcí nebo získat přístup k datovému členu a načíst informace vstupem uživatele.

> [!NOTE]
>  Po ukončení dialogového okna běžné nastavení stránky OLE nebude rozhraní ukládat žádné změny provedené uživatelem. Je až do samotné aplikace, aby ukládala jakékoli hodnoty z tohoto dialogového okna do trvalého umístění, jako je například člen dokumentu aplikace nebo třídy aplikace.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs. h

##  <a name="cpagesetupdialog"></a>  CPageSetupDialog::CPageSetupDialog

Voláním této funkce vytvoříte `CPageSetupDialog` objekt.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parametry

*dwFlags*<br/>
Jeden nebo více příznaků, které lze použít k přizpůsobení nastavení dialogového okna. Hodnoty lze kombinovat pomocí bitového operátoru OR. Tyto hodnoty mají následující význam:

- PSD_DEFAULTMINMARGINS Nastaví minimální možné šířky okrajů stránky tak, aby byly stejné jako minimum tiskárny. Tento příznak je ignorován, pokud jsou také zadány příznaky PSD_MARGINS a PSD_MINMARGINS.

- PSD_INWININIINTLMEASURE není implementováno.

- PSD_MINMARGINS způsobí, že systém použije hodnoty zadané v `rtMinMargin` členu jako minimální povolené šířky pro levý, horní, pravý a dolní okraj. Systém brání uživateli v zadání šířky, která je menší než zadané minimum. Pokud není zadán parametr PSD_MINMARGINS, systém nastaví minimální povolené šířky pro ty, které tiskárna povoluje.

- PSD_MARGINS aktivuje oblast ovládacího prvku okraj.

- PSD_INTHOUSANDTHSOFINCHES způsobí, že se jednotky dialogového okna budou měřit v 1/1000 palcích.

- PSD_INHUNDREDTHSOFMILLIMETERS způsobí, že se jednotky dialogového okna budou měřit v milimetrech 1/100.

- PSD_DISABLEMARGINS zakáže ovládací prvky dialogového okna okraj.

- PSD_DISABLEPRINTER zakáže tlačítko tiskárna.

- PSD_NOWARNING zabraňuje zobrazení zprávy upozornění, když není k dispozici žádná výchozí tiskárna.

- PSD_DISABLEORIENTATION zakáže ovládací prvek dialogu orientace stránky.

- PSD_RETURNDEFAULT způsobí `CPageSetupDialog` vrácení struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES –](/windows/win32/api/commdlg/ns-commdlg-devnames) , které jsou inicializovány pro výchozí tiskárnu systému bez zobrazení dialogového okna. Předpokládá se, že obojí `hDevNames` a `hDevMode` má hodnotu null. v opačném případě vrátí funkce chybu. Pokud je výchozí systémová tiskárna podporovaná starším ovladačem tiskárny (starším než Windows verze 3,0), `hDevNames` vrátí se jenom hodnota. `hDevMode` má hodnotu null.

- PSD_DISABLEPAPER zakáže ovládací prvek pro výběr papíru.

- PSD_SHOWHELP způsobí, že dialogové okno zobrazí tlačítko Help. Pokud je tento příznak zadán, nesmí členmíthodnotunull.`hwndOwner`

- PSD_ENABLEPAGESETUPHOOK povolí funkci zavěšení určenou v `lpfnSetupHook`.

- PSD_ENABLEPAGESETUPTEMPLATE způsobí, že operační systém vytvoří dialogové okno pomocí pole šablony dialogového okna identifikovaného `hInstance` a. `lpSetupTemplateName`

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE označuje, `hInstance` že identifikuje datový blok, který obsahuje předem načtenou šablonu dialogového okna. Pokud je tento `lpSetupTemplateName` příznak zadán, systém ignoruje.

- PSD_ENABLEPAGEPAINTHOOK povolí funkci zavěšení určenou v `lpfnPagePaintHook`.

- PSD_DISABLEPAGEPAINTING zakáže oblast vykreslování dialogového okna.

*pParentWnd*<br/>
Ukazatel na nadřazenou položku nebo vlastníka dialogového okna.

### <a name="remarks"></a>Poznámky

Použijte funkci [DoModal](../../mfc/reference/cdialog-class.md#domodal) k zobrazení dialogového okna.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC

Vytvoří kontext zařízení tiskárny ze struktur [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) a [DEVNAMES –](/windows/win32/api/commdlg/ns-commdlg-devnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač nově vytvořeného kontextu zařízení tiskárny (DC).

##  <a name="domodal"></a>  CPageSetupDialog::DoModal

Voláním této funkce zobrazíte dialogové okno běžné nastavení stránky OLE systému Windows a umožníte uživateli vybrat různé možnosti nastavení tisku, například okraje tisku, velikost a orientaci papíru a cílovou tiskárnu.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Návratová hodnota

IDOK nebo IDCANCEL. Pokud se vrátí IDCANCEL, zavolejte funkci Windows [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) a určete, jestli došlo k chybě.

IDOK a IDCANCEL jsou konstanty, které označují, zda uživatel vybral tlačítko OK nebo Storno.

### <a name="remarks"></a>Poznámky

Kromě toho uživatel má přístup k možnostem nastavení tiskárny, například k síťovému umístění a vlastnostem, které jsou specifické pro vybranou tiskárnu.

Pokud chcete inicializovat různé možnosti dialogu nastavení stránky nastavením členů `m_psd` struktury, měli byste tak učinit před voláním `DoModal`a po vytvoření objektu dialogového okna. Po volání `DoModal`volejte jiné členské funkce pro načtení nastavení nebo zadání informací uživatelem do dialogového okna.

Pokud chcete rozšířit aktuální nastavení zadané uživatelem, zavolejte na [CWinApp:: SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Tato funkce přebírá informace z `CPageSetupDialog` objektu a inicializuje a vybere nový řadič domény tiskárny se správnými atributy.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog).

##  <a name="getdevicename"></a>CPageSetupDialog:: getnázev_zařízení

Tuto funkci zavolejte po `DoModal` načtení názvu aktuálně vybrané tiskárny.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název zařízení používaný `CPageSetupDialog` objektem.

##  <a name="getdevmode"></a>CPageSetupDialog:: getdevmode

Tuto funkci volejte po volání `DoModal` metody pro načtení informací o kontextu `CPageSetupDialog` zařízení tiskárny objektu.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Struktura dat [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , která obsahuje informace o inicializaci zařízení a prostředí ovladače tiskárny. Paměť, kterou tato struktura provedla, je nutné odemknout pomocí funkce Windows [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) , která je popsána v Windows SDK.

##  <a name="getdrivername"></a>CPageSetupDialog:: getnázev_ovladače

Tuto funkci zavolejte po volání metody [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) , která načte název ovladače zařízení definovaného systémem.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Návratová hodnota

`CString` Zadání názvu ovladače definovaného systémem.

### <a name="remarks"></a>Poznámky

Použijte ukazatel na `CString` objekt `GetDriverName` vrácený jako hodnota `lpszDriverName` v volání metody [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getmargins"></a>CPageSetupDialog:: getmarže

Tuto funkci zavolejte po volání `DoModal` , aby se načetly okraje ovladače zařízení tiskárny.

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Parametry

*lpRectMargins*<br/>
Ukazatel na strukturu [Rect](/windows/win32/api/windef/ns-windef-rect) nebo objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , který popisuje (v 1/1000 palcích nebo 1/100 mm) okraje pro tisk aktuálně vybrané tiskárny. Pokud si nejste zajímat tento obdélník, předejte pro tento parametr hodnotu NULL.

*lpRectMinMargins*<br/>
Ukazatel na `RECT` strukturu nebo `CRect` objekt, který popisuje (v 1/1000 palcích nebo 1/100 mm) minimální okraje pro tisk aktuálně vybrané tiskárny. Pokud si nejste zajímat tento obdélník, předejte pro tento parametr hodnotu NULL.

##  <a name="getpapersize"></a>CPageSetupDialog::GetPaperSize

Voláním této funkce načtete velikost papíru vybraného pro tisk.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt [CSize](../../atl-mfc-shared/reference/csize-class.md) , který obsahuje velikost papíru (v 1/1000 palců nebo 1/100 mm) vybraných pro tisk.

##  <a name="getportname"></a>CPageSetupDialog:: GetPort

Voláním této funkce po `DoModal` volání načtěte název aktuálně vybraného portu tiskárny.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název aktuálně vybraného portu tiskárny.

##  <a name="m_psd"></a>  CPageSetupDialog::m_psd

Struktura typu PAGESETUPDLG, jejíž členové ukládají charakteristiky objektu dialogového okna.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Poznámky

Po sestavení `CPageSetupDialog` objektu lze použít `m_psd` k nastavení různých aspektů `DoModal` dialogového okna před voláním členské funkce.

Změníte-li datový člen přímo, přepíšete všechny výchozí chování. `m_psd`

Další informace o struktuře [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-psdw) naleznete v Windows SDK.

Podívejte se na příklad pro [CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog).

##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage

Volá se rozhraním, aby se nakreslil obrázek tištěné stránky.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení tiskárny.

*Nzpráva*<br/>
Určuje zprávu, která označuje oblast aktuálně vykreslené stránky. Může být jedna z následujících akcí:

- WM_PSD_FULLPAGERECT celou oblast stránky.

- WM_PSD_MINMARGINRECT aktuální minimální okraje.

- WM_PSD_MARGINRECT aktuální okraje.

- WM_PSD_GREEKTEXTRECT obsah stránky

- WM_PSD_ENVSTAMPRECT oblast vyhrazenou pro vyjádření razítka razítka.

- WM_PSD_YAFULLPAGERECT oblast pro reprezentaci návratových adres. Tato oblast se rozšíří na okraje oblasti vzorové stránky.

*lpRect*<br/>
Ukazatel na objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) nebo [Rect](/windows/win32/api/windef/ns-windef-rect) obsahující souřadnice oblasti kreslení.

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota, pokud je zpracována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tento obrázek se pak zobrazí jako součást dialogového okna běžné nastavení stránky OLE. Výchozí implementace nakreslí obrázek stránky s textem.

Přepište tuto funkci, pokud chcete přizpůsobit vykreslování konkrétní oblasti obrázku nebo celého obrázku. To lze provést pomocí příkazu **Switch** s příkazy **case** , který kontroluje hodnotu *nzpráva*. Například pro přizpůsobení vykreslování obsahu obrázku stránky můžete použít následující příklad kódu:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Všimněte si, že nemusíte zpracovávat všechny případy *nzpráva*. Můžete se rozhodnout, že budete zpracovávat jednu komponentu obrázku, několik součástí bitové kopie nebo celou oblast.

##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage

Volá se rozhraním, než se nakreslí obraz obrazovky tištěné stránky.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Parametry

*wPaper*<br/>
Určuje hodnotu, která určuje velikost papíru. Tato hodnota může být jedna z hodnot **DMPAPER_** uvedených v popisu struktury [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) .

*wFlags*<br/>
Určuje orientaci dokumentu nebo obálky a to, jestli je tiskárna zařízení s tečkovou maticí nebo HPPCL (jazykem tiskáren Hewlett-Packard Control Language). Tento parametr může mít jednu z následujících hodnot:

- 0x001 papír v režimu na šířku (Jehličková matice)

- 0x003 papír v režimu na šířku (HPPCL)

- 0x005 papír v režimu na výšku (Jehličková matice)

- 0x007 papír v režimu na výšku (HPPCL)

- Obálka 0x00b v režimu na šířku (HPPCL)

- 0x00 obálka v režimu na výšku (Jehličková matice)

- Obálka 0x019 v režimu na šířku (Jehličková matice)

- Obálka 0x01f v režimu na výšku (Jehličková matice)

*pPSD*<br/>
Ukazatel na `PAGESETUPDLG` strukturu. Další informace o [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-psdw)najdete v Windows SDK.

### <a name="return-value"></a>Návratová hodnota

Nenulová hodnota, pokud je zpracována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Přepsáním této funkce upravíte vykreslování obrázku. Pokud tuto funkci přepíšete a vrátíte hodnotu TRUE, je nutné vykreslit celý obrázek. Pokud tuto funkci potlačíte a vrátíte hodnotu FALSE, bude rozhraní vykreslováno pomocí celého výchozího obrázku.

## <a name="see-also"></a>Viz také:

[Ukázka knihovny MFC v programu WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
