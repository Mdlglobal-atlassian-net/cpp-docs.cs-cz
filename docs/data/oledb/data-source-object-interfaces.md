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
ms.openlocfilehash: a615694a9db75cdaf3b187cf6d29248bd26ef978
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501397"
---
# <a name="data-source-object-interfaces"></a>Rozhraní objektu zdroje dat

V následující tabulce jsou uvedena povinná a volitelná rozhraní definovaná OLE DB pro objekt zdroje dat.

|Rozhraní|Povinné?|Implementováno pomocí šablon OLE DB?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|Povinné|Ano|
|`IDBInitialize`|Povinné|Ano|
|`IDBProperties`|Povinné|Ano|
|[IPersist](/windows/win32/api/objidl/nn-objidl-ipersist)|Povinné|Ano|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|volitelná,|Ne|
|`IDBDataSourceAdmin`|volitelná,|Ne|
|`IDBInfo`|volitelná,|Ne|
|[IPersistFile](/windows/win32/api/objidl/nn-objidl-ipersistfile)|volitelná,|Ne|
|`ISupportErrorInfo`|volitelná,|Ne|

Objekt zdroje dat implementuje `IDBProperties`rozhraní, `IDBInitialize`a `IDBCreateSession` prostřednictvím dědičnosti. Můžete zvolit podporu dalších funkcí děděním nebo neděděním z jedné z těchto tříd implementace. Pokud chcete `IDBDataSourceAdmin` rozhraní podporovat, je nutné dědit `IDBDataSourceAdminImpl` z třídy.

## <a name="see-also"></a>Viz také:

[Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
