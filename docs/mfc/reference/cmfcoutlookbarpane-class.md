---
title: "Třída CMFCOutlookBarPane | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
dev_langs: C++
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 59eb92e44a26577866a797243f3a32d53b854365
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane – třída
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Ovládací prvek odvozen od [CMFCToolBar třída](../../mfc/reference/cmfctoolbar-class.md) , lze vložit do panel aplikace Outlook ( [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md)). V podokně panelu Outlook obsahuje sloupec velké tlačítek. Uživatel lze posunout nahoru a dolů seznam tlačítek, pokud je větší než v podokně. Když uživatel odpojí podokně panelu aplikace Outlook z panelu aplikace Outlook, dokáže float nebo ukotvení v hlavním okně rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCOutlookBarPane : public CMFCToolBar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|Výchozí konstruktor.|  
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCOutlookBarPane::AddButton](#addbutton)|Přidá tlačítko panelu řádku aplikace Outlook.|  
|[CMFCOutlookBarPane::CanBeAttached](#canbeattached)|Určuje, zda lze ukotvit podokně do jiného podokno nebo rámec okna. (Přepisuje [CBasePane::CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached).)|  
|`CMFCOutlookBarPane::CanBeRestored`|Určuje, zda systém obnovit panelu nástrojů do původního stavu po přizpůsobení. (Přepisuje [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|  
|[CMFCOutlookBarPane::ClearAll](#clearall)|Uvolní prostředky využívané třídou bitové kopie v podokně panelu aplikace Outlook.|  
|[CMFCOutlookBarPane::Create](#create)|Vytvoří v podokně panelu aplikace Outlook.|  
|`CMFCOutlookBarPane::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|`CMFCOutlookBarPane::Dock`|Voláno rámcem na ukotvení panelu řádku aplikace Outlook. (Přepisuje `CPane::Dock`.)|  
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Určuje, zda posouvacích šipek na panelu aplikace Outlook řádku zálohy seznamu tlačítka podle stránky, nebo tlačítko.|  
|[CMFCOutlookBarPane::GetRegularColor](#getregularcolor)|Vrátí barvu běžný text (bez výběru) podokně panelu aplikace Outlook.|  
|`CMFCOutlookBarPane::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Určuje, zda je obrázek pozadí načten pro podokně panelu aplikace Outlook.|  
|`CMFCOutlookBarPane::IsChangeState`|Určuje, zda může být ukotveno plovoucí podokně. (Přepisuje `CPane::IsChangeState`.)|  
|[CMFCOutlookBarPane::IsDrawShadedHighlight](#isdrawshadedhighlight)|Určuje, zda je tlačítko ohraničení šedou barvou při tlačítko zvýrazněn a zobrazí se obrázek na pozadí.|  
|`CMFCOutlookBarPane::OnBeforeFloat`|Voláno rámcem při podokno je o float. (Přepisuje [CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat).)|  
|[CMFCOutlookBarPane::RemoveButton](#removebutton)|Odebere tlačítka, který má zadaný příkaz ID.|  
|`CMFCOutlookBarPane::RestoreOriginalstate`|Obnoví původní stav panelu nástrojů. (Přepisuje [CMFCToolBar::RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate).)|  
|[CMFCOutlookBarPane::SetBackColor](#setbackcolor)|Nastaví barvu pozadí.|  
|[CMFCOutlookBarPane::SetBackImage](#setbackimage)|Nastaví obrázku pozadí.|  
|[CMFCOutlookBarPane::SetDefaultState](#setdefaultstate)|Obnoví původní sadu tlačítek panelu řádku aplikace Outlook.|  
|[CMFCOutlookBarPane::SetExtraSpace](#setextraspace)|Nastaví počet pixelů odsazení používá kolem tlačítka v podokně panelu aplikace Outlook.|  
|[CMFCOutlookBarPane::SetTextColor](#settextcolor)|Nastaví barvy text regulární a zvýrazněných v podokně panelu aplikace Outlook.|  
|[CMFCOutlookBarPane::SetTransparentColor](#settransparentcolor)|Nastaví průhlednou barvu v podokně panelu aplikace Outlook.|  
|`CMFCOutlookBarPane::SmartUpdate`|Interně používá k aktualizaci panelu aplikace Outlook. (Přepisuje `CMFCToolBar::SmartUpdate`.)|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCOutlookBarPane::EnableContextMenuItems](#enablecontextmenuitems)|Určuje, které položky místní nabídky se zobrazí v režimu vlastní nastavení.|  
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Odebere všechny tlačítek z panelu řádku aplikace Outlook. (Přepisuje [CMFCToolBar::RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons).)|  
  
## <a name="remarks"></a>Poznámky  
 Informace o tom, jak implementovat panel aplikace Outlook najdete v tématu [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).  
  
 Příklad panel aplikace Outlook najdete v části OutlookDemo ukázkový projekt.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak pomocí různých metod `CMFCOutlookBarPane` třídy. Tento příklad ukazuje, jak vytvořit podokně panelu aplikace Outlook, povolte režim scroll stránky, povolit ukotvení a nastavit barvu pozadí panelu aplikace Outlook. Tento fragment kódu je součástí [ukázkové aplikace Outlook více zobrazení](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxoutlookbarpane.h  
  
##  <a name="addbutton"></a>CMFCOutlookBarPane::AddButton  
 Přidá tlačítko panelu řádku aplikace Outlook.  
  
```  
BOOL AddButton(
    UINT uiImage,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    UINT uiImage,  
    UINT uiLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    LPCTSTR szBmpFileName,  
    LPCTSTR szLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HBITMAP hBmp,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1);

 
BOOL AddButton(
    HICON hIcon,  
    LPCTSTR lpszLabel,  
    UINT iIdCommand,  
    int iInsertAt=-1,  
    BOOL bAlphaBlend=FALSE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiImage`  
 Určuje identifikátor prostředku bitmapy.  
  
 [v]`lpszLabel`  
 Určuje text, na tlačítko.  
  
 [v]`iIdCommand`  
 Určuje ID ovládacího prvku tlačítko.  
  
 [v]`iInsertAt`  
 Na stránce panelu aplikace outlook, kam chcete vložit tlačítko Určuje index založený na nule.  
  
 [v]`uiLabel`  
 Řetězec prostředku.  
  
 [v]`szBmpFileName`  
 Určuje název souboru bitové kopie disku načíst.  
  
 [v]`szLabel`  
 Určuje text, na tlačítko.  
  
 [v]`hBmp`  
 Popisovač pro rastrový obrázek na tlačítko.  
  
 [v]`hIcon`  
 Popisovač pro ikonu tlačítka.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud byl úspěšně; přidán tlačítka v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Tuto metodu použijte k vložení nového tlačítka na panelu aplikace Outlook stránku. Obrázek na tlačítko se dají načíst z prostředky aplikace nebo z soubor na disku.  
  
 Pokud ID stránky určuje `uiPageID` je -1, na tlačítko se vloží do na první stránku.  
  
 Pokud index zadaný `iInsertAt` je -1, na tlačítko se přidá na konci stránky.  
  
##  <a name="canbeattached"></a>CMFCOutlookBarPane::CanBeAttached  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="clearall"></a>CMFCOutlookBarPane::ClearAll  
 Uvolní prostředky využívané třídou bitové kopie v podokně panelu aplikace Outlook.  
  
```  
void ClearAll();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá přímo [CMFCToolBarImages::Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear), která je volána pro Image, které jsou používány v podokně panelu aplikace Outlook.  
  
##  <a name="create"></a>CMFCOutlookBarPane::Create  
 Vytvoří v podokně panelu aplikace Outlook.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT uiID=(UINT)-1,  
    DWORD dwControlBarStyle=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pParentWnd`  
 Určuje nadřazeného okna Ovládací prvek panelu podokně aplikace Outlook. Nesmí být `NULL`.  
  
 [v]`dwStyle`  
 Styl okna.  Seznam styly oken, naleznete v části [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [v]`uiID`  
 ID ovládacího prvku. Musí být jedinečný pro povolení ukládání stavu ovládacího prvku.  
  
 [v]`dwControlBarStyle`  
 Určuje zvláštní stylů, které definují chování ovládacího prvku panel podokně Outlook, když je odpojený od panelu aplikace Outlook.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud metoda byla úspěšná. v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 K vytvoření `CMFCOutlookBarPane` objekt, první volání konstruktoru a pak zavolají `Create`, který vytvoří Outlook panelu Ovládací prvek podokna a připojí jej k `CMFCOutlookBarPane` objektu.  
  
 Další informace o `dwControlBarStyle` najdete v části [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
##  <a name="enablecontextmenuitems"></a>CMFCOutlookBarPane::EnableContextMenuItems  
 Určuje, které položky místní nabídky se zobrazí v režimu vlastní nastavení.  
  
```  
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,  
    CMenu* pPopup);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pButton`  
 Ukazatel na tlačítka panelu nástrojů, který klikl na uživatele.  
  
 [v]`pPopup`  
 Ukazatel na místní nabídky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `TRUE` Pokud zobrazené; jinak hodnota by měla být v místní nabídce `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu k úpravě framework standardní místní nabídky, která rozhraní zobrazuje v režimu vlastní nastavení.  
  
 Výchozí implementace kontroluje režimu přizpůsobení ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) a pokud je nastaven na hodnotu `TRUE`, zakáže všechny položky místní nabídky kromě **odstranit**. Potom ho jednoduše předají vstupní parametry, které chcete `CMFCToolBar::EnableContextMenuItems`.  
  
> [!NOTE]
> *Kontextové nabídky* je synonymum pro místní nabídky.  
  
##  <a name="enablepagescrollmode"></a>CMFCOutlookBarPane::EnablePageScrollMode  
 Určuje, zda posouvacích šipek na panelu aplikace Outlook řádku zálohy seznamu tlačítka po stránkách nebo tlačítko pomocí tlačítka.  
  
```  
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bPageScroll`  
 Pokud `TRUE`, povolte režim scroll stránky. Pokud `FALSE`, zakázat režim scroll stránky.  
  
##  <a name="getregularcolor"></a>CMFCOutlookBarPane::GetRegularColor  
 Vrátí běžné (tedy bez vybrané) Barva textu v podokně panelu aplikace Outlook.  
  
```  
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální barvy jako hodnotu barva RGB.  
  
### <a name="remarks"></a>Poznámky  
 Použití [CMFCOutlookBarPane::SetTextColor](#settextcolor) nastavit aktuální barva textu (normální a vybrané) na panelu aplikace Outlook. Výchozí barvy můžete získat pomocí volání [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) fungovat s `COLOR_WINDOW` index.  
  
##  <a name="isbackgroundtexture"></a>CMFCOutlookBarPane::IsBackgroundTexture  
 Určuje, zda je obrázek pozadí načten pro podokně panelu aplikace Outlook.  
  
```  
BOOL IsBackgroundTexture() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud je obrázek pozadí zobrazíte; v opačném případě `FALSE`.  
  
### <a name="remarks"></a>Poznámky  
 Můžete přidat obrázek pozadí voláním [CMFCOutlookBarPane::SetBackImage](#setbackimage) funkce.  
  
 Pokud žádný obrázek na pozadí, pozadí se vykresluje barvou zadat pomocí [CMFCOutlookBarPane::SetBackColor](#setbackcolor).  
  
##  <a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane::IsDrawShadedHighlight  
 Určuje, zda je tlačítko ohraničení šedou barvou při tlačítko zvýrazněn a zobrazí se obrázek na pozadí.  
  
```  
BOOL IsDrawShadedHighlight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud jsou zobrazena šedě; okraje tlačítka v opačném případě `FALSE`.  
  
##  <a name="removeallbuttons"></a>CMFCOutlookBarPane::RemoveAllButtons  
 Odebere všechny tlačítek z panelu řádku aplikace Outlook.  
  
```  
virtual void RemoveAllButtons();
```  
  
##  <a name="removebutton"></a>CMFCOutlookBarPane::RemoveButton  
 Odebere tlačítka, který má zadaný příkaz ID.  
  
```  
BOOL RemoveButton(UINT iIdCommand);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iIdCommand`  
 Určuje ID příkazového tlačítka s odebrat.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud tlačítko byla úspěšně odebrána; `FALSE` Pokud zadaný příkaz ID je neplatné.  
  
##  <a name="setbackcolor"></a>CMFCOutlookBarPane::SetBackColor  
 Nastaví barvu pozadí panelu aplikace Outlook.  
  
```  
void SetBackColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`color`  
 Určuje barvu pozadí nové.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto funkci nastavit aktuální barvu pozadí panelu aplikace Outlook. Barva pozadí se používá pouze v případě, že neexistuje žádný obrázek pozadí.  
  
##  <a name="setbackimage"></a>CMFCOutlookBarPane::SetBackImage  
 Nastaví obrázku pozadí.  
  
```  
void SetBackImage(UINT uiImageID);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiImageID`  
 Určuje ID prostředku bitové kopie.  
  
### <a name="remarks"></a>Poznámky  
 Volat tuto metodu a nastavit možnost aplikace Outlook obrázek pozadí panelu. Seznam obrázky na pozadí probíhá podle vložený [CMFCToolBarImages třída](../../mfc/reference/cmfctoolbarimages-class.md) objektu.  
  
##  <a name="setdefaultstate"></a>CMFCOutlookBarPane::SetDefaultState  
 Obnoví původní sadu tlačítek panelu řádku aplikace Outlook.  
  
```  
void SetDefaultState();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda obnoví původní sadu tlačítek na panelu aplikace Outlook. Tato metoda je jako `CMFCOutlookBarPane::RestoreOriginalstate`kromě toho, že neaktivuje překreslování podokně panelu aplikace Outlook.  
  
##  <a name="setextraspace"></a>CMFCOutlookBarPane::SetExtraSpace  
 Nastaví počet pixelů odsazení používá kolem tlačítka v podokně panelu aplikace Outlook.  
  
```  
void SetExtraSpace()  
```  
  
##  <a name="settextcolor"></a>CMFCOutlookBarPane::SetTextColor  
 Nastaví barvy text regulární a zvýrazněných v podokně panelu aplikace Outlook.  
  
```  
void SetTextColor(
    COLORREF clrRegText,  
    COLORREF clrSelText=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`clrRegText`  
 Určuje barvu nové-vybraný text.  
  
 [v]`clrSelText`  
 Určuje barvu nové pro vybraný text.  
  
##  <a name="settransparentcolor"></a>CMFCOutlookBarPane::SetTransparentColor  
 Nastaví průhlednou barvu v podokně panelu aplikace Outlook.  
  
```  
void SetTransparentColor(COLORREF color);
```  
  
### <a name="parameters"></a>Parametry  
 `color`  
 Určuje průhlednou barvu nové.  
  
### <a name="remarks"></a>Poznámky  
 Průhledná barva je vyžadována k zobrazení průhledné obrázky. Kterýkoli z výskytů tato barva do image je vykresluje barvou pozadí místo.  Není žádný prolnutí popředí a na pozadí bitové kopie.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CMFCOutlookBarTabCtrl – třída](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
