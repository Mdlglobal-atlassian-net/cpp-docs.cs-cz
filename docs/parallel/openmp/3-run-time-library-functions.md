---
title: 3. Funkce běhové knihovny | Microsoft Docs
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
ms.openlocfilehash: d747f775509c6b3b2b95be51d95ea937816d3cd1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688112"
---
# <a name="3-run-time-library-functions"></a>3. Funkce běhové knihovny
Tato část popisuje funkce běhové knihovny jazyka OpenMP C a C++. Záhlaví  **\<omp.h >** deklaruje dva typy, několik funkcí, které slouží k řízení a dotazování paralelní provádění prostředí a uzamčení funkce, které slouží k synchronizaci přístup k datům.  
  
 Typ **omp_lock_t** je typ objektu, který umožňuje reprezentovat, že je k dispozici zámek, nebo že vlákno vlastní zámek. Tyto zámky se označují jako *jednoduché zámky*.  
  
 Typ **omp_nest_lock_t** je typ objektu, který umožňuje reprezentovat buď který zámek je k dispozici, nebo identitu vlákno, který je vlastníkem zámek a *vnoření počet* (popsaný níže). Tyto zámky se označují jako *nestable zámky*.  
  
 Funkce knihovny jsou externí funkce propojení "C".  
  
 Popisy v této kapitole jsou rozdělené do v následujících tématech:  
  
-   Funkce spouštěcího prostředí (viz [části 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) na stránce 35).  
  
-   Funkce uzamčení (viz [části 3.2](../../parallel/openmp/3-2-lock-functions.md) na stránce 41).