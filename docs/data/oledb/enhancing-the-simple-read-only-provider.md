---
title: Rozšíření jednoduchého zprostředkovatele pouze pro čtení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7c88714e4e1651839cdc5fd4b92d3c5222aa08d0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33100015"
---
# <a name="enhancing-the-simple-read-only-provider"></a>Rozšíření jednoduchého zprostředkovatele pouze pro čtení
V této části ukazuje, jak zvýšit [jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md) vytvořené v předchozí části. `IRowsetLocateImpl` Vytvoří implementace `IRowsetLocate` rozhraní a přidá podporu záložky za vás.  
  
 Až budete mít funkční poskytovatele, můžete zvýšit, abyste se poskytovatele aktualizaci, zpracování transakcí nebo zvýšit výkon algoritmu načítání řádků. Většina vylepšení zprostředkovatelů zahrnuje přidání rozhraní ke stávající objekt COM.  
  
 V příkladu v následujících tématech posiluje mechanismus načítání řádku přidáním `IRowsetLocate` rozhraní k `CAgentRowset`. Témata ukazují, jak na:  
  
-   [Ujistěte se, RMyProviderRowset dědí IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).  
  
-   [Dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/creating-a-simple-read-only-provider.md)