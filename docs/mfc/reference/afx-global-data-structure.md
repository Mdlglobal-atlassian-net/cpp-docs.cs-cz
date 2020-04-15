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
- AFXGLOBALS/AFX_GLOBAL_DATA::InitD2D
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
ms.openlocfilehash: 60f7513075e8da7e17f2113c01b954af5a690aaf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363668"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA – struktura

Struktura `AFX_GLOBAL_DATA` obsahuje pole a metody, které se používají ke správě rozhraní nebo přizpůsobení vzhledu a chování aplikace.

## <a name="syntax"></a>Syntaxe

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Vytvoří `AFX_GLOBAL_DATA` strukturu.|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::Vyčištění](#cleanup)|Uvolní prostředky, které jsou přiděleny v rámci, jako jsou stopy, písma a knihovny DLL.|
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Vytvoří transformaci otočení, která se otáčí o zadaný úhel kolem zadaného bodu.|
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Nakreslí pozadí nadřazeného ovládacího prvku v zadané oblasti.|
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Nakreslí zadaný text ve vizuálním stylu určeného motivu.|
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Odebere zadaný pár značek XML ze zadané vyrovnávací paměti.|
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Načte aktuální barvu zadaného prvku uživatelského rozhraní.|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Vrátí ukazatel na `ID2D1Factory` rozhraní, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Načte předdefinovaný kurzor, který se podobá `IDC_HAND`ruce a jehož identifikátor je .|
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Vytvoří a uloží do globálních dat ukazatel rozhraní ITaskBarList.|
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Vytvoří a uloží do globálních dat ukazatel rozhraní ITaskBarList3.|
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Načte metriky spojené s neklientskou oblastí neminimalizovaných oken.|
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Určuje pozice automatických skrytí prostředí.|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Načte výšku textových znaků v aktuálním písmu.|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Vrátí ukazatel na `IWICImagingFactory` rozhraní, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Vrátí ukazatel na `IDWriteFactory` rozhraní, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.|
|[AFX_GLOBAL_DATA::InitD2D](#initd2d)|Inicializuje `D2D` `DirectWrite`, `WIC` a továrny. Volání této metody před inicializování hlavního okna.|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Označuje, zda jsou podporovány předdefinované 32bitové ikony.|
|[AFX_GLOBAL_DATA::Inicializováno](#isd2dinitialized)|Určuje, `D2D` zda byl inicializován.|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Poskytuje jednoduchý způsob volání metody Windows [DwmIsCompositionEnabled.](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled)|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Označuje, zda jsou obrazy aktuálně zobrazeny ve vysokém kontrastu.|
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Detekuje aktuální stav animace nabídky plochy a funkcí automatického skrytí na hlavním panelu.|
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Registruje zadanou třídu okna knihovny MFC.|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Vydává rozhraní získané prostřednictvím GetITaskbarList a GetITaskbarList3 metody.|
|[AFX_GLOBAL_DATA::Pokračovat](#resume)|Znovu inicializuje ukazatele interních funkcí, které přistupují k metodám, které podporují [motivy systému](/windows/win32/Controls/visual-styles-overview)Windows a vizuální styly .|
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Poskytuje jednoduchý způsob, jak volat Metodu Windows [SetLayeredWindowAttributes.](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)|
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Vytvoří zadané logické písmo.|
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Vytvoří a inicializuje objekt položky prostředí z názvu analýzy.|
|[AFX_GLOBAL_DATA::Aktualizovat písma](#updatefonts)|Reintializes logická písma, které jsou používány v rámci.|
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicializuje barvy, hloubku barev, stopy, pera a obrazy, které framework používá.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Povolí nebo zakáže podporu microsoft active accessibility. Funkce Active Accessibility poskytuje spolehlivé metody pro vystavení informací o prvcích uživatelského rozhraní.|
|[AFX_GLOBAL_DATA::Podpora Usnadnění přístupu](#isaccessibilitysupport)|Označuje, zda je povolena podpora aktivní hodování společnosti Microsoft.|
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Označuje, zda operační systém podporuje okna s vrstvami.|

### <a name="data-members"></a>Členové dat

|Name (Název)|Popis|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Označuje, zda aktuální operační systém podporuje prolnutí alfa.|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Označuje, zda je aplikace spuštěna pod systémem Windows 7 OS nebo vyšším|
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Určuje barvu přechodu aktivního titulku. Obvykle se používá pro ukotvení podoken.|
|[AFX_GLOBAL_DATA::clinactivecaptiongradient](#clrinactivecaptiongradient)|Určuje barvu přechodu neaktivního aktivního titulku. Obvykle se používá pro ukotvení podoken.|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Označuje, zda rozhraní používá předdefinované 32bitové barevné ikony nebo ikony s nižším rozlišením.|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Označuje, zda se systémové písmo používá pro nabídky, panely nástrojů a pásy karet.|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Uloží rukojeť pro kurzor ruky.|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Uloží úchyt pro vodorovný strečkurz.|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Uloží úchyt pro svislý kurzor roztažení.|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Uloží úchyt pro ikonu nástroje.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Určuje posun od levého panelu nástrojů automatického skrytí na levou stranu dokovacího pruhu.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Určuje mezeru mezi panely nástrojů automatického skrytí.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Určuje tloušťku přetahovaného rámečku, který se používá ke komunikaci ukotveného stavu.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Určuje tloušťku přetahování rámečku, který se používá ke komunikaci plovoucího stavu.|

### <a name="remarks"></a>Poznámky

Většina dat ve `AFX_GLOBAL_DATA` struktuře je inicializována při spuštění aplikace.

### <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxglobals.h

## <a name="afx_global_databisosalphablendingsupport"></a><a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport

Označuje, zda operační systém podporuje alfa prolnutí.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Poznámky

PRAVDA označuje, že alfa prolnutí je podporováno; jinak NEPRAVDA.

## <a name="afx_global_datacleanup"></a><a name="cleanup"></a>AFX_GLOBAL_DATA::Vyčištění

Uvolní prostředky, které jsou přiděleny v rámci, jako jsou stopy, písma a knihovny DLL.

```
void CleanUp();
```

## <a name="afx_global_datad2d1makerotatematrix"></a><a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D2D1MakeRotateMatrix

Vytvoří transformaci otočení, která se otáčí o zadaný úhel kolem zadaného bodu.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>Parametry

*angle*<br/>
Úhel otáčení ve směru hodinových ručiček ve stupních.

*Centrum*<br/>
Bod, o kterém se má otáčet.

*matice*<br/>
Když tato metoda vrátí, obsahuje nové transformace otočení. Pro tento parametr je nutné přidělit úložiště.

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK v případě úspěchu nebo hodnotu chyby jinak.

## <a name="afx_global_datadrawparentbackground"></a><a name="drawparentbackground"></a>AFX_GLOBAL_DATA::DrawParentBackground

Nakreslí pozadí nadřazeného ovládacího prvku v zadané oblasti.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
[v] Ukazatel na okno ovládacího prvku.

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*lpRect*<br/>
[v] Ukazatel na obdélník, který ohraničuje oblast kreslit. Výchozí hodnota je NULL.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

## <a name="afx_global_datadrawtextonglass"></a><a name="drawtextonglass"></a>AFX_GLOBAL_DATA::DrawTextOnGlass

Nakreslí zadaný text ve vizuálním stylu určeného motivu.

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

*hTéma*<br/>
[v] Zpracování dat motivu okna nebo NULL. Rámec používá zadaný motiv k nakreslení textu, pokud tento parametr není NULL a jsou podporovány motivy. V opačném případě rozhraní nepoužije motiv k nakreslení textu.

Použijte [OpenThemeData](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) metoda k vytvoření HTHEME.

*Pdc*<br/>
[v] Ukazatel na kontext zařízení.

*iPartId*<br/>
[v] Ovládací část, která má požadovaný vzhled textu. Další informace naleznete ve sloupci Části tabulky v [části Části a stavy](/windows/win32/controls/parts-and-states). Pokud je tato hodnota 0, je text nakreslen ve výchozím písmu nebo písmo vybrané do kontextu zařízení.

*iStateId*<br/>
[v] Stav ovládacího prvku, který má požadovaný vzhled textu. Další informace naleznete ve sloupci Stavy v tabulce [Části a stavy](/windows/win32/controls/parts-and-states).

*strText*<br/>
[v] Text k tomu.

*Rect*<br/>
[v] Hranice oblasti, ve které je nakreslena zadaný text.

*dwFlags*<br/>
[v] Bitová kombinace (OR) příznaků, které určují, jak je nakreslen zadaný text.

Pokud `NULL` je parametr *hTheme* nebo pokud motivy nejsou podporovány a povoleny, *parametr nFormat* metody [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) popisuje platné příznaky. Pokud jsou podporovány motivy, parametr *dwFlags* metody [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) popisuje platné příznaky.

*nZářeVelikost*<br/>
[v] Velikost efektu záře, který je nakreslen na pozadí před kreslením zadaného textu. Výchozí hodnota je 0.

*clrText*<br/>
[v] Barva, ve které je nakreslena zadaný text. Výchozí hodnota je výchozí barva.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se motiv používá k nakreslení zadaného textu; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Motiv definuje vizuální styl aplikace. Motiv se nepoužívá k nakreslení textu, pokud je parametr *hTheme* NULL nebo pokud není podporována metoda [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) nebo pokud je zakázána kompozice [Správce oken plochy](/windows/win32/dwm/dwm-overview) (DWM).

## <a name="afx_global_dataenableaccessibilitysupport"></a><a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA::EnableAccessibilitySupport

Povolí nebo zakáže podporu microsoft active accessibility.

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE pro povolení podpory usnadnění; NEPRAVDA pro zakázání podpory usnadnění přístupu. Výchozí hodnota je TRUE.

### <a name="remarks"></a>Poznámky

Active Accessibility je technologie založená na com, která zlepšuje způsob, jakým programy a operační systém Windows spolupracují s produkty asistenčních technologií. Poskytuje spolehlivé metody pro vystavení informací o prvcích uživatelského rozhraní. Novější model usnadnění s názvem Microsoft UI Automation je však nyní k dispozici. Porovnání těchto dvou technologií naleznete v [tématech Automatizace uživatelského rozhraní a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

Pomocí metody [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport) určete, zda je povolena podpora přístupnosti Microsoft Active.

## <a name="afx_global_dataexcludetag"></a><a name="excludetag"></a>AFX_GLOBAL_DATA::ExcludeTag

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
[v] Vyrovnávací paměť textu.

*lpszTag*<br/>
[v] Název dvojice otevíracích a uzavíracích značek XML.

*strTag*<br/>
[out] Když tato metoda vrátí, *strTag* parametr obsahuje text, který je mezi otevření a zavření XML značky, které jsou *pojmenovány parametrem lpszTag.* Všechny úvodní nebo koncové mezery jsou oříznuty z výsledku.

*bIsCharsList*<br/>
[v] TRUE převést symboly pro řídicí znaky v parametru *strTag* na skutečné řídicí znaky; FALSE neprovést převod. Výchozí hodnota je FALSE. Další informace naleznete v tématu Poznámky.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Dvojice značek XML se skládá z pojmenovaných otevíracích a uzavíracích značek, které označují začátek a konec spuštění textu v zadané vyrovnávací paměti. Parametr *strBuffer* určuje vyrovnávací paměť a parametr *lpszTag* určuje název tagů XML.

Pomocí symbolů v následující tabulce můžete kódovat sadu řídicích znaků v zadané vyrovnávací paměti. Zadejte hodnotu TRUE pro parametr *bIsCharsList,* chcete-li převést symboly v parametru *strTag* na skutečné řídicí znaky. Následující tabulka používá [makro _T()](../../c-runtime-library/data-type-mappings.md) k určení řetězce symbolů a řídicích znaků.

|Symbol|Řídicí znak|
|------------|----------------------|
|_T("\\\t")|_T("\t")|
|_T("\\\n")|_T(\n")|
|_T("\\\r")|_T("\r")|
|_T("\\\b")|_T(\b")|
|_T("LT")|_T("\<")|
|_T("GT")|_T(">")|
|_T("AMP")|_T("&")|

## <a name="afx_global_datagetcolor"></a><a name="getcolor"></a>AFX_GLOBAL_DATA::GetColor

Načte aktuální barvu zadaného prvku uživatelského rozhraní.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Parametry

*nBarva*<br/>
[v] Hodnota, která určuje prvek uživatelského rozhraní, jehož barva je načtena. Seznam platných hodnot naleznete v parametru *nIndex* metody [GetSysColor.](/windows/win32/api/winuser/nf-winuser-getsyscolor)

### <a name="return-value"></a>Návratová hodnota

Hodnota barvy RGB zadaného prvku uživatelského rozhraní. Další informace naleznete v tématu Poznámky.

### <a name="remarks"></a>Poznámky

Pokud je parametr *nColor* mimo rozsah, vrácená hodnota je nula. Vzhledem k tomu, že nula je také platná hodnota RGB, nelze tuto metodu použít k určení, zda je barva systému podporována aktuálním operačním systémem. Místo toho použijte [metodu GetSysColorBrush,](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) která vrátí hodnotu NULL, pokud barva není podporována.

## <a name="afx_global_datagetdirect2dfactory"></a><a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA::GetDirect2dFactory

Vrátí ukazatel na rozhraní ID2D1Factory, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní ID2D1Factory, pokud je vytvoření továrny úspěšné, nebo NULL, pokud se vytvoření nezdaří nebo aktuální operační systém nemá podporu D2D.

## <a name="afx_global_datagethandcursor"></a><a name="gethandcursor"></a>AFX_GLOBAL_DATA::GetHandCursor

Načte předdefinovaný kurzor, který se podobá ruce a jehož identifikátor je IDC_HAND.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Návratová hodnota

Rukojeť ručního kurzoru.

## <a name="afx_global_datagetnonclientmetrics"></a><a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA::GetNonClientMetrics

Načte metriky spojené s neklientskou oblastí neminimalizovaných oken.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Parametry

*Info*<br/>
[dovnitř, ven] [Neklientmetrics](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) struktura, která obsahuje škálovatelné metriky spojené s neklientské oblasti neminimalizované okno.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tato metoda je úspěšná; jinak NEPRAVDA.

## <a name="afx_global_datagettextheight"></a><a name="gettextheight"></a>AFX_GLOBAL_DATA::GetTextHeight

Načte výšku textových znaků v aktuálním písmu.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parametry

*bHorz*<br/>
[v] TRUE pro načtení výšky znaků při vodorovném spuštění textu; NEPRAVDA pro načtení výšky znaků při svislém průběhu textu. Výchozí hodnota je TRUE.

### <a name="return-value"></a>Návratová hodnota

Výška aktuálního písma, která se měří od jeho vzestupu k dolnímu toku.

## <a name="afx_global_datagetwicfactory"></a><a name="getwicfactory"></a>AFX_GLOBAL_DATA::GetWICFactory

Vrátí ukazatel na rozhraní IWICImagingFactory, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IWICImagingFactory, pokud je vytvoření továrny úspěšné, nebo null, pokud se vytvoření nezdaří nebo aktuální operační systém nemají podporu WIC.

## <a name="afx_global_datagetwritefactory"></a><a name="getwritefactory"></a>AFX_GLOBAL_DATA::GetWriteFactory

Vrátí ukazatel na rozhraní IDWriteFactory, které je uloženo v globálních datech. Pokud rozhraní není inicializováno, je vytvořeno a má výchozí parametry.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní IDWriteFactory, pokud je vytvoření továrny úspěšné, nebo NULL, pokud se vytvoření nezdaří nebo aktuální operační systém nemají podporu DirectWrite.

## <a name="afx_global_datainitd2d"></a><a name="initd2d"></a>AFX_GLOBAL_DATA::InitD2D

Inicializuje továrny D2D, DirectWrite a WIC. Volání této metody před inicializování hlavního okna.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parametry

*d2dFactoryType*<br/>
Model zřetězení továrny D2D a prostředky, které vytvoří.

*writeFactoryType*<br/>
Hodnota, která určuje, zda bude objekt factory zápisu sdílen nebo izolován

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byly továrny intilalizrd, FALSE - jinak

## <a name="afx_global_datais32biticons"></a><a name="is32biticons"></a>AFX_GLOBAL_DATA::Is32BitIcons

Označuje, zda jsou podporovány předdefinované 32bitové ikony.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou podporovány předdefinované 32bitové ikony; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda vrátí hodnotu PRAVDA, pokud rozhraní podporuje 32bitové vestavěné ikony a pokud operační systém podporuje 16 bitů na pixel nebo více a pokud obrázky nejsou zobrazeny ve vysokém kontrastu.

## <a name="afx_global_dataisaccessibilitysupport"></a><a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA::Podpora Usnadnění přístupu

Označuje, zda je povolena podpora aktivní hodování společnosti Microsoft.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je povolena podpora usnadnění; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Microsoft Active Accessibility bylo dřívější řešení pro zpřístupnění aplikací. Microsoft UI Automation je nový model usnadnění pro Microsoft Windows a je určen k řešení potřeb asistenčních technologických produktů a automatizovaných testovacích nástrojů.

Pomocí metody [AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport) povolte nebo zakažte podporu aktivní přístupnosti.

## <a name="afx_global_dataisd2dinitialized"></a><a name="isd2dinitialized"></a>AFX_GLOBAL_DATA::Inicializováno

Určuje, zda byl D2D inicializován.

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byl D2D inicializován; jinak FALSE.

## <a name="afx_global_dataisdwmcompositionenabled"></a><a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA::IsDwmCompositionEnabled

Poskytuje jednoduchý způsob volání metody Windows [DwmIsCompositionEnabled.](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled)

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je [povolena](/windows/win32/dwm/dwm-overview) kompozice Správce oken plochy (DWM); jinak NEPRAVDA.

## <a name="afx_global_dataishighcontrastmode"></a><a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode

Označuje, zda jsou obrazy aktuálně zobrazeny ve vysokém kontrastu.

```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud jsou obrazy aktuálně zobrazeny v černém nebo bílém režimu vysokého kontrastu; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

V černém režimu s vysokým kontrastem jsou okraje směřující ke světlu bílé a pozadí černé. V bílém režimu s vysokým kontrastem jsou okraje směřující ke světlu černé a pozadí bílé.

## <a name="afx_global_dataiswindowslayersupportavailable"></a><a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable

Označuje, zda operační systém podporuje okna s vrstvami.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud jsou podporována vrstvená okna; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud jsou podporována okna s vrstvami, používají *inteligentní dokovací* značky okna s vrstvami.

## <a name="afx_global_datam_busebuiltin32biticons"></a><a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons

Označuje, zda rozhraní používá předdefinované 32bitové barevné ikony nebo ikony s nižším rozlišením.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Poznámky

True určuje, že rozhraní používá 32bitové ikony barev; FALSE určuje ikony s nižším rozlišením. Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicializuje tento člen na HODNOTU PRAVDA.

Tento člen musí být nastaven při spuštění aplikace.

## <a name="afx_global_datam_busesystemfont"></a><a name="m_busesystemfont"></a>AFX_GLOBAL_DATA::m_bUseSystemFont

Označuje, zda se systémové písmo používá pro nabídky, panely nástrojů a pásy karet.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Poznámky

True určuje použití systémového písma; jinak NEPRAVDA. Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicializuje tento člen na HODNOTU FALSE.

Testování tohoto člena není jediný způsob, jak pro rozhraní k určení písma použít. Metoda `AFX_GLOBAL_DATA::UpdateFonts` také testuje výchozí a alternativní písma, aby určila, jaké vizuální styly jsou k dispozici pro nabídky, panely nástrojů a pásy karet.

## <a name="afx_global_datam_hcurhand"></a><a name="m_hcurhand"></a>AFX_GLOBAL_DATA::m_hcurHand

Uloží rukojeť pro kurzor ruky.

```
HCURSOR m_hcurHand;
```

## <a name="afx_global_datam_hcurstretch"></a><a name="m_hcurstretch"></a>AFX_GLOBAL_DATA::m_hcurStretch

Uloží úchyt pro vodorovný strečkurz.

```
HCURSOR m_hcurStretch;
```

## <a name="afx_global_datam_hcurstretchvert"></a><a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA::m_hcurStretchVert

Uloží úchyt pro svislý kurzor roztažení.

```
HCURSOR m_hcurStretchVert;
```

## <a name="afx_global_datam_hicontool"></a><a name="m_hicontool"></a>AFX_GLOBAL_DATA::m_hiconTool

Uloží úchyt pro ikonu nástroje.

```
HICON m_hiconTool;
```

## <a name="afx_global_datam_nautohidetoolbarmargin"></a><a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin

Určuje posun od levého pruhu nástrojů automatického skrytí na levou stranu dokovacího panelu.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Poznámky

Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicializuje tento člen na 4 pixely.

## <a name="afx_global_datam_nautohidetoolbarspacing"></a><a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing

Určuje mezeru mezi panely nástrojů automatického skrytí.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Poznámky

Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicializuje tento člen na 14 pixelů.

## <a name="afx_global_datam_ndragframethicknessdock"></a><a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Určuje tloušťku přetahovaného rámečku, který se používá k označení ukotveného stavu.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Poznámky

Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicializuje tento člen na 3 pixely.

## <a name="afx_global_datam_ndragframethicknessfloat"></a><a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat

Určuje tloušťku přetahování rámečku, který se používá k označení plovoucího stavu.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Poznámky

Konstruktor `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` inicializuje tento člen na 4 pixely.

## <a name="afx_global_dataonsettingchange"></a><a name="onsettingchange"></a>AFX_GLOBAL_DATA::OnSettingChange

Detekuje aktuální stav animace nabídky plochy a funkcí automatického skrytí na hlavním panelu.

```
void OnSettingChange();
```

### <a name="remarks"></a>Poznámky

Tato metoda nastaví proměnné rozhraní na stav určitých atributů plochy uživatele. Tato metoda detekuje aktuální stav animace nabídky, funkce automatického skrytí nabídky a automatického skrytí panelu úloh.

## <a name="afx_global_dataregisterwindowclass"></a><a name="registerwindowclass"></a>AFX_GLOBAL_DATA::RegisterWindowClass

Registruje zadanou třídu okna knihovny MFC.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Parametry

*lpszClassNamePrefix*<br/>
[v] Název třídy okna pro registraci.

### <a name="return-value"></a>Návratová hodnota

Kvalifikovaný název registrované třídy, pokud je tato metoda úspěšná; v opačném případě [výjimku prostředku](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Poznámky

Vrácená hodnota je seznam parametru *lpszClassNamePrefix* a šestnáctkové textové reprezentace popisovačů aktuální instance aplikace. kurzor aplikace, což je kurzor šipky, jehož identifikátor je IDC_ARROW; a štětec na pozadí. Další informace o registraci tříd oken knihovny MFC naleznete v tématu [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).

## <a name="afx_global_dataresume"></a><a name="resume"></a>AFX_GLOBAL_DATA::Pokračovat

Znovu inicializuje ukazatele interních funkcí, které přistupují k metodám, které podporují motivy systému Windows a vizuální styly.

```
BOOL Resume();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tato metoda je úspěšná; jinak NEPRAVDA. V režimu ladění tato metoda uplatňuje, pokud je tato metoda neúspěšná.

### <a name="remarks"></a>Poznámky

Tato metoda je volána při rozhraní obdrží [zprávu WM_POWERBROADCAST.](/windows/win32/Power/wm-powerbroadcast)

## <a name="afx_global_datasetlayeredattrib"></a><a name="setlayeredattrib"></a>AFX_GLOBAL_DATA::SetLayeredAttrib

Poskytuje jednoduchý způsob, jak volat Metodu Windows [SetLayeredWindowAttributes.](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
[v] Popisovač do vrstveného okna.

*crKey*<br/>
[v] Klíč barvy průhlednosti, který [Správce oken plochy](/windows/win32/dwm/dwm-overview) používá k vytvoření vrstveného okna.

*bAlfa*<br/>
[v] Hodnota alfa, která se používá k popisu krytí vrstveného okna.

*dwFlags*<br/>
[v] Bitová kombinace (OR) příznaků, které určují, které parametry metody se mají použít. Určete LWA_COLORKEY použít jako barvu průhlednosti parametr *crKey.* Určete LWA_ALPHA pro použití parametru *bAlpha* k určení krytí okna s vrstvami.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tato metoda je úspěšná; jinak NEPRAVDA.

## <a name="afx_global_datasetmenufont"></a><a name="setmenufont"></a>AFX_GLOBAL_DATA::SetMenuFont

Vytvoří zadané logické písmo.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Parametry

*lpLogFont*<br/>
[v] Ukazatel na strukturu, která obsahuje atributy písma.

*bHorz*<br/>
[v] TRUE určit, že text běží vodorovně; FALSE určit, že text běží svisle.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud tato metoda je úspěšná; jinak NEPRAVDA. V režimu ladění tato metoda uplatňuje, pokud je tato metoda neúspěšná.

### <a name="remarks"></a>Poznámky

Tato metoda vytvoří vodorovné pravidelné písmo, podtržené písmo a tučné písmo, které se používá ve výchozích položkách nabídky. Tato metoda volitelně vytvoří pravidelné svislé písmo. Další informace o logických písmech naleznete v tématu [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="afx_global_dataupdatefonts"></a><a name="updatefonts"></a>AFX_GLOBAL_DATA::Aktualizovat písma

Reintializes logická písma, které jsou používány v rámci.

```
void UpdateFonts();
```

### <a name="remarks"></a>Poznámky

Další informace o logických `CFont::CreateFontIndirect`písmech naleznete v tématu .

## <a name="afx_global_dataupdatesyscolors"></a><a name="updatesyscolors"></a>AFX_GLOBAL_DATA::UpdateSysColors

Inicializuje barvy, hloubku barev, stopy, pera a obrazy, které framework používá.

```
void UpdateSysColors();
```

## <a name="afx_global_databiswindows7"></a><a name="biswindows7"></a>AFX_GLOBAL_DATA::bIsWindows7

Označuje, zda je aplikace spouštěna v systému Windows 7 nebo vyšší.

```
BOOL bIsWindows7;
```

## <a name="afx_global_dataclractivecaptiongradient"></a><a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA::clrActiveCaptionGradient

Určuje barvu přechodu aktivního titulku. Obvykle se používá pro ukotvení podoken.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="afx_global_dataclrinactivecaptiongradient"></a><a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA::clinactivecaptiongradient

Určuje barvu přechodu neaktivního titulku. Obvykle se používá pro ukotvení podoken.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="afx_global_datagetitaskbarlist"></a><a name="getitaskbarlist"></a>AFX_GLOBAL_DATA::GetITaskbarList

Vytvoří a uloží v globálních `ITaskBarList` datech ukazatel na rozhraní.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `ITaskbarList` rozhraní, pokud je vytvoření objektu seznamu úkolů úspěšné; NULL, pokud se vytvoření nezdaří nebo pokud je aktuální operační systém menší než Windows 7.

## <a name="afx_global_datagetitaskbarlist3"></a><a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA::GetITaskbarList3

Vytvoří a uloží v globálních `ITaskBarList3` datech ukazatel na rozhraní.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `ITaskbarList3` rozhraní, pokud je vytvoření objektu seznamu úkolů úspěšné; NULL, pokud se vytvoření nezdaří nebo pokud je aktuální operační systém menší než Windows 7.

## <a name="afx_global_datagetshellautohidebars"></a><a name="getshellautohidebars"></a>AFX_GLOBAL_DATA::GetShellAutohideBars

Určuje pozice automatických skrytí prostředí.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Návratová hodnota

Celá hodnota s kódované příznaky, které určují umístění automatické ho skrytí pruhy. Může kombinovat následující hodnoty: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT AFX_AUTOHIDE_RIGHT.

## <a name="afx_global_datareleasetaskbarrefs"></a><a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA::ReleaseTaskBarRefs

Uvolní rozhraní získané `GetITaskbarList` prostřednictvím `GetITaskbarList3` a metody.

```
void ReleaseTaskBarRefs();
```

## <a name="afx_global_datashellcreateitemfromparsingname"></a><a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA::ShellCreateItemFromParsingName

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
[v] Ukazatel na zobrazovaný název.

*Pbc*<br/>
Ukazatel na kontext vazby, který řídí operaci analýzy.

*riid řekl:*<br/>
Odkaz na ID rozhraní.

*Ppv*<br/>
[out] Když tato funkce vrátí, obsahuje ukazatel rozhraní požadované v *riid*. Obvykle se jedná `IShellItem` `IShellItem2`nebo .

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK v případě úspěchu. chybová hodnota jinak.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../hierarchy-chart.md)<br/>
[Struktury, styly, zpětná volání a mapy zpráv](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Díly a státy](/windows/win32/controls/parts-and-states)<br/>
[CDC::DrawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Správce oken plochy](/windows/win32/dwm/dwm-overview)<br/>
[Povolit a řídit složení DWM](/windows/win32/dwm/composition-ovw)<br/>
[Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[Funkce GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[Struktura NEKLIENTETRICKY](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[Třída AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[Výjimka afxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[Atributy setlayeredwindow](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
