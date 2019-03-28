---
title: Cfolderpickerdialog – třída
ms.date: 03/27/2019
f1_keywords:
- CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog
- AFXDLGS/CFolderPickerDialog::CFolderPickerDialog
helpviewer_keywords:
- CFolderPickerDialog [MFC], CFolderPickerDialog
ms.assetid: 8db01684-dd1d-4e9c-989e-07a2318a8156
ms.openlocfilehash: 435c91082fa901f0bc9726316f0358fc5a669b29
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565006"
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
|[CFolderPickerDialog::~CFolderPickerDialog](#_dtorcfolderpickerdialog)|Destruktor.|
|[CFolderPickerDialog::CFolderPickerDialog](#cfolderpickerdialog)|Konstruktor|

## <a name="remarks"></a>Poznámky

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

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

##  <a name="_dtorcfolderpickerdialog"></a>  CFolderPickerDialog::~CFolderPickerDialog

Destruktor.

```
virtual ~CFolderPickerDialog();
```

### <a name="remarks"></a>Poznámky

## <a name="see-also"></a>Viz také:

[Třídy](../../mfc/reference/mfc-classes.md)
