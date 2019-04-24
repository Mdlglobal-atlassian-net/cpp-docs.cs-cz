---
title: Cheaderctrl – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 51cdfb481892ba5057d4ca26ff4d6e51665557e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160195"
---
# <a name="cheaderctrl-class"></a>Cheaderctrl – třída

Poskytuje funkce pro Windows běžný ovládací prvek záhlaví.

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
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Vymaže všechny filtry pro ovládací prvek záhlaví.|
|[CHeaderCtrl::ClearFilter](#clearfilter)|Vymaže filtr pro ovládací prvek záhlaví.|
|[CHeaderCtrl::Create](#create)|Vytvoří ovládací prvek záhlaví a připojí ho k `CHeaderCtrl` objektu.|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Vytvoří verzi průhledný obrázek položky v ovládacím prvku hlavička.|
|[CHeaderCtrl::CreateEx](#createex)|Vytvoří ovládací prvek záhlaví se zadanou rozšířené styly Windows a připojí ho k `CListCtrl` objektu.|
|[CHeaderCtrl::DeleteItem](#deleteitem)|Odstraní položku z ovládacího prvku záhlaví.|
|[CHeaderCtrl::DrawItem](#drawitem)|Vykreslí zadané položky záhlaví ovládacího prvku.|
|[CHeaderCtrl::EditFilter](#editfilter)|Začne provádět úpravy zadaný filtr ovládacím prvkem záhlaví.|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Načte šířku na okraji rastrový obrázek v ovládacím prvku hlavička.|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Načte identifikátor položky v aktuálním ovládacího prvku záhlaví, která má fokus.|
|[CHeaderCtrl::GetImageList](#getimagelist)|Načte popisovač použitý pro vykreslení položky hlaviček v ovládacím prvku hlavička seznamu obrázků.|
|[CHeaderCtrl::GetItem](#getitem)|Načte informace o položce v záhlaví ovládacího prvku.|
|[CHeaderCtrl::GetItemCount](#getitemcount)|Získá počet položek v ovládacím prvku hlavička.|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Získá informace o ohraničující obdélník pro zadaný rozevírací tlačítko v ovládacím prvku hlavička.|
|[CHeaderCtrl::GetItemRect](#getitemrect)|Načte ohraničující obdélník pro danou položku v ovládacím prvku hlavička.|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Získá pořadí zleva doprava z položek v ovládacím prvku hlavička.|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Získá aktuální ovládacího prvku záhlaví ohraničující obdélník tlačítku přetečení.|
|[CHeaderCtrl::HitTest](#hittest)|Určuje, která položka záhlaví, pokud existuje, se nachází k určitému bodu.|
|[CHeaderCtrl::InsertItem](#insertitem)|Vloží novou položku do ovládacího prvku záhlaví.|
|[CHeaderCtrl::Layout](#layout)|Načte velikost a umístění v rámci dané obdélníku ovládacího prvku záhlaví.|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Načte hodnotu indexu pro položku na základě jeho pořadí v ovládacím prvku záhlaví.|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Nastavuje šířku na okraji rastrový obrázek v ovládacím prvku hlavička.|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Nastaví interval časového limitu mezi časem atributy filtru Probíhá změna a zveřejňování `HDN_FILTERCHANGE` oznámení.|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Nastaví fokus na zadaná hlavička položky v ovládacím prvku hlavička aktuální.|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Přetáhněte na oddělovač mezi položky hlavičky k označení ruční změny a rozevírací položky záhlaví.|
|[CHeaderCtrl::SetImageList](#setimagelist)|Seznam obrázků přiřadí ovládacím prvkem záhlaví.|
|[CHeaderCtrl::SetItem](#setitem)|Nastaví vlastnosti zadané položky v ovládacím prvku hlavička.|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Nastaví pořadí zleva doprava z položek v ovládacím prvku záhlaví.|

## <a name="remarks"></a>Poznámky

Ovládací prvek záhlaví je okno, které je obvykle umístěn nad sadu sloupců text nebo čísla. Obsahuje název pro každý sloupec a je možné rozdělit na části. Uživatel můžete přetáhnout oddělovače, které oddělují části nastavte šířku každého sloupce. Pro ilustraci záhlaví ovládacího prvku, naleznete v tématu [ovládacích prvků záhlaví](/windows/desktop/Controls/header-controls).

Tento ovládací prvek (a tedy `CHeaderCtrl` třídy) je dostupná jenom pro programy, které jsou spuštěny pod Windows 95/98 a Windows NT verze 3.51 a vyšší.

Funkce pro běžné ovládací prvky Windows 95/Internet Explorer 4.0 přidat zahrnuje následující položky:

- Záhlaví položky vlastní řazení.

- Položky záhlaví přetažení, změny pořadí položek záhlaví. Při vytváření použít hds_dragdrop – styl `CHeaderCtrl` objektu.

- Text záhlaví sloupce neustále zobrazitelné během Změna velikosti sloupců. Použít styl HDS_FULLDRAG při vytváření `CHeaderCtrl` objektu.

- Záhlaví horké sledování, které označí okamžiky položky záhlaví ukazatel na ukazatele myši nad ním. Použít styl HDS_HOTTRACK při vytváření `CHeaderCtrl` objektu.

- Podpora seznamu obrázků. Položky záhlaví mohou obsahovat imagí uložených v `CImageList` objekt nebo text.

Další informace o používání `CHeaderCtrl`, naleznete v tématu [ovládací prvky](../../mfc/controls-mfc.md) a [používání atributu CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

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

Vymaže všechny filtry pro ovládací prvek záhlaví.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování zprávy Win32 [HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter) sloupec hodnotou-1, jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter

Vymaže filtr pro ovládací prvek záhlaví.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Parametry

*nColumn*<br/>
Sloupec hodnotu určující, který filtr vymazat.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování zprávy Win32 [HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>  CHeaderCtrl::Create

Vytvoří ovládací prvek záhlaví a připojí ho k `CHeaderCtrl` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl ovládacího prvku záhlaví. Popis – styly ovládacích prvků záhlaví, naleznete v tématu [– styly ovládacích prvků záhlaví](/windows/desktop/Controls/header-control-styles) v sadě Windows SDK.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku záhlaví. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](/previous-versions/dd162897\(v=vs.85\)) struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku záhlaví, obvykle `CDialog`. Nesmí být NULL.

*nID*<br/>
Určuje ID ovládacího prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se inicializace byla úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CHeaderCtrl` objektu ve dvou krocích. Nejprve volat konstruktor a následně zavolat `Create`, což vytvoří ovládací prvek záhlaví a připojí ho k `CHeaderCtrl` objektu.

Kromě – styly ovládacích prvků záhlaví, můžete použít následující běžné – styly ovládacích prvků k určení, jak ovládací prvek záhlaví umístí a změní velikost sebe sama (viz [– styly běžných ovládacích prvků](/windows/desktop/Controls/common-control-styles) Další informace):

- CCS_BOTTOM způsobí, že ovládací prvek na pozici sám v dolní části klientské oblasti okna nadřazený a nastaví šířku, která má být stejná jako nadřazená šířku okna.

- Zabraňuje CCS_NODIVIDER dvě pixel zvýrazněte ze které je cílem vykreslování v horní části ovládacího prvku.

- CCS_NOMOVEY způsobí, že ovládacího prvku a samotného v reakci na zprávu WM_SIZE přesuňte vodorovně, ale ne svisle, nebo velikost. Pokud použijete CCS_NORESIZE styl tento styl nelze použít. Ovládací prvky záhlaví mají tento styl ve výchozím nastavení.

- CCS_NOPARENTALIGN brání automaticky přechod na horní nebo dolní nadřazené okno ovládacího prvku. Místo toho ovládací prvek udržuje jeho pozice v rámci nadřazené okno bez ohledu na změny velikosti nadřazeného okna. Pokud se používá také CCS_TOP nebo CCS_BOTTOM styl, dojde k přenastavení výšku na výchozí hodnotu, ale nemění pozici a šířku.

- CCS_NORESIZE bránit v použití výchozí šířky a výšky při nastavení počáteční velikosti nebo novou velikost ovládacího prvku. Místo toho ovládací prvek využívá šířku a výšku zadaná v žádosti o vytvoření nebo změna velikosti.

- CCS_TOP způsobí, že ovládací prvek na pozici sám v horní části klientské oblasti okna nadřazený a nastaví šířku, která má být stejná jako nadřazená šířku okna.

Můžete také použít následující styly oken na ovládací prvek hlavičky (viz [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) Další informace):

- WS_CHILD vytvoří podřízené okno. Nelze použít s WS_POPUP style.

- WS_VISIBLE vytvoří okno, které je zpočátku viditelné.

- WS_DISABLED vytvoří okno, které je zpočátku zakázáno.

- WS_GROUP Určuje první prvek skupiny ovládacích prvků, ve kterých uživatel může přesouvat z jednoho ovládacího prvku na další pomocí kláves se šipkami. Všechny ovládací prvky definované ve stylu WS_GROUP po prvním ovládacím prvku, patří do stejné skupiny. Další ovládací prvek se stylem WS_GROUP končí skupině styl a začíná další skupinu (tedy. zakončení jedné skupiny kde začíná další).

- WS_TABSTOP Určuje jeden z několika ovládacích prvků, pomocí kterých uživatel může přecházet pomocí klávesy TAB. Klávesy TAB přesune uživatele na další ovládací prvek určený stylem WS_TABSTOP.

Pokud chcete použít rozšířené windows styly ovládacího prvku, zavolejte [CreateEx](#createex) místo `Create`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>  CHeaderCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidružte jej k `CHeaderCtrl` objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyle*<br/>
Určuje rozšířený styl ovládacího prvku vytváří. Seznam rozšířené styly Windows najdete v tématu *dwExStyle* parametr pro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) v sadě Windows SDK.

*dwStyle*<br/>
Styl záhlaví ovládacího prvku. Popis – styly ovládacích prvků záhlaví, naleznete v tématu [– styly ovládacích prvků záhlaví](/windows/desktop/Controls/header-control-styles) v sadě Windows SDK. Zobrazit [vytvořit](#create) seznam Další styly.

*Rect*<br/>
Odkaz na [RECT](/previous-versions/dd162897\(v=vs.85\)) struktura popisující, velikost a umístění okna, které nelze v souřadnice klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, který je nadřazeného ovládacího prvku.

*nID*<br/>
ID ovládacího prvku podřízené okno.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Použití `CreateEx` místo `Create` použít rozšířené styly Windows určené předponu rozšířeného stylu Windows **WS_EX_**.

##  <a name="createdragimage"></a>  CHeaderCtrl::CreateDragImage

Vytvoří verzi průhledný obrázek položky v ovládacím prvku hlavička.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule položky v rámci ovládacího prvku záhlaví Bitové kopie přiřazené k této položce slouží jako základ pro průhledný obrázek.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [atributu CImageList](../../mfc/reference/cimagelist-class.md) objekt Pokud úspěšné; jinak hodnota NULL. Vrácený seznam obsahuje pouze jednu image.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_CREATEDRAGIMAGE](/windows/desktop/Controls/hdm-createdragimage), jak je popsáno v sadě Windows SDK. Poskytuje pro podporu přetáhnout položky záhlaví.

`CImageList` Objektu, ke kterému Vrácený ukazatel ukazuje je dočasný objekt a další zpracování doby nečinnosti se odstraní.

##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem

Odstraní položku z ovládacího prvku záhlaví.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje z nuly vycházející index položky k odstranění.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

##  <a name="drawitem"></a>  CHeaderCtrl::DrawItem

Volá se rozhraním při úpravě vizuálního aspektu změny vykreslené vlastníkem. záhlaví ovládacího prvku.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel [drawitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) struktura popisující položku, který se má namalovat.

### <a name="remarks"></a>Poznámky

`itemAction` Člena `DRAWITEMSTRUCT` struktury definuje výkresu akci, která se má provést.

Tato členská funkce ve výchozím nastavení nemá žádný účinek. Přepsat tato členská funkce implementovat kreslení pro vykreslené vlastníkem `CHeaderCtrl` objektu.

Aplikace by měl obnovit všechny grafiky zařízení rozhraní GDI systému objekty vybrané pro zadaný kontext zobrazení v *lpDrawItemStruct* před tento člen funkce skončí.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>  CHeaderCtrl::EditFilter

Začne upravovat zadaný filtr ovládacím prvkem záhlaví.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Parametry

*nColumn*<br/>
Sloupec, který chcete upravit.

*bDiscardChanges*<br/>
Hodnotu, která určuje způsob zpracování uživatele uživatele úpravy změny, pokud uživatel Probíhá úprava filtru při [HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter) je zpráva odeslána.

Zadejte hodnotu TRUE pro zrušení změn provedených uživatelem, nebo hodnotu NEPRAVDA tak, aby přijímal změny provedené uživatelem.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování zprávy Win32 [HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin

Načte šířku na okraji rastrový obrázek v ovládacím prvku hlavička.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka okraje rastrového obrázku v pixelech.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_GETBITMAPMARGIN](/windows/desktop/Controls/hdm-getbitmapmargin), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>  CHeaderCtrl::GetFocusedItem

Získá index položky, která má fokus v aktuální ovládacího prvku záhlaví.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Index založený na nule, který má fokus položky záhlaví.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [HDM_GETFOCUSEDITEM](/windows/desktop/Controls/hdm-getfocuseditem) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_headerCtrl`, která je pro přístup k aktuální ovládacího prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, `SetFocusedItem` a `GetFocusedItem` metody. V předchozí části kódu jsme vytvořili ovládacím prvkem záhlaví pět sloupců. Oddělovač sloupců však můžete přetáhnout tak, aby sloupec není viditelný. Následující příklad nastaví a pak potvrdí poslední záhlaví sloupce jako položka fokus.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList

Načte popisovač použitý pro vykreslení položky hlaviček v ovládacím prvku hlavička seznamu obrázků.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [atributu CImageList](../../mfc/reference/cimagelist-class.md) objektu.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_GETIMAGELIST](/windows/desktop/Controls/hdm-getimagelist), jak je popsáno v sadě Windows SDK. `CImageList` Objektu, ke kterému Vrácený ukazatel ukazuje je dočasný objekt a další zpracování doby nečinnosti se odstraní.

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

*nPos*<br/>
Určuje index založený na nule položka, která má načíst.

*pHeaderItem*<br/>
Ukazatel [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) struktura, která obdrží novou položku. Tato struktura se používá s `InsertItem` a `SetItem` členské funkce. Nastavit žádné příznaky `mask` element Ujistěte se, že hodnoty odpovídajících prvků jsou správně vyplněna po návratu. Pokud `mask` prvek je nastaven na hodnotu nula, hodnot v jiné struktuře elementy nemají smysl.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>  CHeaderCtrl::GetItemCount

Získá počet položek v ovládacím prvku hlavička.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek záhlaví ovládacího prvku v případě úspěchu; jinak - 1.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CHeaderCtrl::DeleteItem](#deleteitem).

##  <a name="getitemdropdownrect"></a>  CHeaderCtrl::GetItemDropDownRect

Získá ohraničující obdélník tlačítko rozevíracího seznamu pro položka záhlaví v ovládacím prvku hlavička aktuální.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Položky*|[in] Z nuly vycházející index položky záhlaví, jehož styl je HDF_SPLITBUTTON. Další informace najdete v tématu `fmt` člena [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) struktury.|
|*lpRect*|[out] Ukazatel [RECT](/previous-versions/dd162897\(v=vs.85\)) struktuře získávat informace ohraničující obdélník.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato funkce je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [HDM_GETITEMDROPDOWNRECT](/windows/desktop/Controls/hdm-getitemdropdownrect) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_headerCtrl`, která je pro přístup k aktuální ovládacího prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, `GetItemDropDownRect` metody. V předchozí části kódu jsme vytvořili ovládacím prvkem záhlaví pět sloupců. Následující příklad kódu kreslení 3D obdélník kolem umístění na první sloupec, který je vyhrazen pro rozevírací tlačítko záhlaví.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>  CHeaderCtrl::GetItemRect

Načte ohraničující obdélník pro danou položku v ovládacím prvku hlavička.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule položky ovládacího prvku záhlaví

*lpRect*<br/>
Ukazatel na adresu [RECT](/previous-versions/dd162897\(v=vs.85\)) struktura, která přijímá informace ohraničující obdélník.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování zprávy Win32 [HDM_GETITEMRECT](/windows/desktop/Controls/hdm-getitemrect), jak je popsáno v sadě Windows SDK.

##  <a name="getorderarray"></a>  CHeaderCtrl::GetOrderArray

Získá pořadí zleva doprava z položek v ovládacím prvku hlavička.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Parametry

*piArray*<br/>
Ukazatel na Adresa vyrovnávací paměti, která přijímá index hodnoty položek v ovládacím prvku záhlaví, v pořadí, v jakém jsou uvedeny zleva doprava.

*iCount*<br/>
Počet položek záhlaví ovládacího prvku. Musí být nezáporná.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_GETORDERARRAY](/windows/desktop/Controls/hdm-getorderarray), jak je popsáno v sadě Windows SDK. Poskytuje pro podporu řazení položky záhlaví.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>  CHeaderCtrl::GetOverflowRect

Získá ohraničující obdélník tlačítku přetečení aktuální záhlaví ovládacího prvku.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpRect*|[out] Ukazatel [RECT](/previous-versions/dd162897\(v=vs.85\)) struktura, která přijímá informace ohraničující obdélník.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato funkce je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud ovládací prvek záhlaví obsahuje více položek, než je možné současně zobrazit, ovládací prvek lze zobrazit tlačítku přetečení, umožňuje posouvání položek, které nejsou viditelné. Ovládací prvek záhlaví musí mít HDS_OVERFLOW a HDF_SPLITBUTTON stylů se zobrazí tlačítko přetečení. Ohraničující obdélník obklopuje tlačítku přetečení a existuje pouze v případě, že je zobrazeno tlačítko přetečení. Další informace najdete v tématu [– styly ovládacích prvků záhlaví](/windows/desktop/Controls/header-control-styles).

Tato metoda odesílá [HDM_GETOVERFLOWRECT](/windows/desktop/Controls/hdm-getoverflowrect) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_headerCtrl`, která je pro přístup k aktuální ovládacího prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, `GetOverflowRect` metody. V předchozí části kódu jsme vytvořili ovládacím prvkem záhlaví pět sloupců. Oddělovač sloupců však můžete přetáhnout tak, aby sloupec není viditelný. Pokud některé sloupce nejsou viditelná, kreslení ovládacího prvku záhlaví tlačítku přetečení. Následující příklad kódu kreslení 3D obdélník kolem umístění tlačítku přetečení.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>  CHeaderCtrl::HitTest

Určuje, která položka záhlaví, pokud existuje, se nachází k určitému bodu.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*phdhti*|[out v] Ukazatel [HDHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_hd_hittestinfo) struktura, která určuje bod k testování a přijímá výsledky testu.|

### <a name="return-value"></a>Návratová hodnota

Z nuly vycházející index položky záhlaví, pokud existuje, na zadané pozici; jinak -1.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [HDM_HITTEST](/windows/desktop/Controls/hdm-hittest) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_headerCtrl`, která je pro přístup k aktuální ovládacího prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, `HitTest` metody. V dřívější části tohoto příkladu jsme vytvořili ovládacím prvkem záhlaví pět sloupců. Oddělovač sloupců však můžete přetáhnout tak, aby sloupec není viditelný. Tento příklad sestavy index sloupce, pokud je viditelná a -1, pokud sloupec není viditelný.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>  CHeaderCtrl::InsertItem

Vloží nové položky do záhlaví ovládacího prvku na zadaném indexu.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Index založený na nule položka, která má být vložen. Pokud je hodnota nula, na začátek ovládacího prvku záhlaví vložení položky. Pokud je hodnota větší než maximální hodnota, na konci ovládacího prvku záhlaví vložení položky.

*phdi*<br/>
Ukazatel [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) strukturu, která obsahuje informace o položce, která se má vložit.

### <a name="return-value"></a>Návratová hodnota

Index nové položky v případě úspěchu; jinak - 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>  CHeaderCtrl::Layout

Načte velikost a umístění v rámci dané obdélníku ovládacího prvku záhlaví.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Parametry

*pHeaderLayout*<br/>
Ukazatel [HDLAYOUT](/windows/desktop/api/commctrl/ns-commctrl-_hd_layout) strukturou, který obsahuje informace, které slouží k nastavení velikosti a pozice ovládacího prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k určení příslušné dimenze pro nový ovládací prvek záhlaví, která je tak, aby obsadily dané obdélník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex

Načte hodnotu indexu pro položku na základě jeho pořadí v ovládacím prvku záhlaví.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Parametry

*nOrder*<br/>
Založený na nule pořadí, ve kterém se položka zobrazí v ovládacím prvku záhlaví zleva doprava.

### <a name="return-value"></a>Návratová hodnota

Index položky, na základě jeho pořadí v ovládacím prvku záhlaví. Index se počítá zleva doprava, počínaje 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování – makro Win32 [HDM_ORDERTOINDEX](https://msdn.microsoft.com/library/windows/desktop/bb775355), jak je popsáno v sadě Windows SDK. Poskytuje pro podporu řazení položky záhlaví.

##  <a name="setbitmapmargin"></a>  CHeaderCtrl::SetBitmapMargin

Nastavuje šířku na okraji rastrový obrázek v ovládacím prvku hlavička.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Šířka, zadaný v pixelech, které obklopuje rastrového obrázku v rámci existující ovládací prvek záhlaví rozpětí.

### <a name="return-value"></a>Návratová hodnota

Šířka okraje rastrového obrázku v pixelech.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_SETBITMAPMARGIN](/windows/desktop/Controls/hdm-setbitmapmargin), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout

Nastaví interval časového limitu mezi časem atributy filtru Probíhá změna a zveřejňování [HDN_FILTERCHANGE](/windows/desktop/Controls/hdn-filterchange) oznámení.

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Parametry

*dwTimeOut*<br/>
Hodnota časového limitu v milisekundách.

### <a name="return-value"></a>Návratová hodnota

Index ovládací prvek filtru právě upravuje.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_SETFILTERCHANGETIMEOUT](/windows/desktop/Controls/hdm-setfilterchangetimeout), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem

Nastaví fokus na zadaná hlavička položky v ovládacím prvku hlavička aktuální.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Položky*|[in] Z nuly vycházející index položky záhlaví.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda odesílá [HDM_SETFOCUSEDITEM](/windows/desktop/Controls/hdm-setfocuseditem) zprávu, která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_headerCtrl`, která je pro přístup k aktuální ovládacího prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje, `SetFocusedItem` a `GetFocusedItem` metody. V předchozí části kódu jsme vytvořili ovládacím prvkem záhlaví pět sloupců. Oddělovač sloupců však můžete přetáhnout tak, aby sloupec není viditelný. Následující příklad nastaví a pak potvrdí poslední záhlaví sloupce jako položka fokus.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>  CHeaderCtrl::SetHotDivider

Přetáhněte na oddělovač mezi položky hlavičky k označení ruční změny a rozevírací položky záhlaví.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Parametry

*pt*<br/>
Pozice ukazatele. Ovládací prvek hlavičky zvýrazní příslušné oddělovače na základě pozice ukazatele.

*nIndex*<br/>
Index na zvýrazněný oddělovač.

### <a name="return-value"></a>Návratová hodnota

Index na zvýrazněný oddělovač.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_SETHOTDIVIDER](/windows/desktop/Controls/hdm-sethotdivider), jak je popsáno v sadě Windows SDK. Poskytuje pro podporu přetáhnout položky záhlaví.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>  CHeaderCtrl::SetImageList

Seznam obrázků přiřadí ovládacím prvkem záhlaví.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Ukazatel `CImageList` objekt, který obsahuje seznam obrázků pro přiřazení do ovládacího prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [atributu CImageList](../../mfc/reference/cimagelist-class.md) objekt dříve přiřadili do ovládacího prvku záhlaví.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_SETIMAGELIST](/windows/desktop/Controls/hdm-setimagelist), jak je popsáno v sadě Windows SDK. `CImageList` Objektu, ke kterému Vrácený ukazatel ukazuje je dočasný objekt a další zpracování doby nečinnosti se odstraní.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CHeaderCtrl::GetImageList](#getimagelist).

##  <a name="setitem"></a>  CHeaderCtrl::SetItem

Nastaví vlastnosti zadané položky v ovládacím prvku hlavička.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Index založený na nule položka, která má být manipulovat.

*pHeaderItem*<br/>
Ukazatel [HDITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) strukturu, která obsahuje informace o novou položku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CHeaderCtrl::GetItem](#getitem).

##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray

Nastaví pořadí zleva doprava z položek v ovládacím prvku záhlaví.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Parametry

*iCount*<br/>
Počet položek záhlaví ovládacího prvku.

*piArray*<br/>
Ukazatel na Adresa vyrovnávací paměti, která přijímá index hodnoty položek v ovládacím prvku záhlaví, v pořadí, v jakém jsou uvedeny zleva doprava.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování – makro Win32 [HDM_SETORDERARRAY](/windows/desktop/Controls/hdm-setorderarray), jak je popsáno v sadě Windows SDK. Poskytuje pro podporu řazení položky záhlaví.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CHeaderCtrl::GetOrderArray](#getorderarray).

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl – třída](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl – třída](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList – třída](../../mfc/reference/cimagelist-class.md)
