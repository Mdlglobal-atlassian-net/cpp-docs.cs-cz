---
title: Rozhraní objektu relace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 01d08fb35a1e954aad07153f63ad3ed34282570d
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337843"
---
# <a name="session-object-interfaces"></a>Rozhraní objektu relace
V následující tabulce jsou uvedeny povinných a volitelných rozhraní definované technologie OLE DB pro objekt relace.  
  
|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](https://msdn.microsoft.com/library/ms709721.aspx)|Povinné|Ano|  
|[IOpenRowset](https://msdn.microsoft.com/library/ms716946.aspx)|Povinné|Ano|  
|[ISessionProperties](https://msdn.microsoft.com/library/ms713721.aspx)|Povinné|Ano|  
|[IAlterIndex](https://msdn.microsoft.com/library/ms714943.aspx)|Nepovinné|Ne|  
|[IAlterTable](https://msdn.microsoft.com/library/ms719764.aspx)|Nepovinné|Ne|  
|[IBindResource](https://msdn.microsoft.com/library/ms714936.aspx)|Nepovinné|Ne|  
|[ICreateRow](https://msdn.microsoft.com/library/ms716832.aspx)|Nepovinné|Ne|  
|[IDBCreateCommand](https://msdn.microsoft.com/library/ms711625.aspx)|Nepovinné|Ano|  
|[IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx)|Nepovinné|Ano|  
|[IIndexDefinition](https://msdn.microsoft.com/library/ms711593.aspx)|Nepovinné|Ne|  
|[ISupportErrorInfo](https://msdn.microsoft.com/library/ms715816.aspx)|Nepovinné|Ano|  
|[ITableCreation](https://msdn.microsoft.com/library/ms713639.aspx)|Nepovinné|Ne|  
|[ITableDefinition](https://msdn.microsoft.com/library/ms714277.aspx)|Nepovinné|Ne|  
|[ITableDefinitionWithConstraints](https://msdn.microsoft.com/library/ms720947.aspx)|Nepovinné|Ne|  
|[ITransaction](https://msdn.microsoft.com/library/ms723053.aspx)|Nepovinné|Ne|  
|[ITransactionJoin](https://msdn.microsoft.com/library/ms718071.aspx)|Nepovinné|Ne|  
|[ITransactionLocal](https://msdn.microsoft.com/library/ms714893.aspx)|Nepovinné|Ne|  
|[ITransactionObject](https://msdn.microsoft.com/library/ms713659.aspx)|Nepovinné|Ne|  
  
 Objekt relace vytváří objektu sady řádků. Pokud zprostředkovatel podporuje příkazy, relace také vytvoří příkazový objekt (`CCommand`, implementace rozhraní OLE DB `TCommand`). Implementuje objekt příkazu `ICommand` rozhraní a používá `ICommand::Execute` metodu provést příkazy pro řádků, jak je znázorněno na následujícím obrázku.  
  
 ![Koncepční diagram poskytovatele](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)