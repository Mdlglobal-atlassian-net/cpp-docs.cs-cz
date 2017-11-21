---
title: "CNoAccessor – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
dev_langs: C++
helpviewer_keywords: CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 99bd7cb23f34192f3fd634856193f6616a58af0c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cnoaccessor-class"></a>CNoAccessor – třída
Lze použít jako šablonu argumentu (`TAccessor`) pro šablony třídy, jako například `CCommand` a `CTable`, argument přistupujícího objektu třídy, které vyžadují.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CNoAccessor  
```  
  
## <a name="remarks"></a>Poznámky  
 Použití `CNoAccessor` jako argument šablony, když nechcete, aby třídy pro podporu parametry nebo výstupní sloupce.  
  
 `CNoAccessor`implementuje metodu se zakázaným inzerováním, z nichž každý odpovídají jiné metody přistupující objekt třídy:  
  
-   **BindColumns** -sváže sloupce přistupující objekty.  
  
-   `BindParameters`-Váže k sloupce parametrech vytvořený.  
  
-   **Vytvoření vazby** -vytvoří vazby.  
  
-   **Zavřít** -zavře přistupujícího objektu.  
  
-   `ReleaseAccessors`-Uvolní přístupové objekty vytvořené třídy.  
  
-   `FreeRecordMemory`-Uvolní všechny sloupce v aktuální záznam, který musí být uvolněno.  
  
-   `GetColumnInfo`-Získá informace o sloupci z otevřené sady řádků.  
  
-   `GetNumAccessors`-Načte počet přístupové objekty vytvořené třídy.  
  
-   `IsAutoAccessor`-Vrátí hodnotu true Pokud je během operace přesunu automaticky načíst data pro přistupující objekt.  
  
-   `GetHAccessor`-Načte popisovač přistupujícího objektu zadaného přistupujícího objektu.  
  
-   `GetBuffer`-Načte má ukazatel na záložku vyrovnávací paměti.  
  
-   **NoBindOnNullRowset** -brání datová vazba na prázdný sady řádků.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)