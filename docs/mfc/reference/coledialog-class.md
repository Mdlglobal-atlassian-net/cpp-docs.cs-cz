---
title: Coledialog – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
dev_langs:
- C++
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3c6cebf6af24de860c583398c16c87824ede0075
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401274"
---
# <a name="coledialog-class"></a>Coledialog – třída

Poskytuje funkce, které jsou společné pro dialogová okna pro OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleDialog::GetLastError](#getlasterror)|Získá kód chyby vrácený dialogových oken.|

## <a name="remarks"></a>Poznámky

Knihovny Microsoft Foundation Class poskytuje několik tříd odvozených z `COleDialog`:

- [Coleinsertdialog –](../../mfc/reference/coleinsertdialog-class.md)

- [Coleconvertdialog –](../../mfc/reference/coleconvertdialog-class.md)

- [Colechangeicondialog –](../../mfc/reference/colechangeicondialog-class.md)

- [Colelinksdialog –](../../mfc/reference/colelinksdialog-class.md)

- [Colebusydialog –](../../mfc/reference/colebusydialog-class.md)

- [Coleupdatedialog –](../../mfc/reference/coleupdatedialog-class.md)

- [Colepastespecialdialog –](../../mfc/reference/colepastespecialdialog-class.md)

- [Colepropertiesdialog –](../../mfc/reference/colepropertiesdialog-class.md)

- [Colechangesourcedialog –](../../mfc/reference/colechangesourcedialog-class.md)

Další informace o dialogových oknech OLE konkrétní, najdete v článku [dialogová okna v prostředí OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[Ccommondialog –](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

##  <a name="getlasterror"></a>  COleDialog::GetLastError

Volání `GetLastError` členská funkce, chcete-li získat další informace o chybě při `DoModal` vrátí IDABORT.

```
UINT GetLastError() const;
```

### <a name="return-value"></a>Návratová hodnota

Kódů chyb vrácených nástrojem `GetLastError` závisí na konkrétní dialogu zobrazí.

### <a name="remarks"></a>Poznámky

Zobrazit `DoModal` členské funkce v odvozených třídách informace o určité chybové zprávy.

## <a name="see-also"></a>Viz také

[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)



