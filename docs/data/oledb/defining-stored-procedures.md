---
title: Definování uložených procedur | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2856418da13cc80d47c10295234b47813071a4ec
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336950"
---
# <a name="defining-stored-procedures"></a>Definování uložených procedur
Před volání uložené procedury, musíte nejdřív definovat, pomocí [DEFINE_COMMAND](../../data/oledb/define-command.md) – makro. Při definování příkazu parametry s otazníkem (?) označují jako parametr značky:  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
 Všimněte si, že syntaxe (použití závorek a tak dále) používané v příkladech kódu v tomto tématu je specifická pro SQL Server. Syntaxe používaná v uložených procedurách může lišit podle poskytovatele, který používáte.  
  
 V dalším kroku v mapě parametr zadejte parametry, které jste použili v příkazu, který obsahuje seznam parametrů v pořadí, ve kterém nastávají v příkazu:  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
 Předchozí příklad definuje uloženou proceduru, jak funguje. Obvykle pro efektivní použití kódu databáze obsahuje sadu předdefinovaných uložené procedury s názvy, například "Sales by Year" nebo "dt_adduserobject." Můžete zobrazit jejich definice pomocí SQL Server Enterprise Manager. Následující volání (umístění "?" parametry závisí na rozhraní uložené procedury):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
 V dalším kroku deklarujte třídu příkazu:  
  
```cpp  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>  
```  
  
 Nakonec proveďte volání uložené procedury `OpenRowset` následujícím způsobem:  
  
```cpp  
CSession m_session;  

HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);  
}  
```  
  
 Všimněte si také, že můžete definovat uložené procedury pomocí atributu databáze [db_command](../../windows/db-command.md) následujícím způsobem:  
  
```cpp  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití uložených procedur](../../data/oledb/using-stored-procedures.md)