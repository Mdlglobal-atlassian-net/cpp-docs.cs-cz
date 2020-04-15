---
title: Třída CSplitButton
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
ms.openlocfilehash: 0b54324c3c5503182add15a3dd0a9ecd07c24b18
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318116"
---
# <a name="csplitbutton-class"></a>Třída CSplitButton

Třída `CSplitButton` představuje ovládací prvek rozdělené tlačítko. Ovládací prvek rozděleného tlačítka provádí výchozí chování, když uživatel klepne na hlavní část tlačítka a zobrazí rozevírací nabídku, když uživatel klepne na šipku rozevíracího seznamu tlačítka.

## <a name="syntax"></a>Syntaxe

```
class CSplitButton : public CButton
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSplitButton::CSplitButton](#csplitbutton)|Vytvoří `CSplitButton` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSplitButton::Vytvořit](#create)|Vytvoří ovládací prvek tlačítka rozdělení se zadanými `CSplitButton` styly a připojí ho k aktuálnímu objektu.|
|[CSplitButton::Nabídka SetDropDownMenu](#setdropdownmenu)|Nastaví rozevírací nabídku, která se zobrazí, když uživatel klepne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítka rozdělení.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSplitButton::Dropdown](#ondropdown)|Zpracovává BCN_DROPDOWN oznámení, které systém odešle, když uživatel klepne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítka rozdělení.|

## <a name="remarks"></a>Poznámky

Třída `CSplitButton` je odvozena z třídy [CButton.](../../mfc/reference/cbutton-class.md) Ovládací prvek rozdělené tlačítko je ovládací prvek tlačítka, jehož styl je BS_SPLITBUTTON. Zobrazí vlastní nabídku, když uživatel klepne na šipku rozevíracího seznamu. Další informace naleznete v BS_SPLITBUTTON a BS_DEFSPLITBUTTON stylech ve [stylech tlačítek](/windows/win32/Controls/button-styles).

Následující obrázek znázorňuje dialogové okno, které obsahuje ovládací prvek pager a (1) ovládací prvek tlačítka rozdělení. Na (2) rozevírací šipku již bylo kliknuto a zobrazí se podnabídka (3).

![Dialog s ovládacím prvkem splitbutton a pager.](../../mfc/reference/media/splitbutton_pager.png "Dialog s ovládacím prvkem splitbutton a pager.")

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxcmn.h

Tato třída je podporována v systému Windows Vista a novějších.

Další požadavky pro tuto třídu jsou popsány v [části Požadavky na sestavení pro běžné ovládací prvky systému Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md).

## <a name="csplitbuttoncreate"></a><a name="create"></a>CSplitButton::Vytvořit

Vytvoří ovládací prvek tlačítka rozdělení se zadanými `CSplitButton` styly a připojí ho k aktuálnímu objektu.

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
|*dwStyl*|[v] Bitová kombinace (OR) stylů, které mají být použity na ovládací prvek. Další informace naleznete v [tématu Styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).|
|*Rect*|[v] Odkaz na [rect](/previous-versions/dd162897\(v=vs.85\)) strukturu, která obsahuje umístění a velikost ovládacího prvku.|
|*pParentWnd*|[v] Nenulový ukazatel na [cwnd](../../mfc/reference/cwnd-class.md) objekt, který je nadřazené okno ovládacího prvku.|
|*Nid*|[v] ID ovládacího prvku.|

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je tato metoda úspěšná; jinak NEPRAVDA.

## <a name="csplitbuttoncsplitbutton"></a><a name="csplitbutton"></a>CSplitButton::CSplitButton

Vytvoří `CSplitButton` objekt. Parametry konstruktoru určují podnabídku, která se zobrazí, když uživatel klepne na šipku rozevíracího seznamu ovládacího prvku rozdělit.

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
|*nID menu*|[v] ID prostředku panelu nabídek.|
|*nPodmenuId*|[v] ID prostředku podnabídky.|
|*pNabídka*|[v] Ukazatel na objekt [CMenu,](../../mfc/reference/cmenu-class.md) který určuje podnabídku. Objekt `CSplitButton` odstraní `CMenu` objekt a jeho přidružené HMENU při objektu `CSplitButton` přejde mimo rozsah.|

### <a name="remarks"></a>Poznámky

Pomocí [metody CSplitButton::Create](#create) vytvořte ovládací prvek tlačítka `CSplitButton` rozdělení a připojte jej k objektu.

## <a name="csplitbuttonondropdown"></a><a name="ondropdown"></a>CSplitButton::Dropdown

Zpracovává BCN_DROPDOWN oznámení, které systém odešle, když uživatel klepne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítka rozdělení.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*pNMHDR*|[v] Ukazatel na strukturu [NMHDR,](/windows/win32/api/richedit/ns-richedit-nmhdr) která obsahuje informace o [oznámení BCN_DROPDOWN.](/windows/win32/Controls/bcn-dropdown)|
|*výsledek*|[out] (Nepoužívá se; není vrácena žádná hodnota.) Vrácená hodnota [oznámení BCN_DROPDOWN.](/windows/win32/Controls/bcn-dropdown)|

### <a name="remarks"></a>Poznámky

Když uživatel klepne na šipku rozevíracího seznamu na ovládacím prvku `OnDropDown` tlačítka rozdělení, systém odešle BCN_DROPDOWN oznámení, které metoda zpracovává. `CSplitButton` Objekt však není předá oznámení BCN_DROPDOWN ovládacího prvku, který obsahuje ovládací prvek rozdělit tlačítko. V důsledku toho obsahující ovládací prvek nemůže podporovat vlastní akci v reakci na oznámení.

Chcete-li implementovat vlastní akci, kterou podporuje ovládací prvek obsahující, použijte `CSplitButton` objekt [CButton](../../mfc/reference/cbutton-class.md) se stylem BS_SPLITBUTTON místo objektu. Potom implementujte obslužnou `CButton` rutinu pro oznámení BCN_DROPDOWN v objektu. Další informace naleznete v [tématu Styly tlačítek](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Chcete-li implementovat vlastní akci, kterou podporuje samotný ovládací prvek tlačítka rozdělení, použijte [reflexe zprávy](../../mfc/tn062-message-reflection-for-windows-controls.md). Odvodit vlastní `CSplitButton` třídu z třídy a pojmenujte ji, například CMySplitButton. Pak přidejte do aplikace následující mapu zpráv, která bude zpracovávat oznámení BCN_DROPDOWN:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

## <a name="csplitbuttonsetdropdownmenu"></a><a name="setdropdownmenu"></a>CSplitButton::Nabídka SetDropDownMenu

Nastaví rozevírací nabídku, která se zobrazí, když uživatel klepne na šipku rozevíracího seznamu aktuálního ovládacího prvku tlačítka rozdělení.

```
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*nID menu*|[v] ID prostředku panelu nabídek.|
|*nPodmenuId*|[v] ID prostředku podnabídky.|
|*pNabídka*|[v] Ukazatel na objekt [CMenu,](../../mfc/reference/cmenu-class.md) který určuje podnabídku. Objekt `CSplitButton` odstraní `CMenu` objekt a jeho přidružené HMENU při objektu `CSplitButton` přejde mimo rozsah.|

### <a name="remarks"></a>Poznámky

Parametr *nMenuId* identifikuje řádek nabídek, což je vodorovný seznam položek řádku nabídek. Parametr *nSubMenuId* je číslo indexu založené na nule, které identifikuje podnabídku, což je rozevírací seznam položek nabídky přidružených ke každé položce řádku nabídek. Například typická aplikace má nabídku, která obsahuje položky panelu nabídek, "Soubor", "Upravit" a "Nápověda". Položka řádku nabídky Soubor obsahuje podnabídku, která obsahuje položky nabídky "Otevřít", "Zavřít" a "Ukončit". Po klepnutí na šipku rozevíracího seznamu ovládacího prvku rozděleného tlačítka ovládací prvek zobrazí zadanou podnabídku, nikoli řádek nabídek.

Následující obrázek znázorňuje dialogové okno, které obsahuje ovládací prvek pager a (1) ovládací prvek tlačítka rozdělení. Na (2) rozevírací šipku již bylo kliknuto a zobrazí se podnabídka (3).

![Dialog s ovládacím prvkem splitbutton a pager.](../../mfc/reference/media/splitbutton_pager.png "Dialog s ovládacím prvkem splitbutton a pager.")

### <a name="example"></a>Příklad

První příkaz v následujícím příkladu kódu ukazuje metodu [CSplitButton::SetDropDownMenu.](#setdropdownmenu) Vytvořili jsme nabídku s Editor prostředků Sady Visual Studio, který automaticky pojmenoval ID řádku nabídek, IDR_MENU1. Parametr *nSubMenuId,* který je nulový, odkazuje na jedinou podnabídku řádku nabídek.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Viz také

[Třída CSplitButton](../../mfc/reference/csplitbutton-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CButton – třída](../../mfc/reference/cbutton-class.md)
