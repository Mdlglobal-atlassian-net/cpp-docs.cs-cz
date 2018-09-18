---
title: CAccessor – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
dev_langs:
- C++
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b3adc22d940e79a4f86fec45c0d0e4fc3969f1a7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071416"
---
# <a name="caccessor-class"></a>CAccessor – třída

Představuje jeden z typů přistupujícího objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
template <class T>  
class CAccessor : public CAccessorBase, public T  
```  
  
### <a name="parameters"></a>Parametry  

*T*<br/>
Třída uživatelského záznamu.  
  
## <a name="remarks"></a>Poznámky  

Používá se při záznamu je staticky svázán se zdrojem dat. Záznam obsahuje vyrovnávací paměti. Tato třída podporuje několik přístupových objektů pro sadu řádků.  
  
Pomocí tohoto typu přístupového objektu, když víte, struktury a typ databáze.  
  
Pokud váš přístupový objekt obsahuje pole, které odkazují na paměť (například `BSTR` nebo rozhraní), který musí být uvolněn zavolat členskou funkci [CAccessorRowset::FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md) před další záznam pro čtení.  
  
## <a name="requirements"></a>Požadavky  

**Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)