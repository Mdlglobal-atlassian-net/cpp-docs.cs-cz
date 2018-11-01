---
title: Cfolderpickerdialog – třída
ms.date: 11/04/2016
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: ba189badaa9b1605e3467526e7b92a18a1bb5a73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561301"
---
# <a name="cfolderpickerdialog-class"></a>Cfolderpickerdialog – třída

Cfolderpickerdialog – třída implementuje CFileDialog v režimu pro výběr složky.

## <a name="syntax"></a>Syntaxe

```
class CFolderPickerDialog : public CFileDialog;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[Cfolderpickerdialog –:: ~ cfolderpickerdialog –](#cfolderpickerdialog__~cfolderpickerdialog)|Destruktor.|
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|Konstruktor|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[Ccommondialog –](../../mfc/reference/ccommondialog-class.md)

[CFileDialog](../../mfc/reference/cfiledialog-class.md)

`CFolderPickerDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxdlgs.h

##  <a name="cfolderpickerdialog"></a>  CFolderPickerDialog::CFolderPickerDialog

Konstruktor

```
explicit CFolderPickerDialog(
    LPCTSTR lpszFolder = NULL,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL,
    DWORD dwSize = 0);
```

### <a name="parameters"></a>Parametry

*lpszFolder*<br/>
Výchozí složka.

*dwFlags*<br/>
Kombinace jedné nebo více příznaků, které umožňují přizpůsobit dialogových oken.

*pParentWnd*<br/>
Ukazatel na okno nadřazené nebo vlastníka objektu pole dialogového okna.

*dwSize*<br/>
Velikost LPSTRFILE struktury.

### <a name="remarks"></a>Poznámky

##  <a name="_dtorcfolderpickerdialog"></a>  Cfolderpickerdialog –:: ~ cfolderpickerdialog –

Destruktor.

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také

[Třídy](../../mfc/reference/mfc-classes.md)
