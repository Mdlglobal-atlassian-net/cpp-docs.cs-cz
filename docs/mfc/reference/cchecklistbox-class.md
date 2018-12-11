---
title: Cchecklistbox – třída
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
ms.openlocfilehash: b1e64e947f798becef32fa4d99f21e61133cc8fc
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53177833"
---
# <a name="cchecklistbox-class"></a>Cchecklistbox – třída

Poskytuje funkce pro pole kontrolní seznam Windows.

## <a name="syntax"></a>Syntaxe

```
class CCheckListBox : public CListBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Vytvoří `CCheckListBox` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CCheckListBox::Create](#create)|Vytvoří pole kontrolního seznamu Windows a připojí ho k `CCheckListBox` objektu.|
|[CCheckListBox::DrawItem](#drawitem)|Volá se rozhraním při úpravě vizuálního aspektu uživatelem nakreslený seznam se změní.|
|[CCheckListBox::Enable](#enable)|Povolí nebo zakáže položka pole kontrolního seznamu.|
|[CCheckListBox::GetCheck](#getcheck)|Získá stav zaškrtávacího políčka položky.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Získá styl ovládacího prvku zaškrtávací políčka.|
|[CCheckListBox::IsEnabled](#isenabled)|Určuje, zda je položka povolena.|
|[CCheckListBox::MeasureItem](#measureitem)|Volá se rozhraním, když se vytvoří pole se seznamem stylem vykreslené vlastníkem.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Volá se rozhraním zobrazíte pozici položky zaškrtávací políčko.|
|[CCheckListBox::SetCheck](#setcheck)|Nastaví stav zaškrtávacího políčka položky.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Nastaví styl ovládacího prvku zaškrtávací políčka.|

## <a name="remarks"></a>Poznámky

"Políčko kontrolního seznamu" zobrazí seznam položek, jako jsou názvy souborů. Každá položka v seznamu má zaškrtávací políčko vedle sebe, která uživatel může zaškrtněte nebo zrušte zaškrtnutí.

`CCheckListBox` je jenom pro ovládací prvky vykreslované uživatelem, protože seznam obsahuje více než textovém řetězci. V nejjednodušším pole kontrolního seznamu, které obsahuje textových řetězců a zaškrtávací políčka, ale není potřeba mít textu vůbec. Například můžete mít seznam malé rastrové obrázky zaškrtávací políčko vedle každé položky.

Pokud chcete vytvořit vlastní pole kontrolního seznamu, musí být odvozen ze své vlastní třídy `CCheckListBox`. Chcete-li odvodit vlastní třídu zápis konstruktoru pro odvozenou třídu, pak zavolejte `Create`.

Pokud chcete zpracovávat Windows oznamující zprávy odeslal seznamu k nadřazené úloze (obvykle třída odvozená z [CDialog](../../mfc/reference/cdialog-class.md)), přidat mapu zpráv položku a obslužná rutina zprávy členskou funkci na nadřazené třídu pro každou zprávu.

Každá položka mapování zpráv má následující podobu:

**DÁLE\_**_oznámení_ **(** _id_, _memberFxn_ **)**

kde `id` určuje Identifikátor podřízené okno ovládacího prvku odesílání oznámení a `memberFxn` je název nadřazené členské funkce mají napsané tak, aby oznámení.

Prototyp funkce nadřazeného objektu je následujícím způsobem:

`afx_msg void memberFxn();`

Existuje pouze jedna položka mapování zpráv, které se vztahují speciálně na `CCheckListBox` (ale také zobrazit položky mapy zpráv pro [clistbox –](../../mfc/reference/clistbox-class.md)):

- ON_CLBN_CHKCHANGE uživatele byl změněn stav zaškrtávacího políčka položky.

Pokud vaše políčko kontrolního seznamu je políčko kontrolního seznamu výchozí (seznam řetězců s výchozí velikostí zaškrtávací políčka nalevo od každého), můžete použít výchozí [CCheckListBox::DrawItem](#drawitem) k vykreslení pole kontrolního seznamu. V opačném případě je nutné přepsat [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) funkce a [CCheckListBox::DrawItem](#drawitem) a [CCheckListBox::MeasureItem](#measureitem) funkce.

Políčko kontrolního seznamu můžete vytvořit z šablony dialogového okna nebo přímo v kódu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[Clistbox –](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cchecklistbox"></a>  CCheckListBox::CCheckListBox

Vytvoří `CCheckListBox` objektu.

```
CCheckListBox();
```

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CCheckListBox` objektu ve dvou krocích. Nejprve definovat třídu odvozenou z `CCheckListBox`, zavolejte `Create`, která inicializuje pole kontrolního seznamu Windows a připojí ho k `CCheckListBox` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>  CCheckListBox::Create

Vytvoří pole kontrolního seznamu Windows a připojí ho k `CCheckListBox` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyle*<br/>
Určuje styl políčko kontrolního seznamu. Styl musí být LBS_HASSTRINGS a LBS_OWNERDRAWFIXED (všechny položky v seznamu se stejnou výškou) nebo LBS_OWNERDRAWVARIABLE (položky v seznamu jsou různé výšky). Tento styl je kombinovat s jinými [styly seznamů](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) s výjimkou LBS_USETABSTOPS.

*Rect*<br/>
Určuje pole kontrolního seznamu velikost a umístění. Může být buď [crect –](../../atl-mfc-shared/reference/crect-class.md) objektu nebo [RECT](/windows/desktop/api/windef/ns-windef-tagrect) struktury.

*pParentWnd*<br/>
Určuje pole kontrolního seznamu nadřazené okno (obvykle `CDialog` objekt). Nesmí být NULL.

*nID*<br/>
Určuje ID pole kontrolního seznamu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Můžete vytvořit `CCheckListBox` objektu ve dvou krocích. Nejprve definujte třídu odvozenou z `CcheckListBox` a následně zavolat `Create`, která inicializuje pole kontrolního seznamu Windows a připojí ho k `CCheckListBox`. Zobrazit [CCheckListBox::CCheckListBox](#cchecklistbox) ukázku.

Když `Create` spustí, odešle Windows [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), a [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) zprávy pro ovládací prvek pole kontrolního seznamu.

Tyto zprávy jsou zpracovány ve výchozím nastavení [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), a [ongetminmaxinfo –](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) členské funkce v `CWnd` základní třídy. Chcete-li rozšířit výchozí zpracování zpráv, přidejte mapy zpráv pro odvozenou třídu a členské funkce přepsat předchozí obslužná rutina zprávy. Přepsat `OnCreate`, například k provedení potřebných inicializace pro novou třídu.

Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) do ovládacího prvku pole kontrolní seznam:

- WS_CHILD vždy

- WS_VISIBLE obvykle

- WS_DISABLED jen zřídka

- WS_VSCROLL k přidání svislý posuvník

- WS_HSCROLL k přidání vodorovný posuvník

- WS_GROUP k seskupování ovládacích prvků

- WS_TABSTOP k povolení procházení tabulátorem na tento ovládací prvek

##  <a name="drawitem"></a>  CCheckListBox::DrawItem

Volá se rozhraním při úpravě vizuálního aspektu změní vykreslovaných vlastníkem kontrolní seznam.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhým ukazatelem na [drawitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) strukturu, která obsahuje informace o typu kreslení vyžaduje.

### <a name="remarks"></a>Poznámky

`itemAction` a `itemState` členy `DRAWITEMSTRUCT` struktura definovat výkresu akci, která se má provést.

Ve výchozím nastavení tato funkce kreslení výchozí seznam zaškrtávací políčko, skládající se z seznam řetězců s výchozí velikostí zaškrtávací políčko vlevo. Velikost seznamu zaškrtávací políčko je formát určený v [vytvořit](#create).

Přepište tato členská funkce implementovat vykreslování vykreslené vlastníkem kontrolní seznam polí, které nejsou výchozím nastavení, jako kontrolní seznam polí, seznamů, které nejsou řetězce, s proměnnou výškou položek nebo pomocí zaškrtávacích políček, která nejsou na levé straně. Aplikace by měl obnovit všechny grafiky zařízení rozhraní GDI systému objekty vybrané pro zadaný kontext zobrazení v *lpDrawItemStruct* před ukončením tato členská funkce.

Není-li položky pole kontrolního seznamu stejnou výškou, kontrolního seznamu pole stylu (zadané v poli `Create`) musí být ** LBS_OWNERVARIABLE a je nutné přepsat [measureitem –](#measureitem) funkce.

##  <a name="enable"></a>  CCheckListBox::Enable

Voláním této funkce můžete povolit nebo zakázat položka pole kontrolního seznamu.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky pole kontrolního seznamu povolit.

*bEnabled*<br/>
Určuje, zda je položka povoleno nebo zakázáno.

##  <a name="getcheck"></a>  CCheckListBox::GetCheck

Načte stav zadaného zaškrtávacího políčka.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule zaškrtávacího políčka, která je součástí pole se seznamem.

### <a name="return-value"></a>Návratová hodnota

Stav zadaného zaškrtávacího políčka. V následující tabulce jsou uvedeny možné hodnoty.

|Hodnota|Popis|
|-----------|-----------------|
|BST_CHECKED|Zaškrtávací políčko.|
|BST_UNCHECKED|Zaškrtávací políčko není zaškrtnuto.|
|BST_INDETERMINATE|Stav zaškrtávacího políčka je neurčité.|

##  <a name="getcheckstyle"></a>  CCheckListBox::GetCheckStyle

Volání této funkce získáte na styl box kontrolní seznam.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Návratová hodnota

Styl ovládacího prvku zaškrtávací políčka.

### <a name="remarks"></a>Poznámky

Informace o možných stylů, najdete v části [SetCheckStyle](#setcheckstyle).

##  <a name="isenabled"></a>  CCheckListBox::IsEnabled

Voláním této funkce k určení, zda je položka povolena.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je položka povolena; jinak 0.

##  <a name="measureitem"></a>  CCheckListBox::MeasureItem

Volá se rozhraním, když se vytvoří kontrolní seznam pole se stylem jiný než výchozí.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Dlouhým ukazatelem na [measureitemstruct –](/windows/desktop/api/winuser/ns-winuser-tagmeasureitemstruct) struktury.

### <a name="remarks"></a>Poznámky

Tato členská funkce ve výchozím nastavení nemá žádný účinek. Tato členská funkce přepsání a vyplňte `MEASUREITEMSTRUCT` struktura informovat Windows dimenze položky kontrolního seznamu pole. Pokud políčko kontrolního seznamu se vytvoří s [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) styl, rozhraní volá tuto funkci člena pro každou položku v seznamu. V opačném případě tento člen je volána pouze jednou.

##  <a name="ongetcheckposition"></a>  CCheckListBox::OnGetCheckPosition

Rozhraní volá tuto funkci chcete-li získat umístění a velikost zaškrtávacího políčka v položce.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Parametry

*rectItem*<br/>
Umístění a velikost položky seznamu.

*rectCheckBox*<br/>
Výchozí umístění a velikost zaškrtávacího políčka položky.

### <a name="return-value"></a>Návratová hodnota

Umístění a velikost zaškrtávacího políčka položky.

### <a name="remarks"></a>Poznámky

Výchozí implementace vrací pouze výchozí umístění a velikost zaškrtávacího políčka (`rectCheckBox`). Ve výchozím nastavení zaškrtněte políčko je zarovnán v levém horním rohu položky a je políčko standardní velikosti. Můžou nastat případy, ve kterém chcete zaškrtávací políčka na pravé straně, nebo má zaškrtávací políčko větší nebo menší. V těchto případech přepsat `OnGetCheckPosition` Chcete-li změnit umístění zaškrtávacího políčka a velikost v rámci položky.

##  <a name="setcheck"></a>  CCheckListBox::SetCheck

Nastaví stav zadaného zaškrtávacího políčka.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index založený na nule zaškrtávacího políčka, která je součástí pole se seznamem.

*nZkontrolujte*<br/>
Stav tlačítka pro zadaný zaškrtávací políčko. Možné hodnoty v části poznámky.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny možné hodnoty pro *nZkontrolujte* parametru.

|Hodnota|Popis|
|-----------|-----------------|
|BST_CHECKED|Vyberte zaškrtávací pole zadané.|
|BST_UNCHECKED|Zrušte zaškrtnutí políčka zadané.|
|BST_INDETERMINATE|Nastavte stav zadané zaškrtávací políčko na neurčitou.<br /><br /> Tento stav je k dispozici, pokud je styl zaškrtávacího políčka BS_AUTO3STATE nebo BS_3STATE pouze. Další informace najdete v tématu [styly](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

##  <a name="setcheckstyle"></a>  CCheckListBox::SetCheckStyle

Voláním této funkce nastavit styl zaškrtávacích políček v poli kontrolní seznam.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyle*<br/>
Určuje styl zaškrtnutí políček v poli kontrolní seznam.

### <a name="remarks"></a>Poznámky

Platný styly jsou:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Informace o těchto stylů, najdete v části [styly](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Viz také

[Ukázky knihovny MFC lze kontejner TSTCON](../../visual-cpp-samples.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)
