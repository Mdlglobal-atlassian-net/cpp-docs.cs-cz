---
title: Afx_global_data – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
ms.openlocfilehash: 1d762aef0dd48f3eac8eaeeddee558c4f237b29f
ms.sourcegitcommit: 220fd4fda829f810e15fc1a1d98ab43c46201b47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2018
ms.locfileid: "43352736"
---
# <a name="afxglobaldata-structure"></a>AFX_GLOBAL_DATA – struktura
`AFX_GLOBAL_DATA` Struktura obsahuje pole a metody, které se používají ke správě rozhraní nebo upravit vzhled a chování aplikace.  
  
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
|[AFX_GLOBAL_DATA::Cleanup](#cleanup)|Uvolní prostředky, které jsou přiděleny v rámci rozhraní, jako jsou štětce, písma a knihovny DLL.|  
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Vytvoří otočení transformace, který otáčí podle zadaného úhlu kolem Zadaný bod.|  
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Nakreslí pozadí nadřazeného ovládacího prvku v určené oblasti.|  
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Vykreslí zadaný text ve vizuální styl zadaný motiv.|  
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Odebere zadanou dvojici značky XML ze zadané vyrovnávací paměti.|  
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Načte aktuální barvu prvek zadaného uživatelského rozhraní.|  
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Vrací ukazatel `ID2D1Factory` rozhraní, která je uložena v globálních datech. Pokud není inicializována rozhraní, je vytvořen a má výchozí parametry.|  
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Načte předdefinované kurzor, který vypadá podobně jako na tvar ruky a jehož identifikátor je `IDC_HAND`.|  
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Vytvoří a uloží v globálních datech ukazatel ITaskBarList rozhraní.|  
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Vytvoří a uloží v globálních datech ukazatel ITaskBarList3 rozhraní.|  
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Získá metriky související s neklientskou oblast nonminimized windows.|  
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Určuje umístění prostředí automaticky skrýt pruhy.|  
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Získá výšku textové znaky v aktuálním písmem.|  
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Vrací ukazatel `IWICImagingFactory` rozhraní, která je uložena v globálních datech. Pokud není inicializována rozhraní, je vytvořen a má výchozí parametry.|  
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Vrací ukazatel `IDWriteFactory` rozhraní, která je uložena v globálních datech. Pokud není inicializována rozhraní, je vytvořen a má výchozí parametry.|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Inicializuje `D2D`, `DirectWrite`, a `WIC` objekty pro vytváření. Tuto metodu volejte před dokončením inicializace hlavního okna.|  
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Označuje, zda jsou předdefinované 32-bit ikony.|  
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Určuje, zda `D2D` byl inicializován.|  
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Poskytuje jednoduchý způsob, jak volat Windows [DwmIsCompositionEnabled](/windows/desktop/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) metody.|  
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Určuje, zda Image jsou aktuálně zobrazeny s vysokým kontrastem.|  
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Zjistí aktuální stav nabídky animace a funkcí automatické skrývání hlavním panelu ploše.|  
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Zaregistruje zadanou třídu okna knihovny MFC.|  
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Uvolní rozhraní, které získali prostřednictvím GetITaskbarList a GetITaskbarList3 metody.|  
|[AFX_GLOBAL_DATA::Resume](#resume)|Znovu inicializuje ukazatele interních funkcí, které přístup k metodám, které podporují Windows [motivů a stylů](/windows/desktop/Controls/visual-styles-overview).|  
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Poskytuje jednoduchý způsob, jak volat Windows [SetLayeredWindowAttributes](https://msdn.microsoft.com/library/windows/desktop/ms633540) metody.|  
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Vytvoří zadané logické písma.|  
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Vytvoří a inicializuje objekt prostředí položky z názvu analýzy.|  
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reintializes logické písma, které se používají v rámci rozhraní.|  
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicializuje barvy, barevnou hloubku, štětce, pera a bitové kopie, které se používají v rámci rozhraní.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Povolí nebo zakáže Microsoft Active Accessibility podporu. Active Accessibility poskytuje spolehlivé metody pro odhalení informací o prvky uživatelského rozhraní.|  
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Určuje, zda je povolena podpora Microsoft Active Accessibility.|  
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Určuje, zda operační systém podporuje vrstvami windows.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Určuje, zda aktuální operační systém podporuje alfa míchání.|  
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Určuje, zda aplikace se provádí v rámci operačního systému Windows 7 nebo vyšší|  
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Určuje barvu barevného přechodu aktivní titulek. Obvykle se používá pro ukotvení podoken.|  
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Určuje barvu barevného přechodu neaktivním titulku aktivní. Obvykle se používá pro ukotvení podoken.|  
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Označuje, zda rozhraní používá ikony předdefinované 32bitové barvy nebo ikony nižší rozlišení.|  
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Určuje, zda je pro nabídky, panely nástrojů a pásů karet použít systémové písmo.|  
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Uloží popisovač pro kurzor ručně.|  
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Uloží popisovač pro vodorovné roztáhnout kurzoru.|  
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Uloží popisovač pro vertikální roztáhnout kurzoru.|  
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Uloží popisovač pro ikonu nástroj.|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Určuje posun od nejvíce vlevo automaticky skrývat panel nástrojů k levému okraji dokovací panel.|  
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Určuje mezeru mezi panely nástrojů automaticky skrývat.|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Určuje tloušťku přetáhněte rámce, který se používá ke komunikaci ukotvených stavu.|  
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Určuje tloušťku přetáhněte rámce, který se používá ke komunikaci s plovoucí desetinnou čárkou stavu.|  
  
### <a name="remarks"></a>Poznámky  
 Většina dat `AFX_GLOBAL_DATA` struktura je inicializován při spuštění aplikace.  
  
### <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `AFX_GLOBAL_DATA`   
  
### <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxglobals.h  
  
### <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


## <a name="bisosalphablendingsupport"></a> AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
Určuje, zda operační systém podporuje alfa míchání.  
  
  
```  
BOOL  bIsOSAlphaBlendingSupport;  
```  
  
### <a name="remarks"></a>Poznámky  
 Hodnota TRUE označuje, že je podporovaný alfa míchání; v opačném případě hodnota FALSE.  
  

## <a name="cleanup"></a> AFX_GLOBAL_DATA::Cleanup
Uvolní prostředky, které jsou přiděleny v rámci rozhraní, jako jsou štětce, písma a knihovny DLL.  
  
  
```  
void CleanUp();
```  
## <a name="d2d1makerotatematrix"></a> AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
Vytvoří otočení transformace, který otáčí podle zadaného úhlu kolem Zadaný bod.  
  
  
```  
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,  
    D2D1_POINT_2F center,  
    D2D1_MATRIX_3X2_F *matrix);
```  
  
### <a name="parameters"></a>Parametry   
 *úhel*  
 Úhel po směru hodinových ručiček otočení ve stupních.  
  
 *System Center*  
 Bod o tom, které otočí.  
  
 *matice*  
 Po návratu metody obsahuje nové transformace otočení. Pro tento parametr, musíte přidělit úložiště.  
  
### <a name="return-value"></a>Návratová hodnota  
 V opačném případě vrátí hodnotu S_OK v případě úspěchu nebo chybovou hodnotu.  
  
## <a name="drawparentbackground"></a> AFX_GLOBAL_DATA::DrawParentBackground
Nakreslí pozadí nadřazeného ovládacího prvku v určené oblasti.  
  
  
```  
BOOL DrawParentBackground(
    CWnd* pWnd,   
    CDC* pDC,   
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *pWnd*  
 Ukazatel na okno ovládacího prvku.  
  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
 [in] *lprect –*  
 Ukazatel na obdélník, který oblasti pro kreslení za rozsahem. Výchozí hodnota je NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.  
  
## <a name="drawtextonglass"></a> AFX_GLOBAL_DATA::DrawTextOnGlass
Vykreslí zadaný text ve vizuální styl zadaný motiv.  
  
  
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
 [in] *hTheme*  
 Zpracování dat motiv okna, nebo hodnotu NULL. Rozhraní používá zadaný motiv vykreslování textu, pokud tento parametr není NULL a motivy podporují. V opačném případě rozhraní framework nepoužívá motiv vykreslování textu.  
  
 Použití [OpenThemeData](/windows/desktop/api/uxtheme/nf-uxtheme-openthemedata) metodu pro vytvoření HTHEME.  
  
 [in] *primárního řadiče domény*  
 Ukazatel na kontext zařízení.  
  
 [in] *iPartId*  
 Ovládací prvek součást, která má vzhled požadovaný text. Další informace najdete v tématu části sloupce v tabulce v [částí a stavy](https://msdn.microsoft.com/library/windows/desktop/bb773210). Pokud tato hodnota je 0, text je vykreslen v výchozí písmo nebo písmo vybrané do kontextu zařízení.  
  
 [in] *iStateId*  
 Stav ovládacího prvku, která má vzhled požadovaný text. Další informace najdete v tématu stavy sloupec tabulky v [částí a stavy](https://msdn.microsoft.com/library/windows/desktop/bb773210).  
  
 [in] *strText*  
 Text, chcete-li nakreslit.  
  
 [in] *rect*  
 Hranice v oblasti, ve které je vykresleno zadaným textem.  
  
 [in] *dwFlags*  
 Bitová kombinace (OR) mezi příznaky, které určují, jak je vykreslen zadaným textem.  
  
 Pokud *hTheme* parametr je `NULL` nebo pokud nejsou podporované a povolení motivů *nFormat* parametr [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext) popisuje platnými – metoda Příznaky. Pokud jsou podporovány motivy, *dwFlags* parametr [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex) metoda popisuje platné příznaky.  
  
 [in] *nGlowSize*  
 Velikost záře efekt, který je vykreslen na pozadí před kreslením zadaný text. Výchozí hodnota je 0.  
  
 [in] *clrText*  
 Barva, ve které je vykresleno zadaným textem. Výchozí hodnota je výchozí barvy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud, motiv se používá k nakreslení zadaný text; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Motiv určuje vizuální styl aplikace. Motiv se nepoužívá k vykreslování textu, pokud *hTheme* parametr hodnotu NULL, nebo pokud [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex) metoda není podporována, nebo pokud [Správce oken plochy](/windows/desktop/dwm/dwm-overview) složení (DWM) je zakázané.  
  
### <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COLORREF](/windows/desktop/gdi/colorref)   
 [Části a stavy](https://msdn.microsoft.com/library/windows/desktop/bb773210)   
 [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext)   
 [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex)   
 [Správce oken plochy](/windows/desktop/dwm/dwm-overview)   
 [Povolit a řídit kompozici DWM](/windows/desktop/dwm/composition-ovw)

## <a name="enableaccessibilitysupport"></a> AFX_GLOBAL_DATA::EnableAccessibilitySupport
Povolí nebo zakáže Microsoft Active Accessibility podporu.  
  
  
```  
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *bEnable*  
 TRUE, pokud chcete povolit podporu pro usnadnění; FALSE, pokud chcete zakázat podporu usnadnění přístupu. Výchozí hodnota je TRUE.  
  
### <a name="remarks"></a>Poznámky  
 Active Accessibility je technologie založené na modelu COM, které zlepší způsob, jakým programy a pracovní operačního systému Windows společně s produktů využívajících technologie usnadnění. Poskytuje spolehlivé metody pro odhalení informací o prvky uživatelského rozhraní. Novější model usnadnění volá automatizace uživatelského rozhraní Microsoft je však nyní k dispozici. Porovnání dvou technologie najdete v tématu [automatizace uživatelského rozhraní a Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).  
  
 Použití [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport) metodou ke zjištění, zda je povolena podpora společnosti Microsoft věnovaném usnadnění aktivní.  
  
 
### <a name="see-also"></a>Viz také  
 [Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)   
 [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)

## <a name="excludetag"></a> AFX_GLOBAL_DATA::ExcludeTag
Odebere zadanou dvojici značky XML ze zadané vyrovnávací paměti.  
  
  
```  
BOOL ExcludeTag(
    CString& strBuffer,  
    LPCTSTR lpszTag,  
    CString& strTag,  
    BOOL bIsCharsList = FALSE);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *strBuffer*  
 Vyrovnávací paměť textu.  
  
 [in] *lpszTag*  
 Název páru počátečních a koncových značek XML.  
  
 [out] *strTag*  
 Po návratu tato metoda *strTag* parametr obsahuje text, který je mezi otevírací a zavírací XML značky, které jsou pojmenovány podle *lpszTag* parametru. Ořízne všechny počáteční ani koncové prázdné znaky z výsledku.  
  
 [in] *bIsCharsList*  
 True pro převod symbolů pro řídicí znaky v *strTag* parametr do skutečné řídicí znaky; FALSE, nedojde k provedení převodu. Výchozí hodnota je FALSE. Další informace najdete v části poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Pár značek XML se skládá z s názvem počátečních a koncových značek, které označují začátek a konec běhu textu v zadané vyrovnávací paměti. *StrBuffer* parametr určuje vyrovnávací paměti a *lpszTag* parametr určuje název značky XML.  
  
 Symboly v následující tabulce použijte ke kódování sady řídicí znaky v zadané vyrovnávací paměti. Zadejte hodnotu TRUE pro *bIsCharsList* parametr se převést symboly v *strTag* parametr do skutečné řídicí znaky. V následující tabulce používá [_T()](../../c-runtime-library/data-type-mappings.md) – makro k určení symbolu a řídicí znak řetězce.  
  
|Symbol|Řídicí znak|  
|------------|----------------------|  
|_T ("\\\t")|_T("\t")|  
|_T ("\\\n")|_T("\n")|  
|_T ("\\\r")|_T("\r")|  
|_T ("\\\b")|_T("\b")|  
|_T("LT")|_T ("\<")|  
|_T("GT")|_T("&GT;")|  
|_T("AMP")|_T("&AMP;")|  
  
## <a name="getcolor"></a> AFX_GLOBAL_DATA::GetColor
Načte aktuální barvu prvek zadaného uživatelského rozhraní.  
  
  
```  
COLORREF GetColor(int nColor);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *nColor*  
 Hodnota, která určuje prvek uživatelského rozhraní, jejichž barva se načítají. Seznam platných hodnot najdete v tématu *nIndex* parametr [GetSysColor](https://msdn.microsoft.com/library/windows/desktop/ms724371) metody.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota barvy RGB elementu zadaného uživatelského rozhraní. Další informace najdete v části poznámky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *nColor* parametr je mimo rozsah, vrácená hodnota je nula. Protože nula je také platné hodnoty RGB, tuto metodu nelze použít k určení, zda je podporován systémové barvy podle aktuálního operačního systému. Místo toho použijte [GetSysColorBrush](/windows/desktop/api/winuser/nf-winuser-getsyscolorbrush) metodu, která vrátí hodnotu NULL, pokud není podporovaná barvu.  
  
### <a name="see-also"></a>Viz také  

 [GetSysColor – funkce](https://msdn.microsoft.com/library/windows/desktop/ms724371)   
 [COLORREF](/windows/desktop/gdi/colorref)   
 [GetSysColorBrush](/windows/desktop/api/winuser/nf-winuser-getsyscolorbrush)

## <a name="getdirect2dfactory"></a> AFX_GLOBAL_DATA::GetDirect2dFactory
 Vrací ukazatel na rozhraní ID2D1Factory, která je uložena v globálních datech. Pokud není inicializována rozhraní, je vytvořen a má výchozí parametry.  
  
  
```  
ID2D1Factory* GetDirect2dFactory();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní ID2D1Factory Pokud vytvoření objekt pro vytváření proběhne úspěšně, nebo hodnota NULL, pokud se nezdaří vytváření nebo aktuální operační systém nemají podporu D2D.  
  
## <a name="gethandcursor"></a>  AFX_GLOBAL_DATA::GetHandCursor
Načte předdefinované kurzor, který vypadá podobně jako na tvar ruky a jehož identifikátor je IDC_HAND.  
  
  
```  
HCURSOR GetHandCursor();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač kurzor ručně.  

## <a name="getnonclientmetrics"></a> AFX_GLOBAL_DATA::GetNonClientMetrics
Získá metriky související s neklientskou oblast nonminimized windows.  
  
  
```  
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```  
  
### <a name="parameters"></a>Parametry   
 [out v] *informace*  
 A [NONCLIENTMETRICS](https://msdn.microsoft.com/library/windows/desktop/ff729175) strukturu, která obsahuje škálovatelné metriky související s neklientské oblasti okna nonminimized.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda uspěje; v opačném případě hodnota FALSE.  
 
  
### <a name="see-also"></a>Viz také   
 [Struktura NONCLIENTMETRICS](https://msdn.microsoft.com/library/windows/desktop/ff729175)

## <a name="gettextheight"></a> AFX_GLOBAL_DATA::GetTextHeight
 Získá výšku textové znaky v aktuálním písmem.  
  
  
```  
int GetTextHeight(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *bHorz*  
 TRUE, pokud chcete načíst výška znaků při spuštění text vodorovně. FALSE, pokud chcete načíst výška znaků při spuštění text svisle. Výchozí hodnota je TRUE.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výška aktuální písmo, které je měřená od jeho horní dotah k jeho spodním dotahem.  
  
## <a name="getwicfactory"></a> AFX_GLOBAL_DATA::GetWICFactory
Vrací ukazatel na rozhraní IWICImagingFactory, která je uložena v globálních datech. Pokud není inicializována rozhraní, je vytvořen a má výchozí parametry.  
  
  
```  
IWICImagingFactory* GetWICFactory();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní IWICImagingFactory Pokud vytvoření objekt pro vytváření proběhne úspěšně, nebo hodnota NULL, pokud se nezdaří vytváření nebo aktuální operační systém nemají WIC podpory.  
  
## <a name="getwritefactory"></a> AFX_GLOBAL_DATA::GetWriteFactory
Vrací ukazatel na rozhraní IDWriteFactory, která je uložena v globálních datech. Pokud není inicializována rozhraní, je vytvořen a má výchozí parametry.  
  
  
```  
IDWriteFactory* GetWriteFactory();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rozhraní IDWriteFactory Pokud vytvoření objekt pro vytváření proběhne úspěšně, nebo hodnota NULL, pokud se nezdaří vytváření nebo aktuální operační systém nemají podporu DirectWrite.  
 
## <a name="initd2d"></a> AFX_GLOBAL_DATA::InitD2D
Inicializuje D2D DirectWrite a WIC továren. Tuto metodu volejte před dokončením inicializace hlavního okna.  
  
  
```  
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>Parametry   
 *d2dFactoryType*  
 Model vláken objektu pro vytváření D2D a prostředky, které vytvoří.  
  
 *writeFactoryType*  
 Hodnota, která určuje, zda bude objekt factory zápisu sdílené nebo izolovaný režim  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu TRUE, pokud továren byly intilalizrd, hodnota FALSE – v opačném případě  
  
## <a name="is32biticons"></a> AFX_GLOBAL_DATA::Is32BitIcons
Označuje, zda jsou předdefinované 32-bit ikony.  
  
  
```  
BOOL Is32BitIcons() const;

 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud jsou podporovány předdefinované ikony 32-bit; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu TRUE, pokud rozhraní framework podporuje 32bitové integrované ikony a pokud operační systém podporuje 16 bitů na pixel nebo informace a obrázky nejsou zobrazeny ve vysokém kontrastu.  
  
## <a name="isaccessibilitysupport"></a> AFX_GLOBAL_DATA::IsAccessibilitySupport
Určuje, zda je povolena podpora Microsoft Active Accessibility.  
  
  
```  
BOOL IsAccessibilitySupport() const; 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud je povolena podpora pro usnadnění; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Microsoft Active Accessibility byl starší řešení pro zpřístupnění aplikace. Automatizace uživatelského rozhraní Microsoft je nový model dostupnost pro Microsoft Windows a má sloužit k řešení potřeb produktů využívajících technologie usnadnění a automatizované testovací nástroje.   
  
 Použití [AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport) metoda k povolení nebo zakázání Active Accessibility podpory.  
  

### <a name="see-also"></a>Viz také  
 [Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)

## <a name="isd2dinitialized"></a> AFX_GLOBAL_DATA::IsD2DInitialized
 Určuje, zda byl inicializován D2D  
  
  
```  
BOOL IsD2DInitialized() const; 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud byl inicializován D2D; v opačném případě FALSE.  
  
## <a name="isdwmcompositionenabled"></a> AFX_GLOBAL_DATA::IsDwmCompositionEnabled
Poskytuje jednoduchý způsob, jak volat Windows [DwmIsCompositionEnabled](/windows/desktop/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) metody.  
  
  
```  
BOOL IsDwmCompositionEnabled();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE v případě [Správce oken plochy](/windows/desktop/dwm/dwm-overview) složené je povoleno; jinak FALSE.  
  
### <a name="see-also"></a>Viz také    
 [Správce oken plochy](/windows/desktop/dwm/dwm-overview)   
 [Povolit a řídit kompozici DWM](/windows/desktop/dwm/composition-ovw)

## <a name="ishighcontrastmode"></a> AFX_GLOBAL_DATA::IsHighContrastMode
 Určuje, zda Image jsou aktuálně zobrazeny s vysokým kontrastem.    
```  
BOOL IsHighContrastMode() const; 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud Image jsou aktuálně zobrazeny v režimu vysokého kontrastu černé nebo bílé; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 V režimu Vysoký kontrast – černá hrany směřující světla jsou bílé a na pozadí je černá. V režimu Vysoký kontrast – bílá hrany směřující světla jsou černá a bude bílé pozadí.  
  
## <a name="iswindowslayersupportavailable"></a> AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
Určuje, zda operační systém podporuje vrstvami windows.  
  
  
```  
BOOL IsWindowsLayerSupportAvailable() const; 
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud se vrstvený windows jsou podporovány. v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Pokud se vrstvený windows se podporují, *inteligentního dokování* značky použití časových období vrstvami.  
  
## <a name="m_busebuiltin32biticons"></a> AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
Označuje, zda rozhraní používá ikony předdefinované 32bitové barvy nebo ikony nižší rozlišení.  
  
  
```  
BOOL  m_bUseBuiltIn32BitIcons;  
```  
  
### <a name="remarks"></a>Poznámky  
 Hodnota TRUE Určuje, zda rozhraní používat 32-bit barevných ikon; FALSE určuje nižší rozlišení ikon. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena na hodnotu TRUE.  
  
 Tento člen musí být nastaven na spuštění aplikace.  
  
## <a name="m_busesystemfont"></a> AFX_GLOBAL_DATA::m_bUseSystemFont
Určuje, zda je pro nabídky, panely nástrojů a pásů karet použít systémové písmo.  
  
  
```  
BOOL m_bUseSystemFont;  
```  
  
### <a name="remarks"></a>Poznámky  
 Hodnota TRUE určuje použít systémové písmo; v opačném případě hodnota FALSE. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tohoto člena na hodnotu FALSE.  
  
 Testování tohoto člena není jedině pro rozhraní k určení písmo použít. `AFX_GLOBAL_DATA::UpdateFonts` Metoda otestováním také výchozí a alternativní písma k určení, jaké vizuální styly jsou k dispozici u nabídek, panelů nástrojů a pásů karet.  
  
## <a name="m_hcurhand"></a> AFX_GLOBAL_DATA::m_hcurHand
Uloží popisovač pro kurzor ručně.  
  
  
```  
HCURSOR m_hcurHand;  
```  
  
## <a name="m_hcurstretch"></a> AFX_GLOBAL_DATA::m_hcurStretch
Uloží popisovač pro vodorovné roztáhnout kurzoru.  
  
  
```  
HCURSOR m_hcurStretch;  
```  

## <a name="m_hcurstretchvert"></a> AFX_GLOBAL_DATA::m_hcurStretchVert
Uloží popisovač pro vertikální roztáhnout kurzoru.  
  
  
```  
HCURSOR m_hcurStretchVert;  
```  
  
## <a name="m_hicontool"></a> AFX_GLOBAL_DATA::m_hiconTool
Uloží popisovač pro ikonu nástroj.  
  
  
```  
HICON m_hiconTool;  
```  
## <a name="m_nautohidetoolbarmargin"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
Určuje posun od nejvíce vlevo automaticky skrývat panel nástrojů na levou stranu panelu ukotvení.  
  
  
```  
int  m_nAutoHideToolBarMargin;  
```  
  
### <a name="remarks"></a>Poznámky  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tento člen pro 4 pixelů.  
  
## <a name="m_nautohidetoolbarspacing"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
Určuje mezeru mezi panely nástrojů automaticky skrývat.  
  
  
```  
int   m_nAutoHideToolBarSpacing;  
```  
  
### <a name="remarks"></a>Poznámky  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tento člen pro 14 pixelů.  
  
## <a name="m_ndragframethicknessdock"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Určuje tloušťku přetáhněte rámce, který se používá k označení ukotvených stavu.  
  
  
```  
int  m_nDragFrameThicknessDock;  
```  
  
### <a name="remarks"></a>Poznámky  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tento člen pro 3 pixelů.  
  
## <a name="m_ndragframethicknessfloat"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
Určuje tloušťku přetáhněte rámce, který se používá k označení stavu s plovoucí desetinnou čárkou.  
  
  
```  
int  m_nDragFrameThicknessFloat;  
```  
  
### <a name="remarks"></a>Poznámky  
 `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` Konstruktor inicializuje tento člen pro 4 pixelů.  
  
## <a name="onsettingchange"></a> AFX_GLOBAL_DATA::OnSettingChange
Zjistí aktuální stav nabídky animace a funkcí automatické skrývání hlavním panelu ploše.  
  
  
```  
void OnSettingChange();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda nastaví proměnné framework do stavu určité atributy plocha uživatele. Tato metoda zjišťuje aktuální stav nabídky animace, fade nabídky a hlavním panelu Automatické skrývání funkcí.  
  
## <a name="registerwindowclass"></a> AFX_GLOBAL_DATA::RegisterWindowClass
Zaregistruje zadanou třídu okna knihovny MFC.  
  
  
```  
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *lpszClassNamePrefix*  
 Název třídy okna k registraci.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kvalifikovaný název registrované třídy, pokud tato metoda bude úspěšná; v opačném případě [prostředků výjimka](https://msdn.microsoft.com/library/ddd99292-819b-4fa4-8371-b1954ed5856d).  
  
### <a name="remarks"></a>Poznámky  
 Vrácená hodnota je seznam oddělit středníkem *lpszClassNamePrefix* parametr řetězce a reprezentace šestnáctkového textu zpracovává aktuální instance aplikace; aplikace kurzor, který je na šipku kurzor, jehož identifikátor je IDC_ARROW; a štětec pozadí. Další informace o registrace tříd oken MFC naleznete v tématu [afxregisterclass –](../../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
### <a name="see-also"></a>Viz také    
 [Afxregisterclass –](../../mfc/reference/application-information-and-management.md#afxregisterclass)   
 [Afxthrowresourceexception –](../../mfc/reference/exception-processing.md#afxthrowresourceexception)

## <a name="resume"></a> AFX_GLOBAL_DATA::Resume
 Znovu inicializuje ukazatele interních funkcí, které přístup k metodám, které podporují používání motivů Windows a vizuální styly. 
  
  
```  
BOOL Resume();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda uspěje; v opačném případě hodnota FALSE. V režimu ladění tato metoda vyhodnotí, pokud tato metoda neúspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána, když obdrží rozhraní [WM_POWERBROADCAST](/windows/desktop/Power/wm-powerbroadcast) zprávy.  
  
## <a name="setlayeredattrib"></a> AFX_GLOBAL_DATA::SetLayeredAttrib
Poskytuje jednoduchý způsob, jak volat Windows [SetLayeredWindowAttributes](https://msdn.microsoft.com/library/windows/desktop/ms633540) metody.  
  
  
```  
BOOL SetLayeredAttrib(
    HWND hwnd,  
    COLORREF crKey,  
    BYTE bAlpha,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *hwnd*  
 Popisovač okna vrstvami.  
  
 [in] *crKey*  
 Průhledná barva klíče, který [Správce oken plochy](/windows/desktop/dwm/dwm-overview) používá k vytvoření okna vrstvami.  
  
 [in] *bAlpha*  
 Alfa hodnotu, která se používá k popisu krytí okně vrstvami.  
  
 [in] *dwFlags*  
 Bitová kombinace (OR) mezi příznaky, které určují, které metoda parametry se mají použít. Zadejte LWA_COLORKEY používat *crKey* parametr jako průhlednou barvu. Zadejte LWA_ALPHA používat *bAlpha* parametr k určení krytí okně vrstvami.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda uspěje; v opačném případě hodnota FALSE.   
 
### <a name="see-also"></a>Viz také   
 [COLORREF](/windows/desktop/gdi/colorref)   
 [SetLayeredWindowAttributes](https://msdn.microsoft.com/library/windows/desktop/ms633540)

## <a name="setmenufont"></a> AFX_GLOBAL_DATA::SetMenuFont
Vytvoří zadané logické písma.  
  
  
```  
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry   
 [in] *lpLogFont*  
 Ukazatel na strukturu, která obsahuje atributy písma.  
  
 [in] *bHorz*  
 TRUE, pokud chcete zadat, že text spuštěna vodorovně. FALSE, pokud chcete zadat, že text svisle spuštěna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud metoda uspěje; v opačném případě hodnota FALSE. V režimu ladění tato metoda vyhodnotí, pokud tato metoda neúspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vytvoří vodorovné regulární písmo podtržené písmo, a použít tučné písmo, které je ve výchozím položky nabídky. Tato metoda volitelně vytváří pravidelné svislé písma. Další informace o logické písma, naleznete v tématu [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).  
  
## <a name="updatefonts"></a> AFX_GLOBAL_DATA::UpdateFonts
Reintializes logické písma, které se používají v rámci rozhraní.  
  
  
```  
void UpdateFonts();
```  
  
### <a name="remarks"></a>Poznámky  
 Další informace o logické písma, naleznete v tématu `CFont::CreateFontIndirect`.  
  
## <a name="updatesyscolors"></a> AFX_GLOBAL_DATA::UpdateSysColors
Inicializuje barvy, barevnou hloubku, štětce, pera a bitové kopie, které se používají v rámci rozhraní.  
  
  
```  
void UpdateSysColors();
```  
  
## <a name="biswindows7"></a> AFX_GLOBAL_DATA::bIsWindows7
Určuje, zda aplikace se provádí v rámci Windows 7 nebo vyšší.  
  
  
```  
BOOL bIsWindows7;  
```  
  
## <a name="clractivecaptiongradient"></a> AFX_GLOBAL_DATA::clrActiveCaptionGradient
Určuje barvu barevného přechodu aktivní titulek. Obvykle se používá pro ukotvení podoken.  
  
  
```  
COLORREF clrActiveCaptionGradient;  
```  
  
## <a name="clrinactivecaptiongradient"></a> AFX_GLOBAL_DATA::clrInactiveCaptionGradient
Určuje barvu barevného přechodu v neaktivním titulku. Obvykle se používá pro ukotvení podoken.  
  
  
```  
COLORREF clrInactiveCaptionGradient;  
```  
  
## <a name="getitaskbarlist"></a> AFX_GLOBAL_DATA::GetITaskbarList
Vytvoří a uloží v globálních datech ukazatel `ITaskBarList` rozhraní.  
  
  
```  
ITaskbarList *GetITaskbarList();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `ITaskbarList` rozhraní, pokud bude úspěšné vytvoření úlohy panelu objekt seznamu; Pokud se vytváření nezdaří, nebo pokud aktuální operační systém je menší než Windows 7 s hodnotou NULL.  
  
## <a name="getitaskbarlist3"></a> AFX_GLOBAL_DATA::GetITaskbarList3
Vytvoří a uloží v globálních datech ukazatel `ITaskBarList3` rozhraní.  
  
  
```  
ITaskbarList3 *GetITaskbarList3();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel `ITaskbarList3` rozhraní, pokud bude úspěšné vytvoření úlohy panelu objekt seznamu; Pokud se vytváření nezdaří, nebo pokud aktuální operační systém je menší než Windows 7 s hodnotou NULL.  
  
## <a name="getshellautohidebars"></a> AFX_GLOBAL_DATA::GetShellAutohideBars
Určuje umístění prostředí automaticky skrýt pruhy.  
  
  
```  
int GetShellAutohideBars();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Celočíselná hodnota s kódováním příznaky, které určují umístění automaticky skrýt pruhy. To může kombinovat následující hodnoty: AFX_AUTOHIDE_BOTTOM AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.  
  
## <a name="releasetaskbarrefs"></a> AFX_GLOBAL_DATA::ReleaseTaskBarRefs
Uvolní rozhraní získaných `GetITaskbarList` a `GetITaskbarList3` metody.  
  
  
```  
void ReleaseTaskBarRefs();
```  
  
## <a name="shellcreateitemfromparsingname"></a> AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
Vytvoří a inicializuje objekt prostředí položky z názvu analýzy.  
  
  
```  
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,  
    IBindCtx *pbc,  
    REFIID riid,  
    void **ppv);
```  
  
### <a name="parameters"></a>Parametry   
 *pszPath*  
 [in] Ukazatel na zobrazované jméno.  
  
 *pbc*  
 Ukazatel na kontext vazby, který řídí operace analýzy.  
  
 *riid*  
 Odkaz na identifikátor rozhraní.  
  
 *ppv*  
 [out] Když se tato funkce vrátí, obsahuje ukazatel rozhraní požadovaný v *riid*. Obvykle půjde `IShellItem` nebo `IShellItem2`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu S_OK v případě úspěchu; jinak chybovou hodnotu.  

