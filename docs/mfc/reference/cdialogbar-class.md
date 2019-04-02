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
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58768299"
---
# <a name="cdialogbar-class"></a>CDialogBar – třída

Poskytuje funkce pro nemodální dialogovému oknu Windows na ovládacím panelu.

## <a name="syntax"></a>Syntaxe

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CDialogBar::CDialogBar](#cdialogbar)|Vytvoří `CDialogBar` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CDialogBar::Create](#create)|Vytvoří panel dialogového okna Windows a připojí ho k `CDialogBar` objektu.|

## <a name="remarks"></a>Poznámky

Panel dialogového okna se podobá dialogového okna, protože obsahuje standardní ovládací prvky Windows, které uživatel může mezi kartu. Jiné podobnosti je, že vytvoříte dialogové okno šablony, která představuje panel dialogového okna.

Vytvoření a použití dialogového pruhu se podobá vytváření a používání `CFormView` objektu. Nejprve [editoru dialogového okna](../../windows/dialog-editor.md) k definování šablony dialogového okna se stylem WS_CHILD a žádný jiný styl. Šablona nesmí obsahovat styl WS_VISIBLE. V kódu aplikace volat konstruktor k vytvoření `CDialogBar` objekt a potom voláním `Create` vytvořit panel dialogového okna okno a připojit ho k `CDialogBar` objektu.

Další informace o `CDialogBar`, najdete v článku [dialogové pruhy](../../mfc/dialog-bars.md) a [Technická poznámka 31](../../mfc/tn031-control-bars.md), ovládacích pruhů.

> [!NOTE]
>  V aktuální verzi `CDialogBar` objektu nelze umístit ovládací prvky Windows Forms. Další informace o ovládacích prvcích Windows Forms v jazyce Visual C++, naleznete v tématu [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxext.h

##  <a name="cdialogbar"></a>  CDialogBar::CDialogBar

Vytvoří `CDialogBar` objektu.

```
CDialogBar();
```

##  <a name="create"></a>  CDialogBar::Create

Načte dialogového okna prostředků šablonu určenou položkou `lpszTemplateName` nebo `nIDTemplate`, vytvoří panel dialogového okna okno, nastaví jeho styl a přidruží ji k `CDialogBar` objektu.

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
Ukazatel na nadřazenou `CWnd` objektu.

*lpszTemplateName*<br/>
Ukazatel na název `CDialogBar` objektu dialogového okna prostředků šablony.

*nStyle*<br/>
Styl toolbar. Další toolbar – styly podporovány jsou:

- CBRS_TOP ovládací panel je v horní části okna rámce.

- CBRS_BOTTOM ovládací panel je v dolní části okna rámce.

- Při změně velikosti nadřazené není přemístí CBRS_NOALIGN ovládací panel.

- CBRS_TOOLTIPS ovládací panel zobrazuje popisy tlačítek.

- CBRS_SIZE_DYNAMIC ovládací panel je dynamická.

- CBRS_SIZE_FIXED ovládací panel vyřešen.

- Panel ovládacího prvku CBRS_FLOATING je s plovoucí desetinnou čárkou.

- CBRS_FLYBY stavový řádek zobrazuje informace o tlačítku.

- Uživateli se nezobrazí CBRS_HIDE_INPLACE ovládací panel.

*nID*<br/>
ID ovládacího prvku panel dialogového okna.

*nIDTemplate*<br/>
ID prostředku `CDialogBar` šablony dialog-box objektu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Pokud zadáte CBRS_TOP nebo CBRS_BOTTOM styl zarovnání, je panel dialogového okna šířku okna rámce a výšku, je prostředek určený souborem *nIDTemplate*. Pokud zadáte CBRS_LEFT nebo CBRS_RIGHT styl zarovnání, Výška pruhu dialogové okno je okno rámce a jeho šířka byla u prostředku zadaného parametrem *nIDTemplate*.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFormView – třída](../../mfc/reference/cformview-class.md)<br/>
[CControlBar – třída](../../mfc/reference/ccontrolbar-class.md)
