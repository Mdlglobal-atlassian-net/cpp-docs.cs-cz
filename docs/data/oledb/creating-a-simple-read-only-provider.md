---
title: "Vytvoření jednoduchého zprostředkovatele pouze pro čtení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 830ba99037607f4fc8ceac9bad451381c30c7786
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="creating-a-simple-read-only-provider"></a>Vytvoření jednoduchého zprostředkovatele pouze pro čtení
Po vytvoření zprostředkovatele OLE DB pomocí Průvodce projektu knihovny ATL a Průvodce zprostředkovatele ATL technologie OLE DB, můžete přidat další funkce, které chcete podporovat. Spusťte návrhu svého poskytovatele tak, že prověří jaký typ dat budete odesílat k příjemce a za jakých podmínek. Je velmi důležité určit, jestli potřebujete podporovat příkazy, transakce a další volitelné objekty. Dobrý návrh předem bude rychlost implementace a testování.  
  
 V příkladu se zobrazí ve dvou částech:  
  
-   První část ukazuje postup [vytvoření jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/implementing-the-simple-read-only-provider.md) , který čte dvojici řetězců.  
  
-   Druhá část ukazuje postup [Vylepšení jednoduchého zprostředkovatele pouze pro čtení](../../data/oledb/enhancing-the-simple-read-only-provider.md) přidáním `IRowsetLocate` rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)