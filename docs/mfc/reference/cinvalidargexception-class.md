---
title: Cinvalidargexception – třída
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: d2df9b482fe95ad0a13a85a51037a4cbbc28d057
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392618"
---
# <a name="cinvalidargexception-class"></a>Cinvalidargexception – třída

Tato třída představuje podmínku výjimky neplatný argument.

## <a name="syntax"></a>Syntaxe

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|Konstruktor|

## <a name="remarks"></a>Poznámky

A `CInvalidArgException` objekt představuje podmínku výjimky neplatný argument.

Další informace o zpracování výjimek, najdete v článku [cexception – třída](../../mfc/reference/cexception-class.md) tématu a [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="cinvalidargexception"></a>  CInvalidArgException::CInvalidArgException

Konstruktor

```
CInvalidArgException();
```

### <a name="remarks"></a>Poznámky

Nepoužívejte tento konstruktor přímo. volání funkce globální **AfxThrowInvalidArgException**.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CSimpleException – třída](../../mfc/reference/csimpleexception-class.md)
