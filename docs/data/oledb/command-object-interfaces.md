---
title: Rozhraní příkazového objektu
ms.date: 10/24/2018
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
ms.openlocfilehash: d9f663d4e857d300e5c0f5783b86445ce824ea8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598871"
---
# <a name="command-object-interfaces"></a>Rozhraní příkazového objektu

Objekt příkazu používá `IAccessor` rozhraní k určení vazby parametru. Příjemce volání `IAccessor::CreateAccessor`, předají se jí pole `DBBINDING` struktury. `DBBINDING` obsahuje informace o vazeb sloupců (jako je například typ a délku). Zprostředkovatel přijímá struktury a určuje, jak by se měly převést data a zda jsou potřebné převody.

`ICommandText` Rozhraní poskytuje způsob, jak zadat text příkazu. `ICommandProperties` Rozhraní zpracovává všechny vlastnosti příkazu.

## <a name="see-also"></a>Viz také

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
