---
title: Afx_global_data – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFX_GLOBAL_DATA
dev_langs:
- C++
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf2ffe62760e3879d834409f5b3207588ea06f36
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956304"
---
# <a name="afxglobaldata-structure"></a>AFX_GLOBAL_DATA – struktura
`AFX_GLOBAL_DATA` Struktura obsahuje pole a metody, které se používají ke správě rozhraní nebo přizpůsobit vzhled a chování vaší aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct AFX_GLOBAL_DATA  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Vytvoří `AFX_GLOBAL_DATA` struktury.|  
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::Cleanup](#cleanup)|Uvolní prostředky, které jsou přidělené rozhraní, jako je například štětce, písma a knihovny DLL.|  
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Vytvoří otočení transformaci, která otočí podle určeného úhlu kolem zadané bodu.|  
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Kreslení na pozadí nadřazeného ovládacího prvku v určené oblasti.|  
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Vykreslí zadaný text v vizuální styl zadaný motiv.|  
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Odebere zadanou vyrovnávací paměť na zadaný pár značky XML.|  
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Načte aktuální barvu elementu zadané uživatelské rozhraní.|  
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Vrátí ukazatel `ID2D1Factory` rozhraní, která je uložená v globální data. Pokud není inicializována rozhraní, se vytvoří a má výchozí parametry.|  
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Načte předdefinované kurzor, který vypadá takto: dlaně a jejíž identifikátor je `IDC_HAND`.|  
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Vytvoří a uloží v globálních datech ukazatel na ITaskBarList rozhraní.|  
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Vytvoří a uloží v globálních datech ukazatel na ITaskBarList3 rozhraní.|  
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Načte metriky přidružené k oblasti nonclient nonminimized Windows.|  
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Určuje, že pozice prostředí automaticky skrýt řádky.|  
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Načte výšku textových znaků v aktuálním písmem.|  
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Vrátí ukazatel `IWICImagingFactory` rozhraní, která je uložená v globální data. Pokud není inicializována rozhraní, se vytvoří a má výchozí parametry.|  
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Vrátí ukazatel `IDWriteFactory` rozhraní, která je uložená v globální data. Pokud není inicializována rozhraní, se vytvoří a má výchozí parametry.|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Inicializuje `D2D`, `DirectWrite`, a `WIC` objekty pro vytváření. Tuto metodu volejte před inicializací hlavní okno.|  
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Označuje, zda jsou předdefinované ikony 32-bit.|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Určuje, zda `D2D` byl inicializován.|  
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Poskytuje jednoduchý způsob, jak volat Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) metoda.|  
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Označuje, zda jsou obrázky aktuálně zobrazený s vysokým kontrastem.|  
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Zjistí, aktuální stav nabídky animace a funkce autohide – panelu na ploše.|  
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Zaregistruje zadanou třídu okna knihovny MFC.|  
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Uvolní získaných pomocí metody GetITaskbarList a GetITaskbarList3 rozhraní.|  
|[AFX_GLOBAL_DATA::Resume](#resume)|Znovu inicializuje ukazatele vnitřní funkce, které přístup metody, které podporují Windows [motivy a vizuální styly](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx).|  
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Poskytuje jednoduchý způsob, jak volat Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) metoda.|  
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Vytvoří zadané logické písmo.|  
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Vytvoří a inicializuje objekt prostředí položky z analýzy názvu.|  
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reintializes logické písma, které používají rozhraní.|  
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicializuje barvy, barvy, štětce, pera a bitové kopie, které používají rozhraní.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Povolí nebo zakáže podporu usnadnění společnosti Microsoft. Active Accessibility poskytuje spolehlivé metody pro vystavení informací o prvky uživatelského rozhraní.|  
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Určuje, zda je povolena podpora Microsoft Active Accessibility.|  
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Určuje, zda operační systém podporuje vrstveného windows.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Určuje, zda aktuální operační systém podporuje prolnutí alfa.|  
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Určuje, zda se aplikace spouští v rámci operačního systému Windows 7 nebo vyšší|  
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Určuje barvu barevného přechodu aktivní titulek. Obvykle se používá pro ukotvení podokna.|  
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Určuje barvu barevného přechodu active neaktivním titulku. Obvykle se používá pro ukotvení podokna.|  
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Označuje, zda rozhraní používá předdefinovanou 32bitové barvy ikony nebo ikony nižší rozlišení.|  
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Označuje, zda systém písmo pro pásů karet, nabídek a panelů nástrojů.|  
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Uloží popisovač pro ruční kurzor.|  
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Uloží popisovač pro vodorovné stretch kurzor.|  
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Uloží popisovač pro svislé stretch kurzor.|  
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Uloží popisovač pro ikonu nástroj.|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Určuje posun na panelu nástrojů krajní levé autohide – na levé straně ukotvení panelu.|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Určuje mezery mezi autohide – panely nástrojů.|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Určuje tloušťku přetáhněte rámce, který se používá ke komunikaci ukotveného stavu.|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Určuje tloušťku přetáhněte rámce, který se používá ke komunikaci plovoucí stavu.|  
  
### <a name="remarks"></a>Poznámky  
 Většina dat v `AFX_GLOBAL_DATA` struktura je inicializován při spuštění aplikace.  
  
### <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `AFX_GLOBAL_DATA`   
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxglobals.h  
  
### <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


## <a name="bisosalphablendingsupport"></a> AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
Určuje, zda operační systém podporuje prolnutí alfa.  
  
  
```  
BOOL  bIsOSAlphaBlendingSupport;  
```  
  
### <a name="remarks"></a>Poznámky  
 `TRUE` Označuje, že je podporovaný alfa míchání; v opačném `FALSE`.  
  

## <a name="cleanup"></a> AFX_GLOBAL_DATA::Cleanup
Uvolní prostředky, které jsou přidělené rozhraní, jako je například štětce, písma a knihovny DLL.  
  
  
```  
void CleanUp();
```  
## <a name="d2d1makerotatematrix"></a> AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
Vytvoří otočení transformaci, která otočí podle určeného úhlu kolem zadané bodu.  
  
  
```  
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,  
    D2D1_POINT_2F center,  
    D2D1_MATRIX_3X2_F *matrix);
```  
  
### <a name="parameters"></a>Parametry   
 *úhel*  
 Po směru hodinových ručiček kolem úhel ve stupních.  
  
 *Center*  
 Bod o tom, které otočení.  
  
 *matice*  
 Po návratu tato metoda obsahuje nové otočení transformace. Musíte přidělit úložiště pro tento parametr.  
  
### <a name="return-value"></a>Návratová hodnota  
 V opačném případě vrátí S_OK v případě úspěchu nebo chybovou hodnotu.  
  
## <a name="drawparentbackground"></a> AFX_GLOBAL_DATA::DrawParentBackground
Kreslení na pozadí nadřazeného ovládacího prvku v určené oblasti.  
  
  
```  
BOOL DrawParentBackground(
    CWnd* pWnd,   
    CDC* pDC,   
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry   
 [v] *pWnd*  
 Ukazatel na okno ovládacího prvku.  
  
 [v] *primárního řadiče domény*  
 Ukazatel na kontextu zařízení.  
  
 [v] *lprect –*  
 Ukazatel na obdélníku bounds oblasti k vykreslení. Výchozí hodnota je `NULL`.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda je úspěšná. v opačném `FALSE`.  
  
## <a name="drawtextonglass"></a> AFX_GLOBAL_DATA::DrawTextOnGlass
Vykreslí zadaný text v vizuální styl zadaný motiv.  
  
  
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
 [v] *hTheme*  
 Zpracování dat motiv časového období, nebo `NULL`. Rozhraní používá vykreslování textu, pokud není tento parametr zadaný motiv `NULL` a motivy jsou podporovány. Rozhraní, jinak hodnota nepoužívá motiv vykreslování textu.  
  
 Použití [OpenThemeData](http://msdn.microsoft.com/library/windows/desktop/bb759821) metodu pro vytvoření `HTHEME`.  
  
 [v] *primárního řadiče domény*  
 Ukazatel na kontextu zařízení.  
  
 [v] *iPartId*  
 Ovládací prvek část, která má vzhled požadovaná textu. Další informace najdete v tématu sloupec v tabulce v části [částí a stavy](http://msdn.microsoft.com/library/windows/desktop/bb773210). Pokud tato hodnota je 0, text se vykresluje v výchozí písmo nebo písmo vybrané do kontextu zařízení.  
  
 [v] *iStateId*  
 Řízení stavu, který má vzhled požadovaná textu. Další informace najdete v tématu stavy sloupec tabulky v [částí a stavy](http://msdn.microsoft.com/library/windows/desktop/bb773210).  
  
 [v] *strText*  
 Text k vykreslení.  
  
 [v] *Rect –*  
 Hranice oblasti, ve kterém se nevykreslí zadaný text.  
  
 [v] *dwFlags*  
 Bitová kombinace (nebo) příznaky, které určují, jakým způsobem se vykresluje zadaný text.  
  
 Pokud *hTheme* parametr je `NULL` nebo pokud nejsou podporovány a povoleno, motivy *nFormat* parametr [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) popisuje platném – metoda Příznaky. Pokud motivy jsou podporovány, *dwFlags* parametr [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317) metoda popisuje platný příznaků.  
  
 [v] *nGlowSize*  
 Velikost efekt záře, který je vykreslen na pozadí před kreslení zadaný text. Výchozí hodnota je 0.  
  
 [v] *clrText*  
 Barva, ve kterém se nevykreslí zadaný text. Výchozí hodnota je výchozí barvu.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud motiv slouží k vykreslení zadaný text; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Motiv definuje vizuální styl aplikace. Vykreslování textu, pokud se nepoužívá motiv *hTheme* parametr je `NULL`, nebo pokud [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317) metoda není podporována, nebo pokud [Správce oken plochy](http://msdn.microsoft.com/library/windows/desktop/aa969540) ( Složení Správce oken plochy) je zakázaná.  
  
### <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [Části a stavy](http://msdn.microsoft.com/library/windows/desktop/bb773210)   
 [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)   
 [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317)   
 [Správce oken plochy](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [Zapnutí a řízení složení Správce oken plochy](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="enableaccessibilitysupport"></a> AFX_GLOBAL_DATA::EnableAccessibilitySupport
Povolí nebo zakáže podporu usnadnění společnosti Microsoft.  
  
  
```  
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry   
 [v] *bEnable*  
 `TRUE` Povolit usnadnění přístupu; `FALSE` zakázat usnadnění přístupu. Výchozí hodnota je `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Active Accessibility je technologie založená na modelu COM, která vylepšuje způsob, jakým programy a společně s produktů využívajících technologie usnadnění práce operační systém Windows. Poskytuje spolehlivé metody pro vystavení informací o prvky uživatelského rozhraní. Model novější usnadnění názvem automatizace uživatelského rozhraní Microsoft je však nyní k dispozici. Porovnání těchto dvou technologií najdete v tématu [automatizace uživatelského rozhraní a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).  
  
 Použití [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport) metoda k určení, zda je povoleno Microsoft Active Accessibility podpory.  
  
 
### <a name="see-also"></a>Viz také  
 [Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)   
 [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)

## <a name="excludetag"></a> AFX_GLOBAL_DATA::ExcludeTag
Odebere zadanou vyrovnávací paměť na zadaný pár značky XML.  
  
  
```  
BOOL ExcludeTag(
    CString& strBuffer,  
    LPCTSTR lpszTag,  
    CString& strTag,  
    BOOL bIsCharsList = FALSE);
```  
  
### <a name="parameters"></a>Parametry   
 [v] *strBuffer*  
 Vyrovnávací paměť textu.  
  
 [v] *lpszTag*  
 Název z dvojice otvírání a zavírání značky XML.  
  
 [out] *strTag*  
 Po návratu tato metoda *strTag* parametr obsahuje text, který je mezi počáteční a koncovou XML značky, které byly pojmenovány podle *lpszTag* parametr. Všechny prázdné začátku nebo na konci je oříznut od výsledku.  
  
 [v] *bIsCharsList*  
 `TRUE` Chcete-li převést symboly pro řídicí znaky v *strTag* parametr do skutečné řídicí znaky; `FALSE` nechcete provádět převod. Výchozí hodnota je `FALSE`. Další informace najdete v části poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda je úspěšná. v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Dvojici – značka XML se skládá z s názvem otvírání a zavírání značky, které označují počáteční a koncová spustit textu v zadané vyrovnávací paměti. *StrBuffer* parametr určuje vyrovnávací paměť a *lpszTag* parametr určuje název značky XML.  
  
 Použijte symboly v následující tabulce ke kódování sadu řídicí znaky v zadané vyrovnávací paměti. Zadejte `TRUE` pro *bIsCharsList* parametr převést symboly v *strTag* parametr do skutečné řídicí znaky. V následující tabulce používá [_T()](../../c-runtime-library/data-type-mappings.md) makro a zadejte symbol řídicí řetězce znaků.  
  
|Symbol|Řídicí znak|  
|------------|----------------------|  
|_T – ("\\\t")|_T("\t")|  
|_T – ("\\\n")|_T("\n")|  
|_T – ("\\\r")|_T("\r")|  
|_T – ("\\\b")|_T("\b")|  
|_T("LT")|_T – ("\<")|  
|_T("GT")|_T("&GT;")|  
|_T("AMP")|_T("&AMP;")|  
  
## <a name="getcolor"></a> AFX_GLOBAL_DATA::GetColor
Načte aktuální barvu elementu zadané uživatelské rozhraní.  
  
  
```  
COLORREF GetColor(int nColor);
```  
  
### <a name="parameters"></a>Parametry   
 [v] *nColor*  
 Hodnota, která určuje element uživatelského rozhraní, jehož barvu je načíst. Seznam platných hodnot najdete v tématu *nIndex* parametr [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) metoda.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota Barva RGB element zadaného uživatelského rozhraní. Další informace najdete v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *nColor* parametr je mimo rozsah, návratovou hodnotu nula. Protože nula je také platnou hodnotu RGB, nelze použít tuto metodu k určení, zda systém barvu, která je podporován v aktuálním operačním systému. Místo toho použijte [GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927) metoda, která vrátí `NULL` Pokud barva není podporován.  
  
### <a name="see-also"></a>Viz také  

 [GetSysColor – funkce](http://msdn.microsoft.com/library/windows/desktop/ms724371)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927)

## <a name="getdirect2dfactory"></a> AFX_GLOBAL_DATA::GetDirect2dFactory
 Vrací ukazatel na rozhraní ID2D1Factory, která je uložená v globální data. Pokud není inicializována rozhraní, se vytvoří a má výchozí parametry.  
  
  
```  
ID2D1Factory* GetDirect2dFactory();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1Factory Pokud vytváření továrny neproběhne úspěšně, nebo hodnota NULL, pokud vytvoření nezdaří nebo aktuální operační systém nemají D2D podpory.  
  
## <a name="gethandcursor"></a>  AFX_GLOBAL_DATA::GetHandCursor
Načte předdefinované kurzor, který vypadá takto: dlaně a jejíž identifikátor je `IDC_HAND`.  
  
  
```  
HCURSOR GetHandCursor();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač ruční kurzor.  

## <a name="getnonclientmetrics"></a> AFX_GLOBAL_DATA::GetNonClientMetrics
Načte metriky přidružené k oblasti nonclient nonminimized Windows.  
  
  
```  
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```  
  
### <a name="parameters"></a>Parametry   
 [ve out] *informace*  
 A [NONCLIENTMETRICS](http://msdn.microsoft.com/library/windows/desktop/ff729175) struktura, která obsahuje škálovatelné metriky, které jsou přidružené k oblasti nonclient nonminimized okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda bude úspěšná; v opačném `FALSE`.  
 
  
### <a name="see-also"></a>Viz také   
 [Struktura NONCLIENTMETRICS](http://msdn.microsoft.com/library/windows/desktop/ff729175)

## <a name="gettextheight"></a> AFX_GLOBAL_DATA::GetTextHeight
 Načte výšku textových znaků v aktuálním písmem.  
  
  
```  
int GetTextHeight(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parametry   
 [v] *bHorz*  
 `TRUE` načtení výšku znaků při spuštění textové vodorovně; `FALSE` načíst výšku znaků při spuštění textu ve svislém směru. Výchozí hodnota je `TRUE`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška aktuální písmo, které se měří od jeho horní dotah k jeho spodním dotahem.  
  
## <a name="getwicfactory"></a> AFX_GLOBAL_DATA::GetWICFactory
Vrací ukazatel na rozhraní IWICImagingFactory, která je uložená v globální data. Pokud není inicializována rozhraní, se vytvoří a má výchozí parametry.  
  
  
```  
IWICImagingFactory* GetWICFactory();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní IWICImagingFactory Pokud vytváření továrny neproběhne úspěšně, nebo hodnota NULL, pokud vytvoření nezdaří nebo aktuální operační systém nemají WIC podpory.  
  
## <a name="getwritefactory"></a> AFX_GLOBAL_DATA::GetWriteFactory
Vrací ukazatel na rozhraní IDWriteFactory, která je uložená v globální data. Pokud není inicializována rozhraní, se vytvoří a má výchozí parametry.  
  
  
```  
IDWriteFactory* GetWriteFactory();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní IDWriteFactory Pokud vytváření továrny neproběhne úspěšně, nebo hodnota NULL, pokud vytvoření nezdaří nebo aktuální operační systém nemají DirectWrite podpory.  
 
## <a name="initd2d"></a> AFX_GLOBAL_DATA::InitD2D
Inicializuje D2D DirectWrite a WIC objekty Factory. Tuto metodu volejte před inicializací hlavní okno.  
  
  
```  
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>Parametry   
 *d2dFactoryType*  
 Model vláken D2D tovární nastavení a prostředky vytvoří.  
  
 *writeFactoryType*  
 Hodnotu, která určuje, zda se objekt factory zápisu sdílené nebo izolované  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud objekty Factory měla intilalizrd, FALSE – jinak  
  
## <a name="is32biticons"></a> AFX_GLOBAL_DATA::Is32BitIcons
Označuje, zda jsou předdefinované ikony 32-bit.  
  
  
```  
BOOL Is32BitIcons() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud jsou podporovány předdefinované ikony 32-bit; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu `TRUE` Pokud rozhraní podporuje integrované ikony 32-bit a pokud operační systém podporuje 16 bitů na pixel nebo více, a pokud obrázky nejsou zobrazeny s vysokým kontrastem.  
  
## <a name="isaccessibilitysupport"></a> AFX_GLOBAL_DATA::IsAccessibilitySupport
Určuje, zda je povolena podpora Microsoft Active Accessibility.  
  
  
```  
BOOL IsAccessibilitySupport() const; 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud je povolena podpora usnadnění; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Microsoft Active Accessibility byl dřívější řešení pro zpřístupnění aplikací. Automatizace uživatelského rozhraní Microsoft je nový model usnadnění přístupu pro Microsoft Windows a je určený k vyřešení požadovaných produktů využívajících technologie usnadnění a automatizované testování nástroje.   
  
 Použití [AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport) metoda chcete povolit nebo zakázat podporu usnadnění.  
  

### <a name="see-also"></a>Viz také  
 [Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)

## <a name="isd2dinitialized"></a> AFX_GLOBAL_DATA::IsD2DInitialized
 Určuje, zda D2D byl inicializován  
  
  
```  
BOOL IsD2DInitialized() const; 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud byl inicializován D2D; jinak hodnota FALSE.  
  
## <a name="isdwmcompositionenabled"></a> AFX_GLOBAL_DATA::IsDwmCompositionEnabled
Poskytuje jednoduchý způsob, jak volat Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) metoda.  
  
  
```  
BOOL IsDwmCompositionEnabled();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud [Správce oken plochy](http://msdn.microsoft.com/library/windows/desktop/aa969540) složení (správce) je povoleno, jinak hodnota `FALSE`.  
  
### <a name="see-also"></a>Viz také    
 [Správce oken plochy](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [Zapnutí a řízení složení Správce oken plochy](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="ishighcontrastmode"></a> AFX_GLOBAL_DATA::IsHighContrastMode
 Označuje, zda jsou obrázky aktuálně zobrazený s vysokým kontrastem.    
```  
BOOL IsHighContrastMode() const; 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud jsou bitové kopie aktuálně zobrazený v režimu vysokého kontrastu černé nebo bílé; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 V režimu vysokého kontrastu černé okraje čelí světlým jsou bílé a je černá na pozadí. V režimu vysokého kontrastu bílé jsou černé okraje čelí světlým a je bílé pozadí.  
  
## <a name="iswindowslayersupportavailable"></a> AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
Určuje, zda operační systém podporuje vrstveného windows.  
  
  
```  
BOOL IsWindowsLayerSupportAvailable() const; 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud jsou podporovány vrstveného windows; v opačném `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud jsou podporovány vrstveného windows, *inteligentní ukotvení* značek použijte vrstveného windows.  
  
## <a name="m_busebuiltin32biticons"></a> AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
Označuje, zda rozhraní používá předdefinovanou 32bitové barvy ikony nebo ikony nižší rozlišení.  
  
  
```  
BOOL  m_bUseBuiltIn32BitIcons;  
```  
  
### <a name="remarks"></a>Poznámky  
 `TRUE` Určuje, že rozhraní používat 32bitové barvy ikony; `FALSE` určuje nižší rozlišení ikon. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena `TRUE`.  
  
 Tento člen musí být nastavená při spuštění aplikace.  
  
## <a name="m_busesystemfont"></a> AFX_GLOBAL_DATA::m_bUseSystemFont
Označuje, zda systém písmo pro pásů karet, nabídek a panelů nástrojů.  
  
  
```  
BOOL m_bUseSystemFont;  
```  
  
### <a name="remarks"></a>Poznámky  
 `TRUE` Určuje, pokud chcete použít systém písmo; v opačném `FALSE`. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena `FALSE`.  
  
 Tento člen testování není jedinou možností pro rozhraní k určení písmo, jak použít. `AFX_GLOBAL_DATA::UpdateFonts` Metoda otestováním také výchozí a alternativní písem určit jaké vizuální styly jsou k dispozici u pásů karet, nabídek a panelů nástrojů.  
  
## <a name="m_hcurhand"></a> AFX_GLOBAL_DATA::m_hcurHand
Uloží popisovač pro ruční kurzor.  
  
  
```  
HCURSOR m_hcurHand;  
```  
  
## <a name="m_hcurstretch"></a> AFX_GLOBAL_DATA::m_hcurStretch
Uloží popisovač pro vodorovné stretch kurzor.  
  
  
```  
HCURSOR m_hcurStretch;  
```  

## <a name="m_hcurstretchvert"></a> AFX_GLOBAL_DATA::m_hcurStretchVert
Uloží popisovač pro svislé stretch kurzor.  
  
  
```  
HCURSOR m_hcurStretchVert;  
```  
  
## <a name="m_hicontool"></a> AFX_GLOBAL_DATA::m_hiconTool
Uloží popisovač pro ikonu nástroj.  
  
  
```  
HICON m_hiconTool;  
```  
## <a name="m_nautohidetoolbarmargin"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
Určuje posun na panelu nástrojů krajní levé autohide – na levé straně na ukotvení panelu.  
  
  
```  
int  m_nAutoHideToolBarMargin;  
```  
  
### <a name="remarks"></a>Poznámky  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena 4 pixelů.  
  
## <a name="m_nautohidetoolbarspacing"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
Určuje mezery mezi autohide – panely nástrojů.  
  
  
```  
int   m_nAutoHideToolBarSpacing;  
```  
  
### <a name="remarks"></a>Poznámky  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena 14 pixelů.  
  
## <a name="m_ndragframethicknessdock"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Určuje tloušťku přetáhněte rámce, který slouží k označení ukotveného stavu.  
  
  
```  
int  m_nDragFrameThicknessDock;  
```  
  
### <a name="remarks"></a>Poznámky  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena 3 pixelů.  
  
## <a name="m_ndragframethicknessfloat"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
Určuje tloušťku přetáhněte rámce, který slouží k označení plovoucí stavu.  
  
  
```  
int  m_nDragFrameThicknessFloat;  
```  
  
### <a name="remarks"></a>Poznámky  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena 4 pixelů.  
  
## <a name="onsettingchange"></a> AFX_GLOBAL_DATA::OnSettingChange
Zjistí, aktuální stav nabídky animace a funkce autohide – panelu na ploše.  
  
  
```  
void OnSettingChange();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví framework proměnné stavu určité atributy plocha uživatele. Tato metoda zjišťuje aktuální stav nabídky animace, Objevování nabídky a úloh panelu autohide – funkce.  
  
## <a name="registerwindowclass"></a> AFX_GLOBAL_DATA::RegisterWindowClass
Zaregistruje zadanou třídu okna knihovny MFC.  
  
  
```  
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```  
  
### <a name="parameters"></a>Parametry   
 [v] *lpszClassNamePrefix*  
 Název třídy okno k registraci.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kvalifikovaný název registrované třídy, pokud tato metoda bude úspěšná; v opačném [výjimka zdrojů](http://msdn.microsoft.com/library/ddd99292-819b-4fa4-8371-b1954ed5856d).  
  
### <a name="remarks"></a>Poznámky  
 Vrácená hodnota je seznam oddělený dvojtečkou *lpszClassNamePrefix* řetězec parametrů a hexadecimální textové reprezentace obslužné rutiny pro zpracování aktuální instanci aplikace; kurzor aplikace, která je na šipku kurzor, jehož identifikátor je IDC_ARROW; a štětec pozadí plochy. Další informace o registrace tříd oken MFC najdete v tématu [afxregisterclass –](../../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
### <a name="see-also"></a>Viz také    
 [Afxregisterclass –](../../mfc/reference/application-information-and-management.md#afxregisterclass)   
 [Afxthrowresourceexception –](../../mfc/reference/exception-processing.md#afxthrowresourceexception)

## <a name="resume"></a> AFX_GLOBAL_DATA::Resume
 Znovu inicializuje ukazatele na interní funkce přistupují metody, které podporují Windows motivů a stylů. 
  
  
```  
BOOL Resume();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda bude úspěšná; v opačném `FALSE`. V režimu ladění tato metoda vyhodnotí, pokud tato metoda neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, když obdrží rozhraní [WM_POWERBROADCAST](http://msdn.microsoft.com/library/windows/desktop/aa373247) zprávy.  
  
## <a name="setlayeredattrib"></a> AFX_GLOBAL_DATA::SetLayeredAttrib
Poskytuje jednoduchý způsob, jak volat Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) metoda.  
  
  
```  
BOOL SetLayeredAttrib(
    HWND hwnd,  
    COLORREF crKey,  
    BYTE bAlpha,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry   
 [v] *hwnd*  
 Zpracování do okna vrstev.  
  
 [v] *crKey*  
 Průhledná barva klíče, který [Správce oken plochy](http://msdn.microsoft.com/library/windows/desktop/aa969540) používá k vytváření okna vrstev.  
  
 [v] *bAlpha*  
 Alfa hodnotu, která se používá k popisu krytí okno vrstev.  
  
 [v] *dwFlags*  
 Bitová kombinace (nebo) příznaky, které určují, které parametry metody používat. Zadejte LWA_COLORKEY používat *crKey* parametr jako průhledná barva. Zadejte LWA_ALPHA používat *bAlpha* parametr k určení krytí okno vrstev.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda bude úspěšná; v opačném `FALSE`.   
 
### <a name="see-also"></a>Viz také   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540)

## <a name="setmenufont"></a> AFX_GLOBAL_DATA::SetMenuFont
Vytvoří zadané logické písmo.  
  
  
```  
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry   
 [v] *lpLogFont*  
 Ukazatel na strukturu, která obsahuje atributy písma.  
  
 [v] *bHorz*  
 `TRUE` Chcete-li zadat, že text spuštěna vodorovně; `FALSE` chcete zadat text spuštěna svisle.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE` Pokud tato metoda bude úspěšná; v opačném `FALSE`. V režimu ladění tato metoda vyhodnotí, pokud tato metoda neúspěšná.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří vodorovné regulární písmo podtržené písmo, a tučné písmo, které se používají ve výchozích položek nabídky. Tato metoda vytvoří volitelně regulární svislé písmo. Další informace o logické písem najdete v tématu [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).  
  
## <a name="updatefonts"></a> AFX_GLOBAL_DATA::UpdateFonts
Reintializes logické písma, které používají rozhraní.  
  
  
```  
void UpdateFonts();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace o logické písem najdete v tématu `CFont::CreateFontIndirect`.  
  
## <a name="updatesyscolors"></a> AFX_GLOBAL_DATA::UpdateSysColors
Inicializuje barvy, barvy, štětce, pera a bitové kopie, které používají rozhraní.  
  
  
```  
void UpdateSysColors();
```  
  
## <a name="biswindows7"></a> AFX_GLOBAL_DATA::bIsWindows7
Určuje, zda se aplikace spouští pod Windows 7 nebo vyšší.  
  
  
```  
BOOL bIsWindows7;  
```  
  
## <a name="clractivecaptiongradient"></a> AFX_GLOBAL_DATA::clrActiveCaptionGradient
Určuje barvu barevného přechodu aktivní titulek. Obvykle se používá pro ukotvení podokna.  
  
  
```  
COLORREF clrActiveCaptionGradient;  
```  
  
## <a name="clrinactivecaptiongradient"></a> AFX_GLOBAL_DATA::clrInactiveCaptionGradient
Určuje barvu barevného přechodu neaktivním titulku. Obvykle se používá pro ukotvení podokna.  
  
  
```  
COLORREF clrInactiveCaptionGradient;  
```  
  
## <a name="getitaskbarlist"></a> AFX_GLOBAL_DATA::GetITaskbarList
Vytvoří a uloží v globálních datech ukazatel `ITaskBarList` rozhraní.  
  
  
```  
ITaskbarList *GetITaskbarList();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `ITaskbarList` rozhraní, pokud je úspěšné vytvoření úlohy panelu list objekt; `NULL` Pokud vytvoření nezdaří, nebo pokud aktuální operační systém je menší než Windows 7.  
  
## <a name="getitaskbarlist3"></a> AFX_GLOBAL_DATA::GetITaskbarList3
Vytvoří a uloží v globálních datech ukazatel `ITaskBarList3` rozhraní.  
  
  
```  
ITaskbarList3 *GetITaskbarList3();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `ITaskbarList3` rozhraní, pokud je úspěšné vytvoření úlohy panelu list objekt; `NULL` Pokud vytvoření nezdaří, nebo pokud aktuální operační systém je menší než Windows 7.  
  
## <a name="getshellautohidebars"></a> AFX_GLOBAL_DATA::GetShellAutohideBars
Určuje, že pozice prostředí automaticky skrýt řádky.  
  
  
```  
int GetShellAutohideBars();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celočíselná hodnota s kódovaného příznaky, které určují pozice automaticky skrýt řádky. Ho může kombinovat následující hodnoty: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.  
  
## <a name="releasetaskbarrefs"></a> AFX_GLOBAL_DATA::ReleaseTaskBarRefs
Verze rozhraní získaných pomocí `GetITaskbarList` a `GetITaskbarList3` metody.  
  
  
```  
void ReleaseTaskBarRefs();
```  
  
## <a name="shellcreateitemfromparsingname"></a> AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
Vytvoří a inicializuje objekt prostředí položky z analýzy názvu.  
  
  
```  
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,  
    IBindCtx *pbc,  
    REFIID riid,  
    void **ppv);
```  
  
### <a name="parameters"></a>Parametry   
 *pszPath*  
 [v] Ukazatel na zobrazovaný název.  
  
 *pbc*  
 Ukazatel na kontext vazby, které řídí operaci analýzy.  
  
 *riid*  
 Odkaz na rozhraní ID.  
  
 *ppv*  
 [out] Když tato funkce vrátí, obsahuje ukazatel rozhraní požadovaný v *riid*. Obvykle je `IShellItem` nebo `IShellItem2`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK v případě úspěšného; Chyba hodnotu, jinak hodnota.  

