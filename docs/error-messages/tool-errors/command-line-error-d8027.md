---
title: Chyba příkazového řádku D8027 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8027
dev_langs:
- C++
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc93edb939001a1e1bed5d3f7a4113e8483e81dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33296117"
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