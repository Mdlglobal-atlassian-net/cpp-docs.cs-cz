---
title: CNoRowset – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs:
- C++
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 87d005dc19ef286bc4b0da927ecabcd90e6f0235
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098157"
---
# <a name="cnorowset-class"></a>CNoRowset – třída
Lze použít jako šablonu argumentu (`TRowset`) pro [CCommand](../../data/oledb/ccommand-class.md) nebo [CTable](../../data/oledb/ctable-class.md).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Třídu přistupujícího objektu. Výchozí hodnota je `CAccessorBase`.  
  
## <a name="remarks"></a>Poznámky  
 Použití `CNoRowset` jako argument šablony, pokud příkaz nevrací sadu řádků.  
  
 `CNoRowset` implementuje metodu se zakázaným inzerováním, z nichž každý odpovídají jiné metody přistupující objekt třídy:  
  
-   **BindFinished** -Určuje, po dokončení vazby (vrátí `S_OK`).  
  
-   **Zavřít** -uvolní řádky a aktuální IRowset rozhraní.  
  
-   `GetIID` -Načte ID rozhraní bod připojení.  
  
-   **Getinterface –** -načte rozhraní.  
  
-   `GetInterfacePtr` -Načte ukazatele zapouzdřené rozhraní.  
  
-   **SetAccessor** -nastaví ukazatel na přistupující objekt.  
  
-   **SetupOptionalRowsetInterfaces** -nastaví volitelné rozhraní pro sadu řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)