---
title: Rozhraní objektu transakce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 88b6884ff8543b3aa6ec329330563fbe1ad27b8e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071585"
---
# <a name="transaction-object-interfaces"></a>Rozhraní objektu transakce

Objekt transakce definuje atomickou jednotku práce na zdroji dat a určuje, jak tyto jednotky práce vzájemně souvisí. Tento objekt není přímo podporován šablonami zprostředkovatele OLE DB (to znamená, musíte vytvořit vlastní objekt).  
  
V následující tabulce jsou uvedeny povinných a volitelných rozhraní definované technologie OLE DB pro transakční objekt.  
  
|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|  
|---------------|---------------|--------------------------------------|  
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Povinné|Ne|  
|[ITransaction](/previous-versions/windows/desktop/ms723053\(v=vs.85\))|Povinné|Ne|  
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816\(v=vs.85\))|volitelná,|Ne|  
  
## <a name="see-also"></a>Viz také  

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)