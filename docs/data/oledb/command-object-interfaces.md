---
title: Příkaz rozhraní objektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ea824fda89ccf45c62145a0fe72e55edc614970a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106955"
---
# <a name="command-object-interfaces"></a>Rozhraní příkazového objektu

Objekt příkazu používá `IAccessor` rozhraní k určení vazby parametru. Příjemce volání `IAccessor::CreateAccessor`, předají se jí pole `DBBINDING` struktury. `DBBINDING` obsahuje informace o vazeb sloupců (jako je například typ a délku). Zprostředkovatel přijímá struktury a určuje, jak by se měly převést data a zda jsou potřebné převody.  
  
`ICommandText` Rozhraní poskytuje způsob, jak zadat text příkazu. `ICommandProperties` Rozhraní zpracovává všechny vlastnosti příkazu.  
  
## <a name="see-also"></a>Viz také  

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)