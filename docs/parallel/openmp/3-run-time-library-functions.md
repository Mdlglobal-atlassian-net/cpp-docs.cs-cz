---
title: "3. Funkce běhové knihovny | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f1cbedf8782c9c5ccb25bda3f8b43df8a526f268
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="3-run-time-library-functions"></a>3. Funkce běhové knihovny
Tato část popisuje funkce běhové knihovny jazyka OpenMP C a C++. Záhlaví  **\<omp.h >** deklaruje dva typy, několik funkcí, které slouží k řízení a dotazování paralelní provádění prostředí a uzamčení funkce, které slouží k synchronizaci přístup k datům.  
  
 Typ **omp_lock_t** je typ objektu, který umožňuje reprezentovat, že je k dispozici zámek, nebo že vlákno vlastní zámek. Tyto zámky se označují jako *jednoduché zámky*.  
  
 Typ **omp_nest_lock_t** je typ objektu, který umožňuje reprezentovat buď který zámek je k dispozici, nebo identitu vlákno, který je vlastníkem zámek a *vnoření počet* (popsaný níže). Tyto zámky se označují jako *nestable zámky*.  
  
 Funkce knihovny jsou externí funkce propojení "C".  
  
 Popisy v této kapitole jsou rozdělené do v následujících tématech:  
  
-   Funkce spouštěcího prostředí (viz [části 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) na stránce 35).  
  
-   Funkce uzamčení (viz [části 3.2](../../parallel/openmp/3-2-lock-functions.md) na stránce 41).