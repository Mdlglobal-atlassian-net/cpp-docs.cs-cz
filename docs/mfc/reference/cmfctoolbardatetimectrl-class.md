---
title: "Třída CMFCToolBarDateTimeCtrl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
dev_langs: C++
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 60e9427b569c7f3e15b779b0764e0316945880b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl – třída
Tlačítka panelu nástrojů, který obsahuje ovládací prvek pro výběr data a času.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|Vytvoří `CMFCToolBarDateTimeCtrl` objektu.|  
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|Určuje, zda uživatele lze roztáhnout tlačítko při přizpůsobení. (Přepisuje [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched).)|  
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|Kopíruje vlastnosti z jiného tlačítka panelu nástrojů na tlačítko aktuální. (Přepisuje [CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom).)|  
|`CMFCToolBarDateTimeCtrl::DuplicateData`|Vyhrazeno pro budoucí použití.|  
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|Zkopíruje text tlačítka na panelu nástrojů k nabídce.|  
|`CMFCToolBarDateTimeCtrl::CreateObject`|Rozhraní používá k vytvoření dynamických instance tohoto typu třídy.|  
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|Načte první `CMFCToolBarDateTimeCtrl` objekt v aplikaci, která má zadaný příkaz ID.|  
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|Vrátí ukazatel do ovládacího prvku pro výběr data a času.|  
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|Načte popisovač okna, který je přidružen tlačítka panelu nástrojů. (Přepisuje [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd).)|  
|`CMFCToolBarDateTimeCtrl::GetThisClass`|Používá rozhraní k získání ukazatele na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objekt, který je přidružený tento typ třídy.|  
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|Získá vybrané časové z ovládacího prvku pro výběr data a času a vloží ho v zadané [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura.|  
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|Vrátí vybrané časové z tlačítko čas výběr ovládacího prvku, který má zadaný příkaz ID.|  
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|Určuje, jestli okrajem tlačítko se zobrazí, když uživatel vybere tlačítko. (Přepisuje [CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder).)|  
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|Určuje, zda tlačítko zpracovává [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávy. (Přepisuje [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand).)|  
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|Voláno rámcem při přidání tlačítka do **přizpůsobit** dialogové okno. (Přepisuje [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage).)|  
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|Voláno rámcem vypočítat velikost tlačítko pro zadané zařízení kontextu a ukotvení stavu. (Přepisuje [CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize).)|  
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|Voláno rámcem při vložení do nového panelu nástrojů na tlačítko. (Přepisuje [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd).)|  
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|Voláno rámcem, když uživatel klikne ovládací prvek. (Přepisuje [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick).)|  
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|Voláno rámcem při zpracovává nadřazené nástrojů `WM_CTLCOLOR` zprávy. (Přepisuje [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor).)|  
|`CMFCToolBarDateTimeCtrl::OnDraw`|Voláno rámcem k vykreslení tlačítko pomocí zadané styly a možnosti. (Přepisuje [CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw).)|  
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|Voláno rámcem k vykreslení tlačítko **příkazy** podokně **přizpůsobit** dialogové okno. (Přepisuje [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist).)|  
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|Voláno rámcem, pokud došlo ke změně globální písmo. (Přepisuje [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged).)|  
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|Voláno rámcem, pokud se přesune panel nástrojů nadřazené. (Přepisuje [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove).)|  
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|Voláno rámcem když se stane tlačítko viditelný nebo neviditelná. (Přepisuje [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow).)|  
|`CMFCToolBarDateTimeCtrl::OnSize`|Voláno rámcem, když nadřazené nástrojů změní jeho velikost nebo pozice a tato změna způsobí, že na tlačítko Změnit velikost. (Přepisuje [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize).)|  
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|Voláno rámcem po aktualizaci jeho text popisu tlačítka panelu nástrojů nadřazené. (Přepisuje [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip).)|  
|`CMFCToolBarDateTimeCtrl::Serialize`|Čte tento objekt z archivu nebo zapíše ho do archivu (přepíše [CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize).)|  
|`CMFCToolBarDateTimeCtrl::SetStyle`|Nastavuje styl tlačítka panelu nástrojů. (Přepisuje [CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle).)|  
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|Nastaví datum a čas v ovládacím prvku pro výběr čas.|  
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|Nastaví datum a čas ve všech instancích ovládacího prvku pro výběr času, které mají zadaný příkaz ID.|  
  
## <a name="remarks"></a>Poznámky  
 Příklad použití ovládací prvek pro výběr data a času naleznete v části ToolbarDateTimePicker ukázkový projekt. Informace o tom, jak přidat ovládací tlačítka na panely nástrojů najdete v tématu [návod: vložení ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxtoolbardatetimectrl.h  
  
##  <a name="canbestretched"></a>CMFCToolBarDateTimeCtrl::CanBeStretched  
 Určuje, zda uživatele lze roztáhnout tlačítko při přizpůsobení.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí hodnotu `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení rozhraní neumožňuje uživateli při přizpůsobení funkce stretch tlačítka panelu nástrojů. Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) tím, že se uživateli při přizpůsobení funkce stretch tlačítka panelu nástrojů datum a čas.  
  
##  <a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl  
 Vytvoří a inicializuje [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md) objektu.  
  
```  
CMFCToolBarDateTimeCtrl(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=0,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiID`  
 ID ovládacího prvku.  
  
 [v]`iImage`  
 Index bitové kopie na panelu nástrojů `CMFCToolBarImages` objektu.  
  
 [v]`dwStyle`  
 Styl `CMFCToolBarDateTimeCtrlImpl` okno, které se vytvoří, když uživatel klikne na tlačítko.  
  
 [v]`iWidth`  
 Šířka ovládacího prvku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tento objekt je inicializováno systémové datum a čas. Styl okna interní `CMFCToolBarDateTimeCtrlImpl` objekt zahrnuje `dwStyle` parametr a `WS_CHILD` a `WS_VISIBLE` styly. Tyto styly nelze změnit pomocí `CMFCToolBarDateTimeCtrl::SetStyle`. Použití `SetStyle` změnit styl `CMFCToolBarDateTimeCtrl` ovládacího prvku.  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt `CMFCToolBarDateTimeCtrl` třídy. Tento fragment kódu je součástí [nástrojů Výběr data a času ukázka](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]  
  
##  <a name="copyfrom"></a>CMFCToolBarDateTimeCtrl::CopyFrom  
 Kopíruje vlastnosti z jiného tlačítka panelu nástrojů na tlačítko aktuální.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`src`  
 Odkaz na tlačítko zdroj ze kterého chcete zkopírovat.  
  
### <a name="remarks"></a>Poznámky  
 Volejte tuto metodu pro kopírování jiný tlačítka panelu nástrojů do tohoto tlačítka panelu nástrojů. `src`musí být typu `CMFCToolBarDateTimeCtrl`.  
  
##  <a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl::ExportToMenuButton  
 Zkopíruje text tlačítka na panelu nástrojů k nabídce.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`menuButton`  
 Odkaz na tlačítko nabídky Cíl.  
  
### <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí hodnotu `TRUE`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepsání implementace třídy base ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) načtením řetězec prostředku, který je přidružený k příkazu ID ovládacího prvku. Další informace o řetězce prostředků najdete v tématu [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring).  
  
##  <a name="getbycmd"></a>CMFCToolBarDateTimeCtrl::GetByCmd  
 Načte první `CMFCToolBarDateTimeCtrl` objekt v aplikaci, která má zadaný příkaz ID.  
  
```  
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmd`  
 ID příkazu pro načtení tlačítka.  
  
### <a name="return-value"></a>Návratová hodnota  
 První `CMFCToolBarDateTimeCtrl` objekt v aplikaci, která má zadaný příkaz ID, nebo `NULL` Pokud žádné `CMFCToolBarDateTimeCtrl` objekty mají ID zadaného příkazu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda sdílené nástroj se používá metodami, jako [CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall) a [CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall) nastavit nebo získat data a času všech instancí času ovládací prvek výběru, které mají zadaný příkaz ID.  
  
##  <a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl  
 Vrátí ukazatel do ovládacího prvku pro výběr data a času.  
  
```  
CDateTimeCtrl* GetDateTimeCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na datum a čas ovládací prvek výběru; nebo `NULL` Pokud ovládací prvek neexistuje.  
  
### <a name="remarks"></a>Poznámky  
 `CMFCToolBarDateTimeCtrl` Třídy inicializuje `m_pWndDateTime` – datový člen při vložení `CMFCToolBarDateTimeCtrl` objektu do panelu nástrojů.  
  
##  <a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd  
 Načte popisovač okna, který je přidružen tlačítka panelu nástrojů.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač okna, který je přidružen tlačítka panelu nástrojů datum a čas.  
  
### <a name="remarks"></a>Poznámky  
 Přepíše tuto metodu [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd) metoda.  
  
##  <a name="gettime"></a>CMFCToolBarDateTimeCtrl::GetTime  
 Získá vybrané časové z přidružených datum a čas ovládací prvek pro výběr a umístí jej v zadané [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `[out] timeDest`  
 V první přetížení [COleDateTime třída](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který se zobrazí informace o systémovém čase. V druhé přetížení [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který se zobrazí informace o systémovém čase.  
  
 `[out] pTimeDest`  
 Ukazatel [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura přijímat informace o systémovém čase. Nesmí být `NULL`.  
  
### <a name="return-value"></a>Návratová hodnota  
 V první přetížení nenulové hodnoty, pokud čas je úspěšně zapsána do [COleDateTime třída](../../atl-mfc-shared/reference/coledatetime-class.md) objektu; jinak hodnota 0. V druhé a třetí přetížení, je vrácenou hodnotu `DWORD` který se rovná dwFlag člena, který byl nastaven v [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) struktury.  
  
### <a name="remarks"></a>Poznámky  
 Metoda nastaví [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) struktury člen dwFlags indikující, zda je nastaven pro výběr data a času datum a čas. Pokud se hodnota rovná GDT_NONE, ovládacího prvku nastavena na `no date` stav a používá styl DTS_SHOWNONE. Pokud se hodnota vrácená rovná GDT_VALID, systémového času je úspěšně uložen v cílovém umístění.  
  
##  <a name="gettimeall"></a>CMFCToolBarDateTimeCtrl::GetTimeAll  
 Vrátí čas vybraný uživatelem z tlačítko čas výběr ovládacího prvku, který má zadaný příkaz ID.  
  
```  
static BOOL GetTimeAll(
    UINT uiCmd,  
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,  
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,  
    LPSYSTEMTIME pTimeDest);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] uiCmd`  
 Určuje ID příkazu pro tlačítka panelu nástrojů.  
  
 `[out] timeDest`  
 V první přetížení [COleDateTime třída](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který se zobrazí informace o systémovém čase. V druhé přetížení [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který se zobrazí informace o systémovém čase.  
  
 `[out] pTimeDest`  
 Ukazatel [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura přijímat informace o systémovém čase. Nesmí být `NULL`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud rozhraní nelze najít tlačítka panelu nástrojů, která odpovídá ID příkazu, který `uiCmd`, je vrácenou hodnotu nula v první přetížení a GDT_NONE v další přetížení. Pokud je nalezen tlačítka panelu nástrojů, vrácená hodnota je stejná jako vrácená hodnota z volání [CMFCToolBarDateTimeCtrl::GetTime](#gettime) na toto tlačítko. Návratovou hodnotu nula nebo GDT_NONE může dojít, když na tlačítko je najít, což znamená, že volání `GetTime` nevrátil platné datum z jiného důvodu.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vyhledá tlačítka panelu nástrojů, který má zadaný příkaz ID a volání [CMFCToolBarDateTimeCtrl::GetTime](#gettime) metoda na toto tlačítko.  
  
##  <a name="havehotborder"></a>CMFCToolBarDateTimeCtrl::HaveHotBorder  
 Určuje, jestli okrajem tlačítko se zobrazí, když uživatel vybere tlačítko.  
  
```  
virtual BOOL HaveHotBorder() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě na tlačítko zobrazí jeho ohraničení, pokud vybraná; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda vrátí nenulovou hodnotu, pokud je ovládací prvek viditelný.  
  
##  <a name="notifycommand"></a>CMFCToolBarDateTimeCtrl::NotifyCommand  
 Určuje, zda tlačítko zpracovává [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávy.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iNotifyCode`  
 Oznámení, které souvisí s příkaz.  
  
### <a name="return-value"></a>Návratová hodnota  
 `TRUE`Pokud tlačítko zpracovává `WM_COMMAND` zprávy, nebo `FALSE` indikující, že zpráva měla by ji zpracovat panelu nástrojů nadřazené.  
  
### <a name="remarks"></a>Poznámky  
 Rozhraní framework volá tuto metodu, když je odeslání [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zpráva do nadřazeného okna.  
  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) zpracováním [dtn_datetimechange –](http://msdn.microsoft.com/library/windows/desktop/bb761737) oznámení. Ho aktualizuje stav interní čas a aktualizuje vlastnost čas všech `CMFCToolBarDateTimeCtrl` příkaz objektů se stejným ID.  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl::OnAddToCustomizePage  
 Voláno rámcem při přidání tlačítka do **přizpůsobit** dialogové okno.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace [CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage), pomocí kopírování vlastnosti z první datum a čas ovládacího prvku libovolný panel nástrojů, který má stejné ID příkazu, který jako tento objekt. Tato metoda se nic nestane. Pokud žádný panel nástrojů má ovládacího prvku datum a čas, který má stejné ID příkazu, který jako tento objekt.  
  
 Další informace o **přizpůsobit** dialogové okno, najdete v části [CMFCToolBarsCustomizeDialog třída](../../mfc/reference/cmfctoolbarscustomizedialog-class.md).  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd  
 Voláno rámcem při vložení do nového panelu nástrojů na tlačítko.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParent`  
 Nové nadřazené okno.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepsání implementace třídy base ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) opětovným vytvořením interní `CMFCToolBarDateTimeCtrlImpl` objektu.  
  
##  <a name="onclick"></a>CMFCToolBarDateTimeCtrl::OnClick  
 Voláno rámcem, když uživatel klikne ovládací prvek.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWnd`  
 Nepoužívá se.  
  
 [v]`bDelay`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud tlačítko zpracovává zprávy klikněte na tlačítko; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepsání implementace základní třídy [CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick), vrácením nenulovou hodnotu, pokud interní `CMFCToolBarDateTimeCtrlImpl` objekt je zobrazen.  
  
##  <a name="onctlcolor"></a>CMFCToolBarDateTimeCtrl::OnCtlColor  
 Voláno rámcem při zpracovává nadřazené nástrojů `WM_CTLCOLOR` zprávy.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pDC`  
 Kontext zařízení, který se zobrazí tlačítko.  
  
 [v]`nCtlColor`  
 Nepoužívá se.  
  
### <a name="return-value"></a>Návratová hodnota  
 Popisovač pro globální štětce, který používá rozhraní k vyplnění na pozadí na tlačítko.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepsání implementace základní třídy [CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)a pomocí nastavení textu a pozadí barvy kontextu zadaný zařízení na globální text a barvy pozadí v uvedeném pořadí.  
  
 Další informace o globální možnosti, které jsou k dispozici pro aplikaci najdete v tématu [afx_global_data – struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged  
 Voláno rámcem, pokud došlo ke změně globální písmo.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) tak, že změníte písmo ovládacího prvku na které globální písma.  
  
 Další informace o globální možnosti, které jsou k dispozici pro aplikaci najdete v tématu [afx_global_data – struktura](../../mfc/reference/afx-global-data-structure.md).  
  
##  <a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove  
 Voláno rámcem, pokud se přesune panel nástrojů nadřazené.  
  
```  
virtual void OnMove();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepíše výchozí implementaci třídy ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) tím, že aktualizuje pozici interní `CMFCToolBarDateTimeCtrlImpl` objektu.  
  
##  <a name="onshow"></a>CMFCToolBarDateTimeCtrl::OnShow  
 Voláno rámcem když se stane tlačítko viditelný nebo neviditelná.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`bShow`  
 Určuje, zda je tlačítko viditelná. Pokud tento parametr je `TRUE`, tlačítko je viditelné. Tlačítko, jinak hodnota není viditelný.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) tím, že pokud se zobrazuje na tlačítko `bShow` je `TRUE`. Tuto metodu, jinak hodnota skryje tlačítko.  
  
##  <a name="onsize"></a>CMFCToolBarDateTimeCtrl::OnSize  
 Voláno rámcem, když nadřazené nástrojů změní jeho velikost nebo pozice a tato změna způsobí, že na tlačítko Změnit velikost.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`iSize`  
 Nové šířka tlačítko v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přepíše výchozí implementaci třídy ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) tím, že aktualizuje velikost a umístění interního `CMFCToolBarDateTimeCtrlImpl` objektu.  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl::OnUpdateToolTip  
 Voláno rámcem po aktualizaci jeho text popisu tlačítka panelu nástrojů nadřazené.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`pWndParent`  
 Nadřazené okno.  
  
 [v]`iButtonIndex`  
 Index založený na nule tlačítka v nadřazené tlačítko kolekce.  
  
 [v]`wndToolTip`  
 Ovládací prvek, který zobrazí text popisku.  
  
 [out]`str`  
 A `CString` objekt, který přijme text aktualizované popisku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud metoda aktualizace text popisku; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda rozšiřuje základní třída implementace ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) tím, že zobrazuje text popisku, který je přidružen tlačítko. Pokud tlačítko není ukotven vodorovně, tato metoda neprovede žádnou akci a vrátí `FALSE`.  
  
##  <a name="settime"></a>CMFCToolBarDateTimeCtrl::SetTime  
 Nastaví datum a čas v ovládacím prvku pro výběr čas.  
  
```  
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] timeNew`  
 V první verzi, odkaz na [COleDateTime třída](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje čas, ke kterému bude nastavena ovládacího prvku. V druhé verzi ukazatel na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje čas, ke kterému bude nastavena ovládacího prvku.  
  
 `[in] pTimeNew`  
 Ukazatel [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která obsahuje dobu, na kterou bude nastavena ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví dobu v ovládacím prvku pro výběr data a času voláním [CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime).  
  
##  <a name="settimeall"></a>CMFCToolBarDateTimeCtrl::SetTimeAll  
 Nastaví datum a čas ve všech instancích ovládacího prvku pro výběr času, které mají zadaný příkaz ID.  
  
```  
static BOOL SetTimeAll(
    UINT uiCmd,  
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,  
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,  
    LPSYSTEMTIME pTimeNew=NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `[in] uiCmd`  
 Určuje ID příkazu pro tlačítka panelu nástrojů.  
  
 `[in] timeNew`  
 V první verzi [COleDateTime třída](../../atl-mfc-shared/reference/coledatetime-class.md) objekt, který obsahuje čas, ke kterému bude nastavena ovládacího prvku. V druhé verzi ukazatel na [CTime](../../atl-mfc-shared/reference/ctime-class.md) objekt, který obsahuje čas, ke kterému bude nastavena ovládacího prvku.  
  
 `[in] pTimeNew`  
 Ukazatel [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) struktura, která obsahuje dobu, na kterou bude nastavena ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tlačítka panelu nástrojů s ID určený příkaz bude hledat a nastaví dobu v ovládacím prvku pro výběr data a času voláním [CMFCToolBarDateTimeCtrl::SetTime](#settime).  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton – třída](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [Návod: Umístění ovládacích prvků na panely nástrojů](../../mfc/walkthrough-putting-controls-on-toolbars.md)



