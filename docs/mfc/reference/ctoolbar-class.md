---
title: "Ctoolbar – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
dev_langs: C++
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dec2dac93dae9860dfadd347584fbdf465d15838
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ctoolbar-class"></a>Ctoolbar – třída
Ovládací pruhy, které mají řádek rastrové obrázky tlačítek a volitelné oddělovačů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CToolBar : public CControlBar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CToolBar::CToolBar](#ctoolbar)|Vytvoří `CToolBar` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CToolBar::CommandToIndex](#commandtoindex)|Vrátí index tlačítka s ID daného příkazu.|  
|[CToolBar::Create](#create)|Vytvoří panelu nástrojů systému Windows a připojí jej k `CToolBar` objektu.|  
|[CToolBar::CreateEx](#createex)|Vytvoří `CToolBar` objekt s další styly pro vložený `CToolBarCtrl` objektu.|  
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Načte ID, stylu a bitové kopie počet tlačítko.|  
|[CToolBar::GetButtonStyle](#getbuttonstyle)|Načte styl pro tlačítko.|  
|[CToolBar::GetButtonText](#getbuttontext)|Načte text, který se zobrazí na tlačítko.|  
|[CToolBar::GetItemID](#getitemid)|Vrátí ID příkazu, který tlačítka nebo oddělovače v daném indexu.|  
|[CToolBar::GetItemRect](#getitemrect)|Načte rámeček zobrazení pro položku na daném indexu.|  
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|Umožňuje přímý přístup k podkladové běžného ovládacího prvku.|  
|[CToolBar::LoadBitmap](#loadbitmap)|Načte bitovou mapu obsahující obrázky rastrového obrázku tlačítka.|  
|[CToolBar::LoadToolBar](#loadtoolbar)|Načte prostředek panelu nástrojů vytvořené pomocí editoru prostředků.|  
|[CToolBar::SetBitmap](#setbitmap)|Nastaví rastrové bitové kopie.|  
|[CToolBar::SetButtonInfo](#setbuttoninfo)|Nastaví ID, stylu a bitové kopie počet tlačítko.|  
|[CToolBar::SetButtons](#setbuttons)|Nastaví tlačítko styly a index bitové kopie tlačítko v rámci bitové mapy.|  
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Nastavuje styl pro tlačítko.|  
|[CToolBar::SetButtonText](#setbuttontext)|Nastaví text, který se zobrazí tlačítko.|  
|[CToolBar::SetHeight](#setheight)|Nastaví výšku panelu nástrojů.|  
|[CToolBar::SetSizes](#setsizes)|Nastaví velikosti tlačítek a jejich rastrové obrázky.|  
  
## <a name="remarks"></a>Poznámky  
 Tlačítka může fungovat jako tlačítek, zaškrtněte políčko tlačítka nebo přepínače. `CToolBar`objekty jsou obvykle embedded členy oken s rámečkem objektů odvozených od třídy [CFrameWnd](../../mfc/reference/cframewnd-class.md) nebo [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).  
  
 [CToolBar::GetToolBarCtrl](#gettoolbarctrl), členské funkce nové MFC 4.0, můžete využít výhod podpory Windows běžné ovládacího prvku pro přizpůsobení panelu nástrojů a další funkce. `CToolBar`Členské funkce získáte většinu funkcí běžných ovládacích prvků Windows; ale při volání `GetToolBarCtrl`, můžete udělit panelech nástrojů i více vlastností panelů nástrojů systému Windows 95/98. Při volání `GetToolBarCtrl`, vrátí odkaz na `CToolBarCtrl` objektu. V tématu [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) pro další informace o návrhu panely nástrojů použití běžných ovládacích prvků Windows. Další obecné informace o běžných ovládacích prvcích najdete v tématu [běžné ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb775493) ve Windows SDK.  
  
 Visual C++ nabízí dvě metody pro vytvoření panelu nástrojů. Pokud chcete vytvořit prostředek panelu nástrojů editoru prostředků, postupujte takto:  
  
1.  Vytvořte prostředek panelu nástrojů.  
  
2.  Vytvořit `CToolBar` objektu.  
  
3.  Volání [vytvořit](#create) (nebo [CreateEx](#createex)) funkce panelu nástrojů systému Windows a vytvořte jej do `CToolBar` objektu.  
  
4.  Volání [loadtoolbar –](#loadtoolbar) načíst prostředek panelu nástrojů.  
  
 Jinak postupujte podle těchto kroků:  
  
1.  Vytvořit `CToolBar` objektu.  
  
2.  Volání [vytvořit](#create) (nebo [CreateEx](#createex)) funkce panelu nástrojů systému Windows a vytvořte jej do `CToolBar` objektu.  
  
3.  Volání [loadbitmap –](#loadbitmap) načíst rastrový obrázek, který obsahuje obrázek tlačítka panelu nástrojů.  
  
4.  Volání [setbuttons –](#setbuttons) k nastavení stylů tlačítek a každé tlačítko přidružit image v souboru bitové mapy.  
  
 Všechny Image tlačítka na panelu nástrojů jsou převzaty z jedné bitové mapy, které musí obsahovat jednu bitovou kopii pro každé tlačítko. Všechny Image musí mít stejnou velikost; Výchozí hodnota je 16 pixelů a 15 pixelů. Bitové kopie musí být vedle sebe v souboru bitové mapy.  
  
 `SetButtons` Funkce přebírá ukazatel na pole ID ovládacích prvků a celé číslo, které určuje počet prvků v poli. Funkce se nastaví na hodnotu odpovídající element pole ID každé tlačítko a přiřadí každé tlačítko index bitové kopie, který určuje pozici na tlačítko image v souboru bitové mapy. Pokud k elementu pole má hodnotu **ID_SEPARATOR**, je přiřazen žádný index bitové kopie.  
  
 Pořadí bitové kopie v souboru bitové mapy je obvykle pořadí, ve kterém jsou vykreslovány na obrazovce, ale můžete použít [SetButtonInfo](#setbuttoninfo) funkce změnit vztah mezi pořadí bitové kopie a pořadí vykreslování.  
  
 Všechny tlačítek na panelu nástrojů, mají stejnou velikost. Výchozí hodnota je 24 × 22 pixelů, v souladu s *Windows rozhraní pokyny pro návrh softwaru*. Žádné další prostor mezi dimenzemi bitové kopie a tlačítko se používá k vytvoření ohraničení kolem obrázku.  
  
 Každé tlačítko má jednu image. Různé tlačítko stavy a styly (při stisknutí tlačítka nahoru, dolů, zakázaná, zakázané dolů a neurčitém) se generují z této jeden bitové kopie. Rastrové obrázky může být libovolnou barvu, lze dosáhnout nejlepších výsledků s obrázky v černé a odstínech šedi.  
  
> [!WARNING]
> `CToolBar`podporuje bitmap s maximálně 16 barev. Při načítání bitovou kopii do editoru panelu nástrojů, Visual Studio automaticky převede obrázek rastr 16 barev, v případě potřeby a zobrazí zprávu upozornění, pokud byl převeden bitovou kopii. Pokud používáte image s víc než 16 barvy (pomocí externího editoru upravit obrázek), může aplikace neočekávanému chování.  
  
 Tlačítka panelu nástrojů napodobují tlačítek ve výchozím nastavení. Tlačítka panelu nástrojů můžete však také napodobují tlačítka zaškrtávací políčko nebo přepínače. Zaškrtávací políčko tlačítka mají tři stavy: zaškrtnuto, nezaškrtnuté a neurčitou. Přepínací tlačítka mají jenom dva stavy: zaškrtnutí a vymazat.  
  
 Chcete-li nastavit na jednotlivé tlačítko nebo styl oddělovače bez odkazující na pole, volejte [GetButtonStyle](#getbuttonstyle) načíst styl, a pak zavolají [SetButtonStyle](#setbuttonstyle) místo `SetButtons`. `SetButtonStyle`je velmi užitečné, pokud chcete změnit styl tlačítka v době běhu.  
  
 Přiřadit text, který se zobrazí na tlačítko, volání [GetButtonText](#getbuttontext) načíst text, který se zobrazí na tlačítko a pak zavolají [SetButtonText](#setbuttontext) nastavit text.  
  
 Vytvoření tlačítka zaškrtávací políčko, přiřaďte jej styl **TBBS_CHECKBOX** nebo použijte `CCmdUI` objektu `SetCheck` – členská funkce v `ON_UPDATE_COMMAND_UI` obslužné rutiny. Volání metody `SetCheck` se změní pushbutton tlačítka zaškrtávací políčko. Předat `SetCheck` argument 0 pro není zaškrtnuto, 1 pro zaškrtnuté, nebo 2 pro neurčitou.  
  
 Chcete-li vytvořit přepínače, volejte [CCmdUI](../../mfc/reference/ccmdui-class.md) objektu [setradio –](../../mfc/reference/ccmdui-class.md#setradio) – členská funkce z `ON_UPDATE_COMMAND_UI` obslužné rutiny. Předat `SetRadio` argument 0 nenulové hodnoty pro zaškrtnuté nebo nezaškrtnuté. Chcete-li poskytovat skupina rádiových vzájemně se vylučuje chování, musíte mít `ON_UPDATE_COMMAND_UI` obslužné rutiny pro všechny tlačítka ve skupině.  
  
 Další informace o používání `CToolBar`, najdete v článku [implementace panelu nástrojů MFC](../../mfc/mfc-toolbar-implementation.md) a [Technická poznámka 31: ovládací pruhy](../../mfc/tn031-control-bars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccontrolbar –](../../mfc/reference/ccontrolbar-class.md)  
  
 `CToolBar`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="commandtoindex"></a>CToolBar::CommandToIndex  
 Členské funkce vrátí hodnotu index první tlačítko panelu nástrojů, začínající na pozici 0, jehož ID příkazu, který odpovídá `nIDFind`.  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIDFind`  
 ID příkazu tlačítka panelu nástrojů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index tlačítko nebo -1, pokud žádné tlačítko má ID daného příkazu.  
  
##  <a name="create"></a>CToolBar::Create  
 Tato funkce člen vytvoří nástrojů systému Windows (podřízeného okna) a přidruží ji s `CToolBar` objektu.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,  
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Ukazatel na okno, která je nadřazeným prvkem panel nástrojů.  
  
 `dwStyle`  
 Styl panelu nástrojů. Styly dalších nástrojů, které jsou podporované jsou:  
  
- `CBRS_TOP`Ovládací prvek panelu je v horní části okna rámce.  
  
- `CBRS_BOTTOM`Ovládací prvek panelu je v dolní části okna rámce.  
  
- `CBRS_NOALIGN`Ovládací prvek panelu není změnit jejich umístění při změně velikosti nadřazeného objektu.  
  
- `CBRS_TOOLTIPS`Ovládací prvek panelu zobrazí popisy.  
  
- **Cbrs_size_dynamic –** ovládacích pruhů je dynamický.  
  
- **Cbrs_size_fixed –** ovládacích pruhů vyřešen.  
  
- **CBRS_FLOATING** je plovoucí ovládacích pruhů.  
  
- `CBRS_FLYBY`Stavový řádek zobrazí informace o tlačítko.  
  
- **CBRS_HIDE_INPLACE** není zobrazovat uživateli, ovládacích pruhů.  
  
 `nID`  
 ID podřízeného okna panelu nástrojů  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví taky výška panelu nástrojů na výchozí hodnotu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]  
  
##  <a name="createex"></a>CToolBar::CreateEx  
 Volání této funkce, které chcete vytvořit panel nástrojů systému Windows (podřízeného okna) a přidružit ho pomocí `CToolBar` objektu.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = TBSTYLE_FLAT,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,  
    CRect rcBorders = CRect(
    0, 
    0, 
    0, 
    0), 
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Ukazatel na okno, která je nadřazeným prvkem panel nástrojů.  
  
 `dwCtrlStyle`  
 Další styly pro vytvoření vložený [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) objektu. Ve výchozím nastavení je tato hodnota nastavena **TBSTYLE_FLAT**. Úplný seznam nástrojů styly, najdete v části `dwStyle`.  
  
 `dwStyle`  
 Styl panelu nástrojů. V tématu [Toolbar – ovládací prvek a styly tlačítek](http://msdn.microsoft.com/library/windows/desktop/bb760439) ve Windows SDK pro seznam příslušné styly.  
  
 *rcBorders*  
 A [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který definuje šířku ohraničení panelu nástrojů okna. Tyto hranice jsou nastaveny na 0,0,0,0 ve výchozím nastavení, což by vedlo k panelu nástrojů okno s bez ohraničení.  
  
 `nID`  
 ID podřízeného okna panelu nástrojů  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Nastaví taky výška panelu nástrojů na výchozí hodnotu.  
  
 Použití `CreateEx`, místo [vytvořit](#create), pokud se určité styly musí být k dispozici při vytváření ovládacích prvků panelu embedded nástroj. Například nastavit `dwCtrlStyle` k **TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT** vytvořit panel nástrojů, který vypadá takto: Internet Explorer 4 panely nástrojů.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]  
  
##  <a name="ctoolbar"></a>CToolBar::CToolBar  
 Tato funkce člen vytvoří `CToolBar` objektu a nastaví výchozí velikosti.  
  
```  
CToolBar();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání [vytvořit](#create) členskou funkci pro vytvoření okna panelu nástrojů.  
  
##  <a name="getbuttoninfo"></a>CToolBar::GetButtonInfo  
 Tato funkce člen načte ID ovládacího prvku, stylu a index bitové kopie tlačítka panelu nástrojů nebo oddělovač v umístění, které *nIndex.*  
  
```  
void GetButtonInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& iImage) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index tlačítka panelu nástrojů nebo oddělovač, jejichž informace je možné načíst.  
  
 `nID`  
 Odkaz na **Celé_číslo** , je nastaven na ID příkazu, který tlačítka.  
  
 `nStyle`  
 Odkaz na **Celé_číslo** , je nastaven na styl tlačítko.  
  
 `iImage`  
 Odkaz na celé číslo, které je nastaven na index obrázku tlačítka v rámci bitové mapy.  
  
### <a name="remarks"></a>Poznámky  
 Tyto hodnoty jsou přiřazeny k proměnné odkazuje `nID`, `nStyle`, a `iImage`. Index bitové kopie je pozice bitové kopie v rámci rastrový obrázek, který obsahuje Image pro tlačítka panelu nástrojů. První image je na pozici 0.  
  
 Pokud `nIndex` Určuje oddělovač, `iImage` je nastaven na Šířka oddělovače v pixelech.  
  
##  <a name="getbuttonstyle"></a>CToolBar::GetButtonStyle  
 Volání této funkce člen načíst styl tlačítka nebo oddělovače na panelu nástrojů.  
  
```  
UINT GetButtonStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index panelu nástrojů tlačítko nebo oddělovač styl mají být načteny.  
  
### <a name="return-value"></a>Návratová hodnota  
 Styl tlačítko nebo určeného oddělovače `nIndex`.  
  
### <a name="remarks"></a>Poznámky  
 Styl tlačítko určuje vzhled tlačítka a odpovědí na vstup uživatele. V tématu [SetButtonStyle](#setbuttonstyle) příklady styly tlačítek.  
  
##  <a name="getbuttontext"></a>CToolBar::GetButtonText  
 Volání této funkce člen k načtení textu, který se zobrazí na tlačítko.  
  
```  
CString GetButtonText(int nIndex) const;  
  
void GetButtonText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index textu k načtení.  
  
 `rString`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který bude obsahovat text, který má být načtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt obsahující text tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Druhý formulář člen funkce výplněmi `CString` objekt s textový řetězec.  
  
##  <a name="getitemid"></a>CToolBar::GetItemID  
 Členské funkce vrátí hodnotu ID příkazu, který tlačítko nebo určeného oddělovače `nIndex`.  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index položky, jejíž ID je mají být načteny.  
  
### <a name="return-value"></a>Návratová hodnota  
 ID příkazu, který tlačítko nebo určeného oddělovače `nIndex`.  
  
### <a name="remarks"></a>Poznámky  
 Vrátí oddělovačů **ID_SEPARATOR**.  
  
##  <a name="getitemrect"></a>CToolBar::GetItemRect  
 Tuto funkci člen doplní `RECT` struktura, jejíž adresa je součástí `lpRect` se souřadnicemi tlačítko nebo určeného oddělovače `nIndex`.  
  
```  
virtual void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index položky (tlačítko nebo oddělovač), jejichž obdélníku souřadnice jsou uváděny mají být načteny.  
  
 `lpRect`  
 Adresa [Rect –](../../mfc/reference/rect-structure1.md) struktura, která bude obsahovat souřadnice položky.  
  
### <a name="remarks"></a>Poznámky  
 Souřadnice jsou uváděny v pixelech relativně k levém horním panelu nástrojů.  
  
 Použití `GetItemRect` získat souřadnice oddělovač, který chcete nahradit pole se seznamem nebo jiného ovládacího prvku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CToolBar::SetSizes](#setsizes).  
  
##  <a name="gettoolbarctrl"></a>CToolBar::GetToolBarCtrl  
 Tato funkce člen umožňuje přímý přístup k podkladové běžného ovládacího prvku.  
  
```  
CToolBarCtrl& GetToolBarCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Odkaz na `CToolBarCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Použití `GetToolBarCtrl` chcete využít výhod funkce Windows běžné ovládací prvek panelu nástrojů a chcete využít výhod podpory [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) poskytuje pro přizpůsobení panelu nástrojů.  
  
 Další informace o použití běžných ovládacích prvků, najdete v článku [ovládací prvky](../../mfc/controls-mfc.md) a [běžné ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb775493) ve Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]  
  
##  <a name="loadbitmap"></a>CToolBar::LoadBitmap  
 Volání této funkce člen načíst rastrový obrázek určeného `lpszResourceName` nebo `nIDResource`.  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszResourceName`  
 Ukazatel na název prostředků rastrového obrázku má být načten.  
  
 `nIDResource`  
 ID prostředku bitové mapy má být načten.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Bitmapy by měl obsahovat jeden obrázek pro tlačítko panelu nástrojů. Pokud obrázky nemají standardní velikosti (16 pixelů a 15 pixelů), volání [SetSizes](#setsizes) nastavit tlačítko velikosti a jejich obrázků.  
  
> [!WARNING]
> `CToolBar`podporuje bitmap s maximálně 16 barev. Při načítání bitovou kopii do editoru panelu nástrojů, Visual Studio automaticky převede obrázek rastr 16 barev, v případě potřeby a zobrazí zprávu upozornění, pokud byl převeden bitovou kopii. Pokud používáte image s víc než 16 barvy (pomocí externího editoru upravit obrázek), může aplikace neočekávanému chování.  
  
##  <a name="loadtoolbar"></a>CToolBar::LoadToolBar  
 Volání této funkce člen načíst panelu nástrojů určeného `lpszResourceName` nebo `nIDResource`.  
  
```  
BOOL LoadToolBar(LPCTSTR lpszResourceName);  
BOOL LoadToolBar(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszResourceName`  
 Ukazatel na název prostředku panelu nástrojů, který má být načten.  
  
 `nIDResource`  
 ID prostředku panelu nástrojů má být načten.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [editor panelu nástrojů](../../windows/toolbar-editor.md) v další informace o vytvoření prostředku panelu nástrojů.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CToolBar::CreateEx](#createex).  
  
##  <a name="setbitmap"></a>CToolBar::SetBitmap  
 Volání této funkce člen nastavit pro bitovou kopii rastrového obrázku panelu nástrojů.  
  
```  
BOOL SetBitmap(HBITMAP hbmImageWell);
```  
  
### <a name="parameters"></a>Parametry  
 *hbmImageWell*  
 Popisovač rastrového obrázku, který je přidružen panelu nástrojů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Například volání `SetBitmap` po uživatel provede akci na dokument, který změní akce na tlačítko změnit bitovou kopii rastrové obrázky.  
  
##  <a name="setbuttoninfo"></a>CToolBar::SetButtonInfo  
 Volání této funkce člen nastavit ID příkazu, stylu a číslo bitové kopie na tlačítko.  
  
```  
void SetButtonInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int iImage);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index nule tlačítko nebo oddělovač, pro kterou má být nastavena informace.  
  
 `nID`  
 Hodnota, na kterou je nastaveno na tlačítko příkaz ID.  
  
 `nStyle`  
 Styl nové tlačítko. Podporovány jsou následující styly tlačítek:  
  
- **TBBS_BUTTON** standardní pushbutton (výchozí)  
  
- **TBBS_SEPARATOR** oddělovače  
  
- **TBBS_CHECKBOX** tlačítko automaticky zaškrtávací políčko  
  
- **TBBS_GROUP** označuje začátek skupina tlačítek  
  
- **TBBS_CHECKGROUP** označuje začátek skupina tlačítek, zaškrtávací políčko  
  
- **TBBS_DROPDOWN** vytvoří tlačítko rozevíracího seznamu.  
  
- **TBBS_AUTOSIZE** na tlačítko šířka budou vypočítány na základě na text tlačítka, nikoli na velikost bitové kopie.  
  
- **TBBS_NOPREFIX** textu tlačítka nebude mít předponu akcelerátoru s ním spojená.  
  
 `iImage`  
 Nový index bitové kopie na tlačítko v rámci bitové mapy.  
  
### <a name="remarks"></a>Poznámky  
 Pro oddělovače, které mají styl **TBBS_SEPARATOR**, tato funkce nastaví šířku oddělovače v pixelech k s hodnotou uloženou v `iImage`.  
  
> [!NOTE]
>  Můžete vytvořit také pomocí stavy tlačítko `nStyle` parametr, ale, protože tlačítko stavy jsou řízeny [on_update_command_ui –](message-map-macros-mfc.md#on_update_command_ui) obslužnou rutinu, všechny stavu nastavíte pomocí `SetButtonInfo` ztratí během další nečinnosti zpracování. V tématu [postup aktualizace objektů uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md) a [TN031: ovládací pruhy](../../mfc/tn031-control-bars.md) Další informace.  
  
 Informace o rastrové obrázky a tlačítka, najdete v článku [ctoolbar –](../../mfc/reference/ctoolbar-class.md) přehled a [CToolBar::LoadBitmap](#loadbitmap).  
  
##  <a name="setbuttons"></a>CToolBar::SetButtons  
 Tato funkce člen nastaví ID příkazu pro tlačítko panelu nástrojů na hodnotu zadanou pomocí odpovídající element pole `lpIDArray`.  
  
```  
BOOL SetButtons(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpIDArray`  
 Ukazatel na pole ID příkazů. Může být **NULL** přidělit prázdný tlačítka.  
  
 `nIDCount`  
 Počet prvků v poli, na kterou odkazuje `lpIDArray`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud element pole má hodnotu **ID_SEPARATOR**, oddělovače je vytvořen v odpovídající pozici panelu nástrojů. Tato funkce také nastaví styl každé tlačítko na **TBBS_BUTTON** a každý oddělovače styl **TBBS_SEPARATOR**a přiřadí každé tlačítko index bitové kopie. Index bitové kopie určuje pozici obrázku tlačítka v rámci bitové mapy.  
  
 Není nutné k účtu pro oddělovače v souboru bitové mapy, protože tato funkce nepřiřazuje indexy bitové kopie pro oddělovače. Pokud vaše nástrojů má tlačítka v umístění 0, 1 a 3 a oddělovač na pozici 2, pro Image v umístění 0, 1, 2 ve vaší bitové mapy přiřazené k tlačítka v umístění 0, 1, 3, v uvedeném pořadí.  
  
 Pokud `lpIDArray` je **NULL**, tato funkce přiděluje místo pro počet položek určeného `nIDCount`. Použití [SetButtonInfo](#setbuttoninfo) nastavit atributy každou položku.  
  
##  <a name="setbuttonstyle"></a>CToolBar::SetButtonStyle  
 Volání této funkce člen nastavit styl tlačítka nebo oddělovač, nebo na skupiny tlačítka.  
  
```  
void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index tlačítko nebo oddělovač, jejichž informace je možné nastavit.  
  
 `nStyle`  
 Styl tlačítko. Podporovány jsou následující styly tlačítek:  
  
- **TBBS_BUTTON** standardní pushbutton (výchozí)  
  
- **TBBS_SEPARATOR** oddělovače  
  
- **TBBS_CHECKBOX** tlačítko automaticky zaškrtávací políčko  
  
- **TBBS_GROUP** označuje začátek skupina tlačítek  
  
- **TBBS_CHECKGROUP** označuje začátek skupina tlačítek, zaškrtávací políčko  
  
- **TBBS_DROPDOWN** vytvoří tlačítko rozevíracího seznamu  
  
- **TBBS_AUTOSIZE** na tlačítko šířka budou vypočítány na základě na text tlačítka, nikoli na velikost bitové kopie  
  
- **TBBS_NOPREFIX** textu tlačítka nebude mít předponu akcelerátoru přidruženo  
  
### <a name="remarks"></a>Poznámky  
 Styl tlačítko určuje vzhled tlačítka a odpovědí na vstup uživatele.  
  
 Před voláním `SetButtonStyle`, volání [GetButtonStyle](#getbuttonstyle) – členská funkce načíst styl tlačítko nebo oddělovač.  
  
> [!NOTE]
>  Můžete vytvořit také pomocí stavy tlačítko `nStyle` parametr, ale, protože tlačítko stavy jsou řízeny [on_update_command_ui –](message-map-macros-mfc.md#on_update_command_ui) obslužnou rutinu, všechny stavu nastavíte pomocí `SetButtonStyle` ztratí během další nečinnosti zpracování. V tématu [postup aktualizace objektů uživatelského rozhraní](../../mfc/how-to-update-user-interface-objects.md) a [TN031: ovládací pruhy](../../mfc/tn031-control-bars.md) Další informace.  
  
##  <a name="setbuttontext"></a>CToolBar::SetButtonText  
 Volejte tuto funkci nastavit text pro tlačítko.  
  
```  
BOOL SetButtonText(
    int nIndex,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index tlačítka, jejíž text je možné nastavit.  
  
 `lpszText`  
 Odkazuje na text, který má být nastavena na tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CToolBar::GetToolBarCtrl](#gettoolbarctrl).  
  
##  <a name="setheight"></a>CToolBar::SetHeight  
 Tato funkce člen Nastaví výšku panelu nástrojů na hodnotu v pixelech, zadaný v `cyHeight`.  
  
```  
void SetHeight(int cyHeight);
```  
  
### <a name="parameters"></a>Parametry  
 `cyHeight`  
 Výška v pixelech panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 Po volání [SetSizes](#setsizes), pomocí této funkce člen můžete přepsat výška standardním panelu nástrojů. Pokud výšku je příliš malá, bude tlačítka oříznut, v dolní části.  
  
 Pokud není tato funkce volána, rozhraní velikost tlačítko používá k určení výška panelu nástrojů.  
  
##  <a name="setsizes"></a>CToolBar::SetSizes  
 Volání této funkce člen nastavit tlačítka panelu nástrojů na velikost v pixelech, zadaný v *sizeButton*.  
  
```  
void SetSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>Parametry  
 *sizeButton*  
 Velikost v pixelech každé tlačítko.  
  
 `sizeImage`  
 Velikost v pixelech každé bitové kopie.  
  
### <a name="remarks"></a>Poznámky  
 `sizeImage` Parametr musí obsahovat velikost v pixelech obrázků v rastrového obrázku panelu nástrojů. Dimenze v *sizeButton* musí být dost pro uložení image plus 7 pixelů navíc šířku a 6 pixelů navíc na výšku. Tato funkce také nastaví výšku nástrojů tlačítka.  
  
 Volání této funkce člen pouze pro panely nástrojů, které se neřídí *Windows rozhraní pokyny pro návrh softwaru* doporučení pro velikosti tlačítko a bitové kopie.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CTRLBARS](../../visual-cpp-samples.md)   
 [Ukázka DLGCBR32 MFC](../../visual-cpp-samples.md)   
 [Ukázka MFC DOCKTOOL](../../visual-cpp-samples.md)   
 [Ccontrolbar – třída](../../mfc/reference/ccontrolbar-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl – třída](../../mfc/reference/ctoolbarctrl-class.md)   
 [CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)
