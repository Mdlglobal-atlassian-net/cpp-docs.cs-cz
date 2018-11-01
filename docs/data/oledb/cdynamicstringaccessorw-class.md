---
title: CDynamicStringAccessorW – třída
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorW
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
ms.openlocfilehash: 7052a912363d1256294131da9b89df97f768ecf8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551356"
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW – třída

Umožňuje přístup ke zdroji dat, když nemají žádné informace o schématu databáze (podkladová struktura).

## <a name="syntax"></a>Syntaxe

```cpp
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;
```

## <a name="remarks"></a>Poznámky

Oba požadavku, že zprostředkovatel načíst všechna data z úložiště dat jako řetězce dat, ale `CDynamicStringAccessor` vyžádá data řetězce Unicode.

`CDynamicStringAccessorW` dědí `GetString` a `SetString` z `CDynamicStringAccessor`. Při použití těchto metod v `CDynamicStringAccessorW` objektu, `BaseType` je **WCHAR**.

## <a name="requirements"></a>Požadavky

**Hlavička**: také atldbcli.h

## <a name="see-also"></a>Viz také

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor – třída](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor – třída](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
