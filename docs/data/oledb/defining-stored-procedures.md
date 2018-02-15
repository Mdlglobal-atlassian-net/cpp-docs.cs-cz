---
title: "Definování uložených procedur | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, syntax
- OLE DB, stored procedures
- stored procedures, defining
- stored procedures, OLE DB
ms.assetid: 54949b81-3275-4dd9-96e4-3eda1ed755f2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5f11994ea34e79d9a4d4d8ae5c13ad67529755e0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="defining-stored-procedures"></a>Definování uložených procedur
Před voláním uložené procedury, je nutné nejprve definovat, pomocí [DEFINE_COMMAND](../../data/oledb/define-command.md) makro. Když definujete příkaz, parametry s otazníkem (?) označují jako parametr značky:  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{INSERT {name, phone} into shippers  (?,?)}")  
```  
  
 Všimněte si, že syntaxe (použití složené závorky a tak dále) používané v příklady kódu v tomto tématu je specifická pro SQL Server. Syntaxe, které budete používat v uložené procedury mohou lišit podle zprostředkovatele, které používáte.  
  
 V dalším kroku v mapě parametr zadejte parametry, které jste použili v příkazu výpis parametrů v pořadí, ve kterém nastávají v příkazu:  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(1, m_Name)   // name corresponds to first '?' param  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Phone)  // phone corresponds to second '?' param  
END_PARAM_MAP()  
```  
  
 Předchozí příklad definuje uložené procedury, protože probíhá. Obvykle pro efektivní opětovné použití kódu, databáze obsahuje sadu předdefinovaných uložené procedury s názvy, například "Prodeje podle rok" nebo "dt_adduserobject". Můžete zobrazit jejich definice pomocí správce systému SQL Server Enterprise. Volání je následujícím způsobem (umístění '?' parametry závisí na rozhraní uložené procedury):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL \"Sales by Year\" (?,?) }")  
DEFINE_COMMAND(CMySProcAccessor, _T("{CALL dbo.dt_adduserobject (?,?) }")  
```  
  
 V dalším kroku deklarujte třídu příkazu:  
  
```  
class CMySProc : public CCommand<CAccessor<CMySProcAccessor>>  
```  
  
 Nakonec volání uložené procedury v `OpenRowset` následujícím způsobem:  
  
```  
CSession m_session;  

HRESULT OpenRowset()  
{  
   return CCommand<CAccessor<CMySProcAccessor>>::Open(m_session);  
}  
```  
  
 Všimněte si, že můžete definovat uložené procedury pomocí atributu databáze [db_command](../../windows/db-command.md) následujícím způsobem:  
  
```  
db_command("{ ? = CALL dbo.dt_adduserobject }")  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití uložených procedur](../../data/oledb/using-stored-procedures.md)