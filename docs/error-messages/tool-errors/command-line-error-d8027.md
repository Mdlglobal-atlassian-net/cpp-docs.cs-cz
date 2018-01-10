---
title: "Chyba příkazového řádku D8027 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D8027
dev_langs: C++
helpviewer_keywords: D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1bd66688dbf582bf38fb9a0a3706663db3cf145d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="command-line-error-d8027"></a>Chyba příkazového řádku D8027
nelze provést, součásti.  
  
 Kompilátor nemůže spustit součást dané kompilátoru nebo linkeru.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Není dostatek paměti pro načtení komponentu. Pokud je NMAKE vyvolána kompilátor, spusťte kompilátoru mimo souboru pravidel.  
  
2.  V aktuálním operačním systému nelze spustit komponentu. Zkontrolujte, zda body cesty spustitelné soubory vhodné pro váš operační systém.  
  
3.  Součást byla poškozena. Překopírovat komponentu z disků distribuce, pomocí instalačního programu.  
  
4.  Možnost byl nesprávně zadán. Příklad:  
  
    ```  
    cl /B1 file1.c  
    ```