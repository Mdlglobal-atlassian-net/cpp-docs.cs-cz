---
title: CToolTipCtrl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9436f3809a337b732a2e95d9c30b9baa45c4e8ba
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123107"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl – třída
Zapouzdřuje funkce ovládacího prvku"nástroj tip," malé místní okno, které zobrazuje jeden řádek textu popisující účel nástroj v aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CToolTipCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|Vytvoří `CToolTipCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CToolTipCtrl::Activate](#activate)|Aktivuje a deaktivuje ovládacím prvkem popis tlačítka.|  
|[CToolTipCtrl::AddTool](#addtool)|Zaregistruje nástroj s ovládacím prvkem popis tlačítka.|  
|[CToolTipCtrl::AdjustRect](#adjustrect)|Převede mezi prvkem popis tlačítka text zobrazení obdélníku a jeho obdélníku okna.|  
|[CToolTipCtrl::Create](#create)|Vytvoří prvkem popis tlačítka a připojí jej k `CToolTipCtrl` objektu.|  
|[CToolTipCtrl::CreateEx](#createex)|Vytvoří prvkem popis tlačítka s zadaný Windows rozšířené styly a připojí jej k `CToolTipCtrl` objektu.|  
|[CToolTipCtrl::DelTool](#deltool)|Odebere nástroj ovládacím prvkem popis tlačítka.|  
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Získá velikost popis tlačítka.|  
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Načte informace, jako je například velikost, pozice a text popisu tlačítka okna, které zobrazuje aktuální ovládací prvek popisek.|  
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Načte výchozí, automaticky otevírané okno a reshow doby trvání, které jsou aktuálně nastavené pro nástroj pro ovládací prvek tlačítka.|  
|[CToolTipCtrl::GetMargin](#getmargin)|Načte top, vlevo, dolní a dolního okraje, které jsou nastavené na okno tip nástroj.|  
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Načte maximální šířku pro tip okno nástroje.|  
|[CToolTipCtrl::GetText](#gettext)|Načte text, který udržuje prvkem popis tlačítka pro nástroj.|  
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Načte barvu pozadí v okně nástroje tip.|  
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Načte barvu textu v okně nástroje tip.|  
|[CToolTipCtrl::GetTitle](#gettitle)|Načte název aktuální ovládací prvek popis tlačítka.|  
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Načte počet nástroje udržované prvkem popis tlačítka.|  
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Načte informace o nástroji, který udržuje prvkem popis tlačítka.|  
|[CToolTipCtrl::HitTest](#hittest)|Testy bod zjistit, zda je v rámci ohraničující obdélník daný nástroj. Pokud ano, načte informace o nástroji.|  
|[CToolTipCtrl::Pop](#pop)|Odebere okno zobrazené nástroj tip ze zobrazení.|  
|[CToolTipCtrl::Popup](#popup)|Způsobí, že aktuální ovládací prvek popisek k zobrazení souřadnice poslední zprávy myši.|  
|[CToolTipCtrl::RelayEvent](#relayevent)|Předá zprávu myši prvkem popis tlačítka pro zpracování.|  
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Nastaví počáteční, automaticky otevírané okno a reshow doby trvání pro prvkem popis tlačítka.|  
|[CToolTipCtrl::SetMargin](#setmargin)|Nastaví horní, vlevo, dolní a pravé okraje okna tip nástroj.|  
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Nastaví maximální šířku pro tip okno nástroje.|  
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|V okně tip nástroj nastaví barvu pozadí.|  
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Nastaví barvu textu v okně nástroje tip.|  
|[CToolTipCtrl::SetTitle](#settitle)|Přidá řetězec standardní ikonu a title k popisku tlačítka.|  
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Nastaví informace, které udržuje popis tlačítka pro nástroj.|  
|[CToolTipCtrl::SetToolRect](#settoolrect)|Nastaví nové ohraničující obdélník pro nástroj.|  
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Nastaví vizuální styl tip okno nástroje.|  
|[CToolTipCtrl::Update](#update)|Vynutí nástroj aktuální překreslit.|  
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Nastaví text popisu nástroje pro nástroj.|  
  
## <a name="remarks"></a>Poznámky  
 "Nástroj" je buď v časovém období, jako je například podřízeného okna nebo ovládací prvek nebo definované aplikací obdélníkovou oblast v rámci časového období klientské oblasti. Popis tlačítka je skrytý na většinu času, zobrazování, pouze když uživatel uloží kurzor na nástroj a ponechá ji existuje pro přibližně polovinu druhý. Popis tlačítka se zobrazí u kurzor a zmizí, když uživatel klikne na tlačítko myši nebo přesune kurzor vypnout nástroj.  
  
 `CToolTipCtrl` poskytuje funkce pro ovládací prvek počáteční čas a dobu trvání popis tlačítka šířky okrajů text popisu nástroje, šířka okno tip nástroje sám a barvu pozadí a text popisu. Ovládací prvek popisek jednotný nástroj může poskytovat informace pro více než jeden nástroj.  
  
 `CToolTipCtrl` Třída poskytuje funkce Windows ovládacího prvku běžné tip nástroj. Tento ovládací prvek (a proto `CToolTipCtrl` třída) je k dispozici pouze pro aplikace běžící v rámci verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Další informace o povolení tipů nástrojů najdete v tématu [popisů tlačítek v oknech Neodvozených ze třídy CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
 Další informace o používání `CToolTipCtrl`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md) a [pomocí CToolTipCtrl](../../mfc/using-ctooltipctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolTipCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="activate"></a>  CToolTipCtrl::Activate  
 Volejte tuto funkci aktivovat nebo deaktivovat prvkem popis tlačítka.  
  
```  
void Activate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 *bActivate*  
 Určuje, zda je ovládacím prvkem popis tlačítka aktivace nebo deaktivace.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bActivate* má hodnotu TRUE, je aktivován ovládací prvek; Pokud je hodnota FALSE, je deaktivována.  
  
 Při aktivním prvkem popis tlačítka nástroj tip informace se zobrazí, když se nachází kurzor na nástroj, který je zaregistrován pomocí ovládacího prvku; Pokud je neaktivní, informace o tip nástroje nezobrazí, i když se nachází kurzor na nástroj.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="addtool"></a>  CToolTipCtrl::AddTool  
 Zaregistruje nástroj s ovládacím prvkem popis tlačítka.  
  
```  
BOOL AddTool(
    CWnd* pWnd,  
    UINT nIDText,  
    LPCRECT lpRectTool = NULL,  
    UINT_PTR nIDTool = 0);

 
BOOL AddTool(
    CWnd* pWnd,  
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,  
    LPCRECT lpRectTool = NULL,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Ukazatel na okno, které obsahuje nástroj.  
  
 *nIDText*  
 ID prostředku řetězec, který obsahuje text pro nástroj.  
  
 *lpRectTool*  
 Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura obsahující souřadnice nástroje je ohraničujícího rámečku. Souřadnice jsou relativní vzhledem k levém horním rohu okna identifikovaný klientské oblasti *pWnd*.  
  
 *nIDTool*  
 ID tohoto nástroje.  
  
 *lpszText*  
 Ukazatel na hodnotu text pro nástroj. Pokud tento parametr obsahuje hodnotu LPSTR_TEXTCALLBACK, zprávy oznámení TTN_NEEDTEXT přejděte do nadřazeného okna, *pWnd* odkazuje na.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 *LpRectTool* a *nIDTool* parametry musí být platný, nebo pokud *lpRectTool* má hodnotu NULL, *nIDTool* musí být 0.  
  
 Prvkem popis tlačítka lze přidružit více než jeden nástroj. Volání této funkce při registraci nástroj s ovládacím prvkem popis tlačítka, tak, aby informace uložené v popisu tlačítka se zobrazí, pokud se ukazatel na nástroj.  
  
> [!NOTE]
>  Nelze nastavit popis tlačítka statického ovládacího prvku pomocí `AddTool`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="adjustrect"></a>  CToolTipCtrl::AdjustRect  
 Převede mezi text popisu tlačítka ovládacího prvku zobrazení obdélníku a jeho obdélníku okna.  
  
```  
BOOL AdjustRect(
    LPRECT lprc,  
    BOOL bLarger = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která obsahuje obdélníku nástroj tip okno nebo obdélník zobrazení textu.  
  
 *bLarger*  
 V případě hodnoty TRUE *lprc* slouží k určení obdélníku zobrazení textu a obdrží odpovídající obdélníku okna. Pokud je hodnota FALSE, *lprc* slouží k určení obdélníku okno a obdrží odpovídající obdélník zobrazení textu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud rámeček je úspěšně upravena; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen vypočítá obdélník zobrazení prvkem popis tlačítka text z jeho obdélníku okna nebo obdélníku okna tip nástroje potřebné k zobrazení obdélník zobrazení zadaný text.  
  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_ADJUSTRECT](http://msdn.microsoft.com/library/windows/desktop/bb760352), jak je popsáno v sadě Windows SDK.  
  
##  <a name="create"></a>  CToolTipCtrl::Create  
 Vytvoří prvkem popis tlačítka a připojí jej k `CToolTipCtrl` objektu.  
  
```  
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Určuje nadřazeného okna prvkem popis tlačítka, obvykle `CDialog`. Nesmí být NULL.  
  
 *dwStyle*  
 Určuje styl prvkem popis tlačítka. Najdete v článku **poznámky** části Další informace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud nenulové hodnoty `CToolTipCtrl` objekt je úspěšně vytvořená; jinak hodnota 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CToolTipCtrl` ve dvou krocích. Nejprve volat konstruktor k vytvoření `CToolTipCtrl` objektu a pak zavolají `Create` ovládacím prvkem popis tlačítka a vytvořte jej do `CToolTipCtrl` objektu.  
  
 *DwStyle* parametr může být libovolnou kombinací [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). Kromě toho prvkem popis tlačítka má dvě třídy specifické styly: TTS_ALWAYSTIP a TTS_NOPREFIX.  
  
|Styl|Význam|  
|-----------|-------------|  
|TTS_ALWAYSTIP|Určuje, že se zobrazí popis tlačítka, pokud se ukazatel na nějaký nástroj, bez ohledu na to, jestli je okno vlastníka prvkem popis tlačítka aktivní nebo neaktivní. Bez této styl ovládacím prvkem popis tlačítka se zobrazí, když je aktivní okno nástroje vlastníka, ale ne v případě, že je neaktivní.|  
|TTS_NOPREFIX|Tento styl zabrání systému odstraňování znaků z řetězce ampersand (&). Pokud prvkem popis tlačítka nemá styl TTS_NOPREFIX, systém automaticky odstraní znaky ampersand, což umožňuje aplikaci používat stejný řetězec jako položku nabídky a jako text v prvkem popis tlačítka.|  
  
 Prvkem popis tlačítka má ws_popup – a ws_ex_toolwindow – okno stylů, bez ohledu na to, jestli je možné určit je při vytváření ovládacího prvku.  
  
 Chcete-li vytvořit prvkem popis tlačítka s rozšířené windows styly, volejte [CToolTipCtrl::CreateEx](#createex) místo `Create`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="createex"></a>  CToolTipCtrl::CreateEx  
 Vytvoří ovládacího prvku (podřízeného okna) a přidružit ho pomocí `CToolTipCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwStyle = 0,  
    DWORD dwStyleEx = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Ukazatel na okně, které je nadřazeného ovládacího prvku.  
  
 *dwStyle*  
 Určuje styl prvkem popis tlačítka. Najdete v článku **poznámky** části [vytvořit](#create) Další informace.  
  
 *dwStyleEx*  
 Určuje styl rozšířené vytváří ovládacího prvku. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo `Create` použít rozšířené styly Windows určeného předponu rozšířené styl Windows **WS_EX_**.  
  
##  <a name="ctooltipctrl"></a>  CToolTipCtrl::CToolTipCtrl  
 Vytvoří `CToolTipCtrl` objektu.  
  
```  
CToolTipCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
 Je třeba volat `Create` poté, co vytvořen objekt.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]  
  
##  <a name="deltool"></a>  CToolTipCtrl::DelTool  
 Odebere nástroj určeného *pWnd* a *nIDTool* z kolekce nástroje nepodporuje prvkem popis tlačítka.  
  
```  
void DelTool(
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Ukazatel na okno, které obsahuje nástroj.  
  
 *nIDTool*  
 ID tohoto nástroje.  
  
##  <a name="getbubblesize"></a>  CToolTipCtrl::GetBubbleSize  
 Získá velikost popis tlačítka.  
  
```  
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpToolInfo*  
 Ukazatel na tip nástroje [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost popis tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_GETBUBBLESIZE](http://msdn.microsoft.com/library/windows/desktop/bb760387), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getcurrenttool"></a>  CToolTipCtrl::GetCurrentTool  
 Načte informace, jako je například velikost, pozice a text popisu tlačítka okna zobrazuje aktuální ovládací prvek popisek.  
  
```  
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out] *lpToolInfo*|Ukazatel na [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) struktura, která přijímá informace o aktuální okno popisu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tyto informace se načítají úspěšně; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TTM_GETCURRENTTOOL](http://msdn.microsoft.com/library/windows/desktop/bb760389) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu načte informace o aktuální okno popisu.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]  
  
##  <a name="getdelaytime"></a>  CToolTipCtrl::GetDelayTime  
 Načte počáteční, automaticky otevírané okno a reshow doby trvání nastaveno pro prvkem popis tlačítka.  
  
```  
int GetDelayTime(DWORD dwDuration) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwDuration*  
 Příznak, který určuje hodnotu, která doba trvání bude načten. Tento parametr může být jedna z následujících hodnot:  
  
- Načtení TTDT_AUTOPOP dobu popisek okno zůstává viditelná, pokud ukazatel setrvá v rámci ohraničující obdélník nástroj.  
  
- Načtení TTDT_INITIAL se zobrazí dobu, které musí zůstat ukazatele stojící v rámci nástroje ohraničující obdélník před tip okno nástroje.  
  
- Načtení TTDT_RESHOW dobu potřebnou pro následné nástrojů tip vypadaly jako ukazatel přesune z jednoho nástroje do jiného.  
  
### <a name="return-value"></a>Návratová hodnota  
 Zadaný zpoždění Doba v milisekundách  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_GETDELAYTIME](http://msdn.microsoft.com/library/windows/desktop/bb760390), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getmargin"></a>  CToolTipCtrl::GetMargin  
 Načte top, vlevo, dolní a dolního okraje nastavit pro tip okno nástroje.  
  
```  
void GetMargin(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Adresa `RECT` struktura, která bude přijímat informace okraj. Členové [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura nedefinují ohraničující obdélník. Pro účely této zprávy jsou členové struktury interpretovat následujícím způsobem:  
  
|Člen|Reprezentace|  
|------------|--------------------|  
|`top`|Vzdálenost mezi horní okraj a horní části text popisu nástroje v pixelech.|  
|`left`|Vzdálenost mezi levého okraje a levého konce tip textu v pixelech.|  
|`bottom`|Vzdálenost mezi dolní ohraničení a dolní část textového tip v pixelech.|  
|`right`|Vzdálenost od pravého okraje do pravého konce tip textu v pixelech.|  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_GETMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb760391), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getmaxtipwidth"></a>  CToolTipCtrl::GetMaxTipWidth  
 Načte maximální šířku pro tip okno nástroje.  
  
```  
int GetMaxTipWidth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální šířka pro tip okno nástroje.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_GETMAXTIPWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760392), jak je popsáno v sadě Windows SDK.  
  
##  <a name="gettext"></a>  CToolTipCtrl::GetText  
 Načte text, který udržuje prvkem popis tlačítka pro nástroj.  
  
```  
void GetText(
    CString& str,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *str –*  
 Odkaz na `CString` objekt, který přijme nástroje text.  
  
 *pWnd*  
 Ukazatel na okno, které obsahuje nástroj.  
  
 *nIDTool*  
 ID tohoto nástroje.  
  
### <a name="remarks"></a>Poznámky  
 *PWnd* a *nIDTool* parametry identifikovat nástroj. Pokud tento nástroj byl dříve registrován s ovládacím prvkem popis tlačítka prostřednictvím předchozí volání `CToolTipCtrl::AddTool`, odkazuje *str* parametr je přiřazen nástroje text.  
  
##  <a name="gettipbkcolor"></a>  CToolTipCtrl::GetTipBkColor  
 Načte barvu pozadí v okně nástroje tip.  
  
```  
COLORREF GetTipBkColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která představuje barvu pozadí.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_GETTIPBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760394), jak je popsáno v sadě Windows SDK.  
  
##  <a name="gettiptextcolor"></a>  CToolTipCtrl::GetTipTextColor  
 Načte barvu textu v okně nástroje tip.  
  
```  
COLORREF GetTipTextColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která představuje barvu textu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_GETTIPTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760395), jak je popsáno v sadě Windows SDK.  
  
##  <a name="gettitle"></a>  CToolTipCtrl::GetTitle  
 Načte název aktuální ovládací prvek popis tlačítka.  
  
```  
void GetTitle(PTTGETTITLE pttgt) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out] *pttgt*|Ukazatel na [TTGETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760260) struktura, která obsahuje informace o prvku popisek. Po návratu tato metoda *pszTitle* členem [TTGETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760260) struktury body na text nadpisu.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TTM_GETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760396) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="gettoolcount"></a>  CToolTipCtrl::GetToolCount  
 Načte počet nástroje registrované s ovládacím prvkem popis tlačítka.  
  
```  
int GetToolCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet nástroje registrována s ovládacím prvkem popis tlačítka.  
  
##  <a name="gettoolinfo"></a>  CToolTipCtrl::GetToolInfo  
 Načte informace o nástroji, který udržuje prvkem popis tlačítka.  
  
```  
BOOL GetToolInfo(
    CToolInfo& ToolInfo,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *ToolInfo*  
 Odkaz na `TOOLINFO` objekt, který přijme nástroje text.  
  
 *pWnd*  
 Ukazatel na okno, které obsahuje nástroj.  
  
 *nIDTool*  
 ID tohoto nástroje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `hwnd` a `uId` členy [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) struktura odkazuje *CToolInfo* identifikovat nástroj. Pokud tento nástroj je zaregistrován s ovládacím prvkem popis tlačítka prostřednictvím předchozí volání `AddTool`, `TOOLINFO` struktura, naplní se informace o nástroji.  
  
##  <a name="hittest"></a>  CToolTipCtrl::HitTest  
 Testy bod určit, zda je v rámci ohraničující obdélník daný nástroj, a pokud ano, načíst informace o nástroji.  
  
```  
BOOL HitTest(
    CWnd* pWnd,  
    CPoint pt,  
    LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Ukazatel na okno, které obsahuje nástroj.  
  
 *PT*  
 Ukazatel na `CPoint` objekt obsahující souřadnice bodu má být testována.  
  
 *lpToolInfo*  
 Ukazatel na [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) struktura, která obsahuje informace o nástroji.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je bod určeného vstupů do testovací informace v rámci nástroje ohraničující obdélník; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato funkce vrátí nenulovou hodnotu, struktura na kterou odkazuje *lpToolInfo* , naplní se informace o nástroji, v jehož obdélníku leží bodem.  
  
 `TTHITTESTINFO` Struktura je definován následujícím způsobem:  
  
 `typedef struct _TT_HITTESTINFO { // tthti`  
  
 `HWND hwnd;   // handle of tool or window with tool`  
  
 `POINT pt;    // client coordinates of point to test`  
  
 `TOOLINFO ti; // receives information about the tool`  
  
 `} TTHITTESTINFO, FAR * LPHITTESTINFO;`  
  
 `hwnd`  
 Určuje popisovač nástroje.  
  
 `pt`  
 Určuje souřadnice bodu, pokud je bod je v nástroji pro ohraničujícího rámečku.  
  
 `ti`  
 Informace o nástroji. Další informace o `TOOLINFO` struktury najdete v tématu [CToolTipCtrl::GetToolInfo](#gettoolinfo).  
  
##  <a name="pop"></a>  CToolTipCtrl::Pop  
 Odebere okno zobrazené nástroj tip ze zobrazení.  
  
```  
void Pop();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_POP](http://msdn.microsoft.com/library/windows/desktop/bb760401), jak je popsáno v sadě Windows SDK.  
  
##  <a name="popup"></a>  CToolTipCtrl::Popup  
 Způsobí, že aktuální ovládací prvek popisek k zobrazení souřadnice poslední zprávy myši.  
  
```  
void Popup();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TTM_POPUP](http://msdn.microsoft.com/library/windows/desktop/bb760402) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu se zobrazí okno popisu.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]  
  
##  <a name="relayevent"></a>  CToolTipCtrl::RelayEvent  
 Předá zprávu myši prvkem popis tlačítka pro zpracování.  
  
```  
void RelayEvent(LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMsg*  
 Ukazatel na [MSG](http://msdn.microsoft.com/library/windows/desktop/ms644958) struktura, která obsahuje zprávu (Relay).  
  
### <a name="remarks"></a>Poznámky  
 Prvkem popis tlačítka zpracovává pouze následující zprávy, která se odešlou do ní pomocí `RelayEvent`:  
  
|WM_LBUTTONDOWN|WM_MOUSEMOVE|  
|---------------------|-------------------|  
|WM_LBUTTONUP|WM_RBUTTONDOWN|  
|WM_MBUTTONDOWN|WM_RBUTTONUP|  
|WM_MBUTTONUP||  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="setdelaytime"></a>  CToolTipCtrl::SetDelayTime  
 Nastaví dobu zpoždění prvkem popis tlačítka.  
  
```  
void SetDelayTime(UINT nDelay);

 
void SetDelayTime(
    DWORD dwDuration,  
    int iTime);
```  
  
### <a name="parameters"></a>Parametry  
 *nDelay*  
 Určuje nový čas zpoždění v milisekundách.  
  
 *dwDuration*  
 Příznak, který určuje hodnotu, která doba trvání bude načten. V tématu [CToolTipCtrl::GetDelayTime](#getdelaytime) popis platné hodnoty.  
  
 *iTime*  
 Čas zadaný zpoždění v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Doba zpoždění je doba, které kurzor musí zůstat na nástroj, než se zobrazí okno tip nástroje. Výchozí doba zpoždění je 500 milisekund.  
  
##  <a name="setmargin"></a>  CToolTipCtrl::SetMargin  
 Nastaví horní, vlevo, dolní a pravé okraje okna tip nástroj.  
  
```  
void SetMargin(LPRECT lprc);
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Adresa `RECT` struktura, která obsahuje informace o okraj nastavit. Členové `RECT` struktura nedefinují ohraničující obdélník. V tématu [CToolTipCtrl::GetMargin](#getmargin) popis informace okraj.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_SETMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb760406), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setmaxtipwidth"></a>  CToolTipCtrl::SetMaxTipWidth  
 Nastaví maximální šířku pro tip okno nástroje.  
  
```  
int SetMaxTipWidth(int iWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *iWidth*  
 Nástroj pro maximální šířka okno tip nastavit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí maximální tip šířka.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_SETMAXTIPWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760408), jak je popsáno v sadě Windows SDK.  
  
##  <a name="settipbkcolor"></a>  CToolTipCtrl::SetTipBkColor  
 V okně tip nástroj nastaví barvu pozadí.  
  
```  
void SetTipBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 *CLR*  
 Nové barva pozadí.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_SETTIPBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760411), jak je popsáno v sadě Windows SDK.  
  
##  <a name="settiptextcolor"></a>  CToolTipCtrl::SetTipTextColor  
 Nastaví barvu textu v okně nástroje tip.  
  
```  
void SetTipTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 *CLR*  
 Barva textu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_SETTIPTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760413), jak je popsáno v sadě Windows SDK.  
  
##  <a name="settitle"></a>  CToolTipCtrl::SetTitle  
 Přidá řetězec standardní ikonu a title k popisku tlačítka.  
  
```  
BOOL SetTitle(
    UINT uIcon,  
    LPCTSTR lpstrTitle);
```  
  
### <a name="parameters"></a>Parametry  
 *uIcon*  
 V tématu *ikonu* v [TTM_SETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760414) ve Windows SDK.  
  
 *lpstrTitle*  
 Ukazatel na řetězec názvu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [TTM_SETTITLE](http://msdn.microsoft.com/library/windows/desktop/bb760414), jak je popsáno v sadě Windows SDK.  
  
##  <a name="settoolinfo"></a>  CToolTipCtrl::SetToolInfo  
 Nastaví informace, které udržuje popis tlačítka pro nástroj.  
  
```  
void SetToolInfo(LPTOOLINFO lpToolInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *lpToolInfo*  
 Ukazatel [TOOLINFO](http://msdn.microsoft.com/library/windows/desktop/bb760256) struktura, která určuje informace o nastavení.  
  
##  <a name="settoolrect"></a>  CToolTipCtrl::SetToolRect  
 Nastaví nové ohraničující obdélník pro nástroj.  
  
```  
void SetToolRect(
    CWnd* pWnd,  
    UINT_PTR nIDTool,  
    LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Ukazatel na okno, které obsahuje nástroj.  
  
 *nIDTool*  
 ID tohoto nástroje.  
  
 *lprect –*  
 Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura zadání nové ohraničující obdélník.  
  
##  <a name="setwindowtheme"></a>  CToolTipCtrl::SetWindowTheme  
 Nastaví vizuální styl tip okno nástroje.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parametry  
 *pszSubAppName*  
 Ukazatel na řetězec znaků Unicode, který obsahuje vizuální styl nastavit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu, není použita.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce [TTM_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb760418) zprávy, jak je popsáno v sadě Windows SDK.  
  
##  <a name="update"></a>  CToolTipCtrl::Update  
 Vynutí nástroj aktuální překreslit.  
  
```  
void Update();
```  
  
##  <a name="updatetiptext"></a>  CToolTipCtrl::UpdateTipText  
 Aktualizuje text popisu nástroje pro tento ovládací prvek nástroje.  
  
```  
void UpdateTipText(
    LPCTSTR lpszText,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);

 
void UpdateTipText(
    UINT nIDText,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszText*  
 Ukazatel na hodnotu text pro nástroj.  
  
 *pWnd*  
 Ukazatel na okno, které obsahuje nástroj.  
  
 *nIDTool*  
 ID tohoto nástroje.  
  
 *nIDText*  
 ID prostředku řetězec, který obsahuje text pro nástroj.  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CToolBar – třída](../../mfc/reference/ctoolbar-class.md)
