---
title: COleDialog – třída
ms.date: 11/04/2016
f1_keywords:
- COleDialog
- AFXODLGS/COleDialog
- AFXODLGS/COleDialog::GetLastError
helpviewer_keywords:
- COleDialog [MFC], GetLastError
ms.assetid: b1ed0aca-3914-4b00-af34-4a4fb491aec7
ms.openlocfilehash: 6a1983d426e97dd8063aee2857dc36557aa20677
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366085"
---
# <a name="coledialog-class"></a>COleDialog – třída

Poskytuje funkce společné pro dialogová okna pro OLE.

## <a name="syntax"></a>Syntaxe

```
class COleDialog : public CCommonDialog
```

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleDialog::GetLastError](#getlasterror)|Získá kód chyby vrácené dialogovéokno.|

## <a name="remarks"></a>Poznámky

Knihovna tříd Microsoft Foundation poskytuje `COleDialog`několik tříd odvozených z :

- [COleInsertDialog](../../mfc/reference/coleinsertdialog-class.md)

- [COleConvertDialog](../../mfc/reference/coleconvertdialog-class.md)

- [COleChangeIconDialog](../../mfc/reference/colechangeicondialog-class.md)

- [COleLinksDialog](../../mfc/reference/colelinksdialog-class.md)

- [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)

- [COleUpdateDialog](../../mfc/reference/coleupdatedialog-class.md)

- [COlePasteSpecialDialog](../../mfc/reference/colepastespecialdialog-class.md)

- [COlePropertiesDialog](../../mfc/reference/colepropertiesdialog-class.md)

- [COleChangeSourceDialog](../../mfc/reference/colechangesourcedialog-class.md)

Další informace o dialogových oknech specifických pro OLE naleznete v článku [Dialogová okna v ole](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cdialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`COleDialog`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxodlgs.h

## <a name="coledialoggetlasterror"></a><a name="getlasterror"></a>COleDialog::GetLastError

Volání `GetLastError` členské funkce získat další `DoModal` informace o chybě při vrátí IDABORT.

```
UINT GetLastError() const;
```

### <a name="return-value"></a>Návratová hodnota

Kódy chyb `GetLastError` vrácené závisí na konkrétním zobrazeném dialogovém okně.

### <a name="remarks"></a>Poznámky

Informace `DoModal` o konkrétních chybových zprávách naleznete v členské funkci v odvozených třídách.

## <a name="see-also"></a>Viz také

[CCommonDialog – třída](../../mfc/reference/ccommondialog-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
