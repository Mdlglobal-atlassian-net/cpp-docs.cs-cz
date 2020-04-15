---
title: CFolderPickerDialog – třída
ms.date: 03/27/2019
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: ed3dc151060519bce216cf4a2f3d6559d6b8937e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373847"
---
# <a name="cfolderpickerdialog-class"></a>CFolderPickerDialog – třída

Třída CFolderPickerDialog implementuje cfiledialog v režimu výběru složek.

## <a name="syntax"></a>Syntaxe

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFolderPickerDialog::~CFolderPickerDialog](#_dtorcfolderpickerdialog)|Destruktor.|
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|Konstruktor|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[CFileDialog](../../mfc/reference/cfiledialog-class.md)

`CFolderPickerDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="cfolderpickerdialog"></a>CFolderPickerDialog::CFolderPickerDialog

Konstruktor

```
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL,
    DWORD dwSize = 0);
```

### <a name="parameters"></a>Parametry

*lpszSložka*<br/>
Počáteční složka.

*dwFlags*<br/>
Kombinace jednoho nebo více příznaků, které umožňují přizpůsobit dialogové okno.

*pParentWnd*<br/>
Ukazatel na nadřazené nebo vlastníkovi okna objektu dialogového okna.

*dwVelikost*<br/>
Velikost openfilename struktury.

### <a name="remarks"></a>Poznámky

## <a name="cfolderpickerdialogcfolderpickerdialog"></a><a name="_dtorcfolderpickerdialog"></a>CFolderPickerDialog::~CFolderPickerDialog

Destruktor.

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
