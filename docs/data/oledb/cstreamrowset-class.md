---
title: "CStreamRowset – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
dev_langs: C++
helpviewer_keywords: CStreamRowset class
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 003b6b84195c491d1c72c3de289de375459ba261
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cstreamrowset-class"></a>CStreamRowset – třída
Použít v `CCommand` nebo `CTable` deklarace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
 `ICommand::Execute`Vrátí `ISequentialStream` ukazatele, který je uložen v `m_spStream`. Pak použijete **čtení** metoda pro načtení dat (Unicode string) ve formátu XML. Příklad:  
  
 [!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]  
  
 SQL Server 2000 provádí XML formátování a vrátí všechny sloupce a všechny řádky sady řádků jako jeden řetězec XML.  
  
> [!NOTE]
>  Tato funkce funguje pouze s SQL Server 2000.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)