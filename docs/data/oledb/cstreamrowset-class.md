---
title: CStreamRowset – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
dev_langs:
- C++
helpviewer_keywords:
- CStreamRowset class
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3365767ed36bcdc45e87f08fb038500fa9ac6d82
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100028"
---
# <a name="cstreamrowset-class"></a>CStreamRowset – třída
Použít v `CCommand` nebo `CTable` deklarace.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>  
class CStreamRowset  
```  
  
#### <a name="parameters"></a>Parametry  
 `TAccessor`  
 Třídu přistupujícího objektu.  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CStreamRowset](../../data/oledb/cstreamrowset-cstreamrowset.md)|Konstruktor Vytvoří a inicializuje `CStreamRowset` objektu.|  
|[Zavřete](../../data/oledb/cstreamrowset-close.md)|Verze [ISequentialStream](https://msdn.microsoft.com/en-us/library/ms718035.aspx) ukazatel rozhraní ve třídě.|  
  
## <a name="remarks"></a>Poznámky  
 Použití `CStreamRowset` ve vaší `CCommand` nebo `CTable` deklarace, např.:  
  
 [!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]  
  
 or  
  
 [!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]  
  
 `ICommand::Execute` Vrátí `ISequentialStream` ukazatele, který je uložen v `m_spStream`. Pak použijete **čtení** metoda pro načtení dat (Unicode string) ve formátu XML. Příklad:  
  
 [!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]  
  
 SQL Server 2000 provádí XML formátování a vrátí všechny sloupce a všechny řádky sady řádků jako jeden řetězec XML.  
  
> [!NOTE]
>  Tato funkce funguje pouze s SQL Server 2000.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)