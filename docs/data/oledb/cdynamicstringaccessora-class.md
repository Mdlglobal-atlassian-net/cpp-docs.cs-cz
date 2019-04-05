---
title: CDynamicStringAccessorA – třída
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorA
helpviewer_keywords:
- CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
ms.openlocfilehash: 3a0da9c779230fc1bf58bfa1d685623f844012c7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031349"
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA – třída

Umožňuje přístup ke zdroji dat, když nemají žádné informace o schématu databáze (podkladová struktura).

## <a name="syntax"></a>Syntaxe

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;
```

## <a name="remarks"></a>Poznámky

Oba požadavku, že zprostředkovatel načíst všechna data z úložiště dat jako řetězce dat, ale `CDynamicStringAccessor` požadavky ANSI data řetězce.

`CDynamicStringAccessorA` dědí `GetString` a `SetString` z `CDynamicStringAccessor`. Při použití těchto metod v `CDynamicStringAccessorA` objektu, `BaseType` je **CHAR**.

## <a name="requirements"></a>Požadavky

**Hlavička**: také atldbcli.h

## <a name="see-also"></a>Viz také:

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor – třída](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
