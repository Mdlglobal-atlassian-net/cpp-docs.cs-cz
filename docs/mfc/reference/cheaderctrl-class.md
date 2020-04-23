---
title: Třída CHeaderCtrl
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
ms.openlocfilehash: de1705d47c5692d3563bc7d9cb2646531819197a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750917"
---
# <a name="cheaderctrl-class"></a>Třída CHeaderCtrl

Poskytuje funkce ovládacího prvku záhlaví systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|Vytvoří `CHeaderCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CHeaderCtrl::Vymazat všechny filtry](#clearallfilters)|Vymaže všechny filtry pro ovládací prvek záhlaví.|
|[CHeaderCtrl::Vymazat filtr](#clearfilter)|Vymaže filtr pro ovládací prvek záhlaví.|
|[CHeaderCtrl::Vytvořit](#create)|Vytvoří ovládací prvek záhlaví a `CHeaderCtrl` připojí jej k objektu.|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Vytvoří průhlednou verzi obrázku položky v ovládacím prvku záhlaví.|
|[CHeaderCtrl::CreateEx](#createex)|Vytvoří ovládací prvek záhlaví se zadanými rozšířenými `CListCtrl` styly systému Windows a připojí jej k objektu.|
|[CHeaderCtrl::DeleteItem](#deleteitem)|Odstraní položku z ovládacího prvku záhlaví.|
|[CHeaderCtrl::DrawItem](#drawitem)|Nakreslí zadanou položku ovládacího prvku záhlaví.|
|[CHeaderCtrl::Upravitfiltr](#editfilter)|Spustí úpravy zadaného filtru ovládacího prvku záhlaví.|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Načte šířku okraje rastrového bodu v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Získá identifikátor položky v aktuální ovládací prvek záhlaví, který má fokus.|
|[CHeaderCtrl::GetImageList](#getimagelist)|Načte popisovač seznamu obrázků použitých pro položky záhlaví výkresu v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetItem](#getitem)|Načte informace o položce v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetItemCount](#getitemcount)|Načte počet položek v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Získá informace ohraničující obdélník pro zadané rozevírací tlačítko v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetItemRect](#getitemrect)|Načte ohraničovací obdélník pro danou položku v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Načte pořadí položek zleva doprava v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Získá ohraničující obdélník tlačítka přetečení pro aktuální ovládací prvek záhlaví.|
|[CHeaderCtrl::HitTest](#hittest)|Určuje, která položka záhlaví, pokud existuje, je umístěna v zadaném bodě.|
|[CHeaderCtrl::InsertItem](#insertitem)|Vloží novou položku do ovládacího prvku záhlaví.|
|[CHeaderCtrl::rozložení](#layout)|Načte velikost a umístění ovládacího prvku záhlaví v rámci daného obdélníku.|
|[cheaderctrl::OrderToIndex](#ordertoindex)|Načte hodnotu indexu pro položku na základě jejího pořadí v ovládacím prvku záhlaví.|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Nastaví šířku okraje rastrového bodu v ovládacím prvku záhlaví.|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Nastaví časový interval mezi časem, kdy dojde ke změně v `HDN_FILTERCHANGE` atributech filtru, a zaúčtováním oznámení.|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Nastaví fokus na zadanou položku záhlaví v aktuálním ovládacím prvku záhlaví.|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Změní oddělovač mezi položkami záhlaví tak, aby označoval ruční přetažení položky záhlaví.|
|[CHeaderCtrl::SetImageList](#setimagelist)|Přiřadí seznam obrázků ovládacímu prvku záhlaví.|
|[CHeaderCtrl::SetItem](#setitem)|Nastaví atributy zadané položky v ovládacím prvku záhlaví.|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Nastaví pořadí položek v ovládacím prvku záhlaví zleva doprava.|

## <a name="remarks"></a>Poznámky

Ovládací prvek záhlaví je okno, které je obvykle umístěno nad sadou sloupců textu nebo čísel. Obsahuje název pro každý sloupec a může být rozdělen na části. Uživatel může přetáhnout oddělovače, které oddělují části nastavit šířku každého sloupce. Pro ilustraci ovládacího prvku záhlaví naleznete v tématu [Ovládací prvky záhlaví](/windows/win32/Controls/header-controls).

Tento ovládací prvek `CHeaderCtrl` (a tedy třída) je k dispozici pouze pro programy spuštěné v systémech Windows 95/98 a Windows NT verze 3.51 a novějších.

Funkce přidané pro systém Windows 95/Internet Explorer 4.0 běžné ovládací prvky zahrnují následující:

- Vlastní řazení položky záhlaví.

- Položku záhlaví přetažením pro změnu pořadí položek záhlaví. Při vytváření objektu `CHeaderCtrl` použijte styl HDS_DRAGDROP.

- Text sloupce záhlaví, který lze během změna velikosti sloupce neustále zobrazit. Při vytváření objektu `CHeaderCtrl` použijte styl HDS_FULLDRAG.

- Sledování aktivního sledování záhlaví, které zvýrazní položku záhlaví, když na ni ukazatel najedete myší. Při vytváření objektu `CHeaderCtrl` použijte styl HDS_HOTTRACK.

- Podpora seznamu obrázků. Položky záhlaví mohou obsahovat obrázky uložené v objektu `CImageList` nebo textu.

Další informace o `CHeaderCtrl`použití naleznete v [tématech Ovládací prvky](../../mfc/controls-mfc.md) a [Použití kláves CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

## <a name="cheaderctrlcheaderctrl"></a><a name="cheaderctrl"></a>CHeaderCtrl::CHeaderCtrl

Vytvoří `CHeaderCtrl` objekt.

```
CHeaderCtrl();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

## <a name="cheaderctrlclearallfilters"></a><a name="clearallfilters"></a>CHeaderCtrl::Vymazat všechny filtry

Vymaže všechny filtry pro ovládací prvek záhlaví.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování [win32](/windows/win32/Controls/hdm-clearfilter) HDM_CLEARFILTER se hodnotou sloupce -1, jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

## <a name="cheaderctrlclearfilter"></a><a name="clearfilter"></a>CHeaderCtrl::Vymazat filtr

Vymaže filtr pro ovládací prvek záhlaví.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Parametry

*nSloupec*<br/>
Hodnota sloupce označující, který filtr má být vymazán.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování [win32](/windows/win32/Controls/hdm-clearfilter)HDM_CLEARFILTER zprávy , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

## <a name="cheaderctrlcreate"></a><a name="create"></a>CHeaderCtrl::Vytvořit

Vytvoří ovládací prvek záhlaví a `CHeaderCtrl` připojí jej k objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl ovládacího prvku záhlaví. Popis stylů ovládacích prvků záhlaví naleznete v tématu [Styly řízení záhlaví](/windows/win32/Controls/header-control-styles) v sadě Windows SDK.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku záhlaví. Může to být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/windows/win32/api/windef/ns-windef-rect) struktury.

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího `CDialog`prvku záhlaví, obvykle . Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CHeaderCtrl` dvou krocích. Nejprve zavolejte konstruktoru `Create`a potom volání , který vytvoří `CHeaderCtrl` ovládací prvek záhlaví a připojí jej k objektu.

Kromě stylů ovládacích prvků záhlaví můžete pomocí následujících běžných stylů ovládacích prvků určit, jak se řídicí pozice záhlaví a změní jeho velikost (další informace naleznete v tématu [Běžné styly ovládacích prvků):](/windows/win32/Controls/common-control-styles)

- CCS_BOTTOM Způsobí, že ovládací prvek umístit sám v dolní části nadřazené okno klientské oblasti a nastaví šířku být stejné jako šířka nadřazeného okna.

- CCS_NODIVIDER Zabrání vykreslení dvoupixelového světla v horní části ovládacího prvku.

- CCS_NOMOVEY Způsobí, že ovládací prvek změnit velikost a přesunout sám vodorovně, ale ne svisle, v reakci na zprávu WM_SIZE. Pokud je použit styl CCS_NORESIZE, tento styl se nepoužije. Ovládací prvky záhlaví mají tento styl ve výchozím nastavení.

- CCS_NOPARENTALIGN Zabrání automatickému přesunutí ovládacího prvku do horního nebo dolního okraje nadřazeného okna. Místo toho ovládací prvek udržuje svou pozici v nadřazeném okně i přes změny velikosti nadřazeného okna. Pokud se použije také CCS_TOP nebo CCS_BOTTOM styl, výška se upraví na výchozí hodnotu, ale poloha a šířka zůstanou nezměněny.

- CCS_NORESIZE Zabrání ovládacímu prvku v použití výchozí šířky a výšky při nastavování počáteční velikosti nebo nové velikosti. Místo toho ovládací prvek používá šířku a výšku zadanou v požadavku na vytvoření nebo velikost.

- CCS_TOP Způsobí, že ovládací prvek umístit sám v horní části nadřazené okno klientské oblasti a nastaví šířku být stejné jako šířka nadřazeného okna.

Můžete také použít následující styly oken na ovládací prvek záhlaví (další informace naleznete v tématu [Styly oken):](../../mfc/reference/styles-used-by-mfc.md#window-styles)

- WS_CHILD Vytvoří podřízené okno. Nelze použít se stylem WS_POPUP.

- WS_VISIBLE Vytvoří okno, které je zpočátku viditelné.

- WS_DISABLED Vytvoří okno, které je zpočátku zakázáno.

- WS_GROUP Určuje první ovládací prvek skupiny ovládacích prvků, ve kterém může uživatel přesunout z jednoho ovládacího prvku na další pomocí kláves se šipkami. Všechny ovládací prvky definované WS_GROUP stylu po prvním ovládacím prvku patří do stejné skupiny. Další ovládací prvek se stylem WS_GROUP ukončí skupinu stylů a spustí další skupinu (to znamená, že jedna skupina končí tam, kde začíná další).

- WS_TABSTOP Určuje jeden z libovolného počtu ovládacích prvků, kterými se uživatel může pohybovat pomocí klávesy TAB. Klávesa TAB přesune uživatele na další ovládací prvek určený WS_TABSTOP stylu.

Pokud chcete použít rozšířené styly oken s ovládacím `Create`prvkem, zavolejte [CreateEx](#createex) místo .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

## <a name="cheaderctrlcreateex"></a><a name="createex"></a>CHeaderCtrl::CreateEx

Vytvoří ovládací prvek (podřízené okno) `CHeaderCtrl` a přidruží jej k objektu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwExStyl*<br/>
Určuje rozšířený styl vytvářeného ovládacího prvku. Seznam rozšířených stylů systému Windows naleznete v parametru *dwExStyle* pro [createwindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) v sadě Windows SDK.

*dwStyl*<br/>
Styl ovládacího prvku záhlaví. Popis stylů ovládacích prvků záhlaví naleznete v tématu [Styly řízení záhlaví](/windows/win32/Controls/header-control-styles) v sadě Windows SDK. Seznam dalších stylů najdete v tématu [Vytvoření.](#create)

*Rect*<br/>
Odkaz na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu popisující velikost a umístění okna, které mají být vytvořeny, v klientských souřadnicích *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládací prvek.

*Nid*<br/>
ID podřízeného okna ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Místo `CreateEx` toho `Create` použijte rozšířené styly systému Windows určené **předmluvou**rozšířeného stylu systému Windows WS_EX_ .

## <a name="cheaderctrlcreatedragimage"></a><a name="createdragimage"></a>CHeaderCtrl::CreateDragImage

Vytvoří průhlednou verzi obrázku položky v ovládacím prvku záhlaví.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index na základě nuly položky v ovládacím prvku záhlaví. Obrázek přiřazený k této položce je základem průhledného obrázku.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CImageList,](../../mfc/reference/cimagelist-class.md) pokud je úspěšný; jinak NULL. Vrácený seznam obsahuje pouze jeden obrázek.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage), jak je popsáno v sadě Windows SDK. Je k dispozici pro podporu položky záhlaví přetažení.

Objekt, `CImageList` na který body vráceného ukazatele je dočasný objekt a je odstraněn v dalším zpracování nečinnosti.

## <a name="cheaderctrldeleteitem"></a><a name="deleteitem"></a>CHeaderCtrl::DeleteItem

Odstraní položku z ovládacího prvku záhlaví.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje nulový index položky, kterou chcete odstranit.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

## <a name="cheaderctrldrawitem"></a><a name="drawitem"></a>CHeaderCtrl::DrawItem

Volat rámci při změny vizuální aspekt hlavičky kreslení vlastníka.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na [drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) strukturu popisující položku, která má být vybarvena.

### <a name="remarks"></a>Poznámky

Člen `itemAction` `DRAWITEMSTRUCT` struktury definuje kreslicí akci, která má být provedena.

Ve výchozím nastavení tato členská funkce neprovede žádné. Přepsat tuto členovou funkci implementovat výkres `CHeaderCtrl` pro objekt nakreslení vlastníka.

Aplikace by měla obnovit všechny objekty rozhraní grafického zařízení (GDI) vybrané pro kontext zobrazení dodaný v *lpDrawItemStruct* před ukončením této členské funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

## <a name="cheaderctrleditfilter"></a><a name="editfilter"></a>CHeaderCtrl::Upravitfiltr

Začne upravovat zadaný filtr ovládacího prvku záhlaví.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Parametry

*nSloupec*<br/>
Sloupec, který chcete upravit.

*bDiscardChanges*<br/>
Hodnota, která určuje, jak zacházet se změnami úprav uživatele, pokud uživatel při odeslání [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter) zprávy provádí úpravy filtru.

Zadejte hodnotu TRUE, chcete-li zahodit změny provedené uživatelem, nebo NEPRAVDA, aby bylo nutné přijmout změny provedené uživatelem.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování zprávy Win32 [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter), jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

## <a name="cheaderctrlgetbitmapmargin"></a><a name="getbitmapmargin"></a>CHeaderCtrl::GetBitmapMargin

Načte šířku okraje rastrového bodu v ovládacím prvku záhlaví.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka bitmapového okraje v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)zprávy Win32 , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

## <a name="cheaderctrlgetfocuseditem"></a><a name="getfocuseditem"></a>CHeaderCtrl::GetFocusedItem

Získá index položky, která má fokus v aktuální ovládací prvek záhlaví.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Nula na základě indexu položky záhlaví, která má fokus.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu HDM_GETFOCUSEDITEM,](/windows/win32/Controls/hdm-getfocuseditem) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_headerCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `SetFocusedItem` `GetFocusedItem` metody a. V dřívější části kódu jsme vytvořili ovládací prvek záhlaví s pěti sloupci. Oddělovač sloupců však můžete přetáhnout tak, aby sloupec nebyl viditelný. Následující příklad nastaví a potom potvrdí záhlaví posledního sloupce jako položku fokusu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlgetimagelist"></a><a name="getimagelist"></a>CHeaderCtrl::GetImageList

Načte popisovač seznamu obrázků použitých pro položky záhlaví výkresu v ovládacím prvku záhlaví.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CImageList.](../../mfc/reference/cimagelist-class.md)

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/hdm-getimagelist)Win32 HDM_GETIMAGELIST , jak je popsáno v sadě Windows SDK. Objekt, `CImageList` na který body vráceného ukazatele je dočasný objekt a je odstraněn v dalším zpracování nečinnosti.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

## <a name="cheaderctrlgetitem"></a><a name="getitem"></a>CHeaderCtrl::GetItem

Načte informace o položce ovládacího prvku záhlaví.

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje nulový index položky, kterou chcete načíst.

*položka záhlaví*<br/>
Ukazatel na [hditem](/windows/win32/api/commctrl/ns-commctrl-hditemw) strukturu, která obdrží novou položku. Tato struktura se `InsertItem` používá `SetItem` s a členské funkce. Všechny příznaky nastavené v `mask` prvku zajišťují, že hodnoty v odpovídajících prvcích jsou správně vyplněny při návratu. Pokud `mask` je prvek nastaven na nulu, hodnoty v ostatních elementech struktury jsou bezvýznamné.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

## <a name="cheaderctrlgetitemcount"></a><a name="getitemcount"></a>CHeaderCtrl::GetItemCount

Načte počet položek v ovládacím prvku záhlaví.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek ovládacího prvku záhlaví, pokud je úspěšný; jinak - 1.

### <a name="example"></a>Příklad

  Viz příklad [cheaderctrl::DeleteItem](#deleteitem).

## <a name="cheaderctrlgetitemdropdownrect"></a><a name="getitemdropdownrect"></a>CHeaderCtrl::GetItemDropDownRect

Získá ohraničovací obdélník rozevíracího tlačítka pro položku záhlaví v aktuálním ovládacím prvku záhlaví.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iPoložka*|[v] Nulový index položky záhlaví, jehož styl je HDF_SPLITBUTTON. Další informace naleznete `fmt` v člen [hditem](/windows/win32/api/commctrl/ns-commctrl-hditemw) struktury.|
|*lpRect*|[out] Ukazatel na [rect](/windows/win32/api/windef/ns-windef-rect) struktury pro příjem informace ohraničující obdélník.|

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je tato funkce úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu HDM_GETITEMDROPDOWNRECT,](/windows/win32/Controls/hdm-getitemdropdownrect) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_headerCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `GetItemDropDownRect` metodu. V dřívější části kódu jsme vytvořili ovládací prvek záhlaví s pěti sloupci. Následující příklad kódu nakreslí 3D obdélník kolem umístění v prvním sloupci, který je vyhrazen pro rozbalovací tlačítko záhlaví.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

## <a name="cheaderctrlgetitemrect"></a><a name="getitemrect"></a>CHeaderCtrl::GetItemRect

Načte ohraničovací obdélník pro danou položku v ovládacím prvku záhlaví.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index na základě nuly položky ovládacího prvku záhlaví.

*lpRect*<br/>
Ukazatel na adresu [rect](/windows/win32/api/windef/ns-windef-rect) struktury, která přijímá informace ohraničující obdélník.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování [win32](/windows/win32/Controls/hdm-getitemrect)HDM_GETITEMRECT zprávy , jak je popsáno v sadě Windows SDK.

## <a name="cheaderctrlgetorderarray"></a><a name="getorderarray"></a>CHeaderCtrl::GetOrderArray

Načte pořadí položek zleva doprava v ovládacím prvku záhlaví.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Parametry

*piArray*<br/>
Ukazatel na adresu vyrovnávací paměti, která přijímá hodnoty indexu položek v ovládacím prvku záhlaví, v pořadí, ve kterém se zobrazí zleva doprava.

*iCount*<br/>
Počet položek ovládacího prvku záhlaví. Musí být nenegativní.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)zprávy Win32 , jak je popsáno v sadě Windows SDK. Je k dispozici pro podporu řazení položek záhlaví.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

## <a name="cheaderctrlgetoverflowrect"></a><a name="getoverflowrect"></a>CHeaderCtrl::GetOverflowRect

Získá ohraničující obdélník tlačítka přetečení aktuálního ovládacího prvku záhlaví.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpRect*|[out] Ukazatel na [rect](/windows/win32/api/windef/ns-windef-rect) strukturu, která přijímá informace ohraničující obdélník.|

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud je tato funkce úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud ovládací prvek záhlaví obsahuje více položek, než lze zobrazit současně, ovládací prvek může zobrazit tlačítko přetečení, které se posouvá na položky, které nejsou viditelné. Ovládací prvek záhlaví musí mít HDS_OVERFLOW a HDF_SPLITBUTTON styly, aby se zobrazilo tlačítko přetečení. Ohraničovací obdélník ohraničuje tlačítko přetečení a existuje pouze v případě, že se zobrazí tlačítko přetečení. Další informace naleznete v [tématu Styly záhlaví ovládacího prvku](/windows/win32/Controls/header-control-styles).

Tato metoda odešle [zprávu HDM_GETOVERFLOWRECT,](/windows/win32/Controls/hdm-getoverflowrect) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_headerCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `GetOverflowRect` metodu. V dřívější části kódu jsme vytvořili ovládací prvek záhlaví s pěti sloupci. Oddělovač sloupců však můžete přetáhnout tak, aby sloupec nebyl viditelný. Pokud některé sloupce nejsou viditelné, ovládací prvek záhlaví nakreslí tlačítko přetečení. Následující příklad kódu nakreslí 3D obdélník kolem umístění tlačítka přetečení.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

## <a name="cheaderctrlhittest"></a><a name="hittest"></a>CHeaderCtrl::HitTest

Určuje, která položka záhlaví, pokud existuje, je umístěna v zadaném bodě.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*phdhti*|[dovnitř, ven] Ukazatel na [strukturu HDHITTESTINFO,](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) která určuje bod testování a obdrží výsledky testu.|

### <a name="return-value"></a>Návratová hodnota

Index na základě nuly položky záhlaví, pokud existuje, na zadané pozici; jinak -1.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu HDM_HITTEST,](/windows/win32/Controls/hdm-hittest) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_headerCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `HitTest` metodu. V dřívější části tohoto příkladu kódu jsme vytvořili ovládací prvek záhlaví s pěti sloupci. Oddělovač sloupců však můžete přetáhnout tak, aby sloupec nebyl viditelný. Tento příklad hlásí index sloupce, pokud je viditelný a -1, pokud sloupec není viditelný.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

## <a name="cheaderctrlinsertitem"></a><a name="insertitem"></a>CHeaderCtrl::InsertItem

Vloží novou položku do ovládacího prvku záhlaví v zadaném indexu.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Nulový index položky, která má být vložena. Pokud je hodnota nulová, položka je vložena na začátek ovládacího prvku záhlaví. Pokud je hodnota větší než maximální hodnota, položka je vložena na konec ovládacího prvku záhlaví.

*phdi*<br/>
Ukazatel na [hditem](/windows/win32/api/commctrl/ns-commctrl-hditemw) strukturu, která obsahuje informace o položku, která má být vložena.

### <a name="return-value"></a>Návratová hodnota

Index nové položky v případě úspěchu; jinak - 1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

## <a name="cheaderctrllayout"></a><a name="layout"></a>CHeaderCtrl::rozložení

Načte velikost a umístění ovládacího prvku záhlaví v rámci daného obdélníku.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Parametry

*pRozložení záhlaví*<br/>
Ukazatel na strukturu [HDLAYOUT,](/windows/win32/api/commctrl/ns-commctrl-hdlayout) která obsahuje informace použité k nastavení velikosti a umístění ovládacího prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce se používá k určení příslušné rozměry pro nový ovládací prvek záhlaví, který má obsadit daný obdélník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

## <a name="cheaderctrlordertoindex"></a><a name="ordertoindex"></a>cheaderctrl::OrderToIndex

Načte hodnotu indexu pro položku na základě jejího pořadí v ovládacím prvku záhlaví.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Parametry

*nObjednat*<br/>
Pořadí založené na nule, které se zobrazí v ovládacím prvku záhlaví, zleva doprava.

### <a name="return-value"></a>Návratová hodnota

Index položky na základě jejího pořadí v ovládacím prvku záhlaví. Index se počítá zleva doprava, počínaje 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)maker Win32 , jak je popsáno v sadě Windows SDK. Je k dispozici pro podporu řazení položek záhlaví.

## <a name="cheaderctrlsetbitmapmargin"></a><a name="setbitmapmargin"></a>CHeaderCtrl::SetBitmapMargin

Nastaví šířku okraje rastrového bodu v ovládacím prvku záhlaví.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Parametry

*nŠířka*<br/>
Šířka okraje určeného v obrazových bodech, který obklopuje bitmapu v rámci existujícího ovládacího prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Šířka bitmapového okraje v obrazových bodech.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)zprávy Win32 , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

## <a name="cheaderctrlsetfilterchangetimeout"></a><a name="setfilterchangetimeout"></a>CHeaderCtrl::SetFilterChangeTimeout

Nastaví časový interval mezi časem, kdy dojde ke změně v atributech filtru, a zaúčtováním [oznámení HDN_FILTERCHANGE.](/windows/win32/Controls/hdn-filterchange)

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Parametry

*dwTimeOut*<br/>
Hodnota časového času v milisekundách.

### <a name="return-value"></a>Návratová hodnota

Index ovládacího prvku filtru upravovaný.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)zprávy Win32 , jak je popsáno v sadě Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

## <a name="cheaderctrlsetfocuseditem"></a><a name="setfocuseditem"></a>CHeaderCtrl::SetFocusedItem

Nastaví fokus na zadanou položku záhlaví v aktuálním ovládacím prvku záhlaví.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iPoložka*|[v] Nulový index položky záhlaví.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Tato metoda odešle [zprávu HDM_SETFOCUSEDITEM,](/windows/win32/Controls/hdm-setfocuseditem) která je popsána v sadě Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou , `m_headerCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `SetFocusedItem` `GetFocusedItem` metody a. V dřívější části kódu jsme vytvořili ovládací prvek záhlaví s pěti sloupci. Oddělovač sloupců však můžete přetáhnout tak, aby sloupec nebyl viditelný. Následující příklad nastaví a potom potvrdí záhlaví posledního sloupce jako položku fokusu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlsethotdivider"></a><a name="sethotdivider"></a>CHeaderCtrl::SetHotDivider

Změní oddělovač mezi položkami záhlaví tak, aby označoval ruční přetažení položky záhlaví.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Parametry

*Pt*<br/>
Pozice ukazatele. Ovládací prvek záhlaví zvýrazní příslušný oddělovač na základě polohy ukazatele.

*nIndex*<br/>
Index zvýrazněného děliče.

### <a name="return-value"></a>Návratová hodnota

Index zvýrazněného děliče.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [zprávy](/windows/win32/Controls/hdm-sethotdivider)Win32 HDM_SETHOTDIVIDER , jak je popsáno v sadě Windows SDK. Je k dispozici pro podporu položky záhlaví přetažení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

## <a name="cheaderctrlsetimagelist"></a><a name="setimagelist"></a>CHeaderCtrl::SetImageList

Přiřadí seznam obrázků ovládacímu prvku záhlaví.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*seznam obrázků pImage*<br/>
Ukazatel na `CImageList` objekt obsahující seznam obrázků, který má být přiřazen ovládacímu prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CImageList,](../../mfc/reference/cimagelist-class.md) který byl dříve přiřazen ovládacímu prvku záhlaví.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)zprávy Win32 , jak je popsáno v sadě Windows SDK. Objekt, `CImageList` na který body vráceného ukazatele je dočasný objekt a je odstraněn v dalším zpracování nečinnosti.

### <a name="example"></a>Příklad

  Viz příklad [cheaderctrl::GetImageList](#getimagelist).

## <a name="cheaderctrlsetitem"></a><a name="setitem"></a>CHeaderCtrl::SetItem

Nastaví atributy zadané položky v ovládacím prvku záhlaví.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Nula na základě indexu položky, které mají být manipulováno.

*položka záhlaví*<br/>
Ukazatel na [hditem](/windows/win32/api/commctrl/ns-commctrl-hditemw) strukturu, která obsahuje informace o nové položky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="example"></a>Příklad

  Viz příklad [cheaderctrl::GetItem](#getitem).

## <a name="cheaderctrlsetorderarray"></a><a name="setorderarray"></a>CHeaderCtrl::SetOrderArray

Nastaví pořadí položek v ovládacím prvku záhlaví zleva doprava.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Parametry

*iCount*<br/>
Počet položek ovládacího prvku záhlaví.

*piArray*<br/>
Ukazatel na adresu vyrovnávací paměti, která přijímá hodnoty indexu položek v ovládacím prvku záhlaví, v pořadí, ve kterém se zobrazí zleva doprava.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování [HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)maker Win32 , jak je popsáno v sadě Windows SDK. Je k dispozici pro podporu řazení položek záhlaví.

### <a name="example"></a>Příklad

  Viz příklad [cheaderctrl::GetOrderArray](#getorderarray).

## <a name="see-also"></a>Viz také

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CTabCtrl](../../mfc/reference/ctabctrl-class.md)<br/>
[Třída CListCtrl](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList – třída](../../mfc/reference/cimagelist-class.md)
