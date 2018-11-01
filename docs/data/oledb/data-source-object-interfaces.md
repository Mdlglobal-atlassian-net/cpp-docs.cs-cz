---
title: Rozhraní objektu zdroje dat
ms.date: 10/24/2018
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
ms.openlocfilehash: aaa9e90996750b0518999803487fcb39729c76f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519639"
---
# <a name="data-source-object-interfaces"></a>Rozhraní objektu zdroje dat

V následující tabulce jsou uvedeny povinných a volitelných rozhraní definované pro objekt zdroje dat OLE DB.

|Rozhraní|Povinné?|Šablony technologie OLE DB implementované?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|Povinné|Ano|
|`IDBInitialize`|Povinné|Ano|
|`IDBProperties`|Povinné|Ano|
|[IPersist](/windows/desktop/api/objidl/nn-objidl-ipersist)|Povinné|Ano|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|volitelná,|Ne|
|`IDBDataSourceAdmin`|volitelná,|Ne|
|`IDBInfo`|volitelná,|Ne|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|volitelná,|Ne|
|`ISupportErrorInfo`|volitelná,|Ne|

Zdroje dat objektu implementuje `IDBProperties`, `IDBInitialize`, a `IDBCreateSession` rozhraní prostřednictvím dědičnosti. Můžete nastavit dědění nebo není dědění z jedné z těchto tříd implementace podporovat další funkce. Pokud chcete zajistit podporu `IDBDataSourceAdmin` rozhraní, musí dědit z `IDBDataSourceAdminImpl` třídy.

## <a name="see-also"></a>Viz také

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
