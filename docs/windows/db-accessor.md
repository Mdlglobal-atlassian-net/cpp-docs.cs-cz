---
title: db_accessor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- vc-attr.db_accessor
dev_langs:
- C++
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5faa84773fbf1fe15fd0223c97f0361f1215b149
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dbaccessor"></a>db_accessor
Skupiny **db_column** atributy, které jsou součástí `IAccessor`– na základě vazby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ db_accessor(   
   num,   
   auto   
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 *Poče*  
 Určuje číslo přistupujícího objektu (počítáno od nuly celé číslo indexu). Je nutné zadat čísla přistupujícího objektu ve vzestupném pořadí podle celá čísla nebo definované hodnoty.  
  
 *automaticky*  
 Logická hodnota, která určuje, zda je automaticky načte přistupujícího objektu (**TRUE**) nebo nebyla načtena (**FALSE**).  
  
## <a name="remarks"></a>Poznámky  
 **db_accessor** definuje přistupujícího OLE DB základní následné **db_column** a **db_param –** atributy v rámci stejné třídy nebo funkce. **db_accessor** je použitelné na úrovni člena a používá se do skupiny **db_column** atributy, které jsou součástí technologie OLE DB `IAccessor`– na základě vazby. Se používá ve spojení s buď **db_table** nebo **db_command** atributy. Volání metody tento atribut je podobná volání [BEGIN_ACCESSOR](../data/oledb/begin-accessor.md) a [END_ACCESSOR](../data/oledb/end-accessor.md) makra.  
  
 **db_accessor** generuje sadu řádků a provádí vazbu na odpovídající mapy přistupujícího objektu. Pokud není volána **db_accessor**přistupující objekt 0 se budou automaticky generovat a všechny sloupce vazby budou mapována na tento blok přistupujícího objektu.  
  
 **db_accessor** skupin databáze vazeb sloupců do jednoho nebo více přístupových objektů. Informace o scénářích, ve kterých budete muset použít několik přístupových objektů, najdete v části [použití více přístupových objektů pro sadu řádků](../data/oledb/using-multiple-accessors-on-a-rowset.md). Také v najdete v části "Uživatele záznam podporu pro několik přístupových objektů" [uživatelských záznamů](../data/oledb/user-records.md).  
  
 Pokud příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor přejmenuje třídy pro \_ *YourClassName*přistupujícího objektu, kde *YourClassName* je název, který jste zadali Třída a kompilátor také vytvoří třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd se zobrazí oba třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá **db_accessor** do skupiny sloupců v tabulce objednávky z databáze Northwind do dvou přístupových objektů. Přistupující objekt 0 je automatický přistupující objekt a přistupujícího objektu 1 není.  
  
```  
// cpp_attr_ref_db_accessor.cpp  
// compile with: /LD /link /OPT:NOREF  
#define _ATL_ATTRIBUTES  
#include <atlbase.h>  
#include <atldbcli.h>  
  
[ db_command(L"SELECT LastName, FirstName FROM Orders") ]  
class CEmployees {  
public:  
   [ db_accessor(0, TRUE) ];  
   [ db_column("1") ] LONG m_OrderID;  
   [ db_column("2") ] TCHAR m_CustomerID[6];  
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;   
  
   [ db_accessor(1, FALSE) ];  
   [ db_column("8") ] CURRENCY m_Freight;  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|Bloky atributů|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy příjemce technologie OLE DB](../windows/ole-db-consumer-attributes.md)   
