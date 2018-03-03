---
title: "Třída CMFCDropDownToolbarButton | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
dev_langs:
- C++
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2f9481583c56676d206225ad76f8131c2a79821f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton – třída
Typ tlačítka panelu nástrojů, který se chová jako regulární tlačítko po klepnutí. Ale, otevře se panel nástrojů rozevíracího seznamu ( [CMFCDropDownToolBar třída](../../mfc/reference/cmfcdropdowntoolbar-class.md) Pokud uživatel stiskem tlačítka a obsahuje tlačítka panelu nástrojů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCDropDownToolbarButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|Vytvoří `CMFCDropDownToolbarButton` objektu.|  
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::CopyFrom](#copyfrom)|Kopíruje vlastnosti z jiného tlačítka panelu nástrojů na tlačítko aktuální. (Přepisuje [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCDropDownToolbarButton::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar)|Otevře se panel nástrojů rozevíracího seznamu.|  
|[CMFCDropDownToolbarButton::ExportToMenuButton](#exporttomenubutton)|Zkopíruje text tlačítka na panelu nástrojů k nabídce. (Přepisuje [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton).)|  
|[CMFCDropDownToolbarButton::GetDropDownToolBar](#getdropdowntoolbar)|Načte panelu nástrojů rozevíracího seznamu, který je přidružen tlačítko.|  
|`CMFCDropDownToolbarButton::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|Určuje, zda je aktuálně otevřených panelu nástrojů rozevíracího seznamu.|  
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|Určuje, zda tlačítko lze zobrazit pomocí rozšířených ohraničení. (Přepisuje [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).)|  
|[CMFCDropDownToolbarButton::OnCalculateSize](#oncalculatesize)|Voláno rámcem vypočítat velikost tlačítko pro zadané zařízení kontextu a ukotvení stavu. (Přepisuje [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|`CMFCDropDownToolbarButton::OnCancelMode`|Voláno rámcem pro zpracování [WM_CANCELMODE](http://msdn.microsoft.com/library/windows/desktop/ms632615) zprávy. (Přepisuje `CMCToolBarButton::OnCancelMode`.)|  
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|Voláno rámcem při vložení do nového panelu nástrojů na tlačítko. (Přepisuje [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCDropDownToolbarButton::OnClick](#onclick)|Voláno rámcem, když uživatel klikne na tlačítko myši. (Přepisuje [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|Voláno rámcem, když uživatel uvolní tlačítko myši. (Přepisuje [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup).)|  
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|Voláno rámcem při zpracovává nadřazené nástrojů `WM_HELPHITTEST` zprávy. (Přepisuje [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp).)|  
|[CMFCDropDownToolbarButton::OnCustomizeMenu](#oncustomizemenu)|Upraví zadaný nabídky, pokud aplikace zobrazí na panelu nástrojů nadřazené místní nabídky. (Přepisuje [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu).)|  
|[CMFCDropDownToolbarButton::OnDraw](#ondraw)|Voláno rámcem k vykreslení tlačítko pomocí zadané styly a možnosti. (Přepisuje [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|Voláno rámcem k vykreslení tlačítko **příkazy** podokně **přizpůsobit** dialogové okno. (Přepisuje [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCDropDownToolbarButton::Serialize](#serialize)|Čte tento objekt z archivu nebo zapíše ho do archivu. (Přepisuje [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|[CMFCDropDownToolbarButton::SetDefaultCommand](#setdefaultcommand)|Nastaví výchozí příkaz, který používá rozhraní, když uživatel klikne na tlačítko.|  
  
### <a name="data-members"></a>Datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|Určuje dobu, která uživatel musí podržte tlačítko myši směrem dolů, předtím, než se zobrazí panel nástrojů rozevíracího seznamu.|  
  
## <a name="remarks"></a>Poznámky  
 A `CMFCDropDownToolBarButton` se liší od obyčejnou tlačítko v tom, že má malou šipku v pravém horním rohu na tlačítko. Po výběru tlačítka panelu nástrojů rozevíracího seznamu, rozhraní zobrazí jeho ikonu na tlačítko panelu nástrojů nejvyšší úrovně (tlačítko s malou šipku v pravém dolním rohu).  
  
 Informace o tom, jak implementovat rozevírací seznam nástrojů najdete v tématu [CMFCDropDownToolBar třída](../../mfc/reference/cmfcdropdowntoolbar-class.md).  
  
 `CMFCDropDownToolBarButton` Objektu je možné exportovat do [CMFCToolBarMenuButton třída](../../mfc/reference/cmfctoolbarmenubutton-class.md) objektu a zobrazí jako tlačítka s nabídkou s místní nabídky.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxdropdowntoolbar.h  
  
##  <a name="copyfrom"></a>CMFCDropDownToolbarButton::CopyFrom  
 Kopíruje vlastnosti z jiného tlačítka panelu nástrojů na tlačítko aktuální.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`src`  
 Odkaz na tlačítko zdroj ze kterého chcete zkopírovat.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu pro kopírování jiný tlačítka panelu nástrojů do tohoto tlačítka panelu nástrojů. `src`musí být typu `CMFCDropDownToolbarButton`.  
  
##  <a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton  
 Vytvoří `CMFCDropDownToolbarButton` objektu.  
  
```  
CMFCDropDownToolbarButton();

 
CMFCDropDownToolbarButton(
    LPCTSTR lpszName,  
    CMFCDropDownToolBar* pToolBar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszName`  
 Výchozí text tlačítka.  
  
 [v]`pToolBar`  
 Ukazatel `CMFCDropDownToolBar` objekt, který se zobrazí, když uživatel stiskne tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Druhý přetížení konstruktoru zkopíruje do rozevírací tlačítko na první tlačítko panelu nástrojů, `pToolBar` určuje.  
  
 Obvykle tlačítka panelu nástrojů rozevíracího seznamu používá text z naposledy použitých tlačítka na panelu nástrojů, `pToolBar` určuje. Používá textem určeným parametrem `lpszName` při tlačítko je převést na tlačítka s nabídkou nebo se zobrazí v **příkazy** kartě **přizpůsobit** dialogové okno. Další informace o **přizpůsobit** dialogové okno, najdete v části [CMFCToolBarsCustomizeDialog třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCDropDownToolbarButton` třídy. Tento fragment kódu je součástí [Visual Studio Demo-ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]  
  
##  <a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::DropDownToolbar  
 Otevře se panel nástrojů rozevíracího seznamu.  
  
```  
BOOL DropDownToolbar(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Nadřazené okno rámce rozevíracího seznamu, nebo `NULL` používat nadřazeného okna tlačítka panelu nástrojů rozevíracího seznamu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je metoda úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 [CMFCDropDownToolbarButton::OnClick](#onclick) metoda volá tuto metodu k otevření panelu nástrojů rozevíracího seznamu, když uživatel stiskem tlačítka a obsahuje tlačítka panelu nástrojů.  
  
 Pomocí této metody vytvoří panelu nástrojů rozevíracího seznamu [CMFCDropDownFrame::Create](../../mfc/reference/cmfcdropdownframe-class.md#create) metoda. Pokud panelu nástrojů nadřazené ukotven ve svislém směru, tato metoda umisťuje panelu nástrojů rozevíracího seznamu buď na levé nebo pravé straně panelu nástrojů nadřazené, v závislosti na přizpůsobit. Tuto metodu, jinak hodnota umisťuje panelu nástrojů rozevíracího seznamu pod nadřazený panelu nástrojů.  
  
 Tato metoda selže, pokud `pWnd` je `NULL` a tlačítko panelu nástrojů rozevíracího seznamu nemá nadřazeného okna.  
  
##  <a name="exporttomenubutton"></a>CMFCDropDownToolbarButton::ExportToMenuButton  
 Zkopíruje text tlačítka na panelu nástrojů k nabídce.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`menuButton`  
 Odkaz na tlačítko nabídky Cíl.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud metoda úspěšně. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá implementace třídy base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) a poté na tlačítko nabídky Cíl připojí rozbalovací nabídky, které obsahuje každou položku nabídky panelu nástrojů v toto tlačítko. Tato metoda dílčí nabídky není připojení k místní nabídky.  
  
 Tato metoda selže, pokud panelu nástrojů nadřazené `m_pToolBar`, je `NULL` nebo základní třída implementace vrátí `FALSE`.  
  
##  <a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton::GetDropDownToolBar  
 Načte panelu nástrojů rozevíracího seznamu, který je přidružen tlačítko.  
  
```  
CMFCToolBar* GetDropDownToolBar() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Rozevírací seznam nástrojů, který je přidružen tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí hodnotu `m_pToolBar` – datový člen.  
  
##  <a name="isdropdown"></a>CMFCDropDownToolbarButton::IsDropDown  
 Určuje, zda je aktuálně otevřených panelu nástrojů rozevíracího seznamu.  
  
```  
BOOL IsDropDown() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je aktuálně otevřených; panel nástrojů rozevíracího seznamu jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní se otevře pomocí rozevíracího seznamu panelu nástrojů [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) metoda. Rozhraní framework zavře panelu nástrojů v rozevíracím, když uživatel stiskne tlačítko myši vlevo na neklientská oblast panelu nástrojů rozevíracího seznamu.  
  
##  <a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize  
 Určuje, zda tlačítko lze zobrazit pomocí rozšířených ohraničení.  
  
```  
virtual BOOL IsExtraSize() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud tlačítka panelu nástrojů lze zobrazit pomocí rozšířených ohraničení; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o rozšířených ohraničení najdete v tématu [CMFCToolBarButton::IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize).  
  
##  <a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay  
 Určuje dobu, která uživatel musí podržte tlačítko myši směrem dolů, předtím, než se zobrazí panel nástrojů rozevíracího seznamu.  
  
```  
static UINT m_uiShowBarDelay;  
```  
  
### <a name="remarks"></a>Poznámky  
 Doba zpoždění se měří v milisekundách. Výchozí hodnota je 500. Změnou hodnoty tento člen sdílená data, můžete nastavit jiný zpoždění.  
  
##  <a name="oncalculatesize"></a>CMFCDropDownToolbarButton::OnCalculateSize  
 Voláno rámcem vypočítat velikost tlačítko pro zadané zařízení kontextu a ukotvení stavu.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Kontext zařízení, který se zobrazí tlačítko.  
  
 [v]`sizeDefault`  
 Výchozí velikost tlačítka.  
  
 [v]`bHorz`  
 Stav ukotvení panelu nástrojů nadřazené. Tento parametr je `TRUE` Pokud panelu nástrojů ukotven vodorovně nebo je plovoucí, nebo `FALSE` Pokud panelu nástrojů ukotven svisle.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `SIZE` struktura, která obsahuje dimenze tlačítka v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) přidáním šířku na šipku rozevíracího seznamu na vodorovné dimenze velikosti tlačítko.  
  
##  <a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd  
 Voláno rámcem při vložení do nového panelu nástrojů na tlačítko.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParent`  
 Nové nadřazené okno.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepsání implementace třídy base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) tak, že smažete textový popisek ( [CMFCToolBarButton::m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) a nastavení [ CMFCToolBarButton::m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext) a [CMFCToolBarButton::m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton) datových členů ke `FALSE`.  
  
##  <a name="onclick"></a>CMFCDropDownToolbarButton::OnClick  
 Voláno rámcem, když uživatel klikne na tlačítko myši.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Nadřazené okno tlačítka panelu nástrojů.  
  
 [v]`bDelay`  
 `TRUE`Pokud zpráva má zacházet s zpožděním.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud tlačítko zpracovává zprávy klikněte na tlačítko; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), při aktualizaci stavu panelu nástrojů rozevíracího seznamu.  
  
 Když uživatel klikne na tlačítko panelu nástrojů, tato metoda vytvoří časovače, kterou čeká dobu určeného [CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay) – datový člen a pak otevře z rozevírací nabídky panelu nástrojů pomocí [CMFCDropDownToolbarButton::DropDownToolbar](#dropdowntoolbar) metoda. Tato metoda zavře panelu nástrojů rozevíracího seznamu podruhé uživatel klikne na tlačítko panelu nástrojů.  
  
##  <a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp  
 Voláno rámcem, když uživatel uvolní tlačítko myši.  
  
```  
virtual BOOL OnClickUp();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud tlačítko zpracovává zprávy klikněte na tlačítko; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace [CMFCToolBarButton::OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup), při aktualizaci stavu panelu nástrojů rozevíracího seznamu.  
  
 Tato metoda zastaví časovač nástrojů rozevíracího seznamu, pokud je aktivní. Pokud je otevřen toto okno zavře panelu nástrojů rozevíracího seznamu.  
  
 Další informace o panelu nástrojů rozevírací seznam a rozevírací seznam nástrojů časovače najdete v tématu [CMFCDropDownToolbarButton::OnClick](#onclick).  
  
##  <a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp  
 Voláno rámcem při zpracovává nadřazené nástrojů `WM_HELPHITTEST` zprávy.  
  
```  
virtual BOOL OnContextHelp(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Nadřazené okno tlačítka panelu nástrojů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud tlačítko zpracovává zprávy nápovědy; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) voláním [CMFCDropDownToolbarButton::OnClick](#onclick) metoda s `bDelay` nastavena na `FALSE` . Tato metoda vrátí hodnotu, která vrátí [CMFCDropDownToolbarButton::OnClick](#onclick).  
  
 Další informace o `WM_HELPHITTEST message, see` [TN028: podpora pomoci Context-Sensitive](../../mfc/tn028-context-sensitive-help-support.md).  
  
##  <a name="oncustomizemenu"></a>CMFCDropDownToolbarButton::OnCustomizeMenu  
 Upraví zadaný nabídky, pokud aplikace zobrazí na panelu nástrojů nadřazené místní nabídky.  
  
```  
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pMenu`  
 V nabídce přizpůsobit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí hodnotu `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnCustomizeMenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) zakázáním následující položky:  
  
- **Kopírovat vzhled tlačítka**  
  
- **Vzhled tlačítka**  
  
- **Obrázek**  
  
- **Text**  
  
- **Bitové kopie a Text.**  
  
 Potlačí tuto metodu za účelem upravit místní nabídky, která rozhraní zobrazuje v režimu vlastní nastavení.  
  
##  <a name="ondraw"></a>CMFCDropDownToolbarButton::OnDraw  
 Voláno rámcem k vykreslení tlačítko pomocí zadané styly a možnosti.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Kontext zařízení, který se zobrazí tlačítko.  
  
 [v]`rect`  
 Ohraničující obdélník tlačítko.  
  
 [v]`pImages`  
 Kolekce obrázků panelu nástrojů, který je přidružen tlačítko.  
  
 [v]`bHorz`  
 Stav ukotvení panelu nástrojů nadřazené. Tento parametr je `TRUE` když tlačítko ukotveno vodorovně a `FALSE` když tlačítko ukotveno svisle.  
  
 [v]`bCustomizeMode`  
 Určuje, zda je panel nástrojů v režimu vlastní nastavení. Tento parametr je `TRUE` po panelu nástrojů v režimu přizpůsobení a `FALSE` při panelu nástrojů není v režimu vlastní nastavení.  
  
 [v]`bHighlight`  
 Určuje, zda je označený na tlačítko. Tento parametr je `TRUE` když je označený na tlačítko a `FALSE` při není zvýrazněná tlačítko.  
  
 [v]`bDrawBorder`  
 Určuje, zda má na tlačítko zobrazit jeho ohraničení. Tento parametr je `TRUE` při tlačítko by měl zobrazit jeho ohraničení a `FALSE` při nesmí na tlačítko zobrazit jeho ohraničení.  
  
 [v]`bGrayDisabledButtons`  
 Určuje, jestli stín zakázané tlačítka nebo použijte kolekci zakázané bitové kopie. Tento parametr je `TRUE` při by měla být zakázané tlačítka šedou barvou a `FALSE` když tato metoda by měla použít kolekci zakázané bitové kopie.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu za účelem přizpůsobení panelu nástrojů tlačítko Kreslení.  
  
##  <a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList  
 Voláno rámcem k vykreslení tlačítko **příkazy** podokně **přizpůsobit** dialogové okno.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Kontext zařízení, který se zobrazí tlačítko.  
  
 [v]`rect`  
 Ohraničující obdélník tlačítko.  
  
 [v]`bSelected`  
 Jestli je vybraná tlačítko. Pokud tento parametr je `TRUE`, výběru tlačítka. Pokud tento parametr je `FALSE`, tlačítko není vybraná.  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka v pixelech tlačítko pro daný kontext zadané zařízení.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána přizpůsobení dialogových oken ( **příkazy** kartě) Pokud je tlačítko vyžadována k zobrazení sám sebe na pole se seznamem vykreslování vlastníka.  
  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) změnou textový popisek tlačítka na název tlačítka (to znamená na hodnotu `lpszName` parametr, který je předán konstruktoru).  
  
##  <a name="serialize"></a>CMFCDropDownToolbarButton::Serialize  
 Čte tento objekt z archivu nebo zapíše ho do archivu.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`ar`  
 `CArchive` Objekt, ze které nebo která k serializaci.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) serializací ID prostředku nadřazené panelu nástrojů. Při načítání archivu ( [CArchive::IsLoading](../../mfc/reference/carchive-class.md#isloading) vrátí nenulovou hodnotu), nastaví tato metoda `m_pToolBar` – datový člen na panelu nástrojů, který obsahuje ID serializovaných prostředku.  
  
##  <a name="setdefaultcommand"></a>CMFCDropDownToolbarButton::SetDefaultCommand  
 Nastaví výchozí příkaz, který používá rozhraní, když uživatel klikne na tlačítko.  
  
```  
void SetDefaultCommand(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu výchozí.  
  
### <a name="remarks"></a>Poznámky  
 Voláním této metody lze zadat výchozí příkaz, který rozhraní provede, když uživatel klikne na tlačítko. Položka s ID příkazu, který je určeného `uiCmd` se musí nacházet na panelu nástrojů nadřazené rozevíracího seznamu.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCDropDownToolBar – třída](../../mfc/reference/cmfcdropdowntoolbar-class.md)   
 [CMFCToolBar – třída](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBarMenuButton – třída](../../mfc/reference/cmfctoolbarmenubutton-class.md)   
 [Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)



