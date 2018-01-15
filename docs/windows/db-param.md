---
title: "db_param – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: vc-attr.db_param
dev_langs: C++
helpviewer_keywords: db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5224c406f6e10cd4ef9f0ed64fbdbd7c5cc8e62
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="dbparam"></a>db_param
Přidruží zadané členské proměnné vstupní nebo výstupní parametr a vymezuje proměnnou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      [ db_param(   
   ordinal,   
   paramtype="DBPARAMIO_INPUT",   
   dbtype,   
   precision,   
   scale,   
   status,   
   length  
) ]  
```  
  
#### <a name="parameters"></a>Parametry  
 `ordinal`  
 Číslo sloupce (**DBCOLUMNINFO** pořadí) odpovídající pole v sadě řádků, do kterého se mají vázat data.  
  
 *paramtype* (volitelné)  
 Typ nastavení parametru. Zprostředkovatelé podporují pouze typy vstupně-výstupní parametr, které podporují základní zdroj dat. Typ je kombinací jednoho nebo více **DBPARAMIOENUM** hodnoty:  
  
-   **DBPARAMIO_INPUT** vstupní parametr.  
  
-   **DBPARAMIO_OUTPUT** výstupní parametr.  
  
-   **DBPARAMIO_NOTPARAM** přistupující objekt nemá žádné parametry. Nastavení **eParamIO** na tuto hodnotu v řádku přístupové objekty upozorní uživatele, že parametry jsou ignorovány.  
  
 *Hodnota DbType* (volitelné)  
 OLE DB [typ ukazatele](https://msdn.microsoft.com/en-us/library/ms711251.aspx) položku sloupce.  
  
 *přesnost* (volitelné)  
 Přesnost má být použit pro vstupní sloupec. Podrobnosti najdete v tématu Popis **bPrecision** element [DBBINDING struktura](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *škálování* (volitelné)  
 Škálování, který se má použít pro sloupec položku. Podrobnosti najdete v tématu Popis **bScale** element [DBBINDING struktura](https://msdn.microsoft.com/en-us/library/ms716845.aspx)  
  
 *Stav* (volitelné)  
 Členské proměnné používané pro udržení stav daného sloupce. Stav označuje, zda hodnota sloupce je hodnota dat nebo s jinou hodnotou, například **NULL**. Možné hodnoty, najdete v části [stav](https://msdn.microsoft.com/en-us/library/ms722617.aspx) v *referenční příručka programátora technologie OLE DB*.  
  
 *Délka* (volitelné)  
 Členské proměnné používané pro udržení velikost sloupce v bajtech.  
  
## <a name="remarks"></a>Poznámky  
 **db_param –** definuje parametry, můžete použít v příkazech; proto ji používáte s **db_command**. Například můžete použít **db_param –** pro svázání parametrů v dotazu SQL nebo uložené procedury. Parametry v uložené proceduře jsou rozlišeny pomocí otazník (?) a byste měli vytvořit vazbu datových členů v pořadí, ve kterém se zobrazí parametry.  
  
 **db_param –** vymezuje data členů, které mohou být zahrnuty v OLE DB `ICommandWithParameters`– na základě vazby. Nastaví typ parametru (vstup nebo výstup), typ OLE DB, přesnost, měřítko, stav a délka zadaného parametru. Tento atribut vloží makra příjemce technologie OLE DB BEGIN_PARAM_MAP... END_PARAM_MAP. Každý člen označit s **db_param –** atribut bude zabírat jedna položka v mapě ve formě COLUMN_ENTRY.  
  
 **db_param –** se používá ve spojení s buď [db_table](../windows/db-table.md) nebo [db_command](../windows/db-command.md) atributy.  
  
 Pokud příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor přejmenuje třídy pro \_ *YourClassName*přistupujícího objektu, kde *YourClassName* je název, který jste zadali Třída a kompilátor také vytvoří třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd se zobrazí oba třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří třídu příkazu podle postupu SalesbyYear uložené v databázi Northwind. Ho přiřadí první parametr v uložené proceduře pomocí `m_RETURN_VALUE` proměnnou a definuje jako výstupní parametr. Se přidružuje poslední dva parametry (vstupu) s `m_Beginning_Date` a `m_Ending_Date`.  
  
 V následujícím příkladu `nOutput` proměnné s výstupní parametr.  
  
```  
// db_param.cpp  
// compile with: /LD  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
[ db_source(L"my_connection_string"),   
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")   
]  
struct CSalesbyYear {  
   DBSTATUS m_dwShippedDateStatus;  
   DBSTATUS m_dwOrderIDStatus;  
   DBSTATUS m_dwSubtotalStatus;  
   DBSTATUS m_dwYearStatus;  
  
   DBLENGTH m_dwShippedDateLength;  
   DBLENGTH m_dwOrderIDLength;  
   DBLENGTH m_dwSubtotalLength;  
   DBLENGTH m_dwYearLength;  
  
   // Bind columns  
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;  
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;  
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;  
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];  
  
   // Bind parameters  
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;  
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;  
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;  
};  
```  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="attribute-context"></a>Atribut kontextu  
  
|||  
|-|-|  
|**Platí pro**|**Třída**, `struct`, člen, metoda, místní|  
|**Opakovatelných**|Ne|  
|**Povinné atributy**|Žádné|  
|**Neplatné atributy**|Žádné|  
  
 Další informace o kontexty atributů najdete v tématu [kontexty atributů](../windows/attribute-contexts.md).  
  
## <a name="see-also"></a>Viz také  
 [Atributy příjemce technologie OLE DB](../windows/ole-db-consumer-attributes.md)   
