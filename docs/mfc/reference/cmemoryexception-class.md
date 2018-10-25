---
title: Cmemoryexception – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
dev_langs:
- C++
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: df664db673ee3989d689b8cf28b87cfff32a8dc7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50076812"
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

