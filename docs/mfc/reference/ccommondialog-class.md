---
title: CCommonDialog – třída
ms.date: 11/04/2016
f1_keywords:
- CCommonDialog
- AFXDLGS/CCommonDialog
- AFXDLGS/CCommonDialog::CCommonDialog
helpviewer_keywords:
- CCommonDialog [MFC], CCommonDialog
ms.assetid: 1f68d65f-a0fd-4778-be22-ebbe51a95f95
ms.openlocfilehash: 853a4756df3b70f4f33deb7159b4d1aee610092c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369448"
---
# <a name="ccommondialog-class"></a>CCommonDialog – třída

Základní třída pro třídy, které zapouzdřují funkce běžných dialogových oken systému Windows.

## <a name="syntax"></a>Syntaxe

```
class CCommonDialog : public CDialog
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CCommonDialog::CCommonDialog](#ccommondialog)|Vytvoří `CCommonDialog` objekt.|

## <a name="remarks"></a>Poznámky

Následující třídy zapouzdřují funkce běžných dialogových oken systému Windows:

- [CFileDialog](../../mfc/reference/cfiledialog-class.md)

- [CFontDialog](../../mfc/reference/cfontdialog-class.md)

- [CColorDialog](../../mfc/reference/ccolordialog-class.md)

- [Dialogové okno CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md)

- [CPrintDialog](../../mfc/reference/cprintdialog-class.md)

- [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md)

- [CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)

- [COleDialog](../../mfc/reference/coledialog-class.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

`CCommonDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

## <a name="ccommondialogccommondialog"></a><a name="ccommondialog"></a>CCommonDialog::CCommonDialog

Vytvoří `CCommonDialog` objekt.

```
explicit CCommonDialog(CWnd* pParentWnd);
```

### <a name="parameters"></a>Parametry

*pParentWnd*<br/>
Odkazuje na nadřazený objekt okna nebo objekt vlastníka (typu [CWnd),](../../mfc/reference/cwnd-class.md)ke kterému patří objekt dialogového okna. Pokud je null, nadřazené okno objektu dialogu je nastaveno na hlavní okno aplikace.

### <a name="remarks"></a>Poznámky

Úplné informace naleznete [v tématu CDialog::CDialog.](../../mfc/reference/cdialog-class.md#cdialog)

## <a name="see-also"></a>Viz také

[CDialog – třída](../../mfc/reference/cdialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CFileDialog](../../mfc/reference/cfiledialog-class.md)<br/>
[CFontDialog – třída](../../mfc/reference/cfontdialog-class.md)<br/>
[Třída CColorDialog](../../mfc/reference/ccolordialog-class.md)<br/>
[CPageSetupDialog – třída](../../mfc/reference/cpagesetupdialog-class.md)<br/>
[Třída CPrintDialog](../../mfc/reference/cprintdialog-class.md)<br/>
[Třída CFindReplaceDialog](../../mfc/reference/cfindreplacedialog-class.md)<br/>
[COleDialog – třída](../../mfc/reference/coledialog-class.md)
