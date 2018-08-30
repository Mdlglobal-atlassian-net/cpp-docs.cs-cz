---
title: CDynamicStringAccessorW – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessorW
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 16f4725013d11eb27e4c6669403942cf171032ac
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220071"
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
