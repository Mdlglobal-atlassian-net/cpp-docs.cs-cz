---
title: CCheckListBox – třída
ms.date: 11/04/2016
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
ms.openlocfilehash: f8c725ea30754a42ce3045f1160b7a09c4481e39
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507353"
---
# <a name="cchecklistbox-class"></a>CCheckListBox – třída

Poskytuje funkce v poli kontrolní seznam systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CCheckListBox : public CListBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CCheckListBox::CCheckListBox](#cchecklistbox)|`CCheckListBox` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CCheckListBox:: Create](#create)|Vytvoří okno kontrolní seznam systému Windows a připojí ho k `CCheckListBox` objektu.|
|[CCheckListBox::D rawItem](#drawitem)|Volá se rozhraním, když se změní vizuální aspekt seznamu vykreslování vlastníka.|
|[CCheckListBox:: Enable](#enable)|Povoluje nebo zakazuje položku v poli kontrolního seznamu.|
|[CCheckListBox:: getcheck](#getcheck)|Získá stav zaškrtávacího políčka položky.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Získá styl zaškrtávacích políček ovládacího prvku.|
|[CCheckListBox::IsEnabled](#isenabled)|Určuje, zda je položka povolena.|
|[CCheckListBox::MeasureItem](#measureitem)|Volá se rozhraním, když se vytvoří seznam se stylem vykreslování vlastníka.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Volá se rozhraním, aby se získala pozice zaškrtávacího políčka položky.|
|[CCheckListBox::SetCheck](#setcheck)|Nastaví stav zaškrtávacího políčka položky.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Nastaví styl zaškrtávacích políček ovládacího prvku.|

## <a name="remarks"></a>Poznámky

Kontrolní seznam obsahuje seznam položek, například názvy souborů. Každá položka v seznamu má vedle sebe zaškrtávací políčko, které může uživatel zaškrtnout nebo zrušit jeho zaškrtnutí.

`CCheckListBox`je pouze pro ovládací prvky vykreslené vlastníkem, protože seznam obsahuje více než textové řetězce. V nejjednodušším případě obsahuje pole kontrolní seznam textové řetězce a zaškrtávací políčka, ale není vůbec nutné mít text. Například můžete mít vedle každé položky seznam malých rastrových obrázků se zaškrtávacím políčkem.

Chcete-li vytvořit vlastní kontrolní seznam, musíte odvodit svou vlastní třídu `CCheckListBox`z. Chcete-li odvodit vlastní třídu, napište konstruktor pro odvozenou třídu a `Create`potom zavolejte.

Chcete-li zpracovat oznamovací zprávy systému Windows odesílané seznamem do své nadřazené položky (obvykle třída odvozená z [CDialog](../../mfc/reference/cdialog-class.md)), přidejte položku mapování zpráv a členskou funkci obslužné rutiny zpráv do nadřazené třídy pro každou zprávu.

Každá položka mapování zpráv má následující podobu:

**V\_** _oznámení_ **(** _ID_, _memberFxn_ **)**

kde `id` Určuje ID podřízeného okna ovládacího prvku odesílajícího oznámení a `memberFxn` je název nadřazené členské funkce, kterou jste napsali pro zpracování oznámení.

Prototyp funkce nadřazeného objektu je následující:

`afx_msg void memberFxn();`

K `CCheckListBox` dispozici je pouze jedna položka mapování zpráv, která se týká konkrétně (viz také položky mapování zpráv pro [CListBox –](../../mfc/reference/clistbox-class.md)):

- ON_CLBN_CHKCHANGE uživatel změnil stav zaškrtávacího políčka položky.

Pokud je váš kontrolní seznam výchozím kontrolním seznamem (seznam řetězců s výchozí velikostí na levé straně každé), můžete k vykreslení pole kontrolního seznamu použít výchozí [CCheckListBox::D rawitem](#drawitem) . V opačném případě je nutné přepsat funkci [CListBox –:: CompareItem](../../mfc/reference/clistbox-class.md#compareitem) a [CCheckListBox::D rawitem](#drawitem) a [CCheckListBox:: MeasureItem](#measureitem) Functions.

Můžete vytvořit kontrolní seznam buď ze šablony dialogového okna, nebo přímo v kódu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox –](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="cchecklistbox"></a>CCheckListBox::CCheckListBox

`CCheckListBox` Vytvoří objekt.

```
CCheckListBox();
```

### <a name="remarks"></a>Poznámky

`CCheckListBox` Vytvoříte objekt ve dvou krocích. Nejdřív Definujte třídu odvozenou od `CCheckListBox`a pak zavolejte `Create`, která inicializuje okno kontrolní seznam systému Windows a `CCheckListBox` připojí ho k objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>CCheckListBox:: Create

Vytvoří okno kontrolní seznam systému Windows a připojí ho k `CCheckListBox` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl pole kontrolního seznamu. Styl musí být LBS_HASSTRINGS a buď LBS_OWNERDRAWFIXED (všechny položky v seznamu mají stejnou výšku) nebo LBS_OWNERDRAWVARIABLE (položky v seznamu mají proměnlivou výšku). Tento styl lze kombinovat s dalšími [styly seznamu](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , kromě LBS_USETABSTOPS.

*OBD*<br/>
Určuje velikost a umístění kontrolního seznamu. Může být buď objekt [CRect](../../atl-mfc-shared/reference/crect-class.md) , nebo struktura [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Určuje nadřazené okno okna kontrolního seznamu (obvykle `CDialog` objektu). Nesmí mít hodnotu NULL.

*nID*<br/>
Určuje ID ovládacího prvku v poli kontrolního seznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

`CCheckListBox` Vytvoříte objekt ve dvou krocích. Nejprve definujte třídu odvozenou z `CcheckListBox` a poté zavolejte `Create`, čímž inicializujete pole kontrolní seznam systému Windows a `CCheckListBox`připojíte ho k. Ukázku naleznete v tématu [CCheckListBox:: CCheckListBox](#cchecklistbox) .

Když `Create` se spustí, Windows pošle zprávy [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)a [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) do ovládacího prvku kontrolní okno.

Tyto zprávy jsou ve výchozím nastavení zpracovávány členskými funkcemi [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [Create](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)a [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) v `CWnd` základní třídě. Chcete-li výchozí zpracování zpráv zvětšit, přidejte do odvozené třídy mapu zprávy a přepište předchozí funkce členů obslužné rutiny zpráv. Přepsání `OnCreate`, například k provedení potřebné inicializace pro novou třídu.

Použijte následující [Styly okna](../../mfc/reference/styles-used-by-mfc.md#window-styles) pro ovládací prvek pole kontrolní seznam:

- WS_CHILD vždycky

- WS_VISIBLE obvykle

- WS_DISABLED málokdy

- WS_VSCROLL pro přidání svislého posuvníku

- WS_HSCROLL pro přidání vodorovného posuvníku

- WS_GROUP do skupinových ovládacích prvků

- WS_TABSTOP, aby se na tento ovládací prvek povolovalo procházení

##  <a name="drawitem"></a>CCheckListBox::D rawItem

Volá se rozhraním, když se změní vizuální aspekt kontrolního seznamu vykresleného vlastníkem.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhý ukazatel na strukturu [DRAWITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-drawitemstruct) , která obsahuje informace o typu požadované kresby.

### <a name="remarks"></a>Poznámky

Členové `itemAction` a`itemState` struktury definují akci kreslení, která má být provedena. `DRAWITEMSTRUCT`

Ve výchozím nastavení tato funkce nakreslí výchozí seznam zaškrtávacích políček, který se skládá ze seznamu řetězců, ve kterém každé má zaškrtávací políčko výchozí velikosti vlevo. Velikost seznamu CheckBox je ta, která je zadána v poli [vytvořit](#create).

Tuto členskou funkci přepište, pokud chcete implementovat vykreslování polí kontrolního seznamu pro vykreslení vlastníka, která nejsou ve výchozím nastavení, jako jsou například pole kontrolního seznamu se seznamy, které nejsou řetězcem, s položkami s proměnlivou výškou nebo se zaškrtávacími políčky, které nejsou na levé straně. Aplikace by měla obnovit všechny objekty GDI (Graphics Device Interface) vybrané pro kontext zobrazení zadaný v *lpDrawItemStruct* před ukončením této členské funkce.

Pokud položky v poli kontrolního seznamu nejsou všechny stejné výšky, musí mít styl pole kontrolní seznam `Create`(zadaný v rámci) * * LBS_OWNERVARIABLE a musí přepsat funkci [MeasureItem](#measureitem) .

##  <a name="enable"></a>CCheckListBox:: Enable

Voláním této funkce povolíte nebo zakážete položku kontrolního seznamu.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky pole kontrolního seznamu, která se má povolit

*bEnabled*<br/>
Určuje, jestli je položka povolená nebo zakázaná.

##  <a name="getcheck"></a>CCheckListBox:: getcheck

Načte stav zadaného zaškrtávacího políčka.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nulový index zaškrtávacího políčka, které je obsaženo v poli se seznamem.

### <a name="return-value"></a>Návratová hodnota

Stav zadaného zaškrtávacího políčka. V následující tabulce jsou uvedeny možné hodnoty.

|Value|Popis|
|-----------|-----------------|
|BST_CHECKED|Zaškrtávací políčko je zaškrtnuto.|
|BST_UNCHECKED|Zaškrtávací políčko není zaškrtnuto.|
|BST_INDETERMINATE|Stav zaškrtávacího políčka je neurčitý.|

##  <a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle

Voláním této funkce získáte styl pole kontrolního seznamu.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Návratová hodnota

Styl zaškrtávacích políček ovládacího prvku

### <a name="remarks"></a>Poznámky

Informace o možných stylech naleznete v tématu [SetCheckStyle](#setcheckstyle).

##  <a name="isenabled"></a>CCheckListBox:: deenable

Voláním této funkce určíte, zda je položka povolena.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je položka povolena; v opačném případě 0.

##  <a name="measureitem"></a>CCheckListBox::MeasureItem

Volá se rozhraním, když se vytvoří okno kontrolního seznamu s nevýchozím stylem.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Dlouhý ukazatel na strukturu [MEASUREITEMSTRUCT –](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádnou akci. Přepište tuto členskou funkci a vyplňte `MEASUREITEMSTRUCT` strukturu pro informování oken rozměrů položek box kontrolního seznamu. Pokud je pole kontrolní seznam vytvořeno pomocí stylu [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , rozhraní zavolá tuto členskou funkci pro každou položku v seznamu. V opačném případě se tento člen volá jenom jednou.

##  <a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition

Rozhraní volá tuto funkci, aby získala polohu a velikost zaškrtávacího políčka v položce.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Parametry

*rectItem*<br/>
Pozice a velikost položky seznamu.

*rectCheckBox*<br/>
Výchozí pozice a velikost zaškrtávacího políčka položky.

### <a name="return-value"></a>Návratová hodnota

Pozice a velikost zaškrtávacího políčka položky.

### <a name="remarks"></a>Poznámky

Výchozí implementace vrátí pouze výchozí pozici a velikost zaškrtávacího políčka (`rectCheckBox`). Ve výchozím nastavení je zaškrtávací políčko zarovnané v levém horním rohu položky a je to standardní velikost zaškrtávacího políčka. Můžou nastat případy, kdy chcete mít zaškrtávací políčka na pravé straně, nebo přejete, aby bylo zaškrtávací políčko větší nebo menší. V těchto případech přepište `OnGetCheckPosition` , abyste změnili polohu a velikost zaškrtávacího políčka v rámci položky.

##  <a name="setcheck"></a>CCheckListBox::SetCheck

Nastaví stav zadaného zaškrtávacího políčka.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nulový index zaškrtávacího políčka, které je obsaženo v poli se seznamem.

*Npokuste*<br/>
Stav tlačítka pro zadané zaškrtávací políčko. Možné hodnoty jsou uvedeny v části poznámky.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny možné hodnoty parametru *npokuste* .

|Value|Popis|
|-----------|-----------------|
|BST_CHECKED|Zaškrtněte políčko se zadaným políčkem.|
|BST_UNCHECKED|Zrušte zaškrtnutí uvedeného políčka.|
|BST_INDETERMINATE|Nastavte stav zadaného zaškrtávacího políčka na neurčitý.<br /><br /> Tento stav je k dispozici pouze v případě, že je stylem zaškrtávacího políčka BS_AUTO3STATE nebo BS_3STATE. Další informace naleznete v tématu [styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

##  <a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle

Voláním této funkce nastavíte styl zaškrtávacích políček v poli kontrolní seznam.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
Určuje styl zaškrtávacích políček v poli kontrolní seznam.

### <a name="remarks"></a>Poznámky

Platné styly jsou:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Informace o těchto stylech naleznete v tématu [styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Viz také:

[TSTCON Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)
