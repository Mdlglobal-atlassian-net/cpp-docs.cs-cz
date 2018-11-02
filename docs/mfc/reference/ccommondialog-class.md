---
title: Ccommondialog – třída
ms.date: 11/04/2016
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
ms.openlocfilehash: 47ef6591a69196ea93048e2ce3a77603b12ab4c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432732"
---
# <a name="ccommondialog-class"></a>Ccommondialog – třída

Základní třída pro třídy, které zapouzdřují funkce běžných dialogových oken Windows.

## <a name="syntax"></a>Syntaxe

```
class CCommonDialog : public CDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CCommonDialog::CCommonDialog](#ccommondialog)|Vytvoří `CCommonDialog` objektu.|

## <a name="remarks"></a>Poznámky

Následující třídy zapouzdřují funkce běžných dialogových oken Windows:

- [CFileDialog](../../mfc/reference/cfiledialog-class.md)

- [Cfontdialog –](../../mfc/reference/cfontdialog-class.md)

- [Ccolordialog –](../../mfc/reference/ccolordialog-class.md)

- [Cpagesetupdialog –](../../mfc/reference/cpagesetupdialog-class.md)

- [Cprintdialog –](../../mfc/reference/cprintdialog-class.md)

- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)

- [CFindReplaceDialog.](../../mfc/reference/cfindreplacedialog-class.md)

- [Coledialog –](../../mfc/reference/coledialog-class.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`CCommonDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

##  <a name="ccommondialog"></a>  CCommonDialog::CCommonDialog

Vytvoří `CCommonDialog` objektu.

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Odkazuje na objekt okna nadřazené nebo vlastník (typu [CWnd](../../mfc/reference/cwnd-class.md)), ke které patří objektu dialogového okna. Pokud je hodnota NULL, objektu dialogového okna nadřazené okno bude nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Zobrazit [CDialog::CDialog](../../mfc/reference/cdialog-class.md#cdialog) podrobnější informace.

## <a name="see-also"></a>Viz také

[CDialog – třída](../../mfc/reference/cdialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFileDialog – třída](../../mfc/reference/cfiledialog-class.md)<br/>
[CFontDialog – třída](../../mfc/reference/cfontdialog-class.md)<br/>
[CColorDialog – třída](../../mfc/reference/ccolordialog-class.md)<br/>
[CPageSetupDialog – třída](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[CPrintDialog – třída](../../mfc/reference/cprintdialog-class.md)<br/>
[CFindReplaceDialog – třída](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
