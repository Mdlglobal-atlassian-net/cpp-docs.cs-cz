---
title: "Výstupní parametry | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB, stored procedures
- stored procedures, calling
- stored procedures, parameters
- procedure calls
- procedure calls, stored procedures
ms.assetid: 4f7c2700-1c2d-42f3-8c9f-7e83962b2442
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d1f1a4c84c4567b325bb19e3696170f7960b46b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="output-parameters"></a>Výstupní parametry
Volání uložené procedury je podobná vyvolání příkazu SQL. Hlavní rozdíl je, že uložené procedury použít výstupní parametry (nebo "výstupní parametry") a návratové hodnoty.  
  
 V následující uložené procedury, první '? 'je návratovou hodnotu (phone) a druhá'?' je vstupní parametr (název):  
  
```  
DEFINE_COMMAND(CMySProcAccessor, _T("{ ? = SELECT phone FROM shippers WHERE name = ? }")  
```  
  
 Zadejte vstupní a výstupní parametry v mapě parametr:  
  
```  
BEGIN_PARAM_MAP(CMySProcAccessor)  
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)  
   COLUMN_ENTRY(1, m_Phone)   // Phone is the return value  
   SET_PARAM_TYPE(DBPARAMIO_INPUT)  
   COLUMN_ENTRY(2, m_Name)   // Name is the input parameter  
END_PARAM_MAP()  
```  
  
 Aplikace musí zpracovávat výstup z uložené procedury. Různé zprostředkovatele OLE DB vrací výstupní parametry a návratové hodnoty v různou dobu během zpracování výsledku. Zprostředkovatel Microsoft OLE DB pro SQL Server (SQLOLEDB) například není výstupní parametry a návratové kódy až po příjemce načte nebo nastaví výsledek vrácený uloženou proceduru zruší. Výstup se vrací v posledním TDS paketu ze serveru.  
  
## <a name="row-count"></a>Počet řádků.  
 Pokud použijete ke spuštění uložené procedury, která má výstupní parametry šablony příjemce technologie OLE DB, počet řádků není nastavena, dokud nezavřete sadu řádků.  
  
 Představte si třeba uložená procedura s sadu řádků a výstupním parametrem:  
  
```  
create procedure sp_test  
   @_rowcount integer output  
as  
   select top 50 * from test  
   @_rowcount = @@rowcount  
return 0  
```  
  
 @_rowcount Výstupní sestavy, kolik řádků ve skutečnosti vrátil tabulky test. Tuto uloženou proceduru však omezuje počet řádků, které mají být delší než 50. Například kdyby 100 řádků v testu rowcount by 50 (protože tento kód načte pouze prvních 50 řádků). Pokud by bylo pouze 30 řádků v tabulce, rowcount by byl 30. Je třeba volat **Zavřít** nebo **CloseAll** k naplnit výstupní parametr předtím načíst jeho hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Použití uložených procedur](../../data/oledb/using-stored-procedures.md)