---
title: "Přepsání výchozích hodnot služby zprostředkovatele | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9185f1eb3640a4baeb8f7cc1d7b20169c980a8e1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overriding-provider-service-defaults"></a>Přepsání výchozích hodnot služby zprostředkovatele
Hodnota registru zprostředkovatele pro **OLEDB_SERVICES** se vrátí jako výchozí hodnota [DBPROP_INIT_OLEDBSERVICES](https://msdn.microsoft.com/en-us/library/ms716898.aspx) inicializace vlastnost v objektu zdroje dat.  
  
 Také položku registru existuje, je agregován objekty daného zprostředkovatele a uživatele můžete přepsat výchozí nastavení pro povolené služby nastavením zprostředkovatele **DBPROP_INIT_OLEDBSERVICES** vlastnost před inicializací. Pokud chcete povolit nebo zakázat určitou službu, uživatel obecně získá aktuální hodnota **DBPROP_INIT_OLEDBSERVICES** vlastnost, nastaví nebo vymaže bit pro konkrétní vlastnost, která má být povolena nebo zakázána a resetuje vlastnost. **DBPROP_INIT_OLEDBSERVICES** lze nastavit přímo v OLE DB nebo v připojovacím řetězci předaný ADO nebo **IDataInitialize::GetDatasource**. Odpovídající hodnoty, které mají povolit nebo zakázat jednotlivé služby jsou uvedeny v následující tabulce.  
  
|Povolené výchozí služby|Hodnota vlastnosti DBPROP_INIT_OLEDBSERVICES|Hodnota v připojovacím řetězci|  
|------------------------------|------------------------------------------------|--------------------------------|  
|Všechny služby (výchozí)|**DBPROPVAL_OS_ENABLEALL**|"Služeb OLE DB = -1;"|  
|Všechny kromě sdružování a AutoEnlistment|**DBPROPVAL_OS_ENABLEALL &**<br /><br /> **~ DBPROPVAL_OS_RESOURCEPOOLING &**<br /><br /> **~ DBPROPVAL_OS_TXNENLISTMENT**|"Služeb OLE DB = -4;"|  
|Všechny kromě kurzoru klienta|**DBPROPVAL_OS_ENABLEALL** &<br /><br /> ~**DBPROPVAL_OS_CLIENTCURSOR**|"Služeb OLE DB = -5;"|  
|Všechny kromě sdružování AutoEnlistment a klienta kurzoru|**DBPROPVAL_OS_ENABLEALL &**<br /><br /> **~ DBPROPVAL_OS_TXNENLISTMENT &**<br /><br /> **~ DBPROPVAL_OS_CLIENTCURSOR**|"Služeb OLE DB = -7;"|  
|Žádné služby|~**DBPROPVAL_OS_ENABLEALL**|"Služeb OLE DB = 0;"|  
  
 Pokud položku registru neexistuje pro zprostředkovatele, správci komponent nebudou agregovat objekty daného zprostředkovatele a žádné služby, který bude vyvolán, i když explicitně požadované uživatelem.  
  
## <a name="see-also"></a>Viz také  
 [Sdružování prostředků](https://msdn.microsoft.com/en-us/library/ms713655.aspx)   
 [Jak uživatelé používat sdílení prostředků ve fondech](https://msdn.microsoft.com/en-us/library/ms715907.aspx)   
 [Jak zprostředkovatelé pracovat efektivně sdílení prostředků ve fondech](https://msdn.microsoft.com/en-us/library/ms714906.aspx)   
 [Povolení a zakázání služeb OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)