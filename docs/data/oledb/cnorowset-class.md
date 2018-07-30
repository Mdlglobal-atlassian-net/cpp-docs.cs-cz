---
title: Cnorowset – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: e92c9bfb49bbb64faca633f04bb87f40028b6e1e
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339559"
---
# <a name="cnorowset-class"></a>CNoRowset – třída
Můžete použít jako argument šablony (`TRowset`) pro [CCommand](../../data/oledb/ccommand-class.md) nebo [CTable](../../data/oledb/ctable-class.md).  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
### <a name="parameters"></a>Parametry  
 *TAccessor*  
 Třídu přistupujícího objektu. Výchozí hodnota je `CAccessorBase`.  
  
## <a name="remarks"></a>Poznámky  
 Použití `CNoRowset` jako argument šablony, pokud příkaz nevrací sadu řádků.  
  
 `CNoRowset` implementuje následující metody zástupných procedur, z nichž každý odpovídají jiné přístupové metody pro třídu:  
  
-   `BindFinished` -Určuje po dokončení vazby (vrátí `S_OK`).  
  
-   `Close` -Uvolní řádků a aktuální IRowset rozhraní.  
  
-   `GetIID` -Načte rozhraní ID bodu připojení.  
  
-   `GetInterface` -Načte rozhraní.  
  
-   `GetInterfacePtr` -Načte zapouzdřený ukazatel rozhraní.  
  
-   `SetAccessor` – Nastaví ukazatel na přistupujícím objektu.  
  
-   `SetupOptionalRowsetInterfaces` – Nastaví volitelné rozhraní pro sadu řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)