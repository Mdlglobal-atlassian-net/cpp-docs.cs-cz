---
title: CNotSupportedException – třída
ms.date: 11/04/2016
f1_keywords:
- CNotSupportedException
- AFX/CNotSupportedException
- AFX/CNotSupportedException::CNotSupportedException
helpviewer_keywords:
- CNotSupportedException [MFC], CNotSupportedException
ms.assetid: e517391b-eb94-4c39-ae32-87b45bf7d624
ms.openlocfilehash: b859b939baef018e69b245e597eea90e608253ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363196"
---
# <a name="cnotsupportedexception-class"></a>CNotSupportedException – třída

Představuje výjimku, která je výsledkem požadavku na nepodporovanou funkci.

## <a name="syntax"></a>Syntaxe

```
class CNotSupportedException : public CSimpleException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CNotSupportedException::CNotSupportedException](#cnotsupportedexception)|Vytvoří `CNotSupportedException` objekt.|

## <a name="remarks"></a>Poznámky

Žádná další kvalifikace není nutná ani možná.

Další informace o `CNotSupportedException`použití naleznete v článku [Zpracování výjimek (MFC).](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CNotSupportedException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cnotsupportedexceptioncnotsupportedexception"></a><a name="cnotsupportedexception"></a>CNotSupportedException::CNotSupportedException

Vytvoří `CNotSupportedException` objekt.

```
CNotSupportedException();
```

### <a name="remarks"></a>Poznámky

Nepoužívejte tento konstruktor přímo, ale spíše volat globální funkce [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception). Další informace o zpracování výjimek naleznete v článku [Zpracování výjimek v knihovně MFC](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Viz také

[CException – třída](cexception-class.md)<br/>
[Graf hierarchie](../hierarchy-chart.md)
