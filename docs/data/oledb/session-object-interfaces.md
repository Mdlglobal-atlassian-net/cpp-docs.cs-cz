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
ms.openlocfilehash: 8208a372989fac5fa7c7b0c13b83eb27a4d1444b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42464521"
---
# <a name="session-object-interfaces"></a>Rozhraní objektu relace
V následující tabulce jsou uvedeny povinných a volitelných rozhraní definované technologie OLE DB pro objekt relace.  
  
|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](/previous-versions/windows/desktop/ms709721\(v=vs.85\))|Povinné|Ano|  
|[IOpenRowset](/previous-versions/windows/desktop/ms716946\(v=vs.85\))|Povinné|Ano|  
|[ISessionProperties](/previous-versions/windows/desktop/ms713721\(v=vs.85\))|Povinné|Ano|  
|[IAlterIndex](/previous-versions/windows/desktop/ms714943\(v=vs.85\))|Nepovinné|Ne|  
|[IAlterTable](/previous-versions/windows/desktop/ms719764\(v=vs.85\))|Nepovinné|Ne|  
|[IBindResource](/previous-versions/windows/desktop/ms714936\(v=vs.85\))|Nepovinné|Ne|  
|[ICreateRow](/previous-versions/windows/desktop/ms716832\(v=vs.85\))|Nepovinné|Ne|  
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625\(v=vs.85\))|Nepovinné|Ano|  
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686\(v=vs.85\))|Nepovinné|Ano|  
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593\(v=vs.85\))|Nepovinné|Ne|  
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816\(v=vs.85\))|Nepovinné|Ano|  
|[ITableCreation](/previous-versions/windows/desktop/ms713639\(v=vs.85\))|Nepovinné|Ne|  
|[ITableDefinition](/previous-versions/windows/desktop/ms714277\(v=vs.85\))|Nepovinné|Ne|  
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947\(v=vs.85\))|Nepovinné|Ne|  
|[ITransaction](/previous-versions/windows/desktop/ms723053\(v=vs.85\))|Nepovinné|Ne|  
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071\(v=vs.85\))|Nepovinné|Ne|  
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893\(v=vs.85\))|Nepovinné|Ne|  
|[ITransactionObject](/previous-versions/windows/desktop/ms713659\(v=vs.85\))|Nepovinné|Ne|  
  
 Objekt relace vytváří objektu sady řádků. Pokud zprostředkovatel podporuje příkazy, relace také vytvoří příkazový objekt (`CCommand`, implementace rozhraní OLE DB `TCommand`). Implementuje objekt příkazu `ICommand` rozhraní a používá `ICommand::Execute` metodu provést příkazy pro řádků, jak je znázorněno na následujícím obrázku.  
  
 ![Koncepční diagram poskytovatele](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)