---
title: db_column | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.db_column
dev_langs: C++
helpviewer_keywords: db_column attribute
ms.assetid: 58da4afc-f69c-4ae6-af9a-3f9515f56081
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8fda1cfd5b23ae94da6be070e59add2854fb2687
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dbcolumn"></a>db_column
Zadaný sloupec se váže k proměnné v dané sadě řádků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ db_column(   
   ordinal,   
   dbtype,   
   precision,   
   scale,   
   status,   
   length   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `ordinal`  
 Počet pořadí sloupců (**DBCOLUMNINFO** pořadí) nebo název sloupce (ANSI nebo Unicode string) odpovídající pole v sadě řádků, do kterého se mají vázat data. Pokud používáte čísla, můžete přeskočit po sobě jdoucích řadové číslovky (například: 1, 2, 3, 5). Název může obsahovat mezery, pokud ji podporuje zprostředkovatele OLE DB, které používáte. Například můžete použít některý z následujících formátů:  
  
```  
[db_column("2")] TCHAR szCity[30];  
[db_column(L"city_name")] TCHAR szCity[30];  
```  
  
 *Hodnota DbType* (volitelné)  
 OLE DB [typ ukazatele](https://msdn.microsoft.com/en-us/library/ms711251.aspx) položku sloupce.  
  
 *přesnost* (volitelné)  
 Přesnost má být použit pro vstupní sloupec. Podrobnosti najdete v tématu Popis `bPrecision` element [DBBINDING struktura](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *škálování* (volitelné)  
 Škálování, který se má použít pro sloupec položku. Podrobnosti najdete v tématu Popis `bScale` element [DBBINDING struktura](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *Stav* (volitelné)  
 Členské proměnné používané pro udržení stav daného sloupce. Stav označuje, zda hodnota sloupce je hodnota dat nebo s jinou hodnotou, například **NULL**. Možné hodnoty, najdete v části [stav](https://msdn.microsoft.com/en-us/library/ms722617.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
 *Délka* (volitelné)  
 Členské proměnné používané pro udržení velikost sloupce v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 **db_column** váže zadaného sloupce tabulky k proměnné v dané sadě řádků. Ji vymezuje data členů, které mohou být zahrnuty v OLE DB `IAccessor`– na základě vazby. Tento atribut Nastaví mapu sloupce, které jsou obvykle definovány pomocí makra příjemce technologie OLE DB [BEGIN_COLUMN_MAP](../data/oledb/begin-column-map.md), [END_COLUMN_MAP](../data/oledb/end-column-map.md), a [COLUMN_ENTRY](../data/oledb/column-entry.md). Tyto manipulaci s OLE DB [struktura DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) pro vazbu zadaný sloupec. Každý člen označit s **db_column** atribut bude zabírat jedna položka v mapě sloupce ve formě položku sloupce. Proto volat tento atribut kde vložíte mapy sloupce, který je ve třídě příkazu nebo tabulky.  
  
 Použití **db_column** ve spojení s buď [db_table](../windows/db-table.md) nebo [db_command](../windows/db-command.md) atributy.  
  
 Pokud příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor přejmenuje třídy pro \_ *YourClassName*přistupujícího objektu, kde *YourClassName* je název, který jste zadali Třída a kompilátor také vytvoří třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd se zobrazí oba třídy.  
  
 Příklady tento atribut použít v aplikaci, najdete v tématu ukázky [AtlAgent](http://msdn.microsoft.com/en-us/52bef5da-c1a0-4223-b4e6-9e464b6db409), a [MultiRead](http://msdn.microsoft.com/en-us/5a2a915a-77dc-492f-94b2-1b809995dd5e).  
  
## <a name="example"></a>Příklad  
 Tato ukázka tabulka, která se vytvoří vazbu mezi sloupci **dlouho** – datový člen a určuje stav a délka pole.  
  
```  
// db_column_1.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   DBSTATUS m_dwProductIDStatus;  
   DBLENGTH m_dwProductIDLength;  
  
   [ db_column("1", status="m_dwProductIDStatus", length="m_dwProductIDLength") ] LONG m_ProductID;  
};  
```  
  
## <a name="example"></a>Příklad  
 Tato ukázka váže čtyři sloupce, abyste **dlouho**, řetězec znaků, časovým razítkem a **DB_NUMERIC** celé číslo, v tomto pořadí.  
  
```  
// db_column_2.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_command(L"Select * from Products") ]  
class CProducts {  
   [db_column("1")] LONG m_OrderID;  
   [db_column("2")] TCHAR m_CustomerID[6];  
   [db_column("4")] DB_NUMERIC m_OrderDate;     
   [db_column("7", dbtype="DBTYPE_NUMERIC")] DB_NUMERIC m_ShipVia;  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `struct`, člen, – metoda|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy příjemce technologie OLE DB](../windows/ole-db-consumer-attributes.md)   
 [Class – atributy](../windows/class-attributes.md)   
