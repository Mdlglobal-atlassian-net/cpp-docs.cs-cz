---
title: "Crebarctrl – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
dev_langs:
- C++
helpviewer_keywords:
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 592493a9eb554f0bdeecd291fdbe3ceb54c599c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="crebarctrl-class"></a>Crebarctrl – třída
Zapouzdřuje funkce ovládacího prvku matrice, což je kontejner pro podřízeného okna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CReBarCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|Vytvoří `CReBarCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CReBarCtrl::BeginDrag](#begindrag)|Ovládacího prvku matrice umístí do režimu přetažení myší.|  
|[CReBarCtrl::Create](#create)|Vytvoří ovládacího prvku matrice a připojí jej k `CReBarCtrl` objektu.|  
|[CReBarCtrl::CreateEx](#createex)|Vytvoří ovládacím prvkem matrice s zadaný Windows rozšířené styly a připojí jej k `CReBarCtrl` objektu.|  
|[CReBarCtrl::DeleteBand](#deleteband)|Odstraní pásmo z ovládacího prvku matrice.|  
|[CReBarCtrl::DragMove](#dragmove)|Přetáhněte pozici v ovládacím prvku matrice aktualizací po volání `BeginDrag`.|  
|[CReBarCtrl::EndDrag](#enddrag)|Ukončí operaci přetažení myší řízení matrice.|  
|[CReBarCtrl::GetBandBorders](#getbandborders)|Načte ohraničení pásmo.|  
|[CReBarCtrl::GetBandCount](#getbandcount)|Načte počet pásma aktuálně v ovládacím prvku matrice.|  
|[CReBarCtrl::GetBandInfo](#getbandinfo)|Načte informace o zadané vzdálené správy v ovládacím prvku matrice.|  
|[CReBarCtrl::GetBandMargins](#getbandmargins)|Načte okraje pásmo.|  
|[CReBarCtrl::GetBarHeight](#getbarheight)|Načte ovládacího prvku matrice.|  
|[CReBarCtrl::GetBarInfo](#getbarinfo)|Načte informace o prvku matrice a seznamu obrázků, které používá.|  
|[CReBarCtrl::GetBkColor](#getbkcolor)|Načte výchozí barvu pozadí ovládacího prvku matrice.|  
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|Načte [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) struktura přidruženého k ovládacímu prvku matrice.|  
|[CReBarCtrl::GetDropTarget](#getdroptarget)|Načte ovládacím prvkem matrice `IDropTarget` ukazatel rozhraní.|  
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|Získá styl rozšířené aktuální ovládacího prvku matrice.|  
|[CReBarCtrl::GetImageList](#getimagelist)|Načte seznamu obrázků s ovládacím prvkem matrice přidružené.|  
|[CReBarCtrl::GetPalette](#getpalette)|Načte aktuální palety ovládacího prvku matrice.|  
|[CReBarCtrl::GetRect](#getrect)|Načte ohraničující obdélník pro dané pásmo v ovládacím prvku matrice.|  
|[CReBarCtrl::GetRowCount](#getrowcount)|Načte počet vzdálené řádků v ovládacím prvku matrice.|  
|[CReBarCtrl::GetRowHeight](#getrowheight)|Načte výšku zadaný řádků v ovládacím prvku matrice.|  
|[CReBarCtrl::GetTextColor](#gettextcolor)|Načte ovládacím prvkem matrice výchozí barvy.|  
|[CReBarCtrl::GetToolTips](#gettooltips)|Načte popisovač všechny související s ovládacím prvkem matrice prvkem popis tlačítka.|  
|[CReBarCtrl::HitTest](#hittest)|Určuje, jaká část vzdálené matrice je k danému bodu na obrazovce, pokud matrice vzdálené existuje v tomto bodě.|  
|[CReBarCtrl::IDToIndex](#idtoindex)|Převede na vzdálené indexu v ovládacím prvku matrice vzdálené identifikátoru (ID).|  
|[CReBarCtrl::InsertBand](#insertband)|Vloží novou vzdálené správy v ovládacím prvku matrice.|  
|[CReBarCtrl::MaximizeBand](#maximizeband)|Změní velikost vzdálené správy v ovládacím prvku matrice na největší velikost.|  
|[CReBarCtrl::MinimizeBand](#minimizeband)|Změní velikost vzdálené správy v ovládacím prvku matrice na nejmenší velikost.|  
|[CReBarCtrl::MoveBand](#moveband)|Přesune pásmo z jeden index na jiný.|  
|[CReBarCtrl::PushChevron](#pushchevron)|Prostřednictvím kódu programu nabízených oznámení dvojitou šipku.|  
|[CReBarCtrl::RestoreBand](#restoreband)|Změní velikost vzdálené správy v ovládacím prvku matrice na jeho ideální velikost.|  
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Nastaví vlastnosti existující vzdálené správy v ovládacím prvku matrice.|  
|[CReBarCtrl::SetBandWidth](#setbandwidth)|Nastaví šířku zadaný ukotveného vzdálené správy v ovládacím prvku matrice aktuální.|  
|[CReBarCtrl::SetBarInfo](#setbarinfo)|Nastaví vlastnosti ovládacího prvku matrice.|  
|[CReBarCtrl::SetBkColor](#setbkcolor)|Nastaví barvu pozadí ovládacího prvku matrice výchozí.|  
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Nastaví barevné schéma pro tlačítek v ovládacím prvku matrice.|  
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|Nastaví rozšířené styly pro aktuální ovládacího prvku matrice.|  
|[CReBarCtrl::SetImageList](#setimagelist)|Nastaví ovládacím prvkem matrice seznamu obrázků.|  
|[CReBarCtrl::SetOwner](#setowner)|Nastaví okno ovládacím prvkem matrice vlastníka.|  
|[CReBarCtrl::SetPalette](#setpalette)|Nastaví aktuální palety ovládacího prvku matrice.|  
|[CReBarCtrl::SetTextColor](#settextcolor)|Nastaví barvu textu ovládacím prvkem matrice výchozí.|  
|[CReBarCtrl::SetToolTips](#settooltips)|Přidruží prvkem popis tlačítka s ovládacím prvkem matrice.|  
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|Nastaví vizuální styl ovládacího prvku matrice.|  
|[CReBarCtrl::ShowBand](#showband)|Zobrazí nebo skryje dané pásmo v ovládacím prvku matrice.|  
|[CReBarCtrl::SizeToRect](#sizetorect)|Vyhovuje ovládacím prvkem matrice na zadaný obdélník.|  
  
## <a name="remarks"></a>Poznámky  
 Aplikace, ve které je umístěn ovládacího prvku matrice přiřadí podřízeného okna obsaženého v ovládacím prvku matrice na vzdálené matrice. Podřízeného okna je obvykle jiné běžného ovládacího prvku.  
  
 Ovládací prvky matrice obsahovat jeden nebo více pásma. Každé vzdálené správy může obsahovat kombinaci řádku úchytu, rastrový obrázek, text popisku a podřízeného okna. Vzdálené správy může obsahovat pouze jeden z těchto položek.  
  
 Ovládacího prvku matrice můžete zobrazit podřízeného okna přes rastrový obrázek zadaný pozadí. Všechny ovládací pruhy matrice velikost lze změnit, kromě těch, které používají **RBBS_FIXEDSIZE** stylu. Jako umístění nebo velikost pásmo ovládacího prvku matrice, ovládacího prvku matrice spravuje velikost a umístění podřízeného okna přiřazené k této vzdálené správy. Změnit velikost nebo změnit pořadí pruhy v ovládacím prvku, klikněte na tlačítko a přetáhněte ji vzdálené úchytu panelu.  
  
 Následující obrázek znázorňuje ovládacím prvkem matrice, který má tři pásma:  
  
-   Vzdálené 0 obsahuje ovládacím prvku panel nástrojů plochý, transparentní.  
  
-   Vzdálené 1 obsahuje obě transparentní standardní a transparentní rozevírací tlačítka.  
  
-   Vzdálené 2 obsahuje čtyři standardní tlačítka a pole se seznamem.  
  
     ![Příklad nabídky matrice](../../mfc/reference/media/vc4scc1.gif "vc4scc1")  
  
## <a name="rebar-control"></a>Matrice – ovládací prvek  
 Matrice – ovládací prvky podpory:  
  
-   Seznamy obrázků.  
  
-   Zpracování zpráv.  
  
-   Vlastní kreslení funkce.  
  
-   Celou řadu kromě standardní okno Styly – styly ovládacích prvků. Seznam těchto styly najdete v tématu [– styly ovládacího prvku matrice](http://msdn.microsoft.com/library/windows/desktop/bb774377) ve Windows SDK.  
  
 Další informace najdete v tématu [crebarctrl pomocí –](../../mfc/using-crebarctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="begindrag"></a>CReBarCtrl::BeginDrag  
 Implementuje chování zprávy Win32 [RB_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774429), jak je popsáno v sadě Windows SDK.  
  
```  
void BeginDrag(
    UINT uBand,  
    DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index počítaný od nuly vzdálené správy, který bude mít vliv na operaci přetažení myší.  
  
 `dwPos`  
 A `DWORD` hodnotu, která obsahuje počáteční souřadnic myši. Vodorovné souřadnice je součástí LOWORD a svislé souřadnice je součástí HIWORD. Pokud předáte `(DWORD)-1`, ovládacího prvku matrice použije pozici myš, čas posledního ovládacího prvku vlákno názvem **GetMessage** nebo **PeekMessage**.  
  
##  <a name="create"></a>CReBarCtrl::Create  
 Vytvoří ovládacího prvku matrice a připojí jej k `CReBarCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje kombinaci styly ovládacího prvku matrice použité pro ovládací prvek. V tématu [– styly ovládacího prvku matrice](http://msdn.microsoft.com/library/windows/desktop/bb774377) ve Windows SDK pro seznam podporovaných stylů.  
  
 `rect`  
 Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, což je pozice a velikosti ovládacího prvku matrice.  
  
 `pParentWnd`  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je okno nadřazeného ovládacího prvku matrice. Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku matrice ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je objekt vytvořený úspěšně; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Vytvoření ovládacího prvku matrice ve dvou krocích:  
  
1.  Volání [crebarctrl –](#crebarctrl) k vytvoření `CReBarCtrl` objektu.  
  
2.  Volání této funkce člen, který vytvoří ovládacího prvku matrice Windows a připojí jej k `CReBarCtrl` objektu.  
  
 Při volání **vytvořit**, běžné ovládací prvky jsou inicializovány.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>CReBarCtrl::CreateEx  
 Vytvoří ovládací prvek (podřízeného okna) a přidruží ji s `CReBarCtrl` objektu.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwExStyle`  
 Určuje styl rozšířené vytváří ovládacího prvku. Seznam rozšířené styly Windows najdete v tématu `dwExStyle` parametr pro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) ve Windows SDK.  
  
 `dwStyle`  
 Určuje kombinaci styly ovládacího prvku matrice použité pro ovládací prvek. Seznam podporovaných styly najdete v tématu [– styly ovládacího prvku matrice](http://msdn.microsoft.com/library/windows/desktop/bb774377) ve Windows SDK.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující velikost a umístění okna byly vytvořeny v souřadnice klienta `pParentWnd`.  
  
 `pParentWnd`  
 Ukazatel na okně, které je nadřazeného ovládacího prvku.  
  
 `nID`  
 ID ovládacího prvku podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo [vytvořit](#create) použít rozšířené styly Windows určeného předponu rozšířené styl Windows **WS_EX_**.  
  
##  <a name="crebarctrl"></a>CReBarCtrl::CReBarCtrl  
 Vytvoří `CReBarCtrl` objektu.  
  
```  
CReBarCtrl();
```  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CReBarCtrl::Create](#create).  
  
##  <a name="deleteband"></a>CReBarCtrl::DeleteBand  
 Implementuje chování zprávy Win32 [RB_DELETEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774431), jak je popsáno v sadě Windows SDK.  
  
```  
BOOL DeleteBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index nule pásma k odstranění.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud vzdálené správy úspěšně odstraněno, jinak nenulové hodnoty jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]  
  
##  <a name="dragmove"></a>CReBarCtrl::DragMove  
 Implementuje chování zprávy Win32 [RB_DRAGMOVE](https://msdn.microsoft.com/library/bb774433.aspx), jak je popsáno v sadě Windows SDK.  
  
```  
void DragMove(DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>Parametry  
 `dwPos`  
 A `DWORD` hodnotu, která obsahuje nové souřadnic myši. Vodorovné souřadnice je součástí LOWORD a svislé souřadnice je součástí HIWORD. Pokud předáte `(DWORD)-1`, ovládacího prvku matrice použije pozici myš, čas posledního ovládacího prvku vlákno názvem **GetMessage** nebo **PeekMessage**.  
  
##  <a name="enddrag"></a>CReBarCtrl::EndDrag  
 Implementuje chování zprávy Win32 [RB_ENDDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774435), jak je popsáno v sadě Windows SDK.  
  
```  
void EndDrag();
```  
  
##  <a name="getbandborders"></a>CReBarCtrl::GetBandBorders  
 Implementuje chování zprávy Win32 [RB_GETBANDBORDERS](http://msdn.microsoft.com/library/windows/desktop/bb774437), jak je popsáno v sadě Windows SDK.  
  
```  
void GetBandBorders(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index počítaný od nuly vzdálené správy, pro kterou bude načten ohraničení.  
  
 `prc`  
 Ukazatel [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která bude přijímat ohraničení vzdálené správy. Pokud má ovládacího prvku matrice **RBS_BANDBORDERS** styl, každý člen této struktury obdrží počet pixelů na odpovídající straně vzdálené správy, které tvoří ohraničení. Pokud nemá ovládacího prvku matrice **RBS_BANDBORDERS** styl jen levém členem tato struktura obdrží platné informace. Popis styly ovládacího prvku matrice najdete v tématu [styly ovládacího prvku matrice](http://msdn.microsoft.com/library/windows/desktop/bb774377) ve Windows SDK.  
  
##  <a name="getbandcount"></a>CReBarCtrl::GetBandCount  
 Implementuje chování zprávy Win32 [RB_GETBANDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774439), jak je popsáno v sadě Windows SDK.  
  
```  
UINT GetBandCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet pásma přiřazenou ovládacímu prvku.  
  
##  <a name="getbandinfo"></a>CReBarCtrl::GetBandInfo  
 Implementuje chování zprávy Win32 [RB_GETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774451) jak je popsáno v sadě Windows SDK.  
  
```  
BOOL GetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index počítaný od nuly vzdálené správy, pro kterou se načíst informace.  
  
 `prbbi`  
 Ukazatel [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) k přijetí informací o vzdálené strukturu. Je nutné nastavit `cbSize` členem této struktury a `sizeof(REBARBANDINFO)` a nastavte **fMask** člena do položky, které chcete načíst před odesláním této zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
##  <a name="getbandmargins"></a>CReBarCtrl::GetBandMargins  
 Načte pravého okraje vzdálené správy.  
  
```  
void GetBandMargins(PMARGINS pMargins);
```  
  
### <a name="parameters"></a>Parametry  
 *pMargins*  
 Ukazatel [OKRAJE](http://msdn.microsoft.com/library/windows/desktop/bb773244)struktura, která bude přijímat informace.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce [RB_GETBANDMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb774453) zprávy, jak je popsáno v sadě Windows SDK.  
  
##  <a name="getbarheight"></a>CReBarCtrl::GetBarHeight  
 Načte výška panelu matrice.  
  
```  
UINT GetBarHeight() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která představuje výška v pixelech ovládacího prvku.  
  
##  <a name="getbarinfo"></a>CReBarCtrl::GetBarInfo  
 Implementuje chování zprávy Win32 [RB_GETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774457), jak je popsáno v sadě Windows SDK.  
  
```  
BOOL GetBarInfo(REBARINFO* prbi) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `prbi`  
 Ukazatel [REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395) struktura, která bude přijímat informace o ovládacího prvku matrice. Je nutné nastavit `cbSize` členem této struktury a `sizeof(REBARINFO)` před odesláním této zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
##  <a name="getbkcolor"></a>CReBarCtrl::GetBkColor  
 Implementuje chování zprávy Win32 [RB_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774459), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která představují aktuální výchozí barvu pozadí.  
  
##  <a name="getcolorscheme"></a>CReBarCtrl::GetColorScheme  
 Načte [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) struktura ovládacího prvku matrice.  
  
```  
BOOL GetColorScheme(COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>Parametry  
 `lpcs`  
 Ukazatel [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) struktury, jak je popsáno v sadě Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 **COLORSCHEME** struktura zahrnuje barva zvýraznění tlačítka a barvu stínu tlačítko.  
  
##  <a name="getdroptarget"></a>CReBarCtrl::GetDropTarget  
 Implementuje chování zprávy Win32 [RB_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb774463), jak je popsáno v sadě Windows SDK.  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na [IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679) rozhraní.  
  
##  <a name="getextendedstyle"></a>CReBarCtrl::GetExtendedStyle  
 Získá rozšířené styly ovládacího prvku matrice aktuální.  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Bitová kombinace (nebo) příznaky, které indikují rozšířené styly. Možné příznaky jsou `RBS_EX_SPLITTER` a `RBS_EX_TRANSPARENT`. Další informace najdete v tématu `dwMask` parametr [CReBarCtrl::SetExtendedStyle](#setextendedstyle) metoda.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [RB_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774433) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="getimagelist"></a>CReBarCtrl::GetImageList  
 Získá `CImageList` objekt přidružený k ovládacím prvkem matrice.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CImageList](../../mfc/reference/cimagelist-class.md) objektu. Vrátí **NULL** Pokud je pro ovládací prvek nastavené žádné seznamu obrázků.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen používá velikost a maska informace uložené v [REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395) struktury, jak je popsáno v sadě Windows SDK.  
  
##  <a name="getpalette"></a>CReBarCtrl::GetPalette  
 Načte aktuální palety ovládacího prvku matrice.  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CPalette](../../mfc/reference/cpalette-class.md) určující aktuální palety ovládacího prvku matrice.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že používá tuto funkci člen `CPalette` objektu jako hodnoty, nikoli `HPALETTE`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]  
  
##  <a name="getrect"></a>CReBarCtrl::GetRect  
 Implementuje chování zprávy Win32 [RB_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb774469), jak je popsáno v sadě Windows SDK.  
  
```  
BOOL GetRect(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index vzdálené správy v ovládacím prvku matrice počítáno od nuly.  
  
 `prc`  
 Ukazatel [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která bude přijímat hranice matrice vzdálené správy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]  
  
##  <a name="getrowcount"></a>CReBarCtrl::GetRowCount  
 Implementuje chování zprávy Win32 [RB_GETROWCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774471), jak je popsáno v sadě Windows SDK.  
  
```  
UINT GetRowCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **Celé_číslo** hodnotu, která představuje počet vzdálené řádky v ovládacím prvku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]  
  
##  <a name="getrowheight"></a>CReBarCtrl::GetRowHeight  
 Implementuje chování zprávy Win32 [RB_GETROWHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb774473), jak je popsáno v sadě Windows SDK.  
  
```  
UINT GetRowHeight(UINT uRow) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *uRow*  
 Index počítaný od nuly vzdálené správy, který bude mít výšku načíst.  
  
### <a name="return-value"></a>Návratová hodnota  
 A **Celé_číslo** hodnotu, která představuje výšku řádku, v pixelech.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]  
  
##  <a name="gettextcolor"></a>CReBarCtrl::GetTextColor  
 Implementuje chování zprávy Win32 [RB_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774475), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A **COLORREF** hodnotu, která představují aktuální výchozí barvu textu.  
  
##  <a name="gettooltips"></a>CReBarCtrl::GetToolTips  
 Implementuje chování zprávy Win32 [RB_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb774477), jak je popsáno v sadě Windows SDK.  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že implementace MFC `GetToolTips` vrací ukazatel na `CToolTipCtrl`, nikoli `HWND`.  
  
##  <a name="hittest"></a>CReBarCtrl::HitTest  
 Implementuje chování zprávy Win32 [RB_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb774494), jak je popsáno v sadě Windows SDK.  
  
```  
int HitTest(RBHITTESTINFO* prbht);
```  
  
### <a name="parameters"></a>Parametry  
 *prbht*  
 Ukazatel [RBHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774391) struktury. Před odesláním zprávy, **pt** členem tato struktura je nutné inicializovat na bod, který bude být testována, v souřadnicích klienta.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule pásma v daném bodě nebo -1, pokud žádné vzdálené matrice byla v bodě.  
  
##  <a name="idtoindex"></a>CReBarCtrl::IDToIndex  
 Implementuje chování zprávy Win32 [RB_IDTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774496), jak je popsáno v sadě Windows SDK.  
  
```  
int IDToIndex(UINT uBandID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *uBandID*  
 Identifikátor definované aplikací zadaný vzdálené předaná **interní databáze Windows** členem [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) struktury při vložení vzdálené správy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index počítaný od nuly vzdálené správy v případě úspěchu nebo jinak -1. Pokud existují duplicitní vzdálené indexy, je vrácen první z nich.  
  
##  <a name="insertband"></a>CReBarCtrl::InsertBand  
 Implementuje chování zprávy Win32 [RB_INSERTBAND](http://msdn.microsoft.com/library/windows/desktop/bb774498), jak je popsáno v sadě Windows SDK.  
  
```  
BOOL InsertBand(
    UINT uIndex,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>Parametry  
 *uIndex*  
 Index nule, budou vloženy vzdálené umístění. Pokud tento parametr nastavte na hodnotu -1, ovládacího prvku přidá nové vzdálené správy na posledním místě.  
  
 `prbbi`  
 Ukazatel [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) struktura, která definuje vzdálené správy, který má být vložen. Je nutné nastavit `cbSize` členem této struktury a `sizeof(REBARBANDINFO)` před voláním této funkce.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]  
  
##  <a name="maximizeband"></a>CReBarCtrl::MaximizeBand  
 Změní velikost vzdálené správy v ovládacím prvku matrice na největší velikost.  
  
```  
void MaximizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index vzdálené správy na maximalizovat, počítáno od nuly.  
  
### <a name="remarks"></a>Poznámky  
 Implementuje chování zprávy Win32 [RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500) s `fIdeal` nastaven na hodnotu 0, jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]  
  
##  <a name="minimizeband"></a>CReBarCtrl::MinimizeBand  
 Změní velikost vzdálené správy v ovládacím prvku matrice na nejmenší velikost.  
  
```  
void MinimizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index vzdálené minimalizaci počítáno od nuly.  
  
### <a name="remarks"></a>Poznámky  
 Implementuje chování zprávy Win32 [RB_MINIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774502), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]  
  
##  <a name="moveband"></a>CReBarCtrl::MoveBand  
 Implementuje chování zprávy Win32 [RB_MOVEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774504), jak je popsáno v sadě Windows SDK.  
  
```  
BOOL MoveBand(
    UINT uFrom,  
    UINT uTo);
```  
  
### <a name="parameters"></a>Parametry  
 *uFrom*  
 Index vzdálené přesunování počítáno od nuly.  
  
 *utomatická*  
 Index nule nové pozice vzdálené správy. Hodnota tohoto parametru musí být nikdy větší než počet pásem bez jednoho. Chcete-li získat počet pásem, volejte [GetBandCount](#getbandcount).  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
##  <a name="pushchevron"></a>CReBarCtrl::PushChevron  
 Implementuje chování zprávy Win32 [RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506), jak je popsáno v sadě Windows SDK.  
  
```  
void PushChevron(
    UINT uBand,  
    LPARAM lAppValue);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index nule pásma, jejichž dvojitou má poslat.  
  
 `lAppValue`  
 Aplikace definována 32bitovou hodnotu. V tématu `lAppValue` v [RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506) ve Windows SDK.  
  
##  <a name="restoreband"></a>CReBarCtrl::RestoreBand  
 Změní velikost vzdálené správy v ovládacím prvku matrice na jeho ideální velikost.  
  
```  
void RestoreBand(UINT uBand);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index vzdálené správy na maximalizovat, počítáno od nuly.  
  
### <a name="remarks"></a>Poznámky  
 Implementuje chování zprávy Win32 [RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500) s `fIdeal` nastavit hodnotu 1, jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]  
  
##  <a name="setbandinfo"></a>CReBarCtrl::SetBandInfo  
 Implementuje chování zprávy Win32 [RB_SETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774508), jak je popsáno v sadě Windows SDK.  
  
```  
BOOL SetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index nule pásma, aby přijaly nové nastavení.  
  
 `prbbi`  
 Ukazatel na [REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393) struktura, která definuje vzdálené správy, který má být vložen. Je nutné nastavit `cbSize` členem této struktury a `sizeof(REBARBANDINFO)` před odesláním této zprávy.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]  
  
##  <a name="setbandwidth"></a>CReBarCtrl::SetBandWidth  
 Nastaví šířku zadaný ukotveného vzdálené správy v ovládacím prvku matrice aktuální.  
  
```  
BOOL SetBandWidth(
    UINT uBand,   
    int cxWidth);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`uBand`|Index počítaný od nuly matrice vzdálené.|  
|[v]`cxWidth`|Nové šířka pásma, matrice, v pixelech.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je metoda úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [RB_SETBANDWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb774511) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_rebar`, který používá pro přístup k aktuální ovládacího prvku matrice. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví každé pásmo matrice být šířku stejné.  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]  
  
##  <a name="setbarinfo"></a>CReBarCtrl::SetBarInfo  
 Implementuje chování zprávy Win32 [RB_SETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774513), jak je popsáno v sadě Windows SDK.  
  
```  
BOOL SetBarInfo(REBARINFO* prbi);
```  
  
### <a name="parameters"></a>Parametry  
 `prbi`  
 Ukazatel [REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395) struktura, která obsahuje informace o nastavení. Je nutné nastavit `cbSize` členem této struktury a `sizeof(REBARINFO)` před odesláním této zprávy  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]  
  
##  <a name="setbkcolor"></a>CReBarCtrl::SetBkColor  
 Implementuje chování zprávy Win32 [RB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774515), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 `clr`  
 **COLORREF** hodnotu, která představuje nový výchozí barvu pozadí.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) hodnotu, která představuje předchozí výchozí barvu pozadí.  
  
### <a name="remarks"></a>Poznámky  
 Další informace o při nastavení barvy pozadí a jak nastavit výchozí v tohoto tématu.  
  
##  <a name="setcolorscheme"></a>CReBarCtrl::SetColorScheme  
 Nastaví barevné schéma pro tlačítek v ovládacím prvku matrice.  
  
```  
void SetColorScheme(const COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>Parametry  
 `lpcs`  
 Ukazatel [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) struktury, jak je popsáno v sadě Windows SDK.  
  
### <a name="remarks"></a>Poznámky  
 **COLORSCHEME** struktura zahrnuje barva zvýraznění tlačítka a barvu stínu tlačítko.  
  
##  <a name="setextendedstyle"></a>CReBarCtrl::SetExtendedStyle  
 Nastaví rozšířené styly pro aktuální ovládacího prvku matrice.  
  
```  
DWORD SetExtendedStyle(
    DWORD dwMask,   
    DWORD dwStyleEx);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v]`dwMask`|Bitová kombinace (nebo) příznaky, které určují, které příznaky ve `dwStyleEx` použít parametr. Pomocí jednoho nebo více z následujících hodnot:<br /><br /> RBS_EX_SPLITTER: Ve výchozím nastavení, zobrazit rozdělovače na dolní ve vodorovném režimu a doprava ve svislém režimu.<br /><br /> RBS_EX_TRANSPARENT: Předávání [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055) zpráva do nadřazeného okna.|  
|[v]`dwStyleEx`|Bitová kombinace (nebo) příznaky, které určují, styly, které chcete použít. Pokud chcete nastavit styl, zadejte stejné příznak, který se používá v `dwMask` parametr. Chcete-li obnovit styl, zadejte binární nula.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Předchozí rozšířený styl.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [RB_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774519) zprávy, která je popsána v sadě Windows SDK.  
  
##  <a name="setimagelist"></a>CReBarCtrl::SetImageList  
 Přiřadí ovládacím prvkem matrice seznamu obrázků.  
  
```  
BOOL SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `pImageList`  
 Ukazatel [CImageList](../../mfc/reference/cimagelist-class.md) objekt obsahující seznam obrázků pro přiřazení do ovládacího prvku matrice.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
##  <a name="setowner"></a>CReBarCtrl::SetOwner  
 Implementuje chování zprávy Win32 [RB_SETPARENT](http://msdn.microsoft.com/library/windows/desktop/bb774522), jak je popsáno v sadě Windows SDK.  
  
```  
CWnd* SetOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Ukazatel na `CWnd` objekt, který chcete nastavit jako vlastník ovládacího prvku matrice.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je aktuální vlastník ovládacího prvku matrice.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že tento – členská funkce používá ukazatele na `CWnd` objekty pro aktuální a vybrané vlastník ovládacího prvku matrice, nikoli zpracovává do systému windows.  
  
> [!NOTE]
>  Tato funkce člen nezmění skutečný nadřazeného objektu, který byl nastaven při vytvoření ovládacího prvku; místo odešle zprávy s oznámením v okně, které zadáte.  
  
##  <a name="setpalette"></a>CReBarCtrl::SetPalette  
 Implementuje chování zprávy Win32 [RB_SETPALETTE](http://msdn.microsoft.com/library/windows/desktop/bb774520), jak je popsáno v sadě Windows SDK.  
  
```  
CPalette* SetPalette(HPALETTE hPal);
```  
  
### <a name="parameters"></a>Parametry  
 *hPal*  
 `HPALETTE` Určující nové palety, který bude používat ovládacího prvku matrice.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CPalette](../../mfc/reference/cpalette-class.md) určující předchozí palety ovládacího prvku matrice.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že používá tuto funkci člen `CPalette` objektu jako hodnoty, nikoli `HPALETTE`.  
  
##  <a name="settextcolor"></a>CReBarCtrl::SetTextColor  
 Implementuje chování zprávy Win32 [RB_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774524), jak je popsáno v sadě Windows SDK.  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parametry  
 `clr`  
 A **COLORREF** hodnotu, která představuje nový text barvu `CReBarCtrl` objektu.  
  
### <a name="return-value"></a>Návratová hodnota  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) přidružené hodnotu představující předchozí barvy textu `CReBarCtrl` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Je poskytována pro podporu flexibilitu barvu textu v ovládacím prvku matrice.  
  
##  <a name="settooltips"></a>CReBarCtrl::SetToolTips  
 Přidruží prvkem popis tlačítka s ovládacím prvkem matrice.  
  
```  
void SetToolTips(CToolTipCtrl* pToolTip);
```  
  
### <a name="parameters"></a>Parametry  
 *pToolTip*  
 Ukazatel [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objektu  
  
### <a name="remarks"></a>Poznámky  
 Musíte zničit `CToolTipCtrl` objektu až skončíte s ním.  
  
##  <a name="setwindowtheme"></a>CReBarCtrl::SetWindowTheme  
 Nastaví vizuální styl ovládacího prvku matrice.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parametry  
 `pszSubAppName`  
 Ukazatel na řetězec znaků Unicode, který obsahuje vizuální styl matrice nastavit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí hodnotu, není použita.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen emuluje funkce [RB_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb774530) zprávy, jak je popsáno v sadě Windows SDK.  
  
##  <a name="showband"></a>CReBarCtrl::ShowBand  
 Implementuje chování zprávy Win32 [RB_SHOWBAND](http://msdn.microsoft.com/library/windows/desktop/bb774532), jak je popsáno v sadě Windows SDK.  
  
```  
BOOL ShowBand(
    UINT uBand,  
    BOOL fShow = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `uBand`  
 Index vzdálené správy v ovládacím prvku matrice počítáno od nuly.  
  
 *fShow*  
 Určuje, pokud vzdálené zobrazen nebo skryt. Pokud je tato hodnota **TRUE**, se zobrazí vzdálené správy. Jinak bude skrytá pásma.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
##  <a name="sizetorect"></a>CReBarCtrl::SizeToRect  
 Implementuje chování zprávy Win32 [RB_SIZETORECT](http://msdn.microsoft.com/library/windows/desktop/bb774534), jak je popsáno v sadě Windows SDK.  
  
```  
BOOL SizeToRect(CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 `rect`  
 Odkaz na [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který určuje obdélníku, která ovládacího prvku matrice by měl být dimenzovány pro.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Všimněte si, že používá tuto funkci člen `CRect` objekt jako parametr, ne `RECT` struktura.  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)


