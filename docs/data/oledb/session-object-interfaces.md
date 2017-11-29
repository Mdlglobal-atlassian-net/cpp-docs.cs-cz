---
title: "Rozhraní objektu relace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2748756a4355b8f0befcf1287f8f30f6ece8ef84
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="session-object-interfaces"></a>Rozhraní objektu relace
V následující tabulce jsou povinné a nepovinné rozhraní definované OLE DB pro objekt relace.  
  
|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|  
|---------------|---------------|--------------------------------------|  
|[IGetdataaSource](https://msdn.microsoft.com/en-us/library/ms709721.aspx)|Povinné|Ano|  
|[IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx)|Povinné|Ano|  
|[ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx)|Povinné|Ano|  
|[IAlterIndex](https://msdn.microsoft.com/en-us/library/ms714943.aspx)|Nepovinné|Ne|  
|[IAlterTable](https://msdn.microsoft.com/en-us/library/ms719764.aspx)|Nepovinné|Ne|  
|[IBindResource](https://msdn.microsoft.com/en-us/library/ms714936.aspx)|Nepovinné|Ne|  
|[ICreateRow](https://msdn.microsoft.com/en-us/library/ms716832.aspx)|Nepovinné|Ne|  
|[IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx)|Nepovinné|Ano|  
|[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)|Nepovinné|Ano|  
|[IIndexDefinition](https://msdn.microsoft.com/en-us/library/ms711593.aspx)|Nepovinné|Ne|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Nepovinné|Ano|  
|[ITableCreation](https://msdn.microsoft.com/en-us/library/ms713639.aspx)|Nepovinné|Ne|  
|[ITableDefinition](https://msdn.microsoft.com/en-us/library/ms714277.aspx)|Nepovinné|Ne|  
|[ITableDefinitionWithConstraints](https://msdn.microsoft.com/en-us/library/ms720947.aspx)|Nepovinné|Ne|  
|[ITransaction](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|Nepovinné|Ne|  
|[ITransactionJoin](https://msdn.microsoft.com/en-us/library/ms718071.aspx)|Nepovinné|Ne|  
|[ITransactionLocal](https://msdn.microsoft.com/en-us/library/ms714893.aspx)|Nepovinné|Ne|  
|[ITransactionObject](https://msdn.microsoft.com/en-us/library/ms713659.aspx)|Nepovinné|Ne|  
  
 Objekt relace vytvoří objekt sady řádků. Pokud zprostředkovatel podporuje příkazy, relace také vytvoří objekt příkazu (`CCommand`, implementace OLE DB **TCommand**). Implementuje objekt příkazu `ICommand` rozhraní a používá `ICommand::Execute` metoda ke spuštění příkazů na sadě řádků, jak je znázorněno na následujícím obrázku.  
  
 ![Koncepční diagram zprostředkovatele](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)