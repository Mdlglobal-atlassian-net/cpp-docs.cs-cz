---
title: Ctooltipctrl – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 06f0b78938534f685f14757ca16e5ad2574412f2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684804"
---
# <a name="ctooltipctrl-class"></a>Ctooltipctrl – třída
Zapouzdřuje funkce ovládacího prvku"nástroj tip," malého vyskakovacího okna, která zobrazuje jeden řádek textu popisujícího účel nástroje v aplikaci.  
  
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
|[CToolTipCtrl::Activate](#activate)|Aktivuje a deaktivuje ovládacím prvkem popis tlačítka nástroj.|  
|[CToolTipCtrl::AddTool](#addtool)|Zaregistruje nástroj s ovládacím prvkem popis tlačítka nástroj.|  
|[CToolTipCtrl::AdjustRect](#adjustrect)|Převede mezi text ovládacího prvku tip nástroj zobrazit obdélník a jeho okno obdélník.|  
|[CToolTipCtrl::Create](#create)|Ovládacím prvkem popis tlačítka nástroj vytvoří a připojí ho k `CToolTipCtrl` objektu.|  
|[CToolTipCtrl::CreateEx](#createex)|Vytvoří ovládacím prvkem popis tlačítka nástroj se zadaným rozšířené styly Windows a připojí ho k `CToolTipCtrl` objektu.|  
|[CToolTipCtrl::DelTool](#deltool)|Odebere nástroj z ovládacím prvkem popis tlačítka nástroj.|  
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Získá velikost tlačítka.|  
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Načte informace, jako je například velikost, umístění a textu, od okna popisu, který zobrazuje aktuální ovládací prvek tooltip.|  
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Načte výchozí, automaticky otevírané okno a reshow doby trvání, které jsou aktuálně nastaveny pro nástroj pro ovládací prvek popis tlačítka.|  
|[CToolTipCtrl::GetMargin](#getmargin)|Načte horní, vlevo, dolní a pravý okraj, které jsou nastavené pro popis tlačítka panelu nástrojů.|  
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Získá maximální šířku pro popis tlačítka panelu nástrojů.|  
|[CToolTipCtrl::GetText](#gettext)|Načte text, který udržuje ovládacím prvkem popis tlačítka nástroj pro nástroj.|  
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Zjišťuje barvu pozadí v popis tlačítka panelu nástrojů.|  
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Načte barvu textu v panelu nástrojů tip.|  
|[CToolTipCtrl::GetTitle](#gettitle)|Načte název aktuální ovládací prvek tooltip.|  
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Získá počet nástroje udržuje ovládacím prvkem popis tlačítka nástroj.|  
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Načte informace o nástroje, které udržuje ovládacím prvkem popis tlačítka nástroj.|  
|[CToolTipCtrl::HitTest](#hittest)|Testuje bod k určení, zda je v rámci ohraničující obdélník daného nástroje. Pokud ano, načte informace o tomto nástroji.|  
|[CToolTipCtrl::Pop](#pop)|Popis tlačítka panelu nástrojů zobrazených odebere ze zobrazení.|  
|[CToolTipCtrl::Popup](#popup)|Způsobí, že aktuální ovládací prvek ToolTip zobrazíte na souřadnicích poslední zpráva myši.|  
|[CToolTipCtrl::RelayEvent](#relayevent)|Předá zpráva myši ovládacím prvkem popis tlačítka nástroj pro zpracování.|  
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Nastaví počáteční automaticky otevíraném okně a reshow doby trvání pro ovládacím prvkem popis tlačítka nástroj.|  
|[CToolTipCtrl::SetMargin](#setmargin)|Nastaví horní, vlevo, dolní a pravý okraj pro popis tlačítka panelu nástrojů.|  
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Nastavuje maximální šířku pro popis tlačítka panelu nástrojů.|  
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Nastaví barvu pozadí v popis tlačítka panelu nástrojů.|  
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Nastaví barvu textu v panelu nástrojů tip.|  
|[CToolTipCtrl::SetTitle](#settitle)|Přidá řetězec standardní ikonu a název popisku tlačítka.|  
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Nastaví informace, které udržuje popisku tlačítka pro nástroj.|  
|[CToolTipCtrl::SetToolRect](#settoolrect)|Nastaví nové ohraničující rámeček pro nástroj.|  
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Nastaví vizuální styl popis tlačítka panelu nástrojů.|  
|[CToolTipCtrl::Update](#update)|Přinutí nástroj aktuální vyžadovaly překreslení.|  
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Nastaví text popisu nástroje pro nástroj.|  
  
## <a name="remarks"></a>Poznámky  
 "Nástroje" je buď okno, jako jsou podřízené okno ovládacího prvku nebo definované aplikací obdélníkovou oblast v rámci klientské oblasti okna. Ve většině případů, povolí, jenom když uživatel umístí kurzor na nástroje a ponechá ho existuje pro přibližně polovinu sekundy je skrytý popisku tlačítka. Popis tlačítka zobrazen v blízkosti kurzoru a zmizí, když uživatel stiskne tlačítko myši nebo přesune kurzor mimo nástroj.  
  
 `CToolTipCtrl` poskytuje funkce pro ovládací prvek počáteční čas a dobu trvání popis tlačítka, okraj šířky okolo nástroje text tipu, šířka tip okno nástroje samotného a barvu textu a pozadí tlačítka. Ovládacím prvkem popis tlačítka jediného nástroje může poskytnout informace pro více než jeden nástroj.  
  
 `CToolTipCtrl` Třída poskytuje funkce pro Windows běžné nástroje ovládacím prvkem popis tlačítka. Tento ovládací prvek (a tedy `CToolTipCtrl` třídy) je dostupná jenom pro programy spuštěné v rámci Windows 95/98 a Windows NT verze 3.51 a vyšší.  
  
 Další informace o povolení tipů nástrojů najdete v tématu [popisů tlačítek v Windows Neodvozených ze třídy CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).  
  
 Další informace o používání `CToolTipCtrl`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md) a [použití objektu CToolTipCtrl](../../mfc/using-ctooltipctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CToolTipCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="activate"></a>  CToolTipCtrl::Activate  
 Voláním této funkce můžete aktivovat nebo deaktivovat ovládacím prvkem popis tlačítka nástroj.  
  
```  
void Activate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parametry  
 *bActivate*  
 Určuje, zda ovládacím prvkem popis tlačítka nástroj se aktivuje nebo deaktivuje.  
  
### <a name="remarks"></a>Poznámky  
 Pokud *bActivate* má hodnotu TRUE, je aktivován ovládací prvek, pokud má hodnotu FALSE, je deaktivováno.  
  
 Při aktivním ovládacím prvkem popis tlačítka nástroj tip informace nástroje se zobrazí, když ukazatel zůstane na nástroj, který je registrovaný pomocí ovládacího prvku; Když je neaktivní, tip informace nástroje nezobrazí, i když je kurzor na nástroj.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="addtool"></a>  CToolTipCtrl::AddTool  
 Zaregistruje nástroj s ovládacím prvkem popis tlačítka nástroj.  
  
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
 ID prostředku řetězců obsahující text pro nástroj.  
  
 *lpRectTool*  
 Ukazatel [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktury obsahující souřadnice nástroj společnosti ohraničující obdélník. Souřadnice jsou relativní vzhledem k levého horního rohu klientské oblasti okna identifikovaný *pWnd*.  
  
 *nIDTool*  
 ID tohoto nástroje.  
  
 *lpszText*  
 Ukazatel na text pro nástroj. Pokud tento parametr obsahuje hodnotu LPSTR_TEXTCALLBACK, zprávy oznámení TTN_NEEDTEXT přejít k nadřízenému okna, která *pWnd* odkazuje na.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 *LpRectTool* a *nIDTool* parametry musí být platné, nebo pokud *lpRectTool* má hodnotu NULL, *nIDTool* musí být 0.  
  
 Ovládacím prvkem popis tlačítka nástroj lze přidružit více než jeden nástroj. Voláním této funkce pro registraci nástroje s ovládacím prvkem popis tlačítka nástroje tak, aby informace uložené v popisu tlačítka se zobrazí, když ukazatel zůstane na nástroj.  
  
> [!NOTE]
>  Nelze nastavit popisku tlačítka na statický ovládací prvek pomocí `AddTool`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="adjustrect"></a>  CToolTipCtrl::AdjustRect  
 Převede mezi ovládací prvek tooltip text zobrazení obdélník a jeho okno obdélník.  
  
```  
BOOL AdjustRect(
    LPRECT lprc,  
    BOOL bLarger = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Ukazatel [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která obsahuje obdélník tip okno nástroje nebo zobrazovací obdélník text.  
  
 *bLarger*  
 Při hodnotě TRUE se *lprc* slouží k určení obdélník zobrazení textu a přijímat odpovídající rámeček okna. Pokud má hodnotu FALSE, *lprc* slouží k určení okno obdélníku, a přijímá zobrazovací obdélník odpovídající text.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud dojde k přenastavení úspěšně obdélník; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce vypočítá nástroj tip obdélníku ovládacího prvku textové zobrazení z jeho okno obdélník nebo obdélníku tip okna nástroje, musí zobrazit zobrazovací obdélník zadaný text.  
  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_ADJUSTRECT](/windows/desktop/Controls/ttm-adjustrect), jak je popsáno v sadě Windows SDK.  
  
##  <a name="create"></a>  CToolTipCtrl::Create  
 Ovládacím prvkem popis tlačítka nástroj vytvoří a připojí ho k `CToolTipCtrl` objektu.  
  
```  
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Určuje nadřazené okno ovládacího prvku tip nástroj, obvykle `CDialog`. Nesmí být NULL.  
  
 *dwStyle*  
 Určuje styl ovládacím prvkem popis tlačítka nástroj. Zobrazit **poznámky** části Další informace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulovou hodnotu, pokud `CToolTipCtrl` objekt je úspěšně vytvořený; jinak vrátí hodnotu 0.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CToolTipCtrl` ve dvou krocích. Nejprve volat konstruktor k vytvoření `CToolTipCtrl` objekt a následně zavolat `Create` ovládacím prvkem popis tlačítka nástroje a vytvořte tak `CToolTipCtrl` objektu.  
  
 *DwStyle* parametr může být libovolná kombinace [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles). Kromě toho ovládacím prvkem popis tlačítka nástroj má dvě styly specifický pro třídu: TTS_ALWAYSTIP a TTS_NOPREFIX.  
  
|Styl|Význam|  
|-----------|-------------|  
|TTS_ALWAYSTIP|Určuje, že se zobrazí popis tlačítka, když je ukazatel myši na nástroje, bez ohledu na to, zda okno vlastníka ovládacím prvkem popis tlačítka nástroj aktivní nebo neaktivní. Bez tohoto stylu ovládacím prvkem popis tlačítka nástroje se zobrazí při aktivním nástroje nadřazenému oknu, ale ne v případě, že je neaktivní.|  
|TTS_NOPREFIX|Tento styl zabrání systému odstranění znaků z řetězce ampersand (&). Pokud není ovládacím prvkem popis tlačítka nástroj TTS_NOPREFIX styl, systém automaticky odstraní znaky ampersand, což umožňuje aplikaci používat stejný řetězec jako položku nabídky a jako text v ovládacím prvkem popis tlačítka nástroj.|  
  
 Ovládacím prvkem popis tlačítka nástroj má WS_POPUP a WS_EX_TOOLWINDOW okno styly, bez ohledu na to, zda je určit při vytváření ovládacího prvku.  
  
 K vytvoření ovládacím prvkem popis tlačítka nástroj s rozšířenou windows styly, volání [CToolTipCtrl::CreateEx](#createex) místo `Create`.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="createex"></a>  CToolTipCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízené okno) a přidružte jej k `CToolTipCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwStyle = 0,  
    DWORD dwStyleEx = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentWnd*  
 Ukazatel na okno, který je nadřazeného ovládacího prvku.  
  
 *dwStyle*  
 Určuje styl ovládacím prvkem popis tlačítka nástroj. Zobrazit **poznámky** část [vytvořit](#create) Další informace.  
  
 *dwStyleEx*  
 Určuje rozšířený styl ovládacího prvku vytváří. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo `Create` použít rozšířené styly Windows určené předponu rozšířeného stylu Windows **WS_EX_**.  
  
##  <a name="ctooltipctrl"></a>  CToolTipCtrl::CToolTipCtrl  
 Vytvoří `CToolTipCtrl` objektu.  
  
```  
CToolTipCtrl();
```  
  
### <a name="remarks"></a>Poznámky  
 Je nutné volat `Create` po konstrukci objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]  
  
##  <a name="deltool"></a>  CToolTipCtrl::DelTool  
 Odebere nástroj určený *pWnd* a *nIDTool* z kolekce nástroje podporována ovládacím prvkem popis tlačítka nástroj.  
  
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
 Získá velikost tlačítka.  
  
```  
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lpToolInfo*  
 Ukazatel na nástroj tip [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Velikost tlačítka.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_GETBUBBLESIZE](/windows/desktop/Controls/ttm-getbubblesize), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getcurrenttool"></a>  CToolTipCtrl::GetCurrentTool  
 Načte informace, jako je například velikost, umístění a textu, od okna popisu zobrazí aktuální ovládací prvek tooltip.  
  
```  
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out] *lpToolInfo*|Ukazatel [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) struktura, která obdrží informace o aktuální okno s popisem tlačítka.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud tyto informace se načítají úspěšně; v opačném případě hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TTM_GETCURRENTTOOL](/windows/desktop/Controls/ttm-getcurrenttool) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu načte informace o aktuální okno s popisem tlačítka.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]  
  
##  <a name="getdelaytime"></a>  CToolTipCtrl::GetDelayTime  
 Získá počáteční automaticky otevíraném okně a reshow dob trvání aktuálně nastavený pro ovládacím prvkem popis tlačítka nástroj.  
  
```  
int GetDelayTime(DWORD dwDuration) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwDuration*  
 Příznak, který určuje hodnotu doby trvání, která budou načítat. Tento parametr může být jeden z následujících hodnot:  
  
- Načíst TTDT_AUTOPOP dobu okno popisek zůstává viditelná, pokud ukazatel setrvá uvnitř nástroje ohraničující obdélník.  
  
- Načíst TTDT_INITIAL se zobrazí dobu, po kterou je ukazatel musí zůstat pohybu v rámci nástroje ohraničující obdélník před tip panel nástrojů.  
  
- Načíst TTDT_RESHOW doba potřebná pro následné oknům tip jako ukazatel přesune z jednoho nástroje do jiného.  
  
### <a name="return-value"></a>Návratová hodnota  
 Zadané době doba v milisekundách  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_GETDELAYTIME](/windows/desktop/Controls/ttm-getdelaytime), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getmargin"></a>  CToolTipCtrl::GetMargin  
 Načte horní, vlevo, dolní a pravý okraj nastaven pro popis tlačítka panelu nástrojů.  
  
```  
void GetMargin(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Adresa `RECT` struktura, která bude dostávat informace okraj. Členové [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura nedefinují ohraničující obdélník. Pro účely této zprávy jsou členy struktury interpretován takto:  
  
|Člen|Reprezentace|  
|------------|--------------------|  
|`top`|Vzdálenost mezi horní okraj a horní nástroj text tipu, v pixelech.|  
|`left`|Vzdálenost mezi levého ohraničení a na levém konci text tipu, v pixelech.|  
|`bottom`|Vzdálenost mezi dolního ohraničení a dolní část text tipu, v pixelech.|  
|`right`|Vzdálenost mezi pravého ohraničení a na pravém konci text tipu, v pixelech.|  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_GETMARGIN](/windows/desktop/Controls/ttm-getmargin), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getmaxtipwidth"></a>  CToolTipCtrl::GetMaxTipWidth  
 Získá maximální šířku pro popis tlačítka panelu nástrojů.  
  
```  
int GetMaxTipWidth() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Maximální šířka pro popis tlačítka panelu nástrojů.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_GETMAXTIPWIDTH](/windows/desktop/Controls/ttm-getmaxtipwidth), jak je popsáno v sadě Windows SDK.  
  
##  <a name="gettext"></a>  CToolTipCtrl::GetText  
 Načte text, který udržuje ovládacím prvkem popis tlačítka nástroj pro nástroj.  
  
```  
void GetText(
    CString& str,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *str*  
 Odkaz `CString` objekt, který přijme nástroje text.  
  
 *pWnd*  
 Ukazatel na okno, které obsahuje nástroj.  
  
 *nIDTool*  
 ID tohoto nástroje.  
  
### <a name="remarks"></a>Poznámky  
 *PWnd* a *nIDTool* parametry identifikovat nástroj. Pokud tento nástroj s ovládacím prvkem popis tlačítka nástroj prostřednictvím předchozí volání dříve registrované `CToolTipCtrl::AddTool`, objekt, který odkazuje *str* parametr je přiřazený nástroje text.  
  
##  <a name="gettipbkcolor"></a>  CToolTipCtrl::GetTipBkColor  
 Zjišťuje barvu pozadí v popis tlačítka panelu nástrojů.  
  
```  
COLORREF GetTipBkColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](/windows/desktop/gdi/colorref) hodnotu, která představuje barvu pozadí.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_GETTIPBKCOLOR](/windows/desktop/Controls/ttm-gettipbkcolor), jak je popsáno v sadě Windows SDK.  
  
##  <a name="gettiptextcolor"></a>  CToolTipCtrl::GetTipTextColor  
 Načte barvu textu v panelu nástrojů tip.  
  
```  
COLORREF GetTipTextColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](/windows/desktop/gdi/colorref) hodnotu, která představuje barvu textu.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_GETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-gettiptextcolor), jak je popsáno v sadě Windows SDK.  
  
##  <a name="gettitle"></a>  CToolTipCtrl::GetTitle  
 Načte název aktuální ovládací prvek tooltip.  
  
```  
void GetTitle(PTTGETTITLE pttgt) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out] *pttgt*|Ukazatel [TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle) strukturu, která obsahuje informace o ovládacím prvku ToolTip. Po návratu tato metoda *pszTitle* člena [TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle) struktury body textu nadpisu.|  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TTM_GETTITLE](/windows/desktop/Controls/ttm-gettitle) zprávu, která je popsána v sadě Windows SDK.  
  
##  <a name="gettoolcount"></a>  CToolTipCtrl::GetToolCount  
 Získá počet nástroje zaregistrovaný s ovládacím prvkem popis tlačítka nástroj.  
  
```  
int GetToolCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet nástroje zaregistrovaného ovládacím prvkem popis tlačítka nástroj.  
  
##  <a name="gettoolinfo"></a>  CToolTipCtrl::GetToolInfo  
 Načte informace o nástroje, které udržuje ovládacím prvkem popis tlačítka nástroj.  
  
```  
BOOL GetToolInfo(
    CToolInfo& ToolInfo,  
    CWnd* pWnd,  
    UINT_PTR nIDTool = 0) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *ToolInfo*  
 Odkaz `TOOLINFO` objekt, který přijme nástroje text.  
  
 *pWnd*  
 Ukazatel na okno, které obsahuje nástroj.  
  
 *nIDTool*  
 ID tohoto nástroje.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 `hwnd` a `uId` členy [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) struktura odkazuje *CToolInfo* identifikovat nástroj. Pokud tento nástroj je zaregistrován s ovládacím prvkem popis tlačítka nástroj prostřednictvím předchozí volání `AddTool`, `TOOLINFO` struktura je vyplněna informacemi o tomto nástroji.  
  
##  <a name="hittest"></a>  CToolTipCtrl::HitTest  
 Testuje, přejděte na příkaz zjistit, zda je v rámci ohraničující obdélník daný nástroj a pokud ano, načíst informace o tomto nástroji.  
  
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
 Ukazatel `CPoint` objekt, který obsahuje souřadnice bodu má být testována.  
  
 *lpToolInfo*  
 Ukazatel na [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) strukturu, která obsahuje informace o tomto nástroji.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je bod určené informace o spuštění testu v rámci nástroje ohraničující obdélník; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tato funkce vrací nenulovou hodnotu, struktura odkazované *lpToolInfo* je vyplněna informace o nástroji, v jehož obdélníku je bod.  
  
 `TTHITTESTINFO` Struktura je definována takto:  
  
 `typedef struct _TT_HITTESTINFO { // tthti`  
  
 `HWND hwnd;   // handle of tool or window with tool`  
  
 `POINT pt;    // client coordinates of point to test`  
  
 `TOOLINFO ti; // receives information about the tool`  
  
 `} TTHITTESTINFO, FAR * LPHITTESTINFO;`  
  
 `hwnd`  
 Určuje nástroje popisovač.  
  
 `pt`  
 Určuje souřadnice bodu, pokud je bod je v nástroje ohraničující obdélník.  
  
 `ti`  
 Informace o tomto nástroji. Další informace o `TOOLINFO` struktury, přečtěte si téma [CToolTipCtrl::GetToolInfo](#gettoolinfo).  
  
##  <a name="pop"></a>  CToolTipCtrl::Pop  
 Popis tlačítka panelu nástrojů zobrazených odebere ze zobrazení.  
  
```  
void Pop();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_POP](/windows/desktop/Controls/ttm-pop), jak je popsáno v sadě Windows SDK.  
  
##  <a name="popup"></a>  CToolTipCtrl::Popup  
 Způsobí, že aktuální ovládací prvek tooltip zobrazíte na souřadnicích poslední zpráva myši.  
  
```  
void Popup();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [TTM_POPUP](/windows/desktop/Controls/ttm-popup) zprávu, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu zobrazí okno popisu tlačítka.  
  
 [!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]  
  
##  <a name="relayevent"></a>  CToolTipCtrl::RelayEvent  
 Předá zpráva myši ovládacím prvkem popis tlačítka nástroj pro zpracování.  
  
```  
void RelayEvent(LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMsg*  
 Ukazatel [MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958) strukturu, která obsahuje zprávy k přenosu.  
  
### <a name="remarks"></a>Poznámky  
 Ovládacím prvkem popis tlačítka nástroj zpracuje pouze následující zprávy, které se odesílají do něj pomocí `RelayEvent`:  
  
|WM_LBUTTONDOWN|WM_MOUSEMOVE A|  
|---------------------|-------------------|  
|WM_LBUTTONUP|WM_RBUTTONDOWN|  
|WM_MBUTTONDOWN|WM_RBUTTONUP|  
|WM_MBUTTONUP||  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).  
  
##  <a name="setdelaytime"></a>  CToolTipCtrl::SetDelayTime  
 Nastaví dobu zpoždění pro ovládací prvek popis tlačítka nástroj.  
  
```  
void SetDelayTime(UINT nDelay);

 
void SetDelayTime(
    DWORD dwDuration,  
    int iTime);
```  
  
### <a name="parameters"></a>Parametry  
 *nDelay*  
 Určuje novou dobu zpoždění v milisekundách.  
  
 *dwDuration*  
 Příznak, který určuje hodnotu doby trvání, která budou načítat. Zobrazit [CToolTipCtrl::GetDelayTime](#getdelaytime) popis platných hodnot.  
  
 *iTime*  
 Zadané době doba v milisekundách.  
  
### <a name="remarks"></a>Poznámky  
 Doba zpoždění je doba, po kterou kurzor musí zůstat na nástroji předtím, než se zobrazí okno tipů nástrojů. Výchozí doba zpoždění je 500 milisekund.  
  
##  <a name="setmargin"></a>  CToolTipCtrl::SetMargin  
 Nastaví horní, vlevo, dolní a pravý okraj pro popis tlačítka panelu nástrojů.  
  
```  
void SetMargin(LPRECT lprc);
```  
  
### <a name="parameters"></a>Parametry  
 *lprc*  
 Adresa `RECT` strukturu, která obsahuje informace okraj nastavit. Členové `RECT` struktura nedefinují ohraničující obdélník. Zobrazit [CToolTipCtrl::GetMargin](#getmargin) popis informací okraj.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_SETMARGIN](/windows/desktop/Controls/ttm-setmargin), jak je popsáno v sadě Windows SDK.  
  
##  <a name="setmaxtipwidth"></a>  CToolTipCtrl::SetMaxTipWidth  
 Nastavuje maximální šířku pro popis tlačítka panelu nástrojů.  
  
```  
int SetMaxTipWidth(int iWidth);
```  
  
### <a name="parameters"></a>Parametry  
 *iWidth*  
 Nástroj pro maximální šířku okna tip nastavit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí maximální tip šířka.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_SETMAXTIPWIDTH](/windows/desktop/Controls/ttm-setmaxtipwidth), jak je popsáno v sadě Windows SDK.  
  
##  <a name="settipbkcolor"></a>  CToolTipCtrl::SetTipBkColor  
 Nastaví barvu pozadí v popis tlačítka panelu nástrojů.  
  
```  
void SetTipBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 *CLR*  
 Novou barvou pozadí.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_SETTIPBKCOLOR](/windows/desktop/Controls/ttm-settipbkcolor), jak je popsáno v sadě Windows SDK.  
  
##  <a name="settiptextcolor"></a>  CToolTipCtrl::SetTipTextColor  
 Nastaví barvu textu v panelu nástrojů tip.  
  
```  
void SetTipTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 *CLR*  
 Barva textu.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_SETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-settiptextcolor), jak je popsáno v sadě Windows SDK.  
  
##  <a name="settitle"></a>  CToolTipCtrl::SetTitle  
 Přidá řetězec standardní ikonu a název popisku tlačítka.  
  
```  
BOOL SetTitle(
    UINT uIcon,  
    LPCTSTR lpstrTitle);
```  
  
### <a name="parameters"></a>Parametry  
 *uIcon*  
 Zobrazit *ikonu* v [TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle) v sadě Windows SDK.  
  
 *lpstrTitle*  
 Ukazatel na řetězec názvu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce implementuje chování zprávy Win32 [TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle), jak je popsáno v sadě Windows SDK.  
  
##  <a name="settoolinfo"></a>  CToolTipCtrl::SetToolInfo  
 Nastaví informace, které udržuje popisku tlačítka pro nástroj.  
  
```  
void SetToolInfo(LPTOOLINFO lpToolInfo);
```  
  
### <a name="parameters"></a>Parametry  
 *lpToolInfo*  
 Ukazatel [TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa) struktura, která určuje informace o nastavení.  
  
##  <a name="settoolrect"></a>  CToolTipCtrl::SetToolRect  
 Nastaví nové ohraničující rámeček pro nástroj.  
  
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
 Ukazatel [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) struktura zadání nového ohraničující obdélník.  
  
##  <a name="setwindowtheme"></a>  CToolTipCtrl::SetWindowTheme  
 Nastaví vizuální styl popis tlačítka panelu nástrojů.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parametry  
 *pszSubAppName*  
 Ukazatel na řetězec znaků Unicode, který obsahuje vizuální styl pro nastavení.  
  
### <a name="return-value"></a>Návratová hodnota  
 Návratová hodnota se nepoužívá.  
  
### <a name="remarks"></a>Poznámky  
 Tato členská funkce emuluje funkčnost [TTM_SETWINDOWTHEME](/windows/desktop/Controls/ttm-setwindowtheme) zprávu, jak je popsáno v sadě Windows SDK.  
  
##  <a name="update"></a>  CToolTipCtrl::Update  
 Přinutí nástroj aktuální vyžadovaly překreslení.  
  
```  
void Update();
```  
  
##  <a name="updatetiptext"></a>  CToolTipCtrl::UpdateTipText  
 Aktualizuje nástroj text tipu pro tento ovládací prvek nástroje.  
  
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
 Ukazatel na text pro nástroj.  
  
 *pWnd*  
 Ukazatel na okno, které obsahuje nástroj.  
  
 *nIDTool*  
 ID tohoto nástroje.  
  
 *nIDText*  
 ID prostředku řetězců obsahující text pro nástroj.  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CToolBar – třída](../../mfc/reference/ctoolbar-class.md)
