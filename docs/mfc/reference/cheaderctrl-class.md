---
title: CHeaderCtrl – třída
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
ms.openlocfilehash: 62915da703e1c938e65643ab389999b83c72d459
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741532"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl – třída

Poskytuje funkce pro běžný ovládací prvek záhlaví Windows.

## <a name="syntax"></a>Syntaxe

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|`CHeaderCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Vymaže všechny filtry pro ovládací prvek záhlaví.|
|[CHeaderCtrl::ClearFilter](#clearfilter)|Vymaže filtr pro ovládací prvek záhlaví.|
|[CHeaderCtrl::Create](#create)|Vytvoří ovládací prvek záhlaví a připojí ho k `CHeaderCtrl` objektu.|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Vytvoří transparentní verzi obrázku položky v rámci ovládacího prvku záhlaví.|
|[CHeaderCtrl::CreateEx](#createex)|Vytvoří ovládací prvek záhlaví se zadanými rozšířenými styly Windows a připojí ho k `CListCtrl` objektu.|
|[CHeaderCtrl::DeleteItem](#deleteitem)|Odstraní položku z ovládacího prvku záhlaví.|
|[CHeaderCtrl::DrawItem](#drawitem)|Nakreslí určenou položku ovládacího prvku záhlaví.|
|[CHeaderCtrl::EditFilter](#editfilter)|Spustí úpravu zadaného filtru ovládacího prvku záhlaví.|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Načte šířku okraje rastrového obrázku v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Získá identifikátor položky v aktuálním ovládacím prvku záhlaví, který má fokus.|
|[CHeaderCtrl::GetImageList](#getimagelist)|Načte popisovač seznamu obrázků používaného pro vykreslení položek záhlaví v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetItem](#getitem)|Načte informace o položce v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetItemCount](#getitemcount)|Načte počet položek v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Získá informace o ohraničujícím obdélníku pro zadané tlačítko rozevíracího seznamu v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetItemRect](#getitemrect)|Načte ohraničující obdélník pro danou položku v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Načte pořadí položek zleva doprava v ovládacím prvku záhlaví.|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Získá ohraničující obdélník tlačítka přetečení pro aktuální ovládací prvek záhlaví.|
|[CHeaderCtrl::HitTest](#hittest)|Určuje, která položka záhlaví, je-li k dispozici, je umístěna v zadaném bodě.|
|[CHeaderCtrl::InsertItem](#insertitem)|Vloží novou položku do ovládacího prvku záhlaví.|
|[CHeaderCtrl::Layout](#layout)|Načte velikost a polohu ovládacího prvku záhlaví v daném obdélníku.|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Načte hodnotu indexu pro položku na základě pořadí v ovládacím prvku záhlaví.|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Nastaví šířku okraje rastrového obrázku v ovládacím prvku záhlaví.|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Nastaví časový limit mezi časem, kdy změna proběhne v atributech filtru a při zaúčtování `HDN_FILTERCHANGE` oznámení.|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Nastaví fokus na zadanou položku záhlaví v aktuálním ovládacím prvku záhlaví.|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Změní oddělovač mezi položkami záhlaví tak, aby označovaly ruční přetahování položky záhlaví.|
|[CHeaderCtrl::SetImageList](#setimagelist)|Přiřadí seznam obrázků k ovládacímu prvku záhlaví.|
|[CHeaderCtrl::SetItem](#setitem)|Nastaví atributy zadané položky v ovládacím prvku záhlaví.|
|[CHeaderCtrl:: SetOrderArray](#setorderarray)|Nastaví pořadí položek zleva doprava v ovládacím prvku záhlaví.|

## <a name="remarks"></a>Poznámky

Ovládací prvek záhlaví je okno, které je obvykle umístěno nad sadou sloupců textu nebo čísel. Obsahuje název každého sloupce a může být rozdělen na části. Uživatel může přetáhnout oddělovače, které oddělují části, a nastavit šířku každého sloupce. Ilustrace ovládacího prvku záhlaví naleznete v tématu [ovládací prvky záhlaví](/windows/win32/Controls/header-controls).

Tento ovládací prvek (a `CHeaderCtrl` třída) je k dispozici pouze pro programy, které běží v systémech Windows 95/98 a Windows NT verze 3,51 a novější.

K dispozici jsou funkce pro běžné ovládací prvky Windows 95/Internet Explorer 4,0, které zahrnují následující:

- Vlastní řazení položky záhlaví

- Položka hlavičky přetažení pro změnu pořadí položek záhlaví. Při vytváření `CHeaderCtrl` objektu použijte styl HDS_DRAGDROP.

- Text záhlaví sloupce se průběžně zobrazit během změny velikosti sloupce. Při vytváření `CHeaderCtrl` objektu použijte styl HDS_FULLDRAG.

- Hlavičku horkého sledování, která zvýrazní položku záhlaví, když na ni ukazatel myši najede. Při vytváření `CHeaderCtrl` objektu použijte styl HDS_HOTTRACK.

- Podpora seznamu obrázků. Položky záhlaví mohou obsahovat obrázky uložené v `CImageList` objektu nebo textu.

Další informace o použití `CHeaderCtrl`naleznete v tématu [Controls](../../mfc/controls-mfc.md) and [using CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

##  <a name="cheaderctrl"></a>CHeaderCtrl:: CHeaderCtrl

`CHeaderCtrl` Vytvoří objekt.

```
CHeaderCtrl();
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

##  <a name="clearallfilters"></a>CHeaderCtrl:: ClearAllFilters

Vymaže všechny filtry pro ovládací prvek záhlaví.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování zprávy Win32 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter) s hodnotou sloupce-1, jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>CHeaderCtrl:: ClearFilter

Vymaže filtr pro ovládací prvek záhlaví.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Parametry

*nColumn*<br/>
Hodnota sloupce určující, který filtr se má vymazat

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování zprávy Win32 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>CHeaderCtrl:: Create

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
Určuje styl ovládacího prvku záhlaví. Popis stylů ovládacího prvku záhlaví naleznete v tématu [styly ovládacího prvku záhlaví](/windows/win32/Controls/header-control-styles) v Windows SDK.

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku záhlaví. Může to být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Určuje nadřazené okno ovládacího prvku záhlaví, obvykle a `CDialog`. Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla inicializace úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

`CHeaderCtrl` Vytvoříte objekt ve dvou krocích. Nejprve zavolejte konstruktor a potom zavolejte `Create`, čímž se vytvoří ovládací prvek záhlaví a připojí se `CHeaderCtrl` k objektu.

Kromě stylů ovládacího prvku záhlaví můžete použít následující běžné styly ovládacích prvků k určení, jak ovládací prvek záhlaví pozice a velikost sebe sama (viz [Obecné styly ovládacích prvků](/windows/win32/Controls/common-control-styles) pro další informace):

- CCS_BOTTOM způsobí, že se ovládací prvek umístí do dolní části klientské oblasti v nadřazeném okně a nastaví šířku tak, aby byla stejná jako šířka nadřazeného okna.

- CCS_NODIVIDER zabraňuje vykreslení dvou pixelů v horní části ovládacího prvku.

- CCS_NOMOVEY způsobí, že ovládací prvek změní velikost a přesune ho vodorovně, ale ne svisle, jako odpověď na zprávu WM_SIZE. Pokud se používá styl CCS_NORESIZE, tento styl se nedá použít. Ovládací prvky záhlaví mají ve výchozím nastavení tento styl.

- CCS_NOPARENTALIGN zabraňuje automatickému přesunutí ovládacího prvku do horní nebo dolní části nadřazeného okna. Místo toho ovládací prvek zachovává svou polohu v nadřazeném okně Navzdory změnám velikosti nadřazeného okna. Je-li použit také styl CCS_TOP nebo CCS_BOTTOM, Výška je nastavena na výchozí hodnotu, ale pozice a šířka zůstane beze změny.

- CCS_NORESIZE zabraňuje ovládacímu prvku v použití výchozí šířky a výšky při nastavení počáteční velikosti nebo nové velikosti. Místo toho používá ovládací prvek šířku a výšku zadanou v žádosti o vytvoření nebo změnu velikosti.

- CCS_TOP způsobí, že se ovládací prvek umístí do horní části klientské oblasti nadřazeného okna a nastaví šířku tak, aby byla stejná jako šířka nadřazeného okna.

V ovládacím prvku záhlaví můžete také použít následující styly oken (Další informace najdete v tématu [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) ):

- WS_CHILD vytvoří podřízené okno. Nelze použít se stylem WS_POPUP.

- WS_VISIBLE vytvoří okno, které je zpočátku viditelné.

- WS_DISABLED vytvoří okno, které je zpočátku zakázané.

- WS_GROUP Určuje první ovládací prvek skupiny ovládacích prvků, ve kterém může uživatel přejít z jednoho ovládacího prvku na další pomocí kláves se šipkami. Všechny ovládací prvky definované pomocí stylu WS_GROUP po prvním ovládacím prvku patří do stejné skupiny. Následující ovládací prvek se stylem WS_GROUP ukončí skupinu stylů a spustí další skupinu (to znamená, že jedna skupina končí, kde začíná další).

- WS_TABSTOP Určuje jeden z libovolných ovládacích prvků, pomocí nichž může uživatel přesunout pomocí klávesy TAB. Klávesa TAB přesune uživatele k dalšímu ovládacímu prvku určenému stylem WS_TABSTOP.

Chcete-li použít rozšířené styly systému Windows s ovládacím prvkem, zavolejte [CreateEx](#createex) místo `Create`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>CHeaderCtrl:: CreateEx

Vytvoří ovládací prvek (podřízené okno) a přidruží ho k `CHeaderCtrl` objektu.

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
Určuje rozšířený styl ovládacího prvku, který se vytváří. Seznam rozšířených stylů Windows naleznete v parametru *dwExStyle* pro [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) v Windows SDK.

*dwStyle*<br/>
Styl ovládacího prvku záhlaví Popis stylů ovládacího prvku záhlaví naleznete v tématu [styly ovládacího prvku záhlaví](/windows/win32/Controls/header-control-styles) v Windows SDK. Seznam dalších stylů najdete v tématu [Vytvoření](#create) .

*OBD*<br/>
Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) popisující velikost a umístění okna, které má být vytvořeno, v souřadnicích klienta *pParentWnd*.

*pParentWnd*<br/>
Ukazatel na okno, které je nadřazený ovládacímu prvku.

*nID*<br/>
ID podřízeného okna ovládacího prvku

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Použijte `CreateEx`místo pro použití rozšířených stylů Windows, které jsou určené WS_EX_ rozšířeným stylem Windows. `Create`

##  <a name="createdragimage"></a>  CHeaderCtrl::CreateDragImage

Vytvoří transparentní verzi obrázku položky v rámci ovládacího prvku záhlaví.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky vycházející z nuly v rámci ovládacího prvku záhlaví. Obrázek přiřazený k této položce je základem pro transparentní obrázek.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [atributu CImageList](../../mfc/reference/cimagelist-class.md) , pokud je úspěšný; jinak NULL. Vrácený seznam obsahuje pouze jeden obrázek.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage), jak je popsáno v Windows SDK. Je k dispozici pro podporu přetahování položky hlavičky.

`CImageList` Objekt, na který vracené body ukazatele jsou dočasným objektem a který je odstraněn při dalším zpracování nečinného času.

##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem

Odstraní položku z ovládacího prvku záhlaví.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje index položky vycházející z nuly, který má být odstraněn.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

##  <a name="drawitem"></a>CHeaderCtrl::D rawItem

Volá se rozhraním, když se změní vizuální aspekt ovládacího prvku záhlaví, který je vykreslený vlastníkem.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Ukazatel na strukturu [DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) popisující položku, která se má vykreslit.

### <a name="remarks"></a>Poznámky

`itemAction` Člen`DRAWITEMSTRUCT` struktury definuje akci kreslení, která má být provedena.

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Přepište tuto členskou funkci pro implementaci vykreslování pro objekt vykreslený `CHeaderCtrl` vlastníkem.

Aplikace by měla obnovit všechny objekty GDI (Graphic Device Interface) vybrané pro kontext zobrazení zadaný v *lpDrawItemStruct* před ukončením této členské funkce.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>  CHeaderCtrl::EditFilter

Začne upravovat zadaný filtr ovládacího prvku záhlaví.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Parametry

*nColumn*<br/>
Sloupec, který se má upravit

*bDiscardChanges*<br/>
Hodnota, která určuje, jak se mají zpracovat změny úprav uživatele, pokud je uživatel v procesu úpravou filtru při odeslání zprávy [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter) .

Zadejte hodnotu TRUE, pokud chcete zahodit změny provedené uživatelem, nebo hodnotu FALSE, aby se projevily změny provedené uživatelem.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování zprávy Win32 [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin

Načte šířku okraje rastrového obrázku v ovládacím prvku záhlaví.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Návratová hodnota

Šířka rastrového obrázku v pixelech

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>  CHeaderCtrl::GetFocusedItem

Získá index položky, která má fokus v aktuálním ovládacím prvku záhlaví.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Návratová hodnota

Index vycházející z položky záhlaví s hodnotou nula, která má fokus.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_headerCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `SetFocusedItem` metody a. `GetFocusedItem` V dřívější části kódu jsme vytvořili ovládací prvek záhlaví s pěti sloupci. Oddělovač sloupců však lze přetáhnout, takže sloupec není viditelný. Následující příklad nastaví a pak potvrdí poslední záhlaví sloupce jako položku fokusu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList

Načte popisovač seznamu obrázků používaného pro vykreslení položek záhlaví v ovládacím prvku záhlaví.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [atributu CImageList](../../mfc/reference/cimagelist-class.md) .

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist), jak je popsáno v Windows SDK. `CImageList` Objekt, na který vracené body ukazatele jsou dočasným objektem a který je odstraněn při dalším zpracování nečinného času.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

##  <a name="getitem"></a>CHeaderCtrl:: GetItem

Načte informace o položce ovládacího prvku záhlaví.

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Určuje index založený na nule položky, která se má načíst.

*pHeaderItem*<br/>
Ukazatel na strukturu [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) , která obdrží novou položku. Tato struktura je použita s `InsertItem` členskými funkcemi a. `SetItem` Všechny příznaky nastavené v `mask` elementu zajišťují, aby hodnoty v odpovídajících prvcích byly po návratu správně vyplněny. Pokud je `mask` prvek nastaven na hodnotu nula, hodnoty v ostatních prvcích struktury jsou nevýznamné.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>  CHeaderCtrl::GetItemCount

Načte počet položek v ovládacím prvku záhlaví.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet položek ovládacího prvku záhlaví, pokud proběhlo úspěšně; v opačném případě-1.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CHeaderCtrl::D eleteitem](#deleteitem).

##  <a name="getitemdropdownrect"></a>  CHeaderCtrl::GetItemDropDownRect

Získá ohraničující obdélník tlačítka rozevíracího seznamu pro položku záhlaví v aktuálním ovládacím prvku záhlaví.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iItem*|pro Index položky záhlaví, jejichž styl je HDF_SPLITBUTTON, je počítán od nuly. Další informace naleznete v tématu `fmt` člen struktury [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) .|
|*lpRect*|mimo Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) pro příjem informací o ohraničujícím obdélníku.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato funkce úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_headerCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `GetItemDropDownRect` metodu. V dřívější části kódu jsme vytvořili ovládací prvek záhlaví s pěti sloupci. Následující příklad kódu kreslí kolem umístění v prvním sloupci, který je vyhrazen pro tlačítko pro rozevírací seznam záhlaví, 3D obdélník.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>CHeaderCtrl:: GetItemRect

Načte ohraničující obdélník pro danou položku v ovládacím prvku záhlaví.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index vycházející z položky ovládacího prvku záhlaví (počítáno od nuly).

*lpRect*<br/>
Ukazatel na adresu struktury [Rect](/previous-versions/dd162897\(v=vs.85\)) , která obdrží informace o ohraničujícím obdélníku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato metoda implementuje chování zprávy Win32 [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect), jak je popsáno v Windows SDK.

##  <a name="getorderarray"></a>CHeaderCtrl:: GetOrderArray

Načte pořadí položek zleva doprava v ovládacím prvku záhlaví.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Parametry

*piArray*<br/>
Ukazatel na adresu vyrovnávací paměti, která přijímá hodnoty indexu položek v ovládacím prvku záhlaví, v pořadí, ve kterém jsou uvedeny zleva doprava.

*iCount*<br/>
Počet položek ovládacího prvku záhlaví Hodnota musí být nezáporná.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray), jak je popsáno v Windows SDK. Je k dispozici pro podporu řazení položek záhlaví.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>CHeaderCtrl:: GetOverflowRect

Získá ohraničující obdélník tlačítka přetečení aktuálního ovládacího prvku záhlaví.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*lpRect*|mimo Ukazatel na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která obdrží informace o ohraničujícím obdélníku.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato funkce úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud ovládací prvek záhlaví obsahuje více položek, než lze současně zobrazit, ovládací prvek může zobrazit tlačítko přetečení, které se posouvá na položky, které nejsou viditelné. Aby bylo možné zobrazit tlačítko přetečení, musí mít ovládací prvek Header styly HDS_OVERFLOW a HDF_SPLITBUTTON. Ohraničující obdélník uzavře tlačítko přetečení a existuje pouze v případě, že je zobrazeno tlačítko přetečení. Další informace naleznete v tématu [styly ovládacího prvku záhlaví](/windows/win32/Controls/header-control-styles).

Tato metoda pošle zprávu [HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_headerCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `GetOverflowRect` metodu. V dřívější části kódu jsme vytvořili ovládací prvek záhlaví s pěti sloupci. Oddělovač sloupců však lze přetáhnout, takže sloupec není viditelný. Pokud některé sloupce nejsou viditelné, ovládací prvek záhlaví nakreslí tlačítko přetečení. Následující příklad kódu nakreslí kolem umístění tlačítka přetečení 3D obdélník.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>CHeaderCtrl:: HitTest

Určuje, která položka záhlaví, je-li k dispozici, je umístěna v zadaném bodě.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*phdhti*|[in, out] Ukazatel na strukturu [HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) , která určuje bod k otestování a přijímá výsledky testu.|

### <a name="return-value"></a>Návratová hodnota

Index vycházející z položky záhlaví, pokud existuje, na zadané pozici; v opačném případě-1.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [HDM_HITTEST](/windows/win32/Controls/hdm-hittest) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_headerCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `HitTest` metodu. V dřívější části tohoto příkladu kódu jsme vytvořili ovládací prvek záhlaví s pěti sloupci. Oddělovač sloupců však lze přetáhnout, takže sloupec není viditelný. Tento příklad nahlásí index sloupce, pokud je viditelný, a-1, pokud sloupec není viditelný.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>CHeaderCtrl:: InsertItem

Vloží novou položku do ovládacího prvku záhlaví v zadaném indexu.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Index vycházející z položky, která má být vložena. Pokud je hodnota nula, položka je vložena na začátek ovládacího prvku záhlaví. Pokud je hodnota větší než maximální hodnota, položka je vložena na konec ovládacího prvku záhlaví.

*phdi*<br/>
Ukazatel na strukturu [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) , která obsahuje informace o položce, která má být vložena.

### <a name="return-value"></a>Návratová hodnota

Index nové položky, pokud je úspěšná; v opačném případě-1.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>CHeaderCtrl:: layout

Načte velikost a polohu ovládacího prvku záhlaví v daném obdélníku.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Parametry

*pHeaderLayout*<br/>
Ukazatel na strukturu [HDLAYOUT](/windows/win32/api/commctrl/ns-commctrl-hdlayout) , která obsahuje informace používané k nastavení velikosti a umístění ovládacího prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k určení vhodných dimenzí pro nový ovládací prvek záhlaví, který má zabírat daný obdélník.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>CHeaderCtrl:: OrderToIndex

Načte hodnotu indexu pro položku na základě pořadí v ovládacím prvku záhlaví.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Parametry

*nOrder*<br/>
Pořadí vycházející z nuly, které se položka zobrazí v ovládacím prvku záhlaví, zleva doprava.

### <a name="return-value"></a>Návratová hodnota

Index položky na základě pořadí v ovládacím prvku záhlaví Index se počítá zleva doprava, počínaje 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování makra Win32 [HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex), jak je popsáno v Windows SDK. Je k dispozici pro podporu řazení položek záhlaví.

##  <a name="setbitmapmargin"></a>CHeaderCtrl:: SetBitmapMargin

Nastaví šířku okraje rastrového obrázku v ovládacím prvku záhlaví.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Parametry

*nWidth*<br/>
Šířka, která je určená v pixelech, která obklopuje rastrový obrázek v rámci existujícího ovládacího prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Šířka rastrového obrázku v pixelech

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout

Nastaví interval časového limitu mezi časem změny v atributech filtru a odesláním oznámení [HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange) .

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Parametry

*dwTimeOut*<br/>
Hodnota časového limitu (v milisekundách)

### <a name="return-value"></a>Návratová hodnota

Index upravovaného ovládacího prvku filtru.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout), jak je popsáno v Windows SDK.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem

Nastaví fokus na zadanou položku záhlaví v aktuálním ovládacím prvku záhlaví.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*iItem*|pro Index položky záhlaví vycházející z nuly|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Tato metoda pošle zprávu [HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem) , která je popsána v Windows SDK.

### <a name="example"></a>Příklad

Následující příklad kódu definuje proměnnou, `m_headerCtrl`která se používá pro přístup k aktuálnímu ovládacímu prvku záhlaví. Tato proměnná se používá v následujícím příkladu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Příklad

Následující příklad kódu ukazuje `SetFocusedItem` metody a. `GetFocusedItem` V dřívější části kódu jsme vytvořili ovládací prvek záhlaví s pěti sloupci. Oddělovač sloupců však lze přetáhnout, takže sloupec není viditelný. Následující příklad nastaví a pak potvrdí poslední záhlaví sloupce jako položku fokusu.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>CHeaderCtrl:: SetHotDivider

Změní oddělovač mezi položkami záhlaví tak, aby označovaly ruční přetahování položky záhlaví.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Parametry

*bodů*<br/>
Pozice ukazatele. Ovládací prvek záhlaví zvýrazní odpovídající oddělovač na základě pozice ukazatele.

*nIndex*<br/>
Index zvýrazněného oddělovače.

### <a name="return-value"></a>Návratová hodnota

Index zvýrazněného oddělovače.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider), jak je popsáno v Windows SDK. Je k dispozici pro podporu přetahování položky hlavičky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>CHeaderCtrl:: SetImageList

Přiřadí seznam obrázků k ovládacímu prvku záhlaví.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parametry

*pImageList*<br/>
Ukazatel na `CImageList` objekt obsahující seznam obrázků, který má být přiřazen k ovládacímu prvku záhlaví.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [atributu CImageList](../../mfc/reference/cimagelist-class.md) dříve přiřazený k ovládacímu prvku záhlaví.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování zprávy Win32 [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist), jak je popsáno v Windows SDK. `CImageList` Objekt, na který vracené body ukazatele jsou dočasným objektem a který je odstraněn při dalším zpracování nečinného času.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CHeaderCtrl:: GetImageList](#getimagelist).

##  <a name="setitem"></a>CHeaderCtrl:: SetItem

Nastaví atributy zadané položky v ovládacím prvku záhlaví.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Parametry

*nPos*<br/>
Index položky, která má být zpracována od nuly.

*pHeaderItem*<br/>
Ukazatel na strukturu [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) , která obsahuje informace o nové položce.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CHeaderCtrl:: GetItem](#getitem).

##  <a name="setorderarray"></a>CHeaderCtrl:: SetOrderArray

Nastaví pořadí položek zleva doprava v ovládacím prvku záhlaví.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Parametry

*iCount*<br/>
Počet položek ovládacího prvku záhlaví

*piArray*<br/>
Ukazatel na adresu vyrovnávací paměti, která přijímá hodnoty indexu položek v ovládacím prvku záhlaví, v pořadí, ve kterém jsou uvedeny zleva doprava.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce implementuje chování makra Win32 [HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray), jak je popsáno v Windows SDK. Je k dispozici pro podporu řazení položek záhlaví.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CHeaderCtrl:: GetOrderArray](#getorderarray).

## <a name="see-also"></a>Viz také:

[CWnd – třída](../../mfc/reference/cwnd-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl – třída](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl – třída](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList – třída](../../mfc/reference/cimagelist-class.md)
