---
title: "Rozhraní objektu zdroje dat | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c0a045657b80ddaf70792d1c7f617b0e1f7c0b4a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="data-source-object-interfaces"></a>Rozhraní objektu zdroje dat
V následující tabulce jsou povinné a nepovinné rozhraní určené pro objekt zdroje dat OLE DB.  
  
|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|  
|---------------|---------------|--------------------------------------|  
|`IDBCreateSession`|Povinné|Ano|  
|`IDBInitialize`|Povinné|Ano|  
|`IDBProperties`|Povinné|Ano|  
|[IPersist](http://msdn.microsoft.com/library/windows/desktop/ms688695)|Povinné|Ano|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Nepovinné|Ne|  
|`IDBDataSourceAdmin`|Nepovinné|Ne|  
|`IDBInfo`|Nepovinné|Ne|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Nepovinné|Ne|  
|`ISupportErrorInfo`|Nepovinné|Ne|  
  
 Implementuje objekt zdroje dat `IDBProperties`, `IDBInitialize`, a `IDBCreateSession` prostřednictvím dědičnosti. Můžete se na podporu další funkce, která dědí nebo není dědění z jedné z těchto tříd implementace. Pokud chcete zajistit podporu `IDBDataSourceAdmin` rozhraní, musí dědit z `IDBDataSourceAdminImpl` třídy.  
  
## <a name="see-also"></a>Viz také  
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)