---
title: "CNoRowset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs: C++
helpviewer_keywords: CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 901d857b5095dd882a368b9a87e8a7d38d20bc42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cnorowset-class"></a>CNoRowset – třída
Lze použít jako šablonu argumentu (`TRowset`) pro [CCommand](../../data/oledb/ccommand-class.md) nebo [CTable](../../data/oledb/ctable-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Třídu přistupujícího objektu. Výchozí hodnota je `CAccessorBase`.  
  
## <a name="remarks"></a>Poznámky  
 Použití `CNoRowset` jako argument šablony, pokud příkaz nevrací sadu řádků.  
  
 `CNoRowset`implementuje metodu se zakázaným inzerováním, z nichž každý odpovídají jiné metody přistupující objekt třídy:  
  
-   **BindFinished** -Určuje, po dokončení vazby (vrátí `S_OK`).  
  
-   **Zavřít** -uvolní řádky a aktuální IRowset rozhraní.  
  
-   `GetIID`-Načte ID rozhraní bod připojení.  
  
-   **Getinterface –** -načte rozhraní.  
  
-   `GetInterfacePtr`-Načte ukazatele zapouzdřené rozhraní.  
  
-   **SetAccessor** -nastaví ukazatel na přistupující objekt.  
  
-   **SetupOptionalRowsetInterfaces** -nastaví volitelné rozhraní pro sadu řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)