---
title: 3. Funkce knihovny run-time
ms.date: 11/04/2016
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: e1d8d498be7f58bcf510025c67c539127f450824
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484094"
---
# <a name="3-run-time-library-functions"></a>3. Funkce knihovny run-time

Tato část popisuje funkce knihovny run-time OpenMP – C a C++. Záhlaví  **\<omp.h >** deklaruje dva typy, několik funkcí, které můžete použít k řízení a zadat dotaz na prostředí paralelní zpracování a uzamčení funkce, které slouží k synchronizaci přístupu k datům.

Typ **omp_lock_t** typ objektu, který je schopný reprezentovat, je k dispozici zámek, nebo vlákna je vlastníkem zámku. Tyto zámky se označují jako *jednoduché zámky*.

Typ **omp_nest_lock_t** je schopný reprezentovat buď typ objektu zámek je k dispozici, nebo identitu vlákna, která vlastní zámek a *vnoření počet* (popsaných níže). Tyto zámky se označují jako *vnořitelných zámků*.

Funkce knihovny jsou externí funkce s propojením "C".

Popisy v této kapitole jsou rozdělené do následujících témat:

- Funkce spouštěcího prostředí (viz [části 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) na stránce 35).

- Zamknout funkcí (viz [části 3.2](../../parallel/openmp/3-2-lock-functions.md) na stránce 41).