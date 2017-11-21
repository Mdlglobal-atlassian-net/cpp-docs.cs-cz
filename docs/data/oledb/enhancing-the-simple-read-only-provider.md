---
title: "Rozšíření jednoduchého zprostředkovatele pouze pro čtení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- read-only poviders [C++]
- IRowsetLocate class
- IRowsetLocate class, adding to OLE DB template providers
- simple read-only poviders [C++]
ms.assetid: cba0e09f-44c1-41c1-9456-332aa13dc158
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 30b87ecae6f479c912c937fb2ce23e1f9dc98da3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="enhancing-the-simple-read-only-provider"></a>Rozšíření jednoduchého zprostředkovatele pouze pro čtení
V této části ukazuje, jak zvýšit [jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md) vytvořené v předchozí části. `IRowsetLocateImpl`Vytvoří implementace `IRowsetLocate` rozhraní a přidá podporu záložky za vás.  
  
 Až budete mít funkční poskytovatele, můžete zvýšit, abyste se poskytovatele aktualizaci, zpracování transakcí nebo zvýšit výkon algoritmu načítání řádků. Většina vylepšení zprostředkovatelů zahrnuje přidání rozhraní ke stávající objekt COM.  
  
 V příkladu v následujících tématech posiluje mechanismus načítání řádku přidáním `IRowsetLocate` rozhraní k `CAgentRowset`. Témata ukazují, jak na:  
  
-   [Ujistěte se, RMyProviderRowset dědí IRowsetLocate](../../data/oledb/modifying-the-inheritance-of-rmyproviderrowset.md).  
  
-   [Dynamické určování sloupců vrácených příjemci](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/creating-a-simple-read-only-provider.md)