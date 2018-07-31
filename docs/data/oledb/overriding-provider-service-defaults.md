---
title: Přepsání výchozích hodnot služby zprostředkovatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 106d1991f5312065aa78330888e55383d1f9506a
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337015"
---
# <a name="overriding-provider-service-defaults"></a>Přepsání výchozích hodnot služby zprostředkovatele
Hodnota registru zprostředkovatele pro OLEDB_SERVICES se vrátí jako výchozí hodnota [DBPROP_INIT_OLEDBSERVICES](https://msdn.microsoft.com/library/ms716898.aspx) inicializace vlastnosti na objektu zdroje dat.  
  
 Jako položka registru existuje, zobrazují se objekty zprostředkovatele a uživatel může přepsat poskytovatele výchozí nastavení pro povolené služby tak, že nastavíte `DBPROP_INIT_OLEDBSERVICES` vlastnost před inicializací. Pokud chcete povolit nebo zakázat určité služby, uživatel obvykle získá aktuální hodnotu `DBPROP_INIT_OLEDBSERVICES` vlastnost, nastaví nebo vymaže bit pro konkrétní vlastnost, která má být povolena nebo zakázána a obnoví vlastnost. `DBPROP_INIT_OLEDBSERVICES` můžete nastavit přímo v OLE DB nebo v připojovacím řetězci, který je předán ADO nebo `IDataInitialize::GetDatasource`. Odpovídající hodnoty pro povolení nebo zákaz jednotlivé služby jsou uvedené v následující tabulce.  
  
|Povolené výchozí služby|Hodnota vlastnosti DBPROP_INIT_OLEDBSERVICES|Hodnota připojovacího řetězce|  
|------------------------------|------------------------------------------------|--------------------------------|  
|Všechny služby (výchozí)|`DBPROPVAL_OS_ENABLEALL`|"Služeb OLE DB = -1;"|  
|Všechny s výjimkou sdružování a AutoEnlistment|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"Služeb OLE DB = -4;"|  
|Všechny s výjimkou klientský kurzor|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Služeb OLE DB = -5;"|  
|Všechny s výjimkou sdružování AutoEnlistment a klientský kurzor|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Služeb OLE DB = -7;"|  
|Žádné služby.|`~DBPROPVAL_OS_ENABLEALL`|"Služeb OLE DB = 0;"|  
  
 Pokud položka registru neexistuje pro zprostředkovatele, správce součástí nebude agregovat objekty zprostředkovatele a žádné služby, který bude vyvolán, i v případě, že explicitně požadavku uživatele.  
  
## <a name="see-also"></a>Viz také  
 [Sdružování prostředků](https://msdn.microsoft.com/library/ms713655.aspx)   
 [Jak zákazníci používají fondy prostředků](https://msdn.microsoft.com/library/ms715907.aspx)   
 [Jak poskytovatelů efektivně pracovat s fondy prostředků](https://msdn.microsoft.com/library/ms714906.aspx)   
 [Povolení a zakázání služeb OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)