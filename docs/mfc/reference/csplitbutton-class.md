---
title: CSplitButton – třída
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
ms.openlocfilehash: d493a2d4d1c531250abc1cd60d1d3d5b79dea1b7
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916781"
---
# <a name="csplitbutton-class"></a>CSplitButton – třída

`CSplitButton` Třída reprezentuje ovládací prvek tlačítko rozdělení. Ovládací prvek tlačítko rozdělení provede výchozí chování, když uživatel klikne na hlavní část tlačítka, a když uživatel klikne na šipku rozevíracího seznamu na tlačítku, zobrazí rozevírací nabídku.

## <a name="syntax"></a>Syntaxe

```
class CSplitButton : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSplitButton::CSplitButton](#csplitbutton)|`CSplitButton` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSplitButton:: Create](#create)|Vytvoří ovládací prvek tlačítko rozdělení se zadanými styly a připojí ho k aktuálnímu `CSplitButton` objektu.|
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Nastaví rozevírací nabídku, která se zobrazí, když uživatel klikne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.|

### <a name="protected-methods"></a>Chráněné metody

|Name|Popis|
|----------|-----------------|
|[CSplitButton:: DropDown – rozevírací seznam](#ondropdown)|Zpracovává oznámení BCN_DROPDOWN, které systém odesílá, když uživatel klikne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.|

## <a name="remarks"></a>Poznámky

Třída je odvozena od třídy [CButton.](../../mfc/reference/cbutton-class.md) `CSplitButton` Tlačítko rozdělení je ovládací prvek tlačítko, jehož styl je BS_SPLITBUTTON. Pokud uživatel klikne na šipku rozevíracího seznamu, zobrazí se vlastní nabídka. Další informace naleznete v tématu styly BS_SPLITBUTTON a BS_DEFSPLITBUTTON v [stylech tlačítek](/windows/desktop/Controls/button-styles).

Následující obrázek znázorňuje dialogové okno, které obsahuje ovládací prvek stránkování a ovládací prvek tlačítko rozdělení (1). Na šipku rozevíracího seznamu (2) již bylo kliknuto a zobrazí se podnabídka (3).

![Dialog s ovládacím prvkem SplitButton a pager.](../../mfc/reference/media/splitbutton_pager.png "Dialog s ovládacím prvkem SplitButton a pager.")

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn. h

Tato třída je podporována v systému Windows Vista a novějších.

Další požadavky pro tuto třídu jsou popsány v tématu [požadavky na sestavení pro běžné ovládací prvky systému Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

##  <a name="create"></a>CSplitButton:: Create

Vytvoří ovládací prvek tlačítko rozdělení se zadanými styly a připojí ho k aktuálnímu `CSplitButton` objektu.

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
|*dwStyle*|pro Bitových kombinací (nebo) stylů, které mají být použity pro ovládací prvek. Další informace naleznete v tématu [styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).|
|*OBD*|pro Odkaz na strukturu [Rect](/previous-versions/dd162897\(v=vs.85\)) , která obsahuje pozici a velikost ovládacího prvku.|
|*pParentWnd*|pro Ukazatel bez hodnoty null na objekt [CWnd](../../mfc/reference/cwnd-class.md) , který je nadřazeným oknem ovládacího prvku.|
|*nID*|pro ID ovládacího prvku|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; v opačném případě FALSE.

##  <a name="csplitbutton"></a>CSplitButton::CSplitButton

`CSplitButton` Vytvoří objekt. Parametry konstruktoru určují podnabídku, která se zobrazí, když uživatel klikne na šipku rozevíracího seznamu ovládacího prvku tlačítko rozdělení.

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
|*nMenuId*|pro ID prostředku řádku nabídek|
|*nSubMenuId*|pro ID prostředku podnabídky|
|*pMenu*|pro Ukazatel na objekt [CMenu –](../../mfc/reference/cmenu-class.md) , který určuje podnabídku. Objekt odstraní objekt a jeho přidruženou HMENU, když se `CSplitButton` objekt dostane mimo rozsah. `CMenu` `CSplitButton`|

### <a name="remarks"></a>Poznámky

Použijte metodu [CSplitButton:: Create](#create) k vytvoření ovládacího prvku tlačítko rozdělení a připojte jej k `CSplitButton` objektu.

##  <a name="ondropdown"></a>CSplitButton:: DropDown – rozevírací seznam

Zpracovává oznámení BCN_DROPDOWN, které systém odesílá, když uživatel klikne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pNMHDR*|pro Ukazatel na strukturu [NMHDR](/windows/desktop/api/richedit/ns-richedit-nmhdr) , která obsahuje informace o oznámení [BCN_DROPDOWN](/windows/desktop/Controls/bcn-dropdown) .|
|*pResult*|mimo (Nepoužívá se, není vrácena žádná hodnota.) Návratová hodnota oznámení [BCN_DROPDOWN](/windows/desktop/Controls/bcn-dropdown)|

### <a name="remarks"></a>Poznámky

Když uživatel klikne na šipku rozevíracího seznamu u ovládacího prvku tlačítko rozdělení, systém pošle zprávu s oznámením BCN_DROPDOWN, `OnDropDown` kterou metoda zpracovává. `CSplitButton` Objekt však nepřepošle oznámení BCN_DROPDOWN ovládacímu prvku, který obsahuje ovládací prvek tlačítko rozdělení. V důsledku toho nadřazený ovládací prvek nemůže podporovat vlastní akci v reakci na oznámení.

Chcete-li implementovat vlastní akci, kterou obsahuje ovládací prvek, použijte objekt [CButton](../../mfc/reference/cbutton-class.md) se stylem BS_SPLITBUTTON namísto `CSplitButton` objektu. Potom Implementujte obslužnou rutinu pro BCN_DROPDOWN oznámení v `CButton` objektu. Další informace naleznete v tématu [styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Chcete-li implementovat vlastní akci, kterou vlastní ovládací prvek tlačítko rozdělení podporuje, použijte reflexi [zprávy](../../mfc/tn062-message-reflection-for-windows-controls.md). Odvodit vlastní třídu z `CSplitButton` třídy a pojmenujte ji, například CMySplitButton. Potom do aplikace přidejte následující mapu zpráv pro zpracování oznámení BCN_DROPDOWN:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

##  <a name="setdropdownmenu"></a>CSplitButton::SetDropDownMenu

Nastaví rozevírací nabídku, která se zobrazí, když uživatel klikne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítko rozdělení.

```
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nMenuId*|pro ID prostředku řádku nabídek|
|*nSubMenuId*|pro ID prostředku podnabídky|
|*pMenu*|pro Ukazatel na objekt [CMenu –](../../mfc/reference/cmenu-class.md) , který určuje podnabídku. Objekt odstraní objekt a jeho přidruženou HMENU, když se `CSplitButton` objekt dostane mimo rozsah. `CMenu` `CSplitButton`|

### <a name="remarks"></a>Poznámky

Parametr *nMenuId* identifikuje panel nabídek, což je vodorovný seznam položek panelu nabídek. Parametr *nSubMenuId* je číslo indexu založeného na nule, které identifikuje podnabídku, což je rozevírací seznam položek nabídky přidružených k jednotlivým položkám panelu nabídek. Například Typická aplikace má nabídku, která obsahuje položky panelu nabídek, "soubor", "Upravit" a "nápovědu". Položka panelu nabídky "soubor" obsahuje podnabídku, která obsahuje položky nabídky "otevřít", "Zavřít" a "Exit". Při kliknutí na šipku rozevíracího seznamu ovládacího prvku rozdělení na tlačítko zobrazí ovládací prvek zadanou podnabídku, nikoli řádek nabídek.

Následující obrázek znázorňuje dialogové okno, které obsahuje ovládací prvek stránkování a ovládací prvek tlačítko rozdělení (1). Na šipku rozevíracího seznamu (2) již bylo kliknuto a zobrazí se podnabídka (3).

![Dialog s ovládacím prvkem SplitButton a pager.](../../mfc/reference/media/splitbutton_pager.png "Dialog s ovládacím prvkem SplitButton a pager.")

### <a name="example"></a>Příklad

První příkaz v následujícím příkladu kódu ukazuje metodu [CSplitButton:: SetDropDownMenu](#setdropdownmenu) . Nabídku jsme vytvořili pomocí editoru prostředků sady Visual Studio, který se automaticky jmenuje ID řádku nabídky IDR_MENU1. Parametr *nSubMenuId* , který je nula, odkazuje pouze na podnabídku panelu nabídek.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Viz také:

[CSplitButton – třída](../../mfc/reference/csplitbutton-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)
