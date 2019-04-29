---
title: Rozhraní objektu relace
ms.date: 11/19/2018
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
ms.openlocfilehash: 2fb91365fec0709e1bb2a26afa519e6565862681
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404579"
---
# <a name="session-object-interfaces"></a>Rozhraní objektu relace

V následující tabulce jsou uvedeny povinných a volitelných rozhraní definované technologie OLE DB pro objekt relace.

|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|
|---------------|---------------|--------------------------------------|
|[IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85))|Povinné|Ano|
|[IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85))|Povinné|Ano|
|[ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85))|Povinné|Ano|
|[IAlterIndex](/previous-versions/windows/desktop/ms714943(v=vs.85))|volitelná,|Ne|
|[IAlterTable](/previous-versions/windows/desktop/ms719764(v=vs.85))|volitelná,|Ne|
|[IBindResource](/previous-versions/windows/desktop/ms714936(v=vs.85))|volitelná,|Ne|
|[ICreateRow](/previous-versions/windows/desktop/ms716832(v=vs.85))|volitelná,|Ne|
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85))|volitelná,|Ano|
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))|volitelná,|Ano|
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593(v=vs.85))|volitelná,|Ne|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|volitelná,|Ano|
|[ITableCreation](/previous-versions/windows/desktop/ms713639(v=vs.85))|volitelná,|Ne|
|[ITableDefinition](/previous-versions/windows/desktop/ms714277(v=vs.85))|volitelná,|Ne|
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947(v=vs.85))|volitelná,|Ne|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|volitelná,|Ne|
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071(v=vs.85))|volitelná,|Ne|
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893(v=vs.85))|volitelná,|Ne|
|[ITransactionObject](/previous-versions/windows/desktop/ms713659(v=vs.85))|volitelná,|Ne|

Objekt relace vytváří objektu sady řádků. Pokud zprostředkovatel podporuje příkazy, relace také vytvoří příkazový objekt (`CCommand`, implementace rozhraní OLE DB `TCommand`). Implementuje objekt příkazu `ICommand` rozhraní a používá `ICommand::Execute` metodu provést příkazy pro řádků, jak je znázorněno na následujícím obrázku.

![Koncepční diagram poskytovatele](../../data/oledb/media/vc4u551.gif "koncepční diagram poskytovatele")

## <a name="see-also"></a>Viz také:

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
