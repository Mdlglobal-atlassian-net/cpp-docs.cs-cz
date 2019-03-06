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
ms.openlocfilehash: 386fb83df9ea7a889c8bb11f550313aad0bda926
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418890"
---
# <a name="transaction-object-interfaces"></a>Rozhraní objektu transakce

Objekt transakce definuje atomickou jednotku práce na zdroji dat a určuje, jak tyto jednotky práce vzájemně souvisí. Tento objekt není přímo podporován šablonami zprostředkovatele OLE DB (to znamená, musíte vytvořit vlastní objekt).

V následující tabulce jsou uvedeny povinných a volitelných rozhraní definované technologie OLE DB pro transakční objekt.

|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Povinné|Ne|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Povinné|Ne|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|volitelná,|Ne|

## <a name="see-also"></a>Viz také

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
