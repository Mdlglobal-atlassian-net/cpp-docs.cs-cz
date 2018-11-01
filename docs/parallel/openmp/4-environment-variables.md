---
title: 4. Proměnné prostředí
ms.date: 11/04/2016
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 0dec302762ad22fc3c7f6691ef63df1b07d5940d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456599"
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