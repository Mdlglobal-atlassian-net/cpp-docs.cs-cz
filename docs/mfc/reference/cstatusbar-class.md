---
title: "Cstatusbar – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
dev_langs: C++
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d5a669551bcc28328054e369ff70bbccbc505c5c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cstatusbar-class"></a>Cstatusbar – třída
Ovládací prvek panel s řádek podokna výstup textu nebo "indikátory."  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CStatusBar : public CControlBar  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CStatusBar::CStatusBar](#cstatusbar)|Vytvoří `CStatusBar` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CStatusBar::CommandToIndex](#commandtoindex)|Získá index pro ID dané indikátoru.|  
|[CStatusBar::Create](#create)|Vytvoří stavový řádek, připojí se k `CStatusBar` objektu a nastaví počáteční výšku písma a panelu.|  
|[CStatusBar::CreateEx](#createex)|Vytvoří `CStatusBar` objekt s další styly pro vložený `CStatusBarCtrl` objektu.|  
|[CStatusBar::DrawItem](#drawitem)|Volá se při visual aspektů změny ovládací prvek panelu stavu vykreslování vlastníka.|  
|[CStatusBar::GetItemID](#getitemid)|Získá ID indikátor pro daného indexu.|  
|[CStatusBar::GetItemRect](#getitemrect)|Získá zobrazení rámeček pro daného indexu.|  
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Získá ID indikátoru, stylu a tloušťky pro daného indexu.|  
|[CStatusBar::GetPaneStyle](#getpanestyle)|Získá styl indikátoru pro daného indexu.|  
|[CStatusBar::GetPaneText](#getpanetext)|Získá text indikátoru pro daného indexu.|  
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Umožňuje přímý přístup k podkladové běžného ovládacího prvku.|  
|[CStatusBar::SetIndicators](#setindicators)|Nastaví ID indikátoru.|  
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Nastaví ID indikátoru, stylu a tloušťky pro daného indexu.|  
|[CStatusBar::SetPaneStyle](#setpanestyle)|Nastaví styl indikátoru pro daného indexu.|  
|[CStatusBar::SetPaneText](#setpanetext)|Nastaví ukazatele text pro daného indexu.|  
  
## <a name="remarks"></a>Poznámky  
 Podokna výstup se běžně používají, jako řádky zprávy a jako indikátory stavu. Mezi příklady patří řádky zprávu nápovědy nabídky, které stručně popisují příkaz vybrané nabídky a indikátory, které se zobrazí stav SCROLL LOCK NUMLOCK a jiných klíčů.  
  
 [CStatusBar::GetStatusBarCtrl](#getstatusbarctrl), členské funkce nové MFC 4.0, můžete využít podporu Windows běžné ovládacího prvku pro stavovém řádku přizpůsobení a další funkce. `CStatusBar`Členské funkce získáte většinu funkcí běžných ovládacích prvků Windows; ale při volání `GetStatusBarCtrl`, můžete udělit stavové řádky i více společných vlastností stavového řádku systému Windows 95/98. Při volání `GetStatusBarCtrl`, vrátí odkaz na `CStatusBarCtrl` objektu. V tématu [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) pro další informace o návrhu panely nástrojů použití běžných ovládacích prvků Windows. Další obecné informace o běžných ovládacích prvcích najdete v tématu [běžné ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb775493) ve Windows SDK.  
  
 Rozhraní framework ukládá informace o indikátor pole s krajní levé ukazatele na pozici 0. Při vytváření stavového řádku použijete pole řetězce ID, která přidruží odpovídající indikátory rozhraní. Potom můžete řetězec ID nebo index pro přístup k slouží jako ukazatel.  
  
 Standardně je první indikátoru "elastické": zabírají stavového řádku délku, která nepoužívá jiné ukazatele podokna tak, aby ostatní podokna zarovnaný doprava.  
  
 Při vytváření stavového řádku, postupujte podle těchto kroků:  
  
1.  Vytvořit `CStatusBar` objektu.  
  
2.  Volání [vytvořit](#create) (nebo [CreateEx](#createex)) funkce vytváření stavového řádku okna a jeho k připojení `CStatusBar` objektu.  
  
3.  Volání [SetIndicators](#setindicators) a řetězec ID přidružit každý ukazatel.  
  
 Existují tři způsoby, jak aktualizovat textu v panelu stavového řádku:  
  
1.  Volání [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) aktualizace textu v podokně pouze 0.  
  
2.  Volání [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) ve stavovém řádku `ON_UPDATE_COMMAND_UI` obslužné rutiny.  
  
3.  Volání [SetPaneText](#setpanetext) aktualizovat text pro všechny podokně.  
  
 Volání [SetPaneStyle](#setpanestyle) aktualizovat styl panelu stavového řádku.  
  
 Další informace o používání `CStatusBar`, najdete v článku [stav implementace řádku v prostředí MFC](../../mfc/status-bar-implementation-in-mfc.md) a [Technická poznámka 31: ovládací pruhy](../../mfc/tn031-control-bars.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Ccontrolbar –](../../mfc/reference/ccontrolbar-class.md)  
  
 `CStatusBar`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="commandtoindex"></a>CStatusBar::CommandToIndex  
 Získá index indikátor pro dané ID.  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIDFind`  
 Řetězec ID indikátoru, jejichž index je mají být načteny.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index indikátoru, pokud bylo úspěšné; -1, pokud nebylo úspěšné.  
  
### <a name="remarks"></a>Poznámky  
 Index prvního indikátoru je 0.  
  
##  <a name="create"></a>CStatusBar::Create  
 Stavový řádek (podřízeného okna) vytvoří a přidruží ji s `CStatusBar` objektu.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objektu, jehož okno systému Windows je nadřazená stavový řádek.  
  
 `dwStyle`  
 Styl stavového řádku. Kromě standardní Windows [styly](../../mfc/reference/styles-used-by-mfc.md#window-styles), jsou podporovány tyto styly.  
  
- `CBRS_TOP`Ovládací prvek panelu je v horní části oken s rámečkem.  
  
- `CBRS_BOTTOM`Ovládací prvek panelu je v dolní části oken s rámečkem.  
  
- `CBRS_NOALIGN`Ovládací prvek panelu není změnit jejich umístění při změně velikosti nadřazeného objektu.  
  
 `nID`  
 ID podřízeného okna panelu nástrojů  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Také nastaví počáteční písma a stav výška panelu na výchozí hodnotu.  
  
##  <a name="createex"></a>CStatusBar::CreateEx  
 Volání této funkce na stavovém řádku (podřízeného okna) vytvořte a přidružte ji s `CStatusBar` objektu.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parametry  
 `pParentWnd`  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objektu, jehož okno systému Windows je nadřazená stavový řádek.  
  
 `dwCtrlStyle`  
 Další styly pro vytvoření vložený [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) objektu. Určuje výchozí stavového řádku bez úchyt pro změnu velikosti nebo popisek podporovat. Styly řádku stavu podporovány jsou:  
  
- **SBARS_SIZEGRIP** ovládacího prvku panel stav zahrnuje úchyt na pravém konci stavový řádek. Úchyt je podobná velikosti ohraničení; je obdélníkovou oblast, která může uživatel klikněte a přetáhněte ke změně velikosti nadřazeného okna.  
  
- **SBT_TOOLTIPS** podporuje popisy tlačítek na stavovém řádku.  
  
 Podrobnosti na tyto styly najdete v tématu [nastavení pro třídu CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).  
  
 `dwStyle`  
 Styl panelu stavu. Výchozí hodnota určuje vytvořený viditelné stavového řádku v dolní části okna rámce. Použít libovolnou kombinaci stavový řádek – styly ovládacích prvků uvedených v [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) a [CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create). Tento parametr by měla obsahovat však vždy ws_child – a ws_visible – styly.  
  
 `nID`  
 ID podřízené oken na stavovém řádku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce také nastaví počáteční písmo a nastaví stav výška panelu na výchozí hodnotu.  
  
 Použití `CreateEx`, místo [vytvořit](#create), pokud se určité styly musí být k dispozici při vytváření ovládacích prvků panelu embedded stavu. Například nastavit `dwCtrlStyle` k **SBT_TOOLTIPS** zobrazíte popisy tlačítek v objektu panelu stavu.  
  
##  <a name="cstatusbar"></a>CStatusBar::CStatusBar  
 Vytvoří `CStatusBar` objekt, vytvoří výchozí písmo stavového řádku v případě potřeby a nastaví výchozí hodnoty vlastnosti písma.  
  
```  
CStatusBar();
```  
  
##  <a name="drawitem"></a>CStatusBar::DrawItem  
 Tato funkce člen je voláno rámcem při visual aspektů panelu změny vykreslovaných vlastníkem stavu.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Ukazatel [drawitemstruct –](http://msdn.microsoft.com/library/windows/desktop/bb775802) struktura, která obsahuje informace o typu kreslení vyžaduje.  
  
### <a name="remarks"></a>Poznámky  
 **ItemAction** členem `DRAWITEMSTRUCT` struktura definuje kreslení akci, která má být provedena. Člen funkci implementovat kreslení pro kreslení vlastníka přepsat `CStatusBar` objektu. Aplikace by měla obnovit všechny grafiky zařízení rozhraní GDI objekty vybrané pro zadaný kontext zobrazení v `lpDrawItemStruct` před ukončení této funkce člen.  
  
##  <a name="getitemid"></a>CStatusBar::GetItemID  
 Vrátí ID indikátoru určeného `nIndex`.  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index indikátoru, jejíž ID je mají být načteny.  
  
### <a name="return-value"></a>Návratová hodnota  
 ID indikátoru určeného `nIndex`.  
  
##  <a name="getitemrect"></a>CStatusBar::GetItemRect  
 Zkopíruje souřadnice ukazatele určeného `nIndex` do struktury, na kterou odkazuje `lpRect`.  
  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index indikátoru, jejichž obdélníku souřadnice jsou uváděny mají být načteny.  
  
 `lpRect`  
 Odkazuje na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura nebo [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který se zobrazí souřadnice ukazatele určeného `nIndex`.  
  
### <a name="remarks"></a>Poznámky  
 Souřadnice jsou uváděny v pixelech relativně k levém horním rohu na stavovém řádku.  
  
##  <a name="getpaneinfo"></a>CStatusBar::GetPaneInfo  
 Nastaví `nID`, `nStyle`, a `cxWidth` ID, styl a šířka podokně indikátoru v umístění, které `nIndex`.  
  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index v podokně, jejichž informace je možné načíst.  
  
 `nID`  
 Odkaz na **Celé_číslo** , je nastaven na ID v podokně.  
  
 `nStyle`  
 Odkaz na **Celé_číslo** , je nastaven na styl v podokně.  
  
 `cxWidth`  
 Odkaz na celé číslo, které je nastaven na šířku podokna.  
  
##  <a name="getpanestyle"></a>CStatusBar::GetPaneStyle  
 Volání této funkce člen načíst styl panelu stavového řádku.  
  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index v podokně, jehož styl je mají být načteny.  
  
### <a name="return-value"></a>Návratová hodnota  
 Styl panelu stavového řádku určeného `nIndex`.  
  
### <a name="remarks"></a>Poznámky  
 Podokně styl určuje, jak se zobrazuje v podokně.  
  
 Seznam stylů, které jsou k dispozici pro stavové řádky najdete v tématu [vytvořit](#create).  
  
##  <a name="getpanetext"></a>CStatusBar::GetPaneText  
 Volání této funkce člen k načtení textu, který se zobrazí v podokně stavového řádku.  
  
```  
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index v podokně, jejíž text je mají být načteny.  
  
 `rString`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který obsahuje text, který má být načtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CString` objekt obsahující text v podokně.  
  
### <a name="remarks"></a>Poznámky  
 Druhý formulář člen funkce výplněmi `CString` objekt s textový řetězec.  
  
##  <a name="getstatusbarctrl"></a>CStatusBar::GetStatusBarCtrl  
 Tato funkce člen umožňuje přímý přístup k podkladové běžného ovládacího prvku.  
  
```  
CStatusBarCtrl& GetStatusBarCtrl() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Obsahuje odkaz na [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Použití `GetStatusBarCtrl` chcete využít výhod funkce Windows ovládacího prvku běžné stavového řádku a chcete využít výhod podpory [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) poskytuje pro přizpůsobení stavového řádku. Například pomocí běžného ovládacího prvku, můžete určit styl, který zahrnuje úchyt na stavovém řádku, nebo můžete určit styl tak, aby měl stavového řádku se zobrazí v horní části okna nadřazené klientské oblasti.  
  
 Další obecné informace o běžných ovládacích prvcích najdete v tématu [běžné ovládací prvky](http://msdn.microsoft.com/library/windows/desktop/bb775493) ve Windows SDK.  
  
##  <a name="setindicators"></a>CStatusBar::SetIndicators  
 Nastaví ID pro každý ukazatel na hodnotu zadanou pomocí odpovídající element pole `lpIDArray`, načte řetězec prostředku zadaného parametrem jednotlivých ID a nastaví ukazatele text na řetězec.  
  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpIDArray`  
 Ukazatel na pole ID.  
  
 `nIDCount`  
 Počet prvků v poli, na kterou odkazuje `lpIDArray`.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
##  <a name="setpaneinfo"></a>CStatusBar::SetPaneInfo  
 Nastaví zadaný indikátor podokně na nové ID, styl a šířku.  
  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index v podokně indikátoru, jehož styl má být nastavena.  
  
 `nID`  
 Nové ID pro podokně indikátoru.  
  
 `nStyle`  
 Nový styl indikátoru podokna.  
  
 `cxWidth`  
 Nové šířka pro podokně indikátoru.  
  
### <a name="remarks"></a>Poznámky  
 Podporovány jsou následující styly ukazatele:  
  
- **SBPS_NOBORDERS** žádné 3D ohraničení podokně.  
  
- **SBPS_POPOUT** zpětného ohraničení tak, aby text "POP."  
  
- **SBPS_DISABLED** není kreslení textu.  
  
- **SBPS_STRETCH** Stretch podokně k vyplnění nevyužité místo. Tento styl může mít pouze jeden podokně na stavovém řádku.  
  
- **SBPS_NORMAL** bez stretch, ohraničení a rozbalení.  
  
##  <a name="setpanestyle"></a>CStatusBar::SetPaneStyle  
 Volání této funkce člen nastavit styl panelu stavového řádku.  
  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index v podokně, jehož styl má být nastavena.  
  
 `nStyle`  
 Styl v podokně, jehož styl má být nastavena.  
  
### <a name="remarks"></a>Poznámky  
 Podokně styl určuje, jak se zobrazuje v podokně.  
  
 Seznam stylů, které jsou k dispozici pro stavové řádky najdete v tématu [SetPaneInfo](#setpaneinfo).  
  
##  <a name="setpanetext"></a>CStatusBar::SetPaneText  
 Volání této funkce člen nastavit podokně text na text, na kterou odkazuje `lpszNewText`.  
  
```  
BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index v podokně, jejíž text je možné nastavit.  
  
 `lpszNewText`  
 Ukazatel na nový text podokně.  
  
 *bUpdate*  
 Pokud **TRUE**, v podokně zneplatněna po nastavení textu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Po zavolání metody `SetPaneText`, je nutné přidat obslužnou rutinu aktualizace uživatelského rozhraní pro zobrazení nového textu ve stavovém řádku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CTRLBARS](../../visual-cpp-samples.md)   
 [Ukázka DLGCBR32 MFC](../../visual-cpp-samples.md)   
 [Ccontrolbar – třída](../../mfc/reference/ccontrolbar-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CStatusBarCtrl – třída](../../mfc/reference/cstatusbarctrl-class.md)   
 [Ccontrolbar – třída](../../mfc/reference/ccontrolbar-class.md)
