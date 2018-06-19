---
title: Příkaz rozhraní objektu | Microsoft Docs
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
ms.openlocfilehash: 9c597cc30e23ffce2787eac6c13f6ba8c53f96c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096116"
---
# <a name="command-object-interfaces"></a>Rozhraní příkazového objektu
Objekt příkazu používá `IAccessor` rozhraní k zadání parametru vazby. Volání příjemce `IAccessor::CreateAccessor`, předání pole `DBBINDING` struktury. `DBBINDING` obsahuje informace o vazeb sloupců (například typ a délku). Zprostředkovatel obdrží struktury a určuje, jak by se měly převést data a zda jsou nutné převody.  
  
 `ICommandText` Rozhraní představuje způsob, jak zadat text příkazu. `ICommandProperties` Rozhraní zpracovává všechny vlastnosti příkazu.  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)