---
title: CStreamRowset – třída | Dokumentace Microsoftu
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
- CStreamRowset::CStreamRowset
- CStreamRowset.CStreamRowset
- ATL.CStreamRowset.CStreamRowset
- ATL::CStreamRowset::CStreamRowset
- CStreamRowset
- CStreamRowset<TAccessor>::CStreamRowset
- ATL::CStreamRowset<TAccessor>::CStreamRowset
- CStreamRowset<TAccessor>.Close
- ATL.CStreamRowset<TAccessor>.Close
- CStreamRowset::Close
- CStreamRowset<TAccessor>::Close
- ATL::CStreamRowset::Close
- ATL.CStreamRowset.Close
- ATL::CStreamRowset<TAccessor>::Close
- CStreamRowset.Close
dev_langs:
- C++
helpviewer_keywords:
- CStreamRowset class
- CStreamRowset class, constructor
- Close method
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 76eb58936082c7efde7e7bc87f17e7326ecc8920
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071546"
---
# <a name="cstreamrowset-class"></a>CStreamRowset – třída

Používáno `CCommand` nebo `CTable` deklarace.  
  
## <a name="syntax"></a>Syntaxe

```cpp
template <class TAccessor = CAccessorBase>  
class CStreamRowset  
```  
  
### <a name="parameters"></a>Parametry  

*TAccessor*<br/>
Třídu přistupujícího objektu.  

## <a name="requirements"></a>Požadavky  

**Záhlaví:** také atldbcli.h  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CStreamRowset](#cstreamrowset)|Konstruktor Vytvoří a inicializuje `CStreamRowset` objektu.|  
|[Zavřít](#close)|Verze [ISequentialStream](/previous-versions/windows/desktop/ms718035\(v=vs.85\)) ukazatel rozhraní ve třídě.|  
  
## <a name="remarks"></a>Poznámky  

Použití `CStreamRowset` ve vašich `CCommand` nebo `CTable` prohlášení, například:  
  
[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]  
  
or  
  
[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]  
  
`ICommand::Execute` Vrátí `ISequentialStream` ukazatel, který je uložený v `m_spStream`. Pak použijete `Read` metodu pro načtení dat (řetězce Unicode) ve formátu XML. Příklad:  
  
[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]  
  
SQL Server 2000 provádí XML, formátování a vrátí všechny sloupce a všechny řádky v sadě řádků jako jeden řetězec XML.  
  
> [!NOTE]
>  Tato funkce funguje pouze s SQL Server 2000.  
  
## <a name="cstreamrowset"></a> CStreamRowset::CStreamRowset

Vytvoří a inicializuje `CStreamRowset` objektu.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
CStreamRowset();  
```  

## <a name="close"></a> CStreamRowset::Close

Verze [ISequentialStream](/previous-versions/windows/desktop/ms718035\(v=vs.85\)) ukazatel rozhraní ve třídě.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp
void Close();   
```  
  
## <a name="see-also"></a>Viz také  

[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)