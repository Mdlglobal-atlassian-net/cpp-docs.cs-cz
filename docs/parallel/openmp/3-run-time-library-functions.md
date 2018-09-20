---
title: 3. Funkce knihovny run-time | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c1a05df3b47c2bbf345bc0101f30ffb83b84967
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401844"
---
# <a name="3-run-time-library-functions"></a>3. Funkce knihovny run-time

Tato část popisuje funkce knihovny run-time OpenMP – C a C++. Záhlaví  **\<omp.h >** deklaruje dva typy, několik funkcí, které můžete použít k řízení a zadat dotaz na prostředí paralelní zpracování a uzamčení funkce, které slouží k synchronizaci přístupu k datům.

Typ **omp_lock_t** typ objektu, který je schopný reprezentovat, je k dispozici zámek, nebo vlákna je vlastníkem zámku. Tyto zámky se označují jako *jednoduché zámky*.

Typ **omp_nest_lock_t** je schopný reprezentovat buď typ objektu zámek je k dispozici, nebo identitu vlákna, která vlastní zámek a *vnoření počet* (popsaných níže). Tyto zámky se označují jako *vnořitelných zámků*.

Funkce knihovny jsou externí funkce s propojením "C".

Popisy v této kapitole jsou rozdělené do následujících témat:

- Funkce spouštěcího prostředí (viz [části 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) na stránce 35).

- Zamknout funkcí (viz [části 3.2](../../parallel/openmp/3-2-lock-functions.md) na stránce 41).