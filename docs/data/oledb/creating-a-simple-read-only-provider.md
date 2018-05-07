---
title: Vytvoření jednoduchého zprostředkovatele pouze pro čtení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2662a071f443967b921c4a8db27713bc7c3e8bb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-simple-read-only-provider"></a>Vytvoření jednoduchého zprostředkovatele pouze pro čtení
Po vytvoření zprostředkovatele OLE DB pomocí Průvodce projektu knihovny ATL a Průvodce zprostředkovatele ATL technologie OLE DB, můžete přidat další funkce, které chcete podporovat. Spusťte návrhu svého poskytovatele tak, že prověří jaký typ dat budete odesílat k příjemce a za jakých podmínek. Je velmi důležité určit, jestli potřebujete podporovat příkazy, transakce a další volitelné objekty. Dobrý návrh předem bude rychlost implementace a testování.  
  
 V příkladu se zobrazí ve dvou částech:  
  
-   První část ukazuje postup [vytvoření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md) , který čte dvojici řetězců.  
  
-   Druhá část ukazuje postup [Vylepšení jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md) přidáním `IRowsetLocate` rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)