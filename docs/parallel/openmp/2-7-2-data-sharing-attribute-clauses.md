---
title: 2.7.2 klauzule atributů pro sdílení dat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 47347d3c-18bd-441f-99cf-7737564c417f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ecc6efac6e3d7356e51dc0ec57009ca9e5a71890
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="272-data-sharing-attribute-clauses"></a>2.7.2 Klauzule atributů pro sdílení dat
Několik direktivy přijmout klauzule, které umožňují uživateli řídit sdílení atributy proměnných po dobu trvání oblasti. Sdílení klauzule atributů platí pouze pro proměnné v lexikální rozsah direktiva, na kterém se zobrazí v klauzuli. Ne všechny následující klauzule jsou povoleny na všechny direktivy. Seznam věty, které jsou platné na konkrétní – direktiva jsou popsány s direktivou.  
  
 Pokud je proměnná zobrazené, pokud paralelní nebo zjistil konstrukce pro sdílení práce se a proměnnou není zadán v klauzuli sdílení atribut nebo **threadprivate** direktivy, pak proměnná se sdílí. Statické proměnné, které jsou deklarované v rámci dynamické rozsah paralelní oblast sdílejí. Přidělené paměti haldy (například pomocí **malloc()** v jazyka C nebo C++ nebo **nové** operátor v jazyce C++) se sdílí. (Má ukazatel na tuto paměť, však může být privátní nebo sdílené.) Proměnné s dobou trvání automatické úložiště deklarované v rámci dynamické rozsah paralelní oblasti jsou privátní.  
  
 Většina klauzulích přijmout *seznamu proměnné* argument, který je textový soubor s oddělovači seznam proměnných, které jsou viditelné. Pokud proměnnou odkazuje v klauzuli sdílení dat atribut má typ odvozený z šablony a neexistují žádné další odkazy na tuto proměnnou v programu, chování není definován.  
  
 Všechny proměnné, které se zobrazují v rámci direktivy klauzule musí být viditelná. Klauzule může podle potřeby opakují, ale žádné proměnné je možné zadat více než jednu klauzuli, s tím rozdílem, že proměnné lze zadat v obou **firstprivate** a **lastprivate** klauzule.  
  
 Následující části popisují klauzule atributů pro sdílení dat:  
  
-   **privátní**, [části 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stránce 25.  
  
-   **firstprivate**, [části 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) na stránce 26.  
  
-   **lastprivate**, [části 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) na stránce 27.  
  
-   **sdílené**, [části 2.7.2.4](../../parallel/openmp/2-7-2-4-shared.md) na stránce 27.  
  
-   **výchozí**, [části 2.7.2.5](../../parallel/openmp/2-7-2-5-default.md) na stránce 28.  
  
-   **snížení**, [části 2.7.2.6](../../parallel/openmp/2-7-2-6-reduction.md) na stránce 28.  
  
-   **copyin**, [části 2.7.2.7](../../parallel/openmp/2-7-2-7-copyin.md) na stránce 31.  
  
-   **copyprivate**, [části 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stránce 32.