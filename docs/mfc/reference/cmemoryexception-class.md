---
title: Cmemoryexception – třída
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: e4a399ffb4c0d2161479ed7c84e66eb58a9260ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552838"
---
# <a name="cmemoryexception-class"></a>Cmemoryexception – třída

Představuje podmínku výjimky na více instancí z důvodu nedostatku paměti.

## <a name="syntax"></a>Syntaxe

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMemoryException::CMemoryException](#cmemoryexception)|Vytvoří `CMemoryException` objektu.|

## <a name="remarks"></a>Poznámky

Žádné další kvalifikace je nezbytné nebo je to možné. Paměť výjimky jsou vyvolány automaticky **nové**. Pokud píšete vašich vlastních funkcích paměť, používá `malloc`pro příklad, a zodpovídají za vyvolání výjimky paměti.

Další informace o `CMemoryException`, najdete v článku [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

[Csimpleexception –](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="cmemoryexception"></a>  CMemoryException::CMemoryException

Vytvoří `CMemoryException` objektu.

```
CMemoryException();
```

### <a name="remarks"></a>Poznámky

Nepoužívejte tento konstruktor přímo, ale místo toho volat funkci globální [afxthrowmemoryexception –](exception-processing.md#afxthrowmemoryexception). Tato globální funkce můžete v situaci paměti úspěšná, protože vytvoří objekt výjimky v dříve přidělené paměti. Další informace o zpracování výjimek naleznete v článku [výjimky](../exception-handling-in-mfc.md).

## <a name="see-also"></a>Viz také

[CException – třída](cexception-class.md)<br/>
[Graf hierarchie](../hierarchy-chart.md)

