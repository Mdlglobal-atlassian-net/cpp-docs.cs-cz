---
title: "4. Proměnné prostředí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5fcd308f21d66535a983e70506fe91afb5c7042f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="4-environment-variables"></a>4. Proměnné prostředí
Tato kapitola popisuje OpenMP C a C++ API proměnných prostředí (nebo ekvivalentní mechanismy specifických pro platformy), řídit spuštění paralelní kódu.  Názvy proměnných prostředí, musí být velkými písmeny. Hodnoty, které jsou jim přiřazeny jsou malá a velká písmena a může mít úvodní a koncové mezery.  Úpravy hodnot po spuštění programu se ignorují.  
  
 Proměnné prostředí jsou následující:  
  
-   **OMP_SCHEDULE** nastaví plán spuštění typu a bloku velikost.  
  
-   **OMP_NUM_THREADS** nastaví počet vláken, které se použijí při spuštění.  
  
-   **OMP_DYNAMIC** povolí nebo zakáže dynamické přizpůsobení počet vláken.  
  
-   **OMP_NESTED** povolí nebo zakáže vnořené stupně paralelního zpracování.  
  
 V příkladech v této kapitole pouze ukazují, jak tyto proměnné může být nastaveno v prostředích Unix C prostředí (kontextová nápověda). V Korn prostředí a prostředí DOS akce, které jsou podobné, následujícím způsobem:  
  
 Kontextová nápověda:  
 SETENV OMP_SCHEDULE "dynamická"  
  
 ksh:  
 Export OMP_SCHEDULE = "dynamická"  
  
 DOS:  
 nastavit OMP_SCHEDULE = "dynamická"