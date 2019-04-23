---
title: Rozhraní příkazového objektu
ms.date: 10/24/2018
helpviewer_keywords:
- command object interfaces [C++]
- command objects [OLE DB]
- OLE DB [C++], command object interfaces
ms.assetid: dacff5ae-252c-4f20-9ad7-4e602cc48536
ms.openlocfilehash: 755c44cf8d0cb5bf5066197bfd0ead3e0f25e1f9
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032398"
---
# <a name="command-object-interfaces"></a>Rozhraní příkazového objektu

Objekt příkazu používá `IAccessor` rozhraní k určení vazby parametru. Příjemce volání `IAccessor::CreateAccessor`, předají se jí pole `DBBINDING` struktury. `DBBINDING` obsahuje informace o vazeb sloupců (jako je například typ a délku). Zprostředkovatel přijímá struktury a určuje, jak by se měly převést data a zda jsou potřebné převody.

`ICommandText` Rozhraní poskytuje způsob, jak zadat text příkazu. `ICommandProperties` Rozhraní zpracovává všechny vlastnosti příkazu.

## <a name="see-also"></a>Viz také:

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
