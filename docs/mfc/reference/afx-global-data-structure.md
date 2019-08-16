---
title: AFX_GLOBAL_DATA – struktura
ms.date: 11/04/2016
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
ms.openlocfilehash: dda3056cbed18ef93e09b52cd9d0a6b00e1db177
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507758"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA – struktura

`AFX_GLOBAL_DATA` Struktura obsahuje pole a metody, které slouží ke správě rozhraní nebo přizpůsobení vzhledu a chování aplikace.

## <a name="syntax"></a>Syntaxe

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|`AFX_GLOBAL_DATA` Vytvoří strukturu.|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|Uvolňuje prostředky, které jsou přiděleny rozhraním, jako jsou štětce, písma a knihovny DLL.|
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Vytvoří transformaci otočení, která se otáčí kolem zadaného úhlu kolem určeného bodu.|
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Vykreslí pozadí nadřazeného ovládacího prvku v zadané oblasti.|
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Nakreslí zadaný text ve stylu vizuálu zadaného motivu.|
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Odebere zadaný pár značek XML ze zadané vyrovnávací paměti.|
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Načte aktuální barvu zadaného prvku uživatelského rozhraní.|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Vrátí ukazatel na `ID2D1Factory` rozhraní, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Načte předdefinovaný ukazatel, který se podobá ruce a jehož identifikátor `IDC_HAND`je.|
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Vytvoří a uloží v globálních datech ukazatel na rozhraní ITaskBarList.|
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Vytvoří a uloží v globálních datech ukazatel na rozhraní ITaskBarList3.|
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Načte metriky přidružené k neminimalizujované oblasti oken.|
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Určuje pozice pro automatické skrývání panelů prostředí.|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Načte výšku textových znaků v aktuálním písmu.|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Vrátí ukazatel na `IWICImagingFactory` rozhraní, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Vrátí ukazatel na `IDWriteFactory` rozhraní, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Inicializuje `D2D`, `DirectWrite` a`WIC` továrny. Před inicializací hlavního okna volejte tuto metodu.|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Určuje, zda jsou podporovány předdefinované 32 ikony.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Určuje, zda `D2D` byla inicializována.|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Poskytuje jednoduchý způsob volání metody [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) systému Windows.|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Označuje, zda jsou obrázky aktuálně zobrazovány s vysokým kontrastem.|
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Zjistí aktuální stav animace nabídky plochy a funkce automatické skrývání hlavního panelu.|
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Zaregistruje určenou třídu okna knihovny MFC.|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Vydává rozhraní získaná prostřednictvím metod GetITaskbarList a GetITaskbarList3.|
|[AFX_GLOBAL_DATA::Resume](#resume)|Opětovně inicializuje ukazatele interních funkcí, které přistupují k metodám, které podporují motivy systému Windows [a vizuální styly](/windows/win32/Controls/visual-styles-overview).|
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Poskytuje jednoduchý způsob volání metody [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) systému Windows.|
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Vytvoří zadané logické písmo.|
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Vytvoří a inicializuje objekt položky prostředí z názvu analýzy.|
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reintializes logická písma používaná rozhraním.|
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicializuje barvy, hloubku barev, štětce, pera a obrázky, které používá rozhraní.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Povolí nebo zakáže podporu Microsoft Active Accessibility. Aktivní přístupnost poskytuje spolehlivé metody pro odhalení informací o prvcích uživatelského rozhraní.|
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Určuje, jestli je povolená podpora Microsoft Active Accessibility.|
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Určuje, jestli operační systém podporuje okna s vrstvami.|

### <a name="data-members"></a>Datové členy

|Name|Popis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Určuje, zda aktuální operační systém podporuje prolnutí alfa.|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Určuje, zda je aplikace spouštěna v operačním systému Windows 7 nebo novějším.|
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Určuje barvu přechodu aktivního titulku. Obecně se používá pro dokovací podokna.|
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Určuje barvu přechodu neaktivního aktivního titulku. Obecně se používá pro dokovací podokna.|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Označuje, zda rozhraní používá předdefinované 32 ikony barev nebo ikony nižšího rozlišení.|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Označuje, zda je písmo systému použito pro nabídky, panely nástrojů a pásy.|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Ukládá popisovač pro ukazatel na ruku.|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Ukládá popisovač pro vodorovný ukazatel Stretch.|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Ukládá popisovač pro svislý ukazatel Stretch.|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Ukládá popisovač pro ikonu nástroje.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Určuje posun z levé části panelu nástrojů pro automatické skrývání na levou stranu ukotveného panelu.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Určuje mezeru mezi automaticky skrývat panely nástrojů.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Určuje tloušťku rámečku přetažení, který se používá ke komunikaci ukotveného stavu.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Určuje tloušťku rámečku přetažení, který se používá ke komunikaci s plovoucím stavem.|

### <a name="remarks"></a>Poznámky

Většina dat ve `AFX_GLOBAL_DATA` struktuře je inicializována při spuštění aplikace.

### <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxglobals. h

## <a name="bisosalphablendingsupport"></a> AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport

Určuje, jestli operační systém podporuje prolnutí alfa.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Poznámky

Hodnota TRUE znamená, že je podporováno prolnutí alfa; v opačném případě FALSE.

## <a name="cleanup"></a> AFX_GLOBAL_DATA::CleanUp

Uvolňuje prostředky, které jsou přiděleny rozhraním, jako jsou štětce, písma a knihovny DLL.

```
void CleanUp();
```

## <a name="d2d1makerotatematrix"></a> AFX_GLOBAL_DATA::D2D1MakeRotateMatrix

Vytvoří transformaci otočení, která se otáčí kolem zadaného úhlu kolem určeného bodu.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>Parametry

*pravý*<br/>
Úhel otočení ve směru hodinových ručiček ve stupních.

*center*<br/>
Bod, který se má otočit

*službu*<br/>
Až tato metoda vrátí, obsahuje novou transformaci rotace. Pro tento parametr musíte přidělit úložiště.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK, pokud bylo úspěšné, nebo hodnotu chyby v opačném případě.

## <a name="drawparentbackground"></a> AFX_GLOBAL_DATA::DrawParentBackground

Vykreslí pozadí nadřazeného ovládacího prvku v zadané oblasti.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
pro Ukazatel na okno ovládacího prvku.

*pDC*<br/>
pro Ukazatel na kontext zařízení.

*lpRect*<br/>
pro Ukazatel na obdélník, který je ohraničen oblastí pro vykreslení. Výchozí hodnota je NULL.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

## <a name="drawtextonglass"></a> AFX_GLOBAL_DATA::DrawTextOnGlass

Nakreslí zadaný text ve stylu vizuálu zadaného motivu.

```
BOOL DrawTextOnGlass(
    HTHEME hTheme,
    CDC* pDC,
    int iPartId,
    int iStateId,
    CString strText,
    CRect rect,
    DWORD dwFlags,
    int nGlowSize = 0,
    COLORREF clrText = (COLORREF)-1);
```

### <a name="parameters"></a>Parametry

*hTheme*<br/>
pro Zpracování dat motivu okna nebo hodnoty NULL. Rozhraní používá určený motiv k nakreslení textu, pokud tento parametr není NULL a jsou podporovány motivy. V opačném případě rozhraní nepoužívá k nakreslení textu motiv.

Pomocí metody [OpenThemeData](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) vytvořte HTHEME.

*pDC*<br/>
pro Ukazatel na kontext zařízení.

*iPartId*<br/>
pro Část ovládacího prvku, která má požadovaný vzhled textu. Další informace najdete ve sloupci součásti tabulky v [částech a státech](/windows/win32/controls/parts-and-states). Pokud je tato hodnota 0, text se vykreslí jako výchozí písmo nebo se vybere písmo v kontextu zařízení.

*iStateId*<br/>
pro Stav ovládacího prvku, který má požadovaný vzhled textu. Další informace najdete ve sloupci stavy v tabulce v [částech a státech](/windows/win32/controls/parts-and-states).

*strText*<br/>
pro Text, který má být nakreslen.

*OBD*<br/>
pro Hranice oblasti, ve které je vykreslen zadaný text.

*dwFlags*<br/>
pro Bitová kombinace příznaků (nebo) příznaků, které určují, jak se vykreslí zadaný text.

Pokud je `NULL` parametr hTheme nebo pokud nejsou motivy podporované a povolené, parametr *nFormat* metody [CDC::D rawtext](../../mfc/reference/cdc-class.md#drawtext) popisuje platné příznaky. Pokud jsou podporovány motivy, parametr *dwFlags* metody [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) popisuje platné příznaky.

*nGlowSize*<br/>
pro Velikost efektu záře, který je vykreslen na pozadí před kreslením zadaného textu. Výchozí hodnota je 0.

*clrText*<br/>
pro Barva, ve které je vykreslen zadaný text. Výchozí hodnota je výchozí barva.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se k vykreslení zadaného textu použije motiv. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Motiv definuje vizuální styl aplikace. Motiv se nepoužívá k vykreslení textu, pokud má parametr *hTheme* hodnotu null nebo pokud není metoda [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) podporována, nebo pokud je kompozice [správce oken plochy](/windows/win32/dwm/dwm-overview) (DWM) zakázána.

## <a name="enableaccessibilitysupport"></a> AFX_GLOBAL_DATA::EnableAccessibilitySupport

Povolí nebo zakáže podporu Microsoft Active Accessibility.

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro TRUE, pokud chcete povolit podporu přístupnosti; FALSE, pokud chcete zakázat podporu přístupnosti. Výchozí hodnota je TRUE (pravda).

### <a name="remarks"></a>Poznámky

Aktivní přístupnost je technologie založená na modelu COM, která vylepšuje způsob, jakým programy a operační systém Windows spolupracují s produkty pro usnadnění práce. Poskytuje spolehlivé metody pro odhalení informací o prvcích uživatelského rozhraní. K dispozici je ale novější model usnadnění nazvaný automatizace uživatelského rozhraní Microsoft. Porovnání těchto dvou technologií najdete v tématu [automatizace uživatelského rozhraní a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

K určení, jestli je povolená podpora Microsoft Active Accessibility, použijte metodu [AFX_GLOBAL_DATA:: IsAccessibilitySupport](#isaccessibilitysupport) .

## <a name="excludetag"></a> AFX_GLOBAL_DATA::ExcludeTag

Odebere zadaný pár značek XML ze zadané vyrovnávací paměti.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>Parametry

*strBuffer*<br/>
pro Vyrovnávací paměť textu.

*lpszTag*<br/>
pro Název páru otevírajících a uzavírajících značek XML.

*strTag*<br/>
mimo Když tato metoda vrátí hodnotu, parametr *strTag* obsahuje text, který je mezi otevírací a uzavírací ZNAČKou XML pojmenovanou parametrem *lpszTag* . Z výsledku se oříznou mezery na začátku nebo na konci.

*bIsCharsList*<br/>
pro TRUE pro převod symbolů řídicích znaků v parametru *strTag* do skutečných řídicích znaků; NEPRAVDA k provedení převodu. Výchozí hodnota je FALSE (NEPRAVDA). Další informace najdete v tématu poznámky.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Dvojice značek XML sestává z pojmenovaných otevíracích a ukončovacích značek, které označují začátek a konec běhu textu v zadané vyrovnávací paměti. Parametr *strBuffer* Určuje vyrovnávací paměť a parametr *lpszTag* Určuje název značek XML.

Použijte symboly v následující tabulce ke kódování sady řídicích znaků v zadané vyrovnávací paměti. Zadejte hodnotu TRUE pro parametr *bIsCharsList* pro převod symbolů v parametru *strTag* do skutečných řídicích znaků. Následující tabulka používá makro [_T ()](../../c-runtime-library/data-type-mappings.md) k určení symbolu a řídicích znaků řetězce.

|Písmeno|Řídicí znak|
|------------|----------------------|
|_T ("\\\t")|_T ("\t")|
|_T ("\\\n")|_T ("\n")|
|_T("\\\r")|_T ("\r")|
|_T("\\\b")|_T("\b")|
|_T ("LT")|_T("\<")|
|_T("GT")|_T(">")|
|_T("AMP")|_T("&")|

## <a name="getcolor"></a> AFX_GLOBAL_DATA::GetColor

Načte aktuální barvu zadaného prvku uživatelského rozhraní.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Parametry

*nColor*<br/>
pro Hodnota, která určuje prvek uživatelského rozhraní, jehož barva je načtena. Seznam platných hodnot naleznete v parametru *nIndex* metody [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) .

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB zadaného prvku uživatelského rozhraní. Další informace najdete v tématu poznámky.

### <a name="remarks"></a>Poznámky

Pokud je parametr *nColor* mimo rozsah, vrácená hodnota je nula. Vzhledem k tomu, že nula je také platná hodnota RGB, nelze tuto metodu použít k určení, zda je systémová barva podporována aktuálním operačním systémem. Místo toho použijte metodu [GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) , která vrátí hodnotu null, pokud není barva podporována.

## <a name="getdirect2dfactory"></a> AFX_GLOBAL_DATA::GetDirect2dFactory

Vrátí ukazatel na rozhraní ID2D1Factory, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Factory, pokud je vytvoření továrny úspěšné, nebo hodnotu NULL, pokud se vytvoření nezdaří nebo aktuální operační systém nemá podporu D2D.

## <a name="gethandcursor"></a>  AFX_GLOBAL_DATA::GetHandCursor

Načte předdefinovaný ukazatel, který se podobá ruce a jehož identifikátor je IDC_HAND.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Návratová hodnota

Popisovač kurzoru.

## <a name="getnonclientmetrics"></a> AFX_GLOBAL_DATA::GetNonClientMetrics

Načte metriky přidružené k neminimalizujované oblasti oken.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Parametry

*info*<br/>
[in, out] Struktura [NONCLIENTMETRICS](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) , která obsahuje škálovatelné metriky přidružené k neminimalizováné oblasti okna.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

## <a name="gettextheight"></a> AFX_GLOBAL_DATA::GetTextHeight

Načte výšku textových znaků v aktuálním písmu.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*bHorz*<br/>
pro TRUE pro načtení výšky znaků, když se text spouští vodorovně; FALSE pro načtení výšky znaků při svislém spuštění textu Výchozí hodnota je TRUE (pravda).

### <a name="return-value"></a>Návratová hodnota

Výška aktuálního písma měřená od jeho vzestupného po jeho dolní část.

## <a name="getwicfactory"></a> AFX_GLOBAL_DATA::GetWICFactory

Vrátí ukazatel na rozhraní IWICImagingFactory, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IWICImagingFactory, pokud je vytvoření továrny úspěšné, nebo hodnotu NULL, pokud se vytvoření nezdaří nebo aktuální operační systém nemá podporu funkce WIC.

## <a name="getwritefactory"></a> AFX_GLOBAL_DATA::GetWriteFactory

Vrátí ukazatel na rozhraní IDWriteFactory, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IDWriteFactory, pokud je vytvoření továrny úspěšné, nebo hodnotu NULL, pokud se vytvoření nezdaří nebo aktuální operační systém nemá podporu DirectWrite.

## <a name="initd2d"></a> AFX_GLOBAL_DATA::InitD2D

Inicializuje továrny D2D, DirectWrite a WIC. Před inicializací hlavního okna volejte tuto metodu.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parametry

*d2dFactoryType*<br/>
Model vláken objektu D2D Factory a prostředky, které vytváří.

*writeFactoryType*<br/>
Hodnota, která určuje, zda bude objekt factory pro zápis sdílen nebo izolován

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu TRUE, pokud byly objekty intilalizrd, FALSE – jinak.

## <a name="is32biticons"></a> AFX_GLOBAL_DATA::Is32BitIcons

Určuje, zda jsou podporovány předdefinované 32 ikony.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou podporovány předdefinované ikony 32-bitů; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu TRUE, pokud rozhraní podporuje 32 vestavěné ikony a v případě, že operační systém podporuje 16 bitů na pixel nebo více, a pokud obrázky nejsou zobrazeny s vysokým kontrastem.

## <a name="isaccessibilitysupport"></a> AFX_GLOBAL_DATA::IsAccessibilitySupport

Určuje, jestli je povolená podpora Microsoft Active Accessibility.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je povolená podpora usnadnění; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Microsoft Active Accessibility je dřívější řešení pro zpřístupnění aplikací. Automatizace uživatelského rozhraní Microsoft je nový model usnadnění pro Microsoft Windows a je určený pro řešení potřeb technologií pro usnadnění a automatizovaných testovacích nástrojů.

K povolení nebo zakázání aktivní podpory usnadnění použijte metodu [AFX_GLOBAL_DATA:: EnableAccessibilitySupport](#enableaccessibilitysupport) .

## <a name="isd2dinitialized"></a> AFX_GLOBAL_DATA::IsD2DInitialized

Určuje, zda byl inicializován D2D

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl inicializován D2D; v opačném případě FALSE.

## <a name="isdwmcompositionenabled"></a> AFX_GLOBAL_DATA::IsDwmCompositionEnabled

Poskytuje jednoduchý způsob volání metody [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) systému Windows.

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je povolené složení [správce oken plochy](/windows/win32/dwm/dwm-overview) (DWM); v opačném případě FALSE.

## <a name="ishighcontrastmode"></a> AFX_GLOBAL_DATA::IsHighContrastMode

Označuje, zda jsou obrázky aktuálně zobrazovány s vysokým kontrastem.
```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou obrázky aktuálně zobrazeny v režimu černého a bílého kontrastu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

V režimu černého vysokého kontrastu jsou hrany směřující na světlo bílé a pozadí je černé. V režimu s vysokým kontrastem jsou hrany směřující na světlo černé a pozadí je bílé.

## <a name="iswindowslayersupportavailable"></a> AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable

Určuje, jestli operační systém podporuje okna s vrstvami.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou podporovaná okna s vrstvami. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud jsou vrstvená okna podporovaná , značky inteligentního Docker používají vrstvená okna.

## <a name="m_busebuiltin32biticons"></a> AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons

Označuje, zda rozhraní používá předdefinované 32 ikony barev nebo ikony nižšího rozlišení.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Poznámky

Hodnota TRUE určuje, že rozhraní používá 32 bitů barev ikony. FALSE určuje ikony s nižším rozlišením. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena na hodnotu true.

Tento člen musí být nastaven při spuštění aplikace.

## <a name="m_busesystemfont"></a> AFX_GLOBAL_DATA::m_bUseSystemFont

Označuje, zda je písmo systému použito pro nabídky, panely nástrojů a pásy.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Poznámky

Hodnota TRUE určuje, že se má použít systémové písmo. v opačném případě FALSE. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena na hodnotu false.

Testování tohoto člena není jediným způsobem, jak rozhraní určit písmo, které se má použít. `AFX_GLOBAL_DATA::UpdateFonts` Metoda také testuje výchozí a alternativní písma k určení, které vizuální styly jsou k dispozici pro použití v nabídkách, panelech nástrojů a na pásu karet.

## <a name="m_hcurhand"></a> AFX_GLOBAL_DATA::m_hcurHand

Ukládá popisovač pro ukazatel na ruku.

```
HCURSOR m_hcurHand;
```

## <a name="m_hcurstretch"></a> AFX_GLOBAL_DATA::m_hcurStretch

Ukládá popisovač pro vodorovný ukazatel Stretch.

```
HCURSOR m_hcurStretch;
```

## <a name="m_hcurstretchvert"></a> AFX_GLOBAL_DATA::m_hcurStretchVert

Ukládá popisovač pro svislý ukazatel Stretch.

```
HCURSOR m_hcurStretchVert;
```

## <a name="m_hicontool"></a> AFX_GLOBAL_DATA::m_hiconTool

Ukládá popisovač pro ikonu nástroje.

```
HICON m_hiconTool;
```

## <a name="m_nautohidetoolbarmargin"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin

Určuje posun z levé části panelu nástrojů pro automatické skrývání na levou stranu ukotveného panelu.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Poznámky

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena na 4 pixely.

## <a name="m_nautohidetoolbarspacing"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing

Určuje mezeru mezi automaticky skrývat panely nástrojů.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Poznámky

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena na 14 pixelů.

## <a name="m_ndragframethicknessdock"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Určuje tloušťku rámečku přetažení, který se používá k označení ukotveného stavu.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Poznámky

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena na 3 pixely.

## <a name="m_ndragframethicknessfloat"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat

Určuje tloušťku rámečku přetažení, který se používá k indikaci plovoucího stavu.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Poznámky

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena na 4 pixely.

## <a name="onsettingchange"></a> AFX_GLOBAL_DATA::OnSettingChange

Zjistí aktuální stav animace nabídky plochy a funkce automatické skrývání hlavního panelu.

```
void OnSettingChange();
```

### <a name="remarks"></a>Poznámky

Tato metoda nastaví proměnné rozhraní na stav určitých atributů plochy uživatele. Tato metoda detekuje aktuální stav animace nabídky, nabídku zmizí a panel úloh automaticky skrývat funkce.

## <a name="registerwindowclass"></a> AFX_GLOBAL_DATA::RegisterWindowClass

Zaregistruje určenou třídu okna knihovny MFC.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Parametry

*lpszClassNamePrefix*<br/>
pro Název třídy okna, která se má zaregistrovat

### <a name="return-value"></a>Návratová hodnota

Kvalifikovaný název registrované třídy, pokud je tato metoda úspěšná; v opačném případě [výjimku prostředku](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Poznámky

Vrácená hodnota je seznam řetězců parametrů *lpszClassNamePrefix* oddělených dvojtečkami a hexadecimální text reprezentace popisovačů aktuální instance aplikace. kurzor aplikace, který je ukazatelem šipky, jehož identifikátor je IDC_ARROW; a štětcem na pozadí. Další informace o registraci tříd okna knihovny MFC naleznete v tématu [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).

## <a name="resume"></a> AFX_GLOBAL_DATA::Resume

Opětovně inicializuje ukazatele interních funkcí, které přistupují k metodám, které podporují motivy systému Windows a vizuální styly.

```
BOOL Resume();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE. V režimu ladění tato metoda uplatňuje, pokud je tato metoda neúspěšná.

### <a name="remarks"></a>Poznámky

Tato metoda je volána, když rozhraní obdrží zprávu [WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast) .

## <a name="setlayeredattrib"></a> AFX_GLOBAL_DATA::SetLayeredAttrib

Poskytuje jednoduchý způsob volání metody [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) systému Windows.

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*HWND*<br/>
pro Zpracování do vrstveného okna.

*crKey*<br/>
pro Klíč barvy transparentnosti, který [správce oken plochy](/windows/win32/dwm/dwm-overview) používá k vytvoření vrstveného okna.

*bAlpha*<br/>
pro Hodnota alfa, která se používá k popisu neprůhlednosti vrstveného okna.

*dwFlags*<br/>
pro Bitová kombinace příznaků (nebo) příznaků, které určují parametry metody, které se mají použít. Zadejte LWA_COLORKEY pro použití parametru *crKey* jako barvy průhlednosti. Zadejte LWA_ALPHA pro určení neprůhlednosti vrstveného okna pomocí parametru *bAlpha* .

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

## <a name="setmenufont"></a> AFX_GLOBAL_DATA::SetMenuFont

Vytvoří zadané logické písmo.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
pro Ukazatel na strukturu, která obsahuje atributy písma.

*bHorz*<br/>
pro Hodnota TRUE určuje, že text bude běžet vodorovně; Hodnota FALSE určuje, že text bude běžet svisle.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE. V režimu ladění tato metoda uplatňuje, pokud je tato metoda neúspěšná.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří horizontální normální písmo, podtržené písmo a tučné písmo, které je použito ve výchozích položkách nabídky. Tato metoda volitelně vytvoří normální svislé písmo. Další informace o logických písmech naleznete v tématu [CFont –:: CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="updatefonts"></a> AFX_GLOBAL_DATA::UpdateFonts

Reintializes logická písma používaná rozhraním.

```
void UpdateFonts();
```

### <a name="remarks"></a>Poznámky

Další informace o logických písmech naleznete `CFont::CreateFontIndirect`v tématu.

## <a name="updatesyscolors"></a> AFX_GLOBAL_DATA::UpdateSysColors

Inicializuje barvy, hloubku barev, štětce, pera a obrázky, které používá rozhraní.

```
void UpdateSysColors();
```

## <a name="biswindows7"></a> AFX_GLOBAL_DATA::bIsWindows7

Určuje, zda je aplikace spuštěna v systému Windows 7 nebo vyšším.

```
BOOL bIsWindows7;
```

## <a name="clractivecaptiongradient"></a> AFX_GLOBAL_DATA::clrActiveCaptionGradient

Určuje barvu přechodu aktivního titulku. Obecně se používá pro dokovací podokna.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="clrinactivecaptiongradient"></a> AFX_GLOBAL_DATA::clrInactiveCaptionGradient

Určuje barvu přechodu neaktivního titulku. Obecně se používá pro dokovací podokna.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="getitaskbarlist"></a> AFX_GLOBAL_DATA::GetITaskbarList

Vytvoří a uloží v globálním datovém ukazateli na `ITaskBarList` rozhraní.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `ITaskbarList` rozhraní, pokud je vytvoření objektu seznamu pruhů úkolů úspěšné; Hodnota NULL, pokud je vytvoření neúspěšné nebo pokud je aktuální operační systém menší než Windows 7.

## <a name="getitaskbarlist3"></a> AFX_GLOBAL_DATA::GetITaskbarList3

Vytvoří a uloží v globálním datovém ukazateli na `ITaskBarList3` rozhraní.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `ITaskbarList3` rozhraní, pokud je vytvoření objektu seznamu pruhů úkolů úspěšné; Hodnota NULL, pokud je vytvoření neúspěšné nebo pokud je aktuální operační systém menší než Windows 7.

## <a name="getshellautohidebars"></a> AFX_GLOBAL_DATA::GetShellAutohideBars

Určuje pozice pro automatické skrývání panelů prostředí.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Návratová hodnota

Celočíselná hodnota se zakódovanými příznaky, která určuje pozice pro automatické skrývání pruhů. Může zkombinovat následující hodnoty: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="releasetaskbarrefs"></a> AFX_GLOBAL_DATA::ReleaseTaskBarRefs

Vydává rozhraní získaná `GetITaskbarList` prostřednictvím `GetITaskbarList3` metod a.

```
void ReleaseTaskBarRefs();
```

## <a name="shellcreateitemfromparsingname"></a> AFX_GLOBAL_DATA::ShellCreateItemFromParsingName

Vytvoří a inicializuje objekt položky prostředí z názvu analýzy.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>Parametry

*pszPath*<br/>
pro Ukazatel na zobrazované jméno.

*pbc*<br/>
Ukazatel na kontext vazby, který řídí operaci analýzy.

*riid*<br/>
Odkaz na ID rozhraní.

*ppv*<br/>
mimo Když tato funkce vrátí, obsahuje ukazatel rozhraní požadovaný v *riid*. Obvykle `IShellItem` se jedná o nebo `IShellItem2`.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK, pokud bylo úspěšné. v opačném případě se jedná o chybovou hodnotu.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../hierarchy-chart.md)<br/>
[Struktury, styly, zpětná volání a mapy zpráv](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Části a stavy](/windows/win32/controls/parts-and-states)<br/>
[CDC::DrawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Správce oken plochy](/windows/win32/dwm/dwm-overview)<br/>
[Povolit a řídit kompozici DWM](/windows/win32/dwm/composition-ovw)<br/>
[Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[GetSysColor – funkce](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[Struktura NONCLIENTMETRICS](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
