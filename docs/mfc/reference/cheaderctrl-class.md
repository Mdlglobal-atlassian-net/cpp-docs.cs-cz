---
title: CHeaderCtrl – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl [MFC], CHeaderCtrl
- CHeaderCtrl [MFC], ClearAllFilters
- CHeaderCtrl [MFC], ClearFilter
- CHeaderCtrl [MFC], Create
- CHeaderCtrl [MFC], CreateDragImage
- CHeaderCtrl [MFC], CreateEx
- CHeaderCtrl [MFC], DeleteItem
- CHeaderCtrl [MFC], DrawItem
- CHeaderCtrl [MFC], EditFilter
- CHeaderCtrl [MFC], GetBitmapMargin
- CHeaderCtrl [MFC], GetFocusedItem
- CHeaderCtrl [MFC], GetImageList
- CHeaderCtrl [MFC], GetItem
- CHeaderCtrl [MFC], GetItemCount
- CHeaderCtrl [MFC], GetItemDropDownRect
- CHeaderCtrl [MFC], GetItemRect
- CHeaderCtrl [MFC], GetOrderArray
- CHeaderCtrl [MFC], GetOverflowRect
- CHeaderCtrl [MFC], HitTest
- CHeaderCtrl [MFC], InsertItem
- CHeaderCtrl [MFC], Layout
- CHeaderCtrl [MFC], OrderToIndex
- CHeaderCtrl [MFC], SetBitmapMargin
- CHeaderCtrl [MFC], SetFilterChangeTimeout
- CHeaderCtrl [MFC], SetFocusedItem
- CHeaderCtrl [MFC], SetHotDivider
- CHeaderCtrl [MFC], SetImageList
- CHeaderCtrl [MFC], SetItem
- CHeaderCtrl [MFC], SetOrderArray
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 582ffffc4461edd41078f1a89844bdc260b2dd40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl – třída
Poskytuje funkci ovládacím prvku Windows běžné záhlaví.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CHeaderCtrl : public CWnd  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|Vytvoří `CHeaderCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Vymaže všechny filtry ovládacím prvkem záhlaví.|  
|[CHeaderCtrl::ClearFilter](#clearfilter)|Vymaže filtr pro ovládacím prvkem záhlaví.|  
|[CHeaderCtrl::Create](#create)|Vytvoří ovládacím prvkem záhlaví a připojí jej k `CHeaderCtrl` objektu.|  
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Vytvoří transparentní verze obrázku položky v ovládacím prvku hlavička.|  
|[CHeaderCtrl::CreateEx](#createex)|Vytvoří ovládacím prvkem záhlaví se zadanou Windows rozšířené styly a připojí jej k `CListCtrl` objektu.|  
|[CHeaderCtrl::DeleteItem](#deleteitem)|Vymaže položku z ovládacího prvku záhlaví.|  
|[CHeaderCtrl::DrawItem](#drawitem)|Vykreslí zadané položky ovládacího prvku záhlaví.|  
|[CHeaderCtrl::EditFilter](#editfilter)|Spustí se úpravy zadaný filtr ovládacího prvku záhlaví.|  
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Načte Šířka okraje bitmapu v ovládacím prvku hlavička.|  
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Získá identifikátor položky v ovládacím prvku aktuální záhlaví, který je aktivní.|  
|[CHeaderCtrl::GetImageList](#getimagelist)|Načte popisovač používá pro vykreslování položek záhlaví v ovládacím prvku hlavička seznamu obrázků.|  
|[CHeaderCtrl::GetItem](#getitem)|Načte informace o položce v ovládacím prvku hlavička.|  
|[CHeaderCtrl::GetItemCount](#getitemcount)|Načte počet položek v ovládacím prvku hlavička.|  
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Získá ohraničující obdélník informace pro zadané rozevírací tlačítko v ovládacím prvku hlavička.|  
|[CHeaderCtrl::GetItemRect](#getitemrect)|Načte ohraničující obdélník pro danou položku v ovládacím prvku hlavička.|  
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Načte zleva doprava pořadí položek v ovládacím prvku hlavička.|  
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Získá ohraničující obdélník tlačítko přetečení pro aktuální ovládací prvek záhlaví.|  
|[CHeaderCtrl::HitTest](#hittest)|Určuje, které položky záhlaví, pokud existuje, se nachází v určitém bodě.|  
|[CHeaderCtrl::InsertItem](#insertitem)|Vloží novou položku do ovládacího prvku záhlaví.|  
|[CHeaderCtrl::Layout](#layout)|Načte velikost a umístění ovládacího prvku záhlaví v rámci dané obdélníku.|  
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Načte hodnotu indexu pro položky na základě jeho pořadí v ovládacím prvku záhlaví.|  
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Nastaví šířku okraje bitmapu v ovládacím prvku hlavička.|  
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Nastaví interval časového limitu mezi časem změnu probíhá v atributy filtru a účtování `HDN_FILTERCHANGE` oznámení.|  
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Zadaná hlavička položky v ovládacím prvku aktuální záhlaví nastaví fokus.|  
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Přetáhněte oddělovač mezi položky hlavičky k označení ruční změny a drop položky záhlaví.|  
|[CHeaderCtrl::SetImageList](#setimagelist)|Seznam obrázků přiřadí ovládacím prvkem záhlaví.|  
|[CHeaderCtrl::SetItem](#setitem)|Nastaví atributy zadané položky v ovládacím prvku hlavička.|  
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Nastaví zleva doprava pořadí položek v ovládacím prvku hlavička.|  
  
## <a name="remarks"></a>Poznámky  
 Ovládacím prvkem záhlaví je okno, které je umístěn obvykle výše sadu sloupců text nebo čísla. Obsahuje název pro každý sloupec a je možné rozdělit na části. Uživatele můžete přetáhnout oddělovačů, které oddělují části nastavit šířka každého sloupce. Obrázek ovládacího prvku záhlaví, najdete v části [ovládací prvky hlavičky](http://msdn.microsoft.com/library/windows/desktop/bb775238).  
  
 Tento ovládací prvek (a proto `CHeaderCtrl` třída) je dostupná jenom pro programy, které běží pod verze systému Windows 95/98 a systému Windows NT 3.51 a novějším.  
  
 Funkce, které jsou přidány pro běžné ovládací prvky systému Windows 95 nebo Internet Explorer 4.0 zahrnuje následující položky:  
  
-   Záhlaví položky vlastní řazení.  
  
-   Položky hlavičky přetažení, pro změny pořadí položek záhlaví. Použití `HDS_DRAGDROP` stylu při vytváření `CHeaderCtrl` objektu.  
  
-   Text záhlaví sloupce neustále zobrazitelné při změně velikosti sloupce. Použití `HDS_FULLDRAG` stylu při vytváření `CHeaderCtrl` objektu.  
  
-   Hlavička aktivní sledování, který označuje položky záhlaví, když má ukazatel mohou přesouváním ukazatele myši nad ním. Použití `HDS_HOTTRACK` stylu při vytváření `CHeaderCtrl` objektu.  
  
-   Podpora seznamu obrázků. Položky hlavičky může obsahovat bitové kopie, které jsou uložené v `CImageList` objekt nebo text.  
  
 Další informace o používání `CHeaderCtrl`, najdete v části [ovládací prvky](../../mfc/controls-mfc.md) a [pomocí CHeaderCtrl](../../mfc/using-cheaderctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHeaderCtrl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxcmn.h  
  
##  <a name="cheaderctrl"></a>  CHeaderCtrl::CHeaderCtrl  
 Vytvoří `CHeaderCtrl` objektu.  
  
```  
CHeaderCtrl();
```  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]  
  
##  <a name="clearallfilters"></a>  CHeaderCtrl::ClearAllFilters  
 Vymaže všechny filtry ovládacím prvkem záhlaví.  
  
```  
BOOL ClearAllFilters();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda implementuje chování zprávy Win32 [HDM_CLEARFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775306) s sloupec hodnota -1, jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]  
  
##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter  
 Vymaže filtr pro ovládacím prvkem záhlaví.  
  
```  
BOOL ClearFilter(int nColumn);
```  
  
### <a name="parameters"></a>Parametry  
 `nColumn`  
 Sloupec hodnotu určující, který filtr vymazat.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda implementuje chování zprávy Win32 [HDM_CLEARFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775306), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]  
  
##  <a name="create"></a>  CHeaderCtrl::Create  
 Vytvoří ovládacím prvkem záhlaví a připojí jej k `CHeaderCtrl` objektu.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `dwStyle`  
 Určuje styl ovládacím prvku záhlaví. Popis styly ovládacího prvku záhlaví najdete v tématu [styly ovládacího prvku záhlaví](http://msdn.microsoft.com/library/windows/desktop/bb775241) ve Windows SDK.  
  
 `rect`  
 Určuje velikost a umístění prvku záhlaví. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura.  
  
 `pParentWnd`  
 Určuje nadřazeného prvku záhlaví okna, obvykle `CDialog`. Nesmí být **NULL**.  
  
 `nID`  
 Určuje ID ovládacího prvku záhlaví.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud se inicializace byla úspěšná. jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Můžete vytvořit `CHeaderCtrl` objektu ve dvou krocích. Nejprve volat konstruktor a pak zavolají **vytvořit**, který vytvoří ovládacím prvku záhlaví a připojí jej k `CHeaderCtrl` objektu.  
  
 Kromě styly ovládacího prvku záhlaví, můžete použít následující běžné styly ovládacího prvku určit, jak ovládací prvky záhlaví umisťuje a změní velikost sebe sama (viz [běžné styly ovládacího prvku](http://msdn.microsoft.com/library/windows/desktop/bb775498) Další informace):  
  
- `CCS_BOTTOM` Způsobí, že ovládací prvek na pozici sám v dolní části okna nadřazené klientské oblasti a nastaví šířku, která má být stejná jako nadřazená položka šířku uživatele systému Windows.  
  
- `CCS_NODIVIDER` Zabrání přitahuje v horní části ovládacího prvku zvýraznění dva pixelů.  
  
- `CCS_NOMOVEY` Způsobí, že změna velikosti a přesunout sám sebe vodorovně, ale není svisle v reakci na ovládacího prvku `WM_SIZE` zprávy. Pokud `CCS_NORESIZE` styl se používá, tento styl nevztahuje. Ovládací prvky hlavičky mají tento styl ve výchozím nastavení.  
  
- `CCS_NOPARENTALIGN` Zabrání automaticky Přesun do horní nebo dolní části okna nadřazeného ovládacího prvku. Místo toho ovládacího prvku udržuje pozici v rámci nadřazeného okna navzdory změny velikosti nadřazeného okna. Pokud `CCS_TOP` nebo `CCS_BOTTOM` styl se také používá, výška se upraví na výchozí hodnoty, ale zůstávají pozice a šířka beze změn.  
  
- `CCS_NORESIZE` Ovládací prvek bránit v použití výchozí šířku a výšku při nastavování jeho počáteční velikost nebo novou velikost. Místo toho ovládací prvek používá šířku a výšku určený v požadavku pro vytvoření nebo velikosti.  
  
- `CCS_TOP` Způsobí, že ovládací prvek na pozici sám v horní části okna nadřazené klientské oblasti a nastaví šířku, která má být stejná jako nadřazená položka šířku uživatele systému Windows.  
  
 Můžete taky použít následující styly oken do ovládacího prvku záhlaví (viz [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) Další informace):  
  
- **Ws_child –** vytvoří podřízeného okna. Nelze použít s `WS_POPUP` stylu.  
  
- **Ws_visible –** vytvoří okno, které je původně viditelná.  
  
- **Ws_disabled –** vytvoří okno, které je původně zakázána.  
  
- **Ws_group –** Určuje první prvek skupiny ovládacích prvků, ve kterých může uživatel přesunout z jednoho ovládacího prvku na další pomocí klávesy se šipkami. Všechny ovládací prvky, které jsou definované pomocí **ws_group –** styl po první prvek patří do stejné skupiny. Na další ovládací prvek s **ws_group –** styl končí skupinu stylů a spustí na další skupinu (to znamená, jedna skupina elementy end kde začíná další).  
  
- **Ws_tabstop –** určuje jedné z několika ovládacích prvků, pomocí kterých může uživatel přesunout pomocí klávesy TAB. Klávesy TAB přesune na další ovládací prvek určeného uživatele **ws_tabstop –** stylu.  
  
 Pokud chcete použít rozšířené windows styly s ovládacím prvkem, zavolejte [CreateEx](#createex) místo **vytvořit**.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]  
  
##  <a name="createex"></a>  CHeaderCtrl::CreateEx  
 Vytvoří ovládacího prvku (podřízeného okna) a přidružit ho pomocí `CHeaderCtrl` objektu.  
  
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
 Styl ovládacím prvku záhlaví. Popis styly ovládacího prvku záhlaví najdete v tématu [styly ovládacího prvku záhlaví](http://msdn.microsoft.com/library/windows/desktop/bb775241) ve Windows SDK. V tématu [vytvořit](#create) seznam dalších stylů.  
  
 `rect`  
 Odkaz na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura popisující velikost a umístění okna byly vytvořeny v souřadnice klienta `pParentWnd`.  
  
 `pParentWnd`  
 Ukazatel na okně, které je nadřazeného ovládacího prvku.  
  
 `nID`  
 ID ovládacího prvku podřízeného okna.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Použití `CreateEx` místo **vytvořit** použít rozšířené styly Windows určeného předponu rozšířené styl Windows **WS_EX_**.  
  
##  <a name="createdragimage"></a>  CHeaderCtrl::CreateDragImage  
 Vytvoří transparentní verze obrázku položky v ovládacím prvku hlavička.  
  
```  
CImageList* CreateDragImage(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index založený na nule položky v ovládacím prvku záhlaví. Bitová kopie přiřazená tato položka je základem pro bitovou kopii transparentní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CImageList](../../mfc/reference/cimagelist-class.md) objekt, je-li úspěšná, jinak hodnota **NULL**. Vrácený seznam obsahuje pouze jeden obrázek.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [HDM_CREATEDRAGIMAGE](http://msdn.microsoft.com/library/windows/desktop/bb775308), jak je popsáno v sadě Windows SDK. Je poskytována pro podporu záhlaví položky přetažení.  
  
 `CImageList` Objekt, ke které body Vrácený ukazatel je dočasný objekt a bude odstraněn ze další zpracování doby nečinnosti.  
  
##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem  
 Vymaže položku z ovládacího prvku záhlaví.  
  
```  
BOOL DeleteItem(int nPos);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Určuje index založený na nule položky odstranit.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]  
  
##  <a name="drawitem"></a>  CHeaderCtrl::DrawItem  
 Voláno rámcem při visual aspekt vykreslování vlastníka záhlaví řízení změn.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parametry  
 `lpDrawItemStruct`  
 Ukazatel [drawitemstruct –](http://msdn.microsoft.com/library/windows/desktop/bb775802) struktura popisující položka, která má být vykresluje.  
  
### <a name="remarks"></a>Poznámky  
 **ItemAction** členem `DRAWITEMSTRUCT` struktura definuje kreslení akci, která má být provedena.  
  
 Ve výchozím nastavení tato funkce člen neprovede žádnou akci. Člen funkci implementovat kreslení pro kreslení vlastníka přepsat `CHeaderCtrl` objektu.  
  
 Aplikace by měla obnovit všechny grafiky zařízení rozhraní GDI objekty vybrané pro zadaný kontext zobrazení v `lpDrawItemStruct` před tento člen funkce ukončí.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]  
  
##  <a name="editfilter"></a>  CHeaderCtrl::EditFilter  
 Zahájí upravit zadaný filtr ovládacího prvku záhlaví.  
  
```  
BOOL EditFilter(
    int nColumn,  
    BOOL bDiscardChanges);
```  
  
### <a name="parameters"></a>Parametry  
 `nColumn`  
 Sloupec, který chcete upravit.  
  
 `bDiscardChanges`  
 Hodnotu, která určuje způsob zpracování uživatele je úpravy změny, pokud uživatel právě úpravy filtru při [HDM_EDITFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775312) je zpráva odeslána.  
  
 Zadejte `true` se zahodit změny provedené uživatelem, nebo `false` tak, aby přijímal změny provedené uživatelem.  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda implementuje chování zprávy Win32 [HDM_EDITFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775312), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]  
  
##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin  
 Načte Šířka okraje bitmapu v ovládacím prvku hlavička.  
  
```  
int GetBitmapMargin() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka okraje rastrového obrázku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [HDM_GETBITMAPMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb775314), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]  
  
##  <a name="getfocuseditem"></a>  CHeaderCtrl::GetFocusedItem  
 Získá index položky, který je aktivní v ovládacím prvku aktuální záhlaví.  
  
```  
int GetFocusedItem() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule položky záhlaví, který je aktivní.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [HDM_GETFOCUSEDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775330) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_headerCtrl`, který používá pro přístup k prvku aktuální záhlaví. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `SetFocusedItem` a `GetFocusedItem` metody. V dřívější části kódu jsme vytvořili ovládacím prvkem záhlaví s pěti sloupců. Oddělovač sloupec však můžete přetáhnout tak, aby sloupec není viditelná. V následujícím příkladu nastaví a potom potvrdí poslední záhlaví sloupce jako položka fokus.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList  
 Načte popisovač používá pro vykreslování položek záhlaví v ovládacím prvku hlavička seznamu obrázků.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CImageList](../../mfc/reference/cimagelist-class.md) objektu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [HDM_GETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775332), jak je popsáno v sadě Windows SDK. `CImageList` Objekt, ke které body Vrácený ukazatel je dočasný objekt a bude odstraněn ze další zpracování doby nečinnosti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]  
  
##  <a name="getitem"></a>  CHeaderCtrl::GetItem  
 Načte informace o položkách ovládacího prvku záhlaví.  
  
```  
BOOL GetItem(
    int nPos,  
    HDITEM* pHeaderItem) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Určuje index položky k načtení založený na nule.  
  
 `pHeaderItem`  
 Ukazatel na [HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) struktura, která přijímá nová položka. Tato struktura se používá s `InsertItem` a `SetItem` členské funkce. Žádné příznaky se nastavují **maska** element Ujistěte se, že hodnoty v odpovídajících prvcích jsou správně vyplnit po návratu. Pokud **maska** element je nastaven na hodnotu nula, nemají smysl, hodnoty v jiných elementy struktury.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]  
  
##  <a name="getitemcount"></a>  CHeaderCtrl::GetItemCount  
 Načte počet položek v ovládacím prvku hlavička.  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet řídicí položky hlavičky v případě úspěšného; jinak - 1.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CHeaderCtrl::DeleteItem](#deleteitem).  
  
##  <a name="getitemdropdownrect"></a>  CHeaderCtrl::GetItemDropDownRect  
 Získá ohraničující obdélník rozevírací tlačítko pro položky záhlaví v ovládacím prvku aktuální záhlaví.  
  
```  
BOOL GetItemDropDownRect(
    int iItem,   
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `iItem`|Index položky záhlaví, jehož styl je počítáno od nuly `HDF_SPLITBUTTON`. Další informace najdete v tématu `fmt` členem [HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) struktury.|  
|[out] `lpRect`|Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura získat ohraničující obdélník informace.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` je-li tuto funkci úspěšně; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [HDM_GETITEMDROPDOWNRECT](http://msdn.microsoft.com/library/windows/desktop/bb775339) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_headerCtrl`, který používá pro přístup k prvku aktuální záhlaví. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `GetItemDropDownRect` metoda. V dřívější části kódu jsme vytvořili ovládacím prvkem záhlaví s pěti sloupců. Následující příklad kódu kreslení 3D obdélníku kolem umístění na první sloupec, který je vyhrazený pro rozevírací tlačítko záhlaví.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]  
  
##  <a name="getitemrect"></a>  CHeaderCtrl::GetItemRect  
 Načte ohraničující obdélník pro danou položku v ovládacím prvku hlavička.  
  
```  
BOOL GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIndex`  
 Index založený na nule položky ovládacího prvku záhlaví.  
  
 `lpRect`  
 Ukazatel na adresu [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která přijímá ohraničující obdélník informace.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda implementuje chování zprávy Win32 [HDM_GETITEMRECT](http://msdn.microsoft.com/library/windows/desktop/bb775341), jak je popsáno v sadě Windows SDK.  
  
##  <a name="getorderarray"></a>  CHeaderCtrl::GetOrderArray  
 Načte zleva doprava pořadí položek v ovládacím prvku hlavička.  
  
```  
BOOL GetOrderArray(
    LPINT piArray,  
    int iCount);
```  
  
### <a name="parameters"></a>Parametry  
 `piArray`  
 Ukazatel na adresu vyrovnávací paměť, která přijímá index hodnoty položek v ovládacím prvku záhlaví, v pořadí, ve kterém se zobrazí zleva doprava.  
  
 `iCount`  
 Počet položek ovládacího prvku záhlaví. Musí být nezáporná.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [HDM_GETORDERARRAY](http://msdn.microsoft.com/library/windows/desktop/bb775343), jak je popsáno v sadě Windows SDK. Je poskytována pro podporu řazení položky záhlaví.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]  
  
##  <a name="getoverflowrect"></a>  CHeaderCtrl::GetOverflowRect  
 Získá ohraničující obdélník tlačítko přetečení aktuální ovládacího prvku záhlaví.  
  
```  
BOOL GetOverflowRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[out] `lpRect`|Ukazatel na [Rect –](http://msdn.microsoft.com/library/windows/desktop/dd162897) struktura, která přijímá ohraničující obdélník informace.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` je-li tuto funkci úspěšně; v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud ovládacím prvku záhlaví obsahuje více položek, než lze zobrazit najednou, můžete ovládací prvek zobrazeno tlačítko přetečení, posouvá k položkám, které nejsou viditelné. Ovládací prvek záhlaví musí mít `HDS_OVERFLOW` a `HDF_SPLITBUTTON` stylů se zobrazí tlačítko přetečení. Ohraničující obdélník uzavře tlačítko přetečení a existuje jenom v případě, že se zobrazí tlačítko přetečení. Další informace najdete v tématu [styly ovládacího prvku záhlaví](http://msdn.microsoft.com/library/windows/desktop/bb775241).  
  
 Tato metoda odesílá [HDM_GETOVERFLOWRECT](http://msdn.microsoft.com/library/windows/desktop/bb775345) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_headerCtrl`, který používá pro přístup k prvku aktuální záhlaví. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `GetOverflowRect` metoda. V dřívější části kódu jsme vytvořili ovládacím prvkem záhlaví s pěti sloupců. Oddělovač sloupec však můžete přetáhnout tak, aby sloupec není viditelná. Pokud některé sloupce nejsou viditelné, ovládacím prvku záhlaví nevykresluje tlačítko přetečení. Následující příklad kódu kreslení 3D obdélníku kolem umístění tlačítka přetečení.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]  
  
##  <a name="hittest"></a>  CHeaderCtrl::HitTest  
 Určuje, které položky záhlaví, pokud existuje, se nachází v určitém bodě.  
  
```  
int HitTest(LPHDHITTESTINFO* phdhti);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[ve out] `phdhti`|Ukazatel na [HDHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb775245) struktura, která určuje bod k testování a přijímá výsledky testu.|  
  
### <a name="return-value"></a>Návratová hodnota  
 Index založený na nule položky záhlaví, pokud existuje, na zadané pozici; jinak hodnota -1.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [HDM_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb775349) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_headerCtrl`, který používá pro přístup k prvku aktuální záhlaví. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `HitTest` metoda. V dřívější části Tento příklad kódu jsme vytvořili ovládacím prvkem záhlaví s pěti sloupců. Oddělovač sloupec však můžete přetáhnout tak, aby sloupec není viditelná. Tento příklad sestavy index sloupce, pokud je zobrazen a -1, pokud sloupec není viditelná.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]  
  
##  <a name="insertitem"></a>  CHeaderCtrl::InsertItem  
 Vloží novou položku do ovládacího prvku záhlaví v zadaném indexu.  
  
```  
int InsertItem(
    int nPos,  
    HDITEM* phdi);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Index založený na nule položky, které má být vložen. Pokud je hodnota nula, položka vložena na začátku prvku záhlaví. Pokud je hodnota větší než maximální hodnota, položku vložit na konci tohoto ovládacího prvku záhlaví.  
  
 *phdi*  
 Ukazatel na [HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) struktura, která obsahuje informace o položce má být vložen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index nové položky v případě úspěšného; jinak - 1.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]  
  
##  <a name="layout"></a>  CHeaderCtrl::Layout  
 Načte velikost a umístění ovládacího prvku záhlaví v rámci dané obdélníku.  
  
```  
BOOL Layout(HDLAYOUT* pHeaderLayout);
```  
  
### <a name="parameters"></a>Parametry  
 *pHeaderLayout*  
 Ukazatel na [HDLAYOUT](http://msdn.microsoft.com/library/windows/desktop/bb775249) struktura, která obsahuje informace, které slouží k nastavení velikost a umístění ovládacího prvku záhlaví.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží k určení příslušné dimenze nové ovládacího prvku záhlaví, který je tak, aby zabíral dané rámeček.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]  
  
##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex  
 Načte hodnotu indexu pro položky na základě jeho pořadí v ovládacím prvku záhlaví.  
  
```  
int OrderToIndex(int nOrder) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *nOrder*  
 Počítaný od nuly pořadí, ve kterém se položka zobrazí v ovládacím prvku záhlaví zleva doprava.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index položky na základě jeho pořadí v ovládacím prvku záhlaví. Index počty zleva doprava, počínaje 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování makro Win32 [HDM_ORDERTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb775355), jak je popsáno v sadě Windows SDK. Je poskytována pro podporu řazení položky záhlaví.  
  
##  <a name="setbitmapmargin"></a>  CHeaderCtrl::SetBitmapMargin  
 Nastaví šířku okraje bitmapu v ovládacím prvku hlavička.  
  
```  
int SetBitmapMargin(int nWidth);
```  
  
### <a name="parameters"></a>Parametry  
 `nWidth`  
 Šířka, zadaný v pixelech doba, která obklopuje rastrového obrázku v rámci existujícího ovládacího prvku záhlaví.  
  
### <a name="return-value"></a>Návratová hodnota  
 Šířka okraje rastrového obrázku v pixelech.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [HDM_SETBITMAPMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb775357), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]  
  
##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout  
 Nastaví interval časového limitu mezi časem změnu probíhá v atributy filtru a účtování [HDN_FILTERCHANGE](http://msdn.microsoft.com/library/windows/desktop/bb775277) oznámení.  
  
```  
int SetFilterChangeTimeout(DWORD dwTimeOut);
```  
  
### <a name="parameters"></a>Parametry  
 *dwTimeOut*  
 Hodnota časového limitu v milisekundách.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index prvku filtru upravována.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [HDM_SETFILTERCHANGETIMEOUT](http://msdn.microsoft.com/library/windows/desktop/bb775359), jak je popsáno v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]  
  
##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem  
 Zadaná hlavička položky v ovládacím prvku aktuální záhlaví nastaví fokus.  
  
```  
BOOL SetFocusedItem(int iItem);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|[v] `iItem`|Index položky záhlaví počítáno od nuly.|  
  
### <a name="return-value"></a>Návratová hodnota  
 `true` Pokud tato metoda je úspěšná. v opačném `false`.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda odesílá [HDM_SETFOCUSEDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775361) zprávy, která je popsána v sadě Windows SDK.  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu definuje proměnnou, `m_headerCtrl`, který používá pro přístup k prvku aktuální záhlaví. Tato proměnná se používá v dalším příkladu.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `SetFocusedItem` a `GetFocusedItem` metody. V dřívější části kódu jsme vytvořili ovládacím prvkem záhlaví s pěti sloupců. Oddělovač sloupec však můžete přetáhnout tak, aby sloupec není viditelná. V následujícím příkladu nastaví a potom potvrdí poslední záhlaví sloupce jako položka fokus.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="sethotdivider"></a>  CHeaderCtrl::SetHotDivider  
 Přetáhněte oddělovač mezi položky hlavičky k označení ruční změny a drop položky záhlaví.  
  
```  
int SetHotDivider(CPoint pt);  
int SetHotDivider(int nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 `pt`  
 Umístění ukazatele. Ovládacím prvku záhlaví označuje odpovídající dělicí na základě pozice ukazatele.  
  
 `nIndex`  
 Index zvýrazněná oddělovače.  
  
### <a name="return-value"></a>Návratová hodnota  
 Index zvýrazněná oddělovače.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [HDM_SETHOTDIVIDER](http://msdn.microsoft.com/library/windows/desktop/bb775363), jak je popsáno v sadě Windows SDK. Je poskytována pro podporu záhlaví položky přetažení.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]  
  
##  <a name="setimagelist"></a>  CHeaderCtrl::SetImageList  
 Seznam obrázků přiřadí ovládacím prvkem záhlaví.  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parametry  
 `pImageList`  
 Ukazatel na `CImageList` objekt obsahující seznam obrázků pro přiřazení do ovládacího prvku záhlaví.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CImageList](../../mfc/reference/cimagelist-class.md) dříve přiřazen do ovládacího prvku záhlaví objekt.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování zprávy Win32 [HDM_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775365), jak je popsáno v sadě Windows SDK. `CImageList` Objekt, ke které body Vrácený ukazatel je dočasný objekt a bude odstraněn ze další zpracování doby nečinnosti.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CHeaderCtrl::GetImageList](#getimagelist).  
  
##  <a name="setitem"></a>  CHeaderCtrl::SetItem  
 Nastaví atributy zadané položky v ovládacím prvku hlavička.  
  
```  
BOOL SetItem(
    int nPos,  
    HDITEM* pHeaderItem);
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Index založený na nule položky na Upravit.  
  
 `pHeaderItem`  
 Ukazatel na [HDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) struktura, která obsahuje informace o novou položku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CHeaderCtrl::GetItem](#getitem).  
  
##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray  
 Nastaví zleva doprava pořadí položek v ovládacím prvku hlavička.  
  
```  
BOOL SetOrderArray(
    int iCount,  
    LPINT piArray);
```  
  
### <a name="parameters"></a>Parametry  
 `iCount`  
 Počet položek ovládacího prvku záhlaví.  
  
 `piArray`  
 Ukazatel na adresu vyrovnávací paměť, která přijímá index hodnoty položek v ovládacím prvku záhlaví, v pořadí, ve kterém se zobrazí zleva doprava.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce člen implementuje chování makro Win32 [HDM_SETORDERARRAY](http://msdn.microsoft.com/library/windows/desktop/bb775369), jak je popsáno v sadě Windows SDK. Je poskytována pro podporu řazení položky záhlaví.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CHeaderCtrl::GetOrderArray](#getorderarray).  
  
## <a name="see-also"></a>Viz také  
 [Třída CWnd](../../mfc/reference/cwnd-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CTabCtrl – třída](../../mfc/reference/ctabctrl-class.md)   
 [CListCtrl – třída](../../mfc/reference/clistctrl-class.md)   
 [CImageList – třída](../../mfc/reference/cimagelist-class.md)
