---
title: 1. Úvod | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 883af9cb48a0fb13dbb9a758d6f8174096d4c0c3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685837"
---
# <a name="1-introduction"></a>1. Úvod
Tento dokument určuje kolekci proměnných prostředí, které lze použít k určení stupně paralelního zpracování sdílené paměti v programy C a C++, direktivy kompilátoru a funkce knihovny. Funkce popsané v tomto dokumentu se souhrnně označuje jako *OpenMP C/C++ rozhraní API (Application Program)*. Cílem této specifikaci je zajistit model pro paralelní programování, který umožňuje programu, který má být přenosná v architekturách sdílené paměti od různých výrobců. Rozhraní API jazyka C/C++ OpenMP bude podporovat kompilátory od více dodavatelů. Další informace o OpenMP, včetně *OpenMP Fortran aplikační programovací rozhraní*, naleznete na následujícím webu:  
  
 [http://www.openmp.org](http://www.openmp.org)  
  
 Direktivy, funkce knihovny a proměnné definované v tomto dokumentu vám umožní uživatelům vytvářet a spravovat paralelní programy při umožňující přenositelnost. Direktivy rozšířit C a C++ sekvenční programování modelu s jeden program víc dat (SPMD) konstrukce, konstrukce pro sdílení práce a konstrukce synchronizace a poskytují podporu pro sdílení a privatizace data. Kompilátory, které podporují OpenMP C a C++ API bude obsahovat možnost příkazového řádku pro kompilátor, která aktivuje a umožňuje výklad všechny direktivy kompilátoru OpenMP.