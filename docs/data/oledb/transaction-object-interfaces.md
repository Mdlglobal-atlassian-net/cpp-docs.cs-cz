---
title: Rozhraní objektu transakce
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
ms.openlocfilehash: b86064c162dcacfbbc5877614c63d92d0f2bd347
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501242"
---
# <a name="transaction-object-interfaces"></a>Rozhraní objektu transakce

Objekt Transaction definuje atomickou jednotku práce na zdroji dat a určuje, jak vzájemně souvisí tyto jednotky práce. Tento objekt není přímo podporován šablonami poskytovatele OLE DB (to znamená, že je nutné vytvořit vlastní objekt).

V následující tabulce jsou uvedena povinná a volitelná rozhraní definovaná OLE DB pro objekt transakce.

|Rozhraní|Povinné?|Implementováno pomocí šablon OLE DB?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Povinné|Ne|
|[Metody ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Povinné|Ne|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|volitelná,|Ne|

## <a name="see-also"></a>Viz také:

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
