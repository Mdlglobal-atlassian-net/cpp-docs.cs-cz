---
title: CDialogBar – třída
ms.date: 11/04/2016
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
ms.openlocfilehash: cf9a2658807959108b3bb0af672d4c1835b58bc5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375666"
---
# <a name="cdialogbar-class"></a>CDialogBar – třída

Poskytuje funkce dialogového okna Windows bezma v ovládacím panelu.

## <a name="syntax"></a>Syntaxe

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CDialogBar::cdialogbar](#cdialogbar)|Vytvoří `CDialogBar` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CDialogBar::Vytvořit](#create)|Vytvoří dialogový panel systému Windows `CDialogBar` a připojí jej k objektu.|

## <a name="remarks"></a>Poznámky

Dialogové okno se podobá dialogovému oknu v tom, že obsahuje standardní ovládací prvky systému Windows, mezi nimiž může uživatel tabulátor. Další podobností je vytvoření šablony dialogu představující dialogový panel.

Vytvoření a použití dialogového panelu je `CFormView` podobné vytváření a používání objektu. Nejprve pomocí [editoru dialogů](../../windows/dialog-editor.md) definujte šablonu dialogu se stylem WS_CHILD a žádný jiný styl. Šablona nesmí mít styl WS_VISIBLE. V kódu aplikace zavolejte konstruktoru `CDialogBar` k vytvoření `Create` objektu, pak volání k vytvoření `CDialogBar` dialogového okna a připojit k objektu.

Další informace `CDialogBar`naleznete v článku [Dialogová panely](../../mfc/dialog-bars.md) a [technická poznámka 31](../../mfc/tn031-control-bars.md), Ovládací panely.

> [!NOTE]
> V aktuální verzi `CDialogBar` objekt nemůže být hostitelem ovládacích prvků windows forms. Další informace o ovládacích prvcích systému Windows Forms v jazyce Visual C++ naleznete [v tématu Použití uživatelského ovládacího prvku formuláře systému Windows v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Ovládací panel CControl](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

## <a name="cdialogbarcdialogbar"></a><a name="cdialogbar"></a>CDialogBar::cdialogbar

Vytvoří `CDialogBar` objekt.

```
CDialogBar();
```

## <a name="cdialogbarcreate"></a><a name="create"></a>CDialogBar::Vytvořit

Načte šablonu prostředku dialogového okna určenou `lpszTemplateName` nebo `nIDTemplate`, vytvoří okno dialogového panelu, nastaví jeho styl a přidruží k objektu. `CDialogBar`

```
virtual BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

virtual BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Ukazatel na nadřazený `CWnd` objekt.

*lpszTemplateName*<br/>
Ukazatel na název šablony `CDialogBar` prostředku dialogového okna objektu.

*nStyl*<br/>
Styl panelu nástrojů. Další podporované styly panelu nástrojů jsou:

- CBRS_TOP Ovládací panel je v horní části okna rámce.

- CBRS_BOTTOM Ovládací panel je v dolní části okna rámce.

- CBRS_NOALIGN Ovládací panel není přemístěn, když je velikost nadřazené velikosti.

- CBRS_TOOLTIPS Ovládací panel zobrazuje tipy nástrojů.

- CBRS_SIZE_DYNAMIC Ovládací panel je dynamický.

- CBRS_SIZE_FIXED Ovládací lišta je pevná.

- CBRS_FLOATING Ovládací panel je plovoucí.

- CBRS_FLYBY stavový řádek zobrazuje informace o tlačítku.

- CBRS_HIDE_INPLACE Ovládací panel se uživateli nezobrazí.

*Nid*<br/>
ID ovládacího prvku dialogového panelu.

*nIDŠablona*<br/>
ID prostředku šablony `CDialogBar` dialogového okna objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud zadáte styl zarovnání CBRS_TOP nebo CBRS_BOTTOM, šířka dialogového pruhu je šířka okna rámečku a jeho výška je výška prostředku určeného *nIDTemplate*. Pokud zadáte CBRS_LEFT nebo CBRS_RIGHT stylu zarovnání, výška dialogového pruhu je výška okna rámečku a jeho šířka je šířka prostředku určeného *nIDTemplate*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Viz také

[Ukázka knihovny MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)
