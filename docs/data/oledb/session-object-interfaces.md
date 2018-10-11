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
ms.openlocfilehash: 957fe69b413496af46aa8e19afd45ee41e58b490
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081770"
---
# <a name="session-object-interfaces"></a>Rozhraní objektu relace

V následující tabulce jsou uvedeny povinných a volitelných rozhraní definované technologie OLE DB pro objekt relace.  
  
|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](/previous-versions/windows/desktop/ms709721)|Povinné|Ano|  
|[IOpenRowset](/previous-versions/windows/desktop/ms716946)|Povinné|Ano|  
|[ISessionProperties](/previous-versions/windows/desktop/ms713721)|Povinné|Ano|  
|[IAlterIndex](/previous-versions/windows/desktop/ms714943)|volitelná,|Ne|  
|[IAlterTable](/previous-versions/windows/desktop/ms719764)|volitelná,|Ne|  
|[IBindResource](/previous-versions/windows/desktop/ms714936)|volitelná,|Ne|  
|[ICreateRow](/previous-versions/windows/desktop/ms716832)|volitelná,|Ne|  
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625)|volitelná,|Ano|  
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)|volitelná,|Ano|  
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593)|volitelná,|Ne|  
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|volitelná,|Ano|  
|[ITableCreation](/previous-versions/windows/desktop/ms713639)|volitelná,|Ne|  
|[ITableDefinition](/previous-versions/windows/desktop/ms714277)|volitelná,|Ne|  
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947)|volitelná,|Ne|  
|[ITransaction](/previous-versions/windows/desktop/ms723053)|volitelná,|Ne|  
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071)|volitelná,|Ne|  
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893)|volitelná,|Ne|  
|[ITransactionObject](/previous-versions/windows/desktop/ms713659)|volitelná,|Ne|  
  
Objekt relace vytváří objektu sady řádků. Pokud zprostředkovatel podporuje příkazy, relace také vytvoří příkazový objekt (`CCommand`, implementace rozhraní OLE DB `TCommand`). Implementuje objekt příkazu `ICommand` rozhraní a používá `ICommand::Execute` metodu provést příkazy pro řádků, jak je znázorněno na následujícím obrázku.  
  
![Koncepční diagram poskytovatele](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>Viz také  

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)