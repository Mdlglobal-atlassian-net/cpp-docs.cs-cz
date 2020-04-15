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
ms.openlocfilehash: 8ca8d3b2cb4ce3c5b070d883e0a418ebec3665b1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352373"
---
# <a name="cchecklistbox-class"></a>CCheckListBox – třída

Poskytuje funkce zaškrtávacího seznamu systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CCheckListBox : public CListBox
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Vytvoří `CCheckListBox` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CCheckListBox::Vytvořit](#create)|Vytvoří zaškrtávací seznam systému Windows a připojí jej k objektu. `CCheckListBox`|
|[CCheckListBox::DrawItem](#drawitem)|Volat rámci při změně vizuální aspekt seznamu vlastníka kreslit.|
|[CCheckListBox::Povolit](#enable)|Povolí nebo zakáže položku zaškrtávacího seznamu.|
|[CCheckListBox::GetCheck](#getcheck)|Získá stav zaškrtávacího políčka položky.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Získá styl zaškrtávacích políček ovládacího prvku.|
|[CCheckListBox::Je povoleno](#isenabled)|Určuje, zda je položka povolena.|
|[CCheckListBox::MeasureItem](#measureitem)|Volat rámci při vytvoření seznamu se stylem kreslení vlastníka.|
|[CCheckListBox::OnGetCheckPozice](#ongetcheckposition)|Volat rámci získat pozici položky zaškrtávací políčko.|
|[CCheckListBox::SetCheck](#setcheck)|Nastaví stav zaškrtávacího políčka položky.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Nastaví styl zaškrtávacích políček ovládacího prvku.|

## <a name="remarks"></a>Poznámky

V zaškrtávací políčko se zobrazí seznam položek, například názvů souborů. Každá položka v seznamu má vedle sebe zaškrtávací políčko, které může uživatel zkontrolovat nebo vymazat.

`CCheckListBox`je pouze pro ovládací prvky nakreslené vlastníkem, protože seznam obsahuje více než textové řetězce. V nejjednodušším případě zaškrtávací políčko obsahuje textové řetězce a zaškrtávací políčka, ale nemusíte mít text vůbec. Můžete mít například seznam malých bitmap se zaškrtávacím políčkem vedle každé položky.

Chcete-li vytvořit vlastní zaškrtávací `CCheckListBox`seznam, musíte odvodit vlastní třídu z aplikace . Chcete-li odvodit vlastní třídu, napište `Create`konstruktor pro odvozenou třídu a pak volejte .

Pokud chcete zpracovat zprávy oznámení systému Windows odeslané seznamem jeho nadřazené (obvykle třídy odvozené z [CDialog](../../mfc/reference/cdialog-class.md)), přidejte položku mapy zprávy a členskou funkci obslužné rutiny zprávy do nadřazené třídy pro každou zprávu.

Každá položka mapy zpráv má následující podobu:

**ON\_**_Oznámení_ **(** _id_, _memberFxn_ **)**

kde `id` určuje ID podřízeného okna ovládacího `memberFxn` prvku odesílajícího oznámení a je název nadřazené členské funkce, kterou jste napsali pro zpracování oznámení.

Prototyp funkce nadřazeného objektu je následující:

`afx_msg void memberFxn();`

Existuje pouze jedna položka mapy zpráv, která se `CCheckListBox` konkrétně jedná o (ale viz také položky mapy zpráv pro [CListBox](../../mfc/reference/clistbox-class.md)):

- ON_CLBN_CHKCHANGE Uživatel změnil stav zaškrtávacího políčka položky.

Pokud je políčko zaškrtávacího seznamu výchozím zaškrtávaným políčkem (seznam řetězců se zaškrtávacími políčky výchozí velikosti nalevo od každého z nich), můžete k nakreslení zaškrtávacího seznamu použít výchozí pole [CCheckListBox::DrawItem.](#drawitem) V opačném případě musíte přepsat funkci [CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) a [CCheckListBox::DrawItem](#drawitem) a [CCheckListBox::MeasureItem.](#measureitem)

Zaškrtávací políčko můžete vytvořit buď ze šablony dialogového okna, nebo přímo v kódu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cchecklistboxcchecklistbox"></a><a name="cchecklistbox"></a>CCheckListBox::CCheckListBox

Vytvoří `CCheckListBox` objekt.

```
CCheckListBox();
```

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CCheckListBox` dvou krocích. Nejprve definujte třídu odvozenou z `CCheckListBox`, pak volejte `Create`, která inicializuje zaškrtávací seznam systému Windows a připojí jej k objektu. `CCheckListBox`

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

## <a name="cchecklistboxcreate"></a><a name="create"></a>CCheckListBox::Vytvořit

Vytvoří zaškrtávací seznam systému Windows a připojí jej k objektu. `CCheckListBox`

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*dwStyl*<br/>
Určuje styl zaškrtávacího seznamu. Styl musí být LBS_HASSTRINGS a musí být buď LBS_OWNERDRAWFIXED (všechny položky v seznamu mají stejnou výšku) nebo LBS_OWNERDRAWVARIABLE (položky v seznamu mají různé výšky). Tento styl lze kombinovat s jinými [styly seznamu](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) kromě LBS_USETABSTOPS.

*Rect*<br/>
Určuje velikost a umístění zaškrtávacího seznamu. Může být buď [CRect](../../atl-mfc-shared/reference/crect-class.md) objekt nebo [RECT](/windows/win32/api/windef/ns-windef-rect) struktury.

*pParentWnd*<br/>
Určuje nadřazené okno zaškrtávacího seznamu (obvykle `CDialog` objekt). Nesmí být null.

*Nid*<br/>
Určuje ID ovládacího prvku zaškrtávacího seznamu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Objekt vytvoříte ve `CCheckListBox` dvou krocích. Nejprve definujte třídu `CcheckListBox` odvozenou `Create`z a pak volejte , která inicializuje `CCheckListBox`zaškrtávací seznam systému Windows a připojí jej k . Viz [CCheckListBox::CCheckListBox](#cchecklistbox) pro ukázku.

Při `Create` spuštění odesílá systém Windows zprávy [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)a [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) ovládacímu prvku zaškrtávacího seznamu.

Tyto zprávy jsou ve výchozím nastavení zpracovány členy [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)a [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) v `CWnd` základní třídě. Chcete-li rozšířit výchozí zpracování zpráv, přidejte mapu zpráv do odvozené třídy a přepište předchozí členské funkce obslužné rutiny zprávy. Přepište `OnCreate`, například provést potřebnou inicializaci pro novou třídu.

Použijte následující [styly oken](../../mfc/reference/styles-used-by-mfc.md#window-styles) u ovládacího prvku zaškrtávacího seznamu:

- WS_CHILD vždy

- WS_VISIBLE Obvykle

- WS_DISABLED Zřídka

- WS_VSCROLL Přidání svislého posuvníku

- WS_HSCROLL Přidání vodorovného posuvníku

- WS_GROUP Chcete-li seskupit ovládací prvky

- WS_TABSTOP Povolení tabulátoru k tomuto ovládacímu prvku

## <a name="cchecklistboxdrawitem"></a><a name="drawitem"></a>CCheckListBox::DrawItem

Volat rámci při změně vizuální aspekt zaškrtávacího seznamu nakreslené vlastníka.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parametry

*lpDrawItemStruct*<br/>
Dlouhý ukazatel na strukturu [DRAWITEMSTRUCT,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) která obsahuje informace o požadovaném typu výkresu.

### <a name="remarks"></a>Poznámky

A `itemAction` `itemState` členové `DRAWITEMSTRUCT` struktury definují akci kreslení, která má být provedena.

Ve výchozím nastavení tato funkce nakreslí výchozí seznam zaškrtávacích potýkajících s tuze, která se skládá ze seznamu řetězců, z nichž každý má zaškrtávací políčko výchozí velikosti vlevo. Velikost seznamu zaškrtávacího políčka je uvedena v poli [Vytvořit](#create).

Přepište tuto členská funkci implementovat kreslení zaškrtávacích polí vlastníka draw, které nejsou výchozí, jako jsou například zaškrtávací seznamy se seznamy, které nejsou řetězce, s položkami s proměnnou výškou nebo se zaškrtávacími políčky, které nejsou na levé straně. Aplikace by měla obnovit všechny objekty rozhraní grafického zařízení (GDI) vybrané pro kontext zobrazení dodaný v *lpDrawItemStruct* před ukončením této členské funkce.

Pokud položky zaškrtávacího seznamu nejsou všechny stejné `Create`výšky, styl zaškrtávacího seznamu (zadaný v ) musí být **LBS_OWNERVARIABLE**a je nutné přepsat funkci [MeasureItem.](#measureitem)

## <a name="cchecklistboxenable"></a><a name="enable"></a>CCheckListBox::Povolit

Volánítéto funkce chcete-li povolit nebo zakázat položku zaškrtávacího seznamu.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky zaškrtávacího seznamu, která má být povolena.

*bPovoleno*<br/>
Určuje, zda je položka povolena nebo zakázána.

## <a name="cchecklistboxgetcheck"></a><a name="getcheck"></a>CCheckListBox::GetCheck

Načte stav zadaného zaškrtávacího políčka.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nulový index zaškrtávacího políčka, které je obsaženo v seznamu.

### <a name="return-value"></a>Návratová hodnota

Stav zadaného zaškrtávacího políčka. V následující tabulce jsou uvedeny možné hodnoty.

|Hodnota|Popis|
|-----------|-----------------|
|BST_CHECKED|Zaškrtávací políčko je zaškrtnuto.|
|BST_UNCHECKED|Zaškrtávací políčko není zaškrtnuto.|
|BST_INDETERMINATE|Stav zaškrtávacího políčka je neurčitý.|

## <a name="cchecklistboxgetcheckstyle"></a><a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle

Volání této funkce získat styl zaškrtávacího seznamu.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Návratová hodnota

Styl zaškrtávacích políček ovládacího prvku.

### <a name="remarks"></a>Poznámky

Informace o možných stylech naleznete v tématu [SetCheckStyle](#setcheckstyle).

## <a name="cchecklistboxisenabled"></a><a name="isenabled"></a>CCheckListBox::Je povoleno

Volání této funkce k určení, zda je povolena položka.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Index položky.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je položka povolena; jinak 0.

## <a name="cchecklistboxmeasureitem"></a><a name="measureitem"></a>CCheckListBox::MeasureItem

Volat rámci při vytvoření zaškrtávacího seznamu s nevýchozí styl.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parametry

*lpMeasureItemStruct*<br/>
Dlouhý ukazatel na strukturu [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení tato členská funkce neprovede žádné. Přepsat tuto člennou funkci `MEASUREITEMSTRUCT` a vyplnit strukturu informovat Windows o rozměrech položek zaškrtávacího seznamu. Pokud je zaškrtávací seznam vytvořen s [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) stylem, framework volá tuto členskou funkci pro každou položku v seznamu. V opačném případě se tento člen nazývá pouze jednou.

## <a name="cchecklistboxongetcheckposition"></a><a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPozice

Rozhraní Framework volá tuto funkci získat pozici a velikost zaškrtávacího políčka v položce.

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

Výchozí implementace vrátí pouze výchozí pozici a velikost`rectCheckBox`zaškrtávacího políčka ( ). Ve výchozím nastavení je zaškrtávací políčko zarovnáno v levém horním rohu položky a jedná se o standardní velikost zaškrtávacího políčka. Mohou existovat případy, kdy chcete zaškrtávací políčka vpravo nebo chcete větší nebo menší zaškrtávací políčko. V těchto případech `OnGetCheckPosition` přepište změnit umístění zaškrtávacího políčka a velikost v rámci položky.

## <a name="cchecklistboxsetcheck"></a><a name="setcheck"></a>CCheckListBox::SetCheck

Nastaví stav zadaného zaškrtávacího políčka.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Parametry

*nIndex*<br/>
Nulový index zaškrtávacího políčka, které je obsaženo v seznamu.

*nKontrola*<br/>
Stav tlačítka pro zadané zaškrtávací políčko. Možné hodnoty naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny možné hodnoty parametru *nCheck.*

|Hodnota|Popis|
|-----------|-----------------|
|BST_CHECKED|Zaškrtněte zadaný zaškrtávací políčko.|
|BST_UNCHECKED|Zrušte zaškrtnutí zadaného políčka.|
|BST_INDETERMINATE|Nastavte zadaný stav zaškrtávacího políčka na neurčitý stav.<br /><br /> Tento stav je k dispozici pouze v případě, že styl zaškrtávacího políčka je BS_AUTO3STATE nebo BS_3STATE. Další informace naleznete v [tématu Styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

## <a name="cchecklistboxsetcheckstyle"></a><a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle

Voláním této funkce nastavte styl zaškrtávacích políček v zaškrtávacím seznamu.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Parametry

*nStyl*<br/>
Určuje styl zaškrtávacích políček v zaškrtávacím seznamu.

### <a name="remarks"></a>Poznámky

Platné styly jsou:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Informace o těchto stylech naleznete v [tématu Styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CListBox – třída](../../mfc/reference/clistbox-class.md)
