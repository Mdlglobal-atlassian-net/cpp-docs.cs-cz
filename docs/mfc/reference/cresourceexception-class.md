---
title: CResourceException – třída
ms.date: 11/04/2016
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
ms.openlocfilehash: 557bfe1cc41c3dda65bd95d7d687820c0b9862b7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368332"
---
# <a name="cresourceexception-class"></a>CResourceException – třída

Generováno v případě, že systém Windows nemůže najít nebo přidělit požadovaný prostředek.

## <a name="syntax"></a>Syntaxe

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|Vytvoří `CResourceException` objekt.|

## <a name="remarks"></a>Poznámky

Žádná další kvalifikace není nutná ani možná.

Další informace o `CResourceException`použití naleznete v článku [Zpracování výjimek (MFC).](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="cresourceexceptioncresourceexception"></a><a name="cresourceexception"></a>CResourceException::CResourceException

Vytvoří `CResourceException` objekt.

```
CResourceException();
```

### <a name="remarks"></a>Poznámky

Nepoužívejte tento konstruktor přímo, ale spíše volat globální funkce [AfxThrowResourceException](exception-processing.md#afxthrowresourceexception). Další informace o výjimkách naleznete v článku [Zpracování výjimek v knihovně MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Viz také

[CException – třída](cexception-class.md)<br/>
[Graf hierarchie](../hierarchy-chart.md)
