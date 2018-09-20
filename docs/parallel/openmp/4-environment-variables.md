---
title: 4. Proměnné prostředí | Dokumentace Microsoftu
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
ms.openlocfilehash: aec56dad334dcd27de2068e660ff8ec5a6e72f90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415486"
---
# <a name="4-environment-variables"></a>4. Proměnné prostředí

Tato kapitola popisuje rozhraní API C++ a C OpenMP – proměnné prostředí (nebo ekvivalentní mechanismů specifická pro platformu), které nastavují spuštění paralelního kódu.  Názvy proměnných prostředí musí být uváděny velkými písmeny. Hodnoty přiřazené k jejich jsou malá a velká písmena a může obsahovat úvodní a koncové prázdné znaky.  Úpravy hodnot po spuštění programu se ignorují.

Proměnné prostředí jsou následující:

- **OMP_SCHEDULE** nastaví velikost typu a bloků dat za běhu plánu.

- **OMP_NUM_THREADS** nastaví počet vláken během provádění.

- **OMP_DYNAMIC** povolí nebo zakáže dynamické úpravy počtu vláken.

- **OMP_NESTED** povolí nebo zakáže vnořené paralelismu.

Příklady v této kapitole pouze ukazují, jak tyto proměnné může být nastaveno v prostředích Unix C prostředí (kontextová nápověda). V Korn prostředí a prostředí DOS akce, které jsou podobné, následujícím způsobem:

Kontextová nápověda: setenv OMP_SCHEDULE "dynamické"

ksh: export OMP_SCHEDULE = "dynamické"

DOS: nastavte OMP_SCHEDULE = "dynamické"