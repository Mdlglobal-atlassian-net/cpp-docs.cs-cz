---
title: Chyba sestavení projektu PRJ0006 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0006
dev_langs:
- C++
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 151c22bf13c13de21e89a5c96185cf1c4c1ca349
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317476"
---
# <a name="project-build-error-prj0006"></a>Chyba sestavení projektu PRJ0006
Nelze otevřít dočasný soubor 'file'. Ujistěte se, že soubor existuje a že adresář není chráněna proti zápisu.  
  
 Visual C++ nelze vytvořit dočasný soubor během procesu vytváření. Příčiny tohoto stavu:  
  
-   Žádné dočasného adresáře.  
  
-   Jen pro čtení dočasný adresář.  
  
-   Nedostatek místa na disku.  
  
-   $(Intdir) – složka je buď jen pro čtení nebo obsahuje dočasné soubory, které jsou jen pro čtení.  
  
 Tato chyba nastane také následující chyba PRJ0007: Nelze vytvořit adresář' výstupní adresář". Chyba PRJ0007 znamená, že nelze vytvořit adresář $(IntDir), zdání vytváření dočasně souborů se také nezdaří.  
  
 Dočasné soubory se vytvoří vždy, když zadáte:  
  
-   Soubor odezvy.  
  
-   Vlastní krok sestavení.  
  
-   Události sestavení.