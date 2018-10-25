---
title: Cresourceexception – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs:
- C++
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e1fea7db1ef79eed2bc2678bd1e9283c71bb161
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071859"
---
# <a name="cresourceexception-class"></a>Cresourceexception – třída

Vygeneruje, když Windows nemůže najít nebo přidělit požadovaný prostředek.

## <a name="syntax"></a>Syntaxe

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|Vytvoří `CResourceException` objektu.|

## <a name="remarks"></a>Poznámky

Žádné další kvalifikace je nezbytné nebo je to možné.

Další informace o používání `CResourceException`, najdete v článku [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

[Csimpleexception –](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

##  <a name="cresourceexception"></a>  CResourceException::CResourceException

Vytvoří `CResourceException` objektu.

```
CResourceException();
```

### <a name="remarks"></a>Poznámky

Nepoužívejte tento konstruktor přímo, ale místo toho volat funkci globální [afxthrowresourceexception –](exception-processing.md#afxthrowresourceexception). Další informace o výjimkách, najdete v článku [zpracování výjimek v prostředí MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Viz také

[CException – třída](cexception-class.md)<br/>
[Graf hierarchie](../hierarchy-chart.md)

