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
ms.openlocfilehash: 0caecc797a3175d5769f98e181e1d99ef6b1ad16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389096"
---
# <a name="transaction-object-interfaces"></a>Rozhraní objektu transakce

Objekt transakce definuje atomickou jednotku práce na zdroji dat a určuje, jak tyto jednotky práce vzájemně souvisí. Tento objekt není přímo podporován šablonami zprostředkovatele OLE DB (to znamená, musíte vytvořit vlastní objekt).

V následující tabulce jsou uvedeny povinných a volitelných rozhraní definované technologie OLE DB pro transakční objekt.

|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Povinné|Ne|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Povinné|Ne|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|volitelná,|Ne|

## <a name="see-also"></a>Viz také:

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
