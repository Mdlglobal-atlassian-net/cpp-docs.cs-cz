---
title: CInvalidArgException – třída
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: b28b6e84043b85a8117694a67ff5fff13e7c786b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372364"
---
# <a name="cinvalidargexception-class"></a>CInvalidArgException – třída

Tato třída představuje neplatnou podmínku výjimky argumentu.

## <a name="syntax"></a>Syntaxe

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CInvalidargException::CInvalidargException](#cinvalidargexception)|Konstruktor|

## <a name="remarks"></a>Poznámky

Objekt `CInvalidArgException` představuje neplatnou podmínku výjimky argumentu.

Další informace o zpracování výjimek naleznete v tématu [CException Class](../../mfc/reference/cexception-class.md) a [Exception Handling (MFC).](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cinvalidargexceptioncinvalidargexception"></a><a name="cinvalidargexception"></a>CInvalidargException::CInvalidargException

Konstruktor

```
CInvalidArgException();
```

### <a name="remarks"></a>Poznámky

Nepoužívejte tento konstruktor přímo; volání globální funkce **AfxThrowInvalidArgException**.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CSimpleException – třída](../../mfc/reference/csimpleexception-class.md)
