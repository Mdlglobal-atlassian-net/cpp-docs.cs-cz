---
title: Csplitbutton – třída
ms.date: 11/19/2018
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
ms.openlocfilehash: 56c006eaa9b0c9860a973727602fd29a33d7ec43
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176625"
---
# <a name="csplitbutton-class"></a>Csplitbutton – třída

`CSplitButton` Třída představuje ovládací tlačítko rozdělení. Tlačítko rozdělení ovládání provede výchozí chování, když uživatel klikne na hlavní část tlačítka a zobrazí rozevírací nabídky po kliknutí tlačítko šipky rozevíracího seznamu.

## <a name="syntax"></a>Syntaxe

```
class CSplitButton : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSplitButton::CSplitButton](#csplitbutton)|Vytvoří `CSplitButton` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSplitButton::Create](#create)|Vytvoří ovládací tlačítko rozdělení se zadaným styly a připojí ho k aktuální `CSplitButton` objektu.|
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Nastaví rozevírací nabídky, který se zobrazí, když uživatel klepne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CSplitButton::OnDropDown](#ondropdown)|Zpracovává BCN_DROPDOWN oznámení, že systém odešle, když uživatel klepne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.|

## <a name="remarks"></a>Poznámky

`CSplitButton` Je třída odvozena z [CButton](../../mfc/reference/cbutton-class.md) třídy. Tlačítko rozdělení ovládání je ovládací prvek tlačítko, jehož styl je BS_SPLITBUTTON. Vlastní nabídky se zobrazí po kliknutí na šipku rozevíracího seznamu. Další informace najdete v tématu styly BS_SPLITBUTTON a BS_DEFSPLITBUTTON [styly](/windows/desktop/Controls/button-styles).

Následující obrázek znázorňuje dialogové okno, které obsahuje ovládací prvek stránkování a ovládací tlačítko rozdělení (1). Již bylo kliknuto na šipku rozevíracího seznamu (2) a zobrazí se podnabídky (3).

![Dialogové okno s ovládacím prvkem a stránkovacím. ](../../mfc/reference/media/splitbutton_pager.png "Dialogového okna pomocí ovládacího prvku splitbutton a stránkování.")

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

Tato třída je podporován v systému Windows Vista nebo novější.

Další požadavky pro tuto třídu jsou popsány v [vytvářet požadavky pro Windows Vista běžné ovládací prvky](../../mfc/build-requirements-for-windows-vista-common-controls.md).

##  <a name="create"></a>  CSplitButton::Create

Vytvoří ovládací tlačítko rozdělení se zadaným styly a připojí ho k aktuální `CSplitButton` objektu.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*dwStyle*|[in] Bitová kombinace (nebo) stylů pro ovládací prvek. Další informace najdete v tématu [styly](../../mfc/reference/styles-used-by-mfc.md#button-styles).|
|*Rect*|[in] Odkaz na [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) strukturu, která obsahuje umístění a velikost ovládacího prvku.|
|*pParentWnd*|[in] Nenulový ukazatel [CWnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku.|
|*nID*|[in] ID ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud tato metoda je úspěšná. v opačném případě hodnota FALSE.

##  <a name="csplitbutton"></a>  CSplitButton::CSplitButton

Vytvoří `CSplitButton` objektu. Zadejte parametry konstruktoru podnabídky, který se zobrazí, když uživatel klepne na šipku rozevíracího seznamu ovládacího prvku tlačítko rozdělení.

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nMenuId*|[in] ID prostředku z řádku nabídek.|
|*nSubMenuId*|[in] ID prostředku podnabídky.|
|*pMenu*|[in] Ukazatel [cmenu –](../../mfc/reference/cmenu-class.md) objekt, který určuje podnabídky. `CSplitButton` Objekt odstraní `CMenu` objektu a jeho přidružené HMENU při `CSplitButton` objekt dostane mimo rozsah.|

### <a name="remarks"></a>Poznámky

Použití [CSplitButton::Create](#create) metodu pro vytvoření ovládacího prvku tlačítko rozdělení a připojte ji k `CSplitButton` objektu.

##  <a name="ondropdown"></a>  CSplitButton::OnDropDown

Zpracovává BCN_DROPDOWN oznámení, že systém odešle, když uživatel klepne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pNMHDR*|[in] Ukazatel [NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr) strukturu, která obsahuje informace o [BCN_DROPDOWN](/windows/desktop/Controls/bcn-dropdown) oznámení.|
|*pResult*|[out] (Není používána a není vrácena žádná hodnota.) Návratová hodnota [BCN_DROPDOWN](/windows/desktop/Controls/bcn-dropdown) oznámení.|

### <a name="remarks"></a>Poznámky

Když uživatel klikne na rozevírací šipku na ovládací tlačítko rozdělení, systém odešle oznámení BCN_DROPDOWN zpráva, která `OnDropDown` metoda obslužné rutiny. Ale `CSplitButton` objekt nepředává BCN_DROPDOWN oznámení do ovládacího prvku, který obsahuje tlačítko rozdělení ovládání. V důsledku toho nemůže podporovat nadřazeného ovládacího prvku vlastní akce v reakci na oznámení.

Implementovat vlastní akci, která obsahuje ovládací prvek podporuje, používat [CButton](../../mfc/reference/cbutton-class.md) objektu stylu BS_SPLITBUTTON místo `CSplitButton` objektu. Potom implementujte obslužnou rutinu pro BCN_DROPDOWN oznámení v `CButton` objektu. Další informace najdete v tématu [styly](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Chcete-li implementovat vlastní akci, že tlačítko rozdělení podporuje ovládací prvek vlastní, použijte [zprávy reflexe](../../mfc/tn062-message-reflection-for-windows-controls.md). Odvodit vlastní třídu z `CSplitButton` třídy a pojmenujte ji třeba CMySplitButton. Pak přidejte následující mapování zpráv pro vaši aplikaci obsluhování BCN_DROPDOWN oznámení:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

##  <a name="setdropdownmenu"></a>  CSplitButton::SetDropDownMenu

Nastaví rozevírací nabídky, který se zobrazí, když uživatel klepne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.

```
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nMenuId*|[in] ID prostředku z řádku nabídek.|
|*nSubMenuId*|[in] ID prostředku podnabídky.|
|*pMenu*|[in] Ukazatel [cmenu –](../../mfc/reference/cmenu-class.md) objekt, který určuje podnabídky. `CSplitButton` Objekt odstraní `CMenu` objektu a jeho přidružené HMENU při `CSplitButton` objekt dostane mimo rozsah.|

### <a name="remarks"></a>Poznámky

*NMenuId* parametr identifikuje panel nabídek, což je vodorovné seznam položky panelu nabídek. *NSubMenuId* parametr je založený na nule, který identifikuje podnabídky, což je rozevírací seznam položek nabídky, které jsou spojené s každou položku nabídky panelu číslo indexu. Například Typická aplikace má nabídku, která obsahuje položky panelu nabídek "File", "Edit" a "Nápověda". Položka nabídky panelu "File" obsahuje podnabídku obsahující položky nabídky "Otevřít," "Zavřít" a "Ukončit." Po kliknutí na šipku rozevíracího seznamu ovládacího prvku tlačítko rozdělení ovládací prvek zobrazuje podnabídky zadaného řádku nabídek.

Následující obrázek znázorňuje dialogové okno, které obsahuje ovládací prvek stránkování a ovládací tlačítko rozdělení (1). Již bylo kliknuto na šipku rozevíracího seznamu (2) a zobrazí se podnabídky (3).

![Dialogové okno s ovládacím prvkem a stránkovacím. ](../../mfc/reference/media/splitbutton_pager.png "Dialogového okna pomocí ovládacího prvku splitbutton a stránkování.")

### <a name="example"></a>Příklad

První příkaz v následujícím příkladu kódu ukazuje, [CSplitButton::SetDropDownMenu](#setdropdownmenu) metody. Jsme vytvořili v nabídce sady Visual Studio prostředku editor, který automaticky pojmenuje Identifikátor řádku nabídky IDR_MENU1. *NSubMenuId* parametr, který je nula, odkazuje na pouze podnabídky panelu nabídek.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Viz také

[CSplitButton – třída](../../mfc/reference/csplitbutton-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)
