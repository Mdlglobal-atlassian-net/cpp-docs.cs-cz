---
title: Ccontrolbar – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CControlBar
- AFXEXT/CControlBar
- AFXEXT/CControlBar::CControlBar
- AFXEXT/CControlBar::CalcDynamicLayout
- AFXEXT/CControlBar::CalcFixedLayout
- AFXEXT/CControlBar::CalcInsideRect
- AFXEXT/CControlBar::DoPaint
- AFXEXT/CControlBar::DrawBorders
- AFXEXT/CControlBar::DrawGripper
- AFXEXT/CControlBar::EnableDocking
- AFXEXT/CControlBar::GetBarStyle
- AFXEXT/CControlBar::GetBorders
- AFXEXT/CControlBar::GetCount
- AFXEXT/CControlBar::GetDockingFrame
- AFXEXT/CControlBar::IsFloating
- AFXEXT/CControlBar::OnUpdateCmdUI
- AFXEXT/CControlBar::SetBarStyle
- AFXEXT/CControlBar::SetBorders
- AFXEXT/CControlBar::SetInPlaceOwner
- AFXEXT/CControlBar::m_bAutoDelete
- AFXEXT/CControlBar::m_pInPlaceOwner
dev_langs:
- C++
helpviewer_keywords:
- CControlBar [MFC], CControlBar
- CControlBar [MFC], CalcDynamicLayout
- CControlBar [MFC], CalcFixedLayout
- CControlBar [MFC], CalcInsideRect
- CControlBar [MFC], DoPaint
- CControlBar [MFC], DrawBorders
- CControlBar [MFC], DrawGripper
- CControlBar [MFC], EnableDocking
- CControlBar [MFC], GetBarStyle
- CControlBar [MFC], GetBorders
- CControlBar [MFC], GetCount
- CControlBar [MFC], GetDockingFrame
- CControlBar [MFC], IsFloating
- CControlBar [MFC], OnUpdateCmdUI
- CControlBar [MFC], SetBarStyle
- CControlBar [MFC], SetBorders
- CControlBar [MFC], SetInPlaceOwner
- CControlBar [MFC], m_bAutoDelete
- CControlBar [MFC], m_pInPlaceOwner
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d6eb567babdea0d747e6b684f6373403cb685c6
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956665"
---
# <a name="ccontrolbar-class"></a>Ccontrolbar – třída
Základní třída pro třídy ovládacích pruhů [cstatusbar –](../../mfc/reference/cstatusbar-class.md), [ctoolbar –](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md), a [ COleResizeBar](../../mfc/reference/coleresizebar-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CControlBar : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CControlBar::CControlBar](#ccontrolbar)|Vytvoří `CControlBar` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CControlBar::CalcDynamicLayout](#calcdynamiclayout)|Vrátí velikost panelu dynamické řízení jako [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.|  
|[CControlBar::CalcFixedLayout](#calcfixedlayout)|Vrátí velikost panelu Ovládací prvek jako [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.|  
|[CControlBar::CalcInsideRect](#calcinsiderect)|Vrátí aktuální dimenze oblasti ovládací prvek panelu; včetně ohraničení.|  
|[CControlBar::DoPaint](#dopaint)|Vykreslí ohraničení a úchytu ovládacího panelu.|  
|[CControlBar::DrawBorders](#drawborders)|Vykreslí ohraničení panelu ovládacího prvku.|  
|[CControlBar::DrawGripper](#drawgripper)|Vykreslí úchytu ovládacího panelu.|  
|[CControlBar::EnableDocking](#enabledocking)|Umožňuje ovládacích pruhů ukotveného nebo plovoucí.|  
|[CControlBar::GetBarStyle](#getbarstyle)|Načte nastavení ovládacího prvku panel stylu.|  
|[CControlBar::GetBorders](#getborders)|Načte hodnoty ohraničení panelu ovládacího prvku.|  
|[CControlBar::GetCount](#getcount)|Vrátí počet jinou hodnotu než `HWND` prvků v ovládacím panelu.|  
|[CControlBar::GetDockingFrame](#getdockingframe)|Vrací ukazatel na rámec, ke které je ovládací prvek panel ukotven.|  
|[CControlBar::IsFloating](#isfloating)|Vrátí nenulovou hodnotu, pokud je nejistá ovládacích pruhů plovoucí ovládacích pruhů.|  
|[CControlBar::OnUpdateCmdUI](#onupdatecmdui)|Volání obslužných rutin příkaz uživatelského rozhraní.|  
|[CControlBar::SetBarStyle](#setbarstyle)|Upravuje nastavení ovládacího panelu styl.|  
|[CControlBar::SetBorders](#setborders)|Nastaví hodnoty ohraničení panelu ovládacího prvku.|  
|[CControlBar::SetInPlaceOwner](#setinplaceowner)|Změní vlastníka místní ovládacích pruhů.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CControlBar::m_bAutoDelete](#m_bautodelete)|Pokud nenulové hodnoty, `CControlBar` je odstraněn objekt, když je zničení ovládacího panelu Windows.|  
|[CControlBar::m_pInPlaceOwner](#m_pinplaceowner)|Vlastník místní ovládacích pruhů.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvek panelu je okno, které je obvykle zarovnaný doleva nebo doprava okně s rámečkem. Může obsahovat podřízené položky, které jsou buď `HWND`– na základě ovládací prvky, které jsou windows, které generují a reagovat na zpráv systému Windows, nebo jiný - `HWND`– na základě položek, které nejsou windows a spravují v kódu aplikace nebo kódu framework. Seznamy a ovládacích prvcích pro úpravy jsou příklady `HWND`– ovládací prvky založené na; stavového řádku podokna a rastrový obrázek tlačítka jsou příklady bez - `HWND`– na základě ovládací prvky.  
  
 Ovládací prvek panelu windows jsou obvykle podřízená okna nadřazeného rámce okna a jsou obvykle stejné úrovně k zobrazení klienta nebo klienta MDI rámce okna. A `CControlBar` objektu používá informace o obdélníku klienta nadřazeného okna na pozici sám sebe. Potom informuje nadřazené okno, kolik místa zůstane nepřidělené v nadřazené okno klientské oblasti.  
  
 Další informace o `CControlBar`, najdete v části:  
  
- [Ovládací pruhy](../../mfc/control-bars.md)  
  
- [Technická poznámka 31: Ovládací pruhy](../../mfc/tn031-control-bars.md).  
  
-   Článek znalostní báze Knowledge Base Q242577: PRB: aktualizace příkaz uživatelského rozhraní obslužné rutiny provést není práci pro nabídky připojit do dialogového okna  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CControlBar`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxext.h  
  
##  <a name="calcdynamiclayout"></a>  CControlBar::CalcDynamicLayout  
 Volá rámec této – členská funkce pro výpočet dimenze dynamické panelu nástrojů.  
  
```  
virtual CSize CalcDynamicLayout(
    int nLength,  
    DWORD nMode);
```  
  
### <a name="parameters"></a>Parametry  
 *nLength*  
 Požadovaný dimenzi ovládacích pruhů vodorovné nebo svislé, v závislosti na *dwMode*.  
  
 *nMode*  
 Následující předdefinované příznaky se používají k určení výška a Šířka pruhu dynamické řízení. Použít bitové operace OR (&#124;) operátor kombinovat příznaků.  
  
|Příznaky režimu rozložení|Co znamená|  
|-----------------------|-------------------|  
|`LM_STRETCH`|Určuje, zda by měl být roztažen tak ovládacích pruhů, aby velikost rámečku. Nastavit, pokud panelu není ukotvení panelu (není k dispozici pro ukotvení). Není nastaven při panelu ukotvený nebo plovoucí (k dispozici pro ukotvení). Pokud nastavíte, `LM_STRETCH` ignoruje *nLength* a vrátí dimenze na základě `LM_HORZ` stavu. `LM_STRETCH` Podobně jako funguje *bStretch* parametr použitý v [CalcFixedLayout](#calcfixedlayout); najdete v části tohoto členská funkce pro další informace o vztah mezi roztažení a orientace.|  
|`LM_HORZ`|Označuje, že je na panelu orientované vodorovně nebo svisle. Nastavte, pokud je vodorovně orientované na panelu, a pokud je svisle orientované, není nastaven. `LM_HORZ` Podobně jako funguje *bHorz* parametr použitý v [CalcFixedLayout](#calcfixedlayout); najdete v části tohoto členská funkce pro další informace o vztah mezi roztažení a orientace.|  
|`LM_MRUWIDTH`|Naposledy použité dynamické šířku. Ignoruje *nLength* parametr a používá zapamatovaných naposledy použité šířky.|  
|`LM_HORZDOCK`|Vodorovný ukotven dimenzí. Ignoruje *nLength* parametr a vrátí velikost dynamické s největší šířku.|  
|`LM_VERTDOCK`|Svislý ukotven dimenzí. Ignoruje *nLength* parametr a vrátí velikost dynamické s největší výšku.|  
|`LM_LENGTHY`|Nastavit, pokud *nLength* Určuje výšku (směru osy Y) namísto šířku.|  
|`LM_COMMIT`|Obnoví `LM_MRUWIDTH` aktuální šířky plovoucí ovládacích pruhů.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Ovládacích pruhů velikost, v pixelech, nástroje [CSize](../../atl-mfc-shared/reference/csize-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Člen funkci poskytnout vlastní dynamické rozložení v odvozujete od třídy přepsat `CControlBar`. MFC – třídy odvozené od `CControlBar`, jako například [ctoolbar –](../../mfc/reference/ctoolbar-class.md), funkci člena přepsat a zadat své vlastní implementaci.  
  
##  <a name="calcfixedlayout"></a>  CControlBar::CalcFixedLayout  
 Volání této funkce člen k výpočtu vodorovné velikosti ovládacích pruhů.  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parametry  
 *bStretch*  
 Určuje, zda by měl být roztažen tak panelu, aby velikost rámečku. *BStretch* parametr je nenulové hodnoty v případě, že na panelu není ukotvení panelu (není k dispozici pro ukotvení) a 0, když je ukotveného nebo plovoucí (k dispozici pro ukotvení).  
  
 *bHorz*  
 Označuje, že je na panelu orientované vodorovně nebo svisle. *BHorz* parametr je nenulové hodnoty v případě panelu orientován vodorovně a je 0, pokud je to svisle orientovaný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ovládacích pruhů velikost, v pixelech, nástroje `CSize` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací pruhy například panely nástrojů lze roztáhnout vodorovně nebo svisle pro přizpůsobení tlačítka obsažené v ovládacím panelu.  
  
 Pokud *bStretch* je **TRUE**, funkce stretch dimenze podél orientaci poskytované *bHorz*. Jinými slovy Pokud *bHorz* je **FALSE**, ovládacích pruhů je roztažen tak svisle. Pokud *bStretch* je **FALSE**, dojde k žádné stretch. Následující tabulka uvádí počet možných kombinací a výsledný styly ovládacích pruhů, z *bStretch* a *bHorz*.  
  
|bStretch|bHorz|Roztažení|Orientace|Ukotvení nebo nebyla ukotvení|  
|--------------|-----------|----------------|-----------------|--------------------------|  
|**HODNOTA TRUE**|**HODNOTA TRUE**|Vodorovné roztažení|Vodorovně|Není ukotvení|  
|**HODNOTA TRUE**|**FALSE**|Svislé roztažení|Orientovány svisle|Není ukotvení|  
|**FALSE**|**HODNOTA TRUE**|Žádné roztažení k dispozici|Vodorovně|Ukotvení|  
|**FALSE**|**FALSE**|Žádné roztažení k dispozici|Orientovány svisle|Ukotvení|  
  
##  <a name="calcinsiderect"></a>  CControlBar::CalcInsideRect  
 Tato funkce pro výpočet klientské oblasti ovládacích pruhů volá framework.  
  
```  
virtual void CalcInsideRect(
    CRect& rect,  
    BOOL bHorz) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Rect –*  
 Obsahuje aktuální dimenze ovládací prvek panelu; včetně ohraničení.  
  
 *bHorz*  
 Označuje, že je na panelu orientované vodorovně nebo svisle. *BHorz* parametr je nenulové hodnoty v případě panelu orientován vodorovně a je 0, pokud je to svisle orientovaný.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána před vykreslením ovládacích pruhů.  
  
 Funkci pro přizpůsobení vykreslování ohraničení a panelu úchytu ovládacího panelu přepište.  
  
##  <a name="ccontrolbar"></a>  CControlBar::CControlBar  
 Vytvoří `CControlBar` objektu.  
  
```  
CControlBar();
```  
  
##  <a name="dopaint"></a>  CControlBar::DoPaint  
 Voláno rámcem k vykreslení ohraničení a panelu úchytu ovládacího panelu.  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 *primárního řadiče domény*  
 Odkazuje na kontext zařízení, který má být používané k vykreslování ohraničení a úchytu ovládacího panelu.  
  
### <a name="remarks"></a>Poznámky  
 Funkci k přizpůsobení chování vykreslování ovládacích pruhů přepište.  
  
 Další metodou přizpůsobení je přepsat `DrawBorders` a `DrawGripper` funkce a přidat vlastní kód vykreslování ohraničení a úchytu. Protože tyto metody jsou volány výchozí `DoPaint` metodu, pomocí přepsání `DoPaint` není potřeba.  
  
##  <a name="drawborders"></a>  CControlBar::DrawBorders  
 Voláno rámcem k vykreslení ohraničení panelu ovládacího prvku.  
  
```  
virtual void DrawBorders(
    CDC* pDC,  
    CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 *primárního řadiče domény*  
 Odkazuje na kontext zařízení, který má být používané k vykreslování ohraničení panelu ovládacího prvku.  
  
 *Rect –*  
 A `CRect` objekt obsahující rozměry ovládacích pruhů.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto funkci k přizpůsobení vzhledu ohraničení panelu ovládacího prvku.  
  
##  <a name="drawgripper"></a>  CControlBar::DrawGripper  
 Voláno rámcem k vykreslení úchytu ovládacího panelu.  
  
```  
virtual void DrawGripper(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parametry  
 *primárního řadiče domény*  
 Odkazuje na kontext zařízení, který má být používané k vykreslování úchytu ovládacího panelu.  
  
 *Rect –*  
 A `CRect` objekt obsahující rozměry úchytu ovládacího panelu.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkci můžete přizpůsobit vzhled úchytu ovládacího panelu.  
  
##  <a name="enabledocking"></a>  CControlBar::EnableDocking  
 Volejte tuto funkci povolit ovládacích pruhů chcete ukotvit.  
  
```  
void EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *dwDockStyle*  
 Určuje, jestli ovládacích pruhů podporuje ukotvení a postranní jeho nadřazeného okna, do kterého lze ukotvit ovládacích pruhů, pokud podporován. Může být jeden nebo více následujících akcí:  
  
- `CBRS_ALIGN_TOP` Umožňuje ukotvení v horní části oblasti klienta.  
  
- `CBRS_ALIGN_BOTTOM` Umožňuje ukotvení v dolní části klientské oblasti.  
  
- `CBRS_ALIGN_LEFT` Umožňuje ukotvení na levé straně klienta.  
  
- `CBRS_ALIGN_RIGHT` Umožňuje ukotvení na pravé straně klienta.  
  
- `CBRS_ALIGN_ANY` Umožňuje ukotvení na žádné straně klientské oblasti.  
  
- `CBRS_FLOAT_MULTI` Umožňuje více ovládací pruhy k obtékání v rámci jedné zkrácená okna.  
  
 Pokud je 0 (značí, to znamená, že žádné příznaky), nebude ukotvení panelu ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Postranní zadaný musí shodovat s jedním postranní povolené pro ukotvení v rámci okna cílové nebo ovládacích pruhů nelze jej ukotven k této oken s rámečkem.  
  
##  <a name="getbarstyle"></a>  CControlBar::GetBarStyle  
 Volání této funkce určete, který **CBRS_** (styly ovládacího prvku panel) aktuálně nastavení pro ovládací prvek panelu.  
  
```  
DWORD GetBarStyle();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Aktuální **CBRS_** (styly ovládacího prvku panel) nastavení pro ovládací prvek panelu. V tématu [CControlBar::SetBarStyle](#setbarstyle) úplný seznam dostupných stylů.  
  
### <a name="remarks"></a>Poznámky  
 Nezpracovává **WS_** styly (styl okna).  
  
##  <a name="getborders"></a>  CControlBar::GetBorders  
 Vrátí aktuální hodnoty ohraničení panelu ovládacího prvku.  
  
```  
CRect GetBorders() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 A `CRect` objekt, který obsahuje aktuální šířku každé straně objekt ovládacího prvku panel (v pixelech). Například hodnota *levém* člena z [CRect](../../atl-mfc-shared/reference/crect-class.md) objektu, je šířka ohraničení vlevo.  
  
##  <a name="getcount"></a>  CControlBar::GetCount  
 Vrátí počet jinou hodnotu než `HWND` položky na `CControlBar` objektu.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet jinou hodnotu než `HWND` položky na `CControlBar` objektu. Funkce vrátí hodnotu 0 [CDialogBar](../../mfc/reference/cdialogbar-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Typ položky závisí na objekt odvozené: podokna pro [cstatusbar –](../../mfc/reference/cstatusbar-class.md) objekty a tlačítka a oddělovače pro [ctoolbar –](../../mfc/reference/ctoolbar-class.md) objekty.  
  
##  <a name="getdockingframe"></a>  CControlBar::GetDockingFrame  
 Volání této funkce člen k získání ukazatele na aktuální rámce okna, ke kterému je ukotven ovládacích pruhů.  
  
```  
CFrameWnd* GetDockingFrame() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na rámec okna v případě úspěšného; v opačném případě **NULL**.  
  
 Pokud ovládacích pruhů není ukotven k okně s rámečkem (Pokud je plovoucí ovládacích pruhů), vrátí tato funkce ukazatel ke své nadřazené úloze [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md).  
  
### <a name="remarks"></a>Poznámky  
 Další informace o lze ukotvit ovládací pruhy najdete v tématu [CControlBar::EnableDocking](#enabledocking) a [CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar).  
  
##  <a name="isfloating"></a>  CControlBar::IsFloating  
 Volání této funkce člen můžete určit, zda je plovoucí nebo ukotveného panelu ovládacího prvku.  
  
```  
BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je plovoucí ovládacích pruhů; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Změnit stav ovládacích pruhů z ukotven číslo na plovoucí, volání [CFrameWnd::FloatControlBar](../../mfc/reference/cframewnd-class.md#floatcontrolbar).  
  
##  <a name="m_bautodelete"></a>  CControlBar::m_bAutoDelete  
 Pokud nenulové hodnoty, `CControlBar` je odstraněn objekt, když je zničení ovládacího panelu Windows.  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>Poznámky  
 *m_bAutoDelete* je veřejné proměnné typu **BOOL**.  
  
 Objekt ovládacího prvku panel je obvykle vložený objekt oken s rámečkem. V takovém případě *m_bAutoDelete* je 0, protože objekt embedded ovládací prvek panelu zničen při zničena rámce okna.  
  
 Tuto proměnnou nastavit na nenulovou hodnotu, pokud přidělíte `CControlBar` objekt na haldě a vy nemáte v plánu volání **odstranit**.  
  
##  <a name="m_pinplaceowner"></a>  CControlBar::m_pInPlaceOwner  
 Vlastník místní ovládacích pruhů.  
  
```  
CWnd* m_pInPlaceOwner;  
```  
  
##  <a name="onupdatecmdui"></a>  CControlBar::OnUpdateCmdUI  
 Tato funkce člen je voláno rámcem k aktualizaci stavu na panelu nástrojů nebo stav.  
  
```  
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,  
    BOOL bDisableIfNoHndler) = 0;  
```  
  
### <a name="parameters"></a>Parametry  
 *pTarget*  
 Body do hlavního rámce okna aplikace. Ukazatel this se používá pro směrování zpráv aktualizace.  
  
 *bDisableIfNoHndler*  
 Příznak, který indikuje, zda prvek, který nemá žádná obslužná rutina aktualizace by měla být automaticky zobrazen jako zakázáno.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li aktualizovat podokna nebo jednotlivé tlačítko, použijte `ON_UPDATE_COMMAND_UI` makro mapy zpráv správně nastavit obslužnou rutinu aktualizace. V tématu [on_update_command_ui –](message-map-macros-mfc.md#on_update_command_ui) Další informace o použití této makra.  
  
 `OnUpdateCmdUI` je voláno rámcem, když je aplikace nečinnosti. Okně s rámečkem aktualizovat musí být podřízeného okna alespoň nepřímo viditelné rámce okna. `OnUpdateCmdUI` je rozšířené přepisovatelné.  
  
##  <a name="setbarstyle"></a>  CControlBar::SetBarStyle  
 Volání této funkce můžete nastavit požadovanou **CBRS_** styly pro ovládací prvek panelu.  
  
```  
void SetBarStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parametry  
 *dwStyle*  
 Požadované styly pro ovládací prvek panelu. Může být jeden nebo více následujících akcí:  
  
- `CBRS_ALIGN_TOP` Umožňuje panelu řízení ukotvit do horní části klientské oblasti okně s rámečkem.  
  
- `CBRS_ALIGN_BOTTOM` Umožňuje panelu řízení ukotvit k dolnímu okraji klientské oblasti okně s rámečkem.  
  
- `CBRS_ALIGN_LEFT` Umožňuje panelu řízení ukotveny na levé straně klientské oblasti okně s rámečkem.  
  
- `CBRS_ALIGN_RIGHT` Umožňuje panelu řízení ukotveny na pravé straně klientské oblasti okně s rámečkem.  
  
- `CBRS_ALIGN_ANY` Umožňuje panelu řízení ukotveny na žádné straně klientské oblasti okně s rámečkem.  
  
- `CBRS_BORDER_TOP` Způsobí, že ohraničení, které se mají vykreslovat na horním okraji ovládacích pruhů, pokud je viditelné.  
  
- `CBRS_BORDER_BOTTOM` Způsobí, že ohraničení, které se mají vykreslovat na dolním okraji ovládacích pruhů, pokud je viditelné.  
  
- `CBRS_BORDER_LEFT` Způsobí, že ohraničení, které se mají vykreslovat na levém okraji ovládacích pruhů, pokud je viditelné.  
  
- `CBRS_BORDER_RIGHT` Způsobí, že ohraničení, které se mají vykreslovat na pravý okraj ovládacích pruhů, pokud je viditelné.  
  
- `CBRS_FLOAT_MULTI` Umožňuje více ovládací pruhy k obtékání v rámci jedné zkrácená okna.  
  
- `CBRS_TOOLTIPS` Způsobí, že popisy tlačítek, který se má zobrazit pro ovládací prvek panelu.  
  
- `CBRS_FLYBY` Způsobí, že text zprávy aktualizovat ve stejnou dobu jako popisy.  
  
- `CBRS_GRIPPER` Způsobí, že úchytu, podobně jako využívá pruhy v `CReBar` objekt, které se mají vykreslovat pro žádné `CControlBar`-odvozené třídy.  
  
### <a name="remarks"></a>Poznámky  
 Nemá vliv **WS_** nastavení (styl okna).  
  
##  <a name="setborders"></a>  CControlBar::SetBorders  
 Volání této funkce k nastavení velikosti ovládacích pruhů ohraničení.  
  
```  
void SetBorders(
    int cxLeft = 0,  
    int cyTop = 0,  
    int cxRight = 0,  
    int cyBottom = 0);  
  
void SetBorders(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parametry  
 *cxLeft*  
 Šířka levého okraje ovládacích pruhů (v pixelech).  
  
 *cyTop*  
 Výška horního okraje ovládacích pruhů (v pixelech).  
  
 *cxRight*  
 Šířka pravého okraje ovládacích pruhů (v pixelech).  
  
 *cyBottom*  
 Výška ovládacích pruhů dolní ohraničení (v pixelech).  
  
 *lprect –*  
 Ukazatel [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt, který obsahuje aktuální šířku (v pixelech) každou ohraničení panelu objekt ovládacího prvku.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu nastaví horní a dolní ohraničení panelu řízení 5 pixelů a levého a pravého ohraničení 2 pixelů:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#61](../../mfc/codesnippet/cpp/ccontrolbar-class_1.cpp)]  
  
##  <a name="setinplaceowner"></a>  CControlBar::SetInPlaceOwner  
 Změní vlastníka místní ovládacích pruhů.  
  
```  
void SetInPlaceOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 *pWnd*  
 Ukazatel na `CWnd` objektu.  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC CTRLBARS](../../visual-cpp-samples.md)   
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Ctoolbar – třída](../../mfc/reference/ctoolbar-class.md)   
 [CDialogBar – třída](../../mfc/reference/cdialogbar-class.md)   
 [Cstatusbar – třída](../../mfc/reference/cstatusbar-class.md)   
 [CReBar – třída](../../mfc/reference/crebar-class.md)
