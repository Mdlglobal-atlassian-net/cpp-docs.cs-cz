---
title: 4. Proměnné prostředí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edd4f795a3511358d2b95b93e180b9b21b964dd2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690998"
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