---
title: CMemoryException – třída
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 375b4227a25ae4c18cfd263eff4c3ec13f1304e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369998"
---
# <a name="cmemoryexception-class"></a>CMemoryException – třída

Představuje podmínku výjimky mimo paměť.

## <a name="syntax"></a>Syntaxe

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMemoryException::CMemoryException](#cmemoryexception)|Vytvoří `CMemoryException` objekt.|

## <a name="remarks"></a>Poznámky

Žádná další kvalifikace není nutná ani možná. Výjimky paměti jsou vyvolány automaticky **novým**. Pokud píšete vlastní paměťové `malloc`funkce, pomocí , například, pak jste zodpovědní za vyvolání výjimky paměti.

Další informace `CMemoryException`naleznete v článku [Zpracování výjimek (MFC).](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>CMemoryException::CMemoryException

Vytvoří `CMemoryException` objekt.

```
CMemoryException();
```

### <a name="remarks"></a>Poznámky

Nepoužívejte tento konstruktor přímo, ale spíše volat globální funkce [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception). Tato globální funkce může být úspěšná v situaci nedostatku paměti, protože vytváří objekt výjimky v dříve přidělené paměti. Další informace o zpracování výjimek naleznete v [článku výjimky](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Viz také

[CException – třída](cexception-class.md)<br/>
[Graf hierarchie](../hierarchy-chart.md)
