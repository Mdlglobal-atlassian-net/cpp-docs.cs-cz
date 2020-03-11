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
ms.openlocfilehash: af84c5239a9cb3cbddb1ab4f0230e5b1a3373573
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883617"
---
# <a name="cdialogbar-class"></a>CDialogBar – třída

Poskytuje funkce nemodálního dialogového okna systému Windows v ovládacím panelu.

## <a name="syntax"></a>Syntaxe

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CDialogBar:: CDialogBar](#cdialogbar)|Vytvoří objekt `CDialogBar`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CDialogBar:: Create](#create)|Vytvoří panel dialogového okna Windows a připojí ho k objektu `CDialogBar`.|

## <a name="remarks"></a>Poznámky

Dialogové okno se podobá dialogovému oknu v tom, že obsahuje standardní ovládací prvky systému Windows, které uživatel může kartu mezi. Další podobností je, že vytvoříte šablonu dialogu, která představuje panel dialogového okna.

Vytvoření a použití panelu dialogového okna se podobá vytvoření a použití objektu `CFormView`. Nejprve pomocí [editoru dialogového okna](../../windows/dialog-editor.md) definujte šablonu dialogového okna se stylem WS_CHILD a žádný jiný styl. Šablona nesmí mít WS_VISIBLE stylu. V kódu aplikace zavolejte konstruktor pro vytvoření objektu `CDialogBar` a potom zavolejte `Create` a vytvořte okno dialogového okna a připojte ho k objektu `CDialogBar`.

Další informace o `CDialogBar`naleznete v části [dialogová okna](../../mfc/dialog-bars.md) článku a v [technické poznámce 31](../../mfc/tn031-control-bars.md), ovládací panely.

> [!NOTE]
>  V aktuální verzi `CDialogBar` objekt nemůže hostovat ovládací prvky model Windows Forms. Další informace o ovládacích prvcích model Windows Forms v vizuálu C++naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar –](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext. h

##  <a name="cdialogbar"></a>CDialogBar:: CDialogBar

Vytvoří objekt `CDialogBar`.

```
CDialogBar();
```

##  <a name="create"></a>CDialogBar:: Create

Načte šablonu prostředků dialogového okna určenou `lpszTemplateName` nebo `nIDTemplate`, vytvoří okno dialogového okna, nastaví jeho styl a přidruží ho k objektu `CDialogBar`.

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
Ukazatel na nadřazený objekt `CWnd`.

*lpszTemplateName*<br/>
Ukazatel na název šablony prostředku dialogového okna `CDialogBar`ového objektu.

*nStyle*<br/>
Styl panelu nástrojů Podporovány jsou další styly panelů nástrojů:

- Ovládací panel CBRS_TOP je v horní části okna rámce.

- Ovládací panel CBRS_BOTTOM na konci okna rámce.

- Ovládací panel CBRS_NOALIGN není přemístění při změně velikosti nadřazeného objektu.

- Ovládací panel CBRS_TOOLTIPS zobrazí popisy nástrojů.

- Ovládací panel CBRS_SIZE_DYNAMIC je dynamický.

- Je opraven ovládací panel CBRS_SIZE_FIXED.

- Ovládací panel CBRS_FLOATING je plovoucí.

- CBRS_FLYBY stavového řádku se zobrazí informace o tlačítku.

- Uživateli se nezobrazí ovládací panel CBRS_HIDE_INPLACE.

*nID*<br/>
ID ovládacího prvku panelu dialogového okna

*nIDTemplate*<br/>
ID prostředku šablony dialogového okna `CDialogBar`ho objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Zadáte-li styl zarovnání CBRS_TOP nebo CBRS_BOTTOM, Šířka panelu dialogového okna je to, že okno rámce a jeho výška je to, že se jedná o zdroj určený parametrem *nIDTemplate*. Zadáte-li styl zarovnání CBRS_LEFT nebo CBRS_RIGHT, výška panelu dialogového okna je to, že okno rámce a jeho šířka je to pro prostředek určený parametrem *nIDTemplate*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Viz také

[CTRLBARS Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)
