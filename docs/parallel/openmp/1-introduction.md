---
title: "1. Úvod | Microsoft Docs"
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
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f850e236ebfd056da93700df06ec830e5a573284
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="1-introduction"></a>1. Úvod
Tento dokument určuje kolekci proměnných prostředí, které lze použít k určení stupně paralelního zpracování sdílené paměti v programy C a C++, direktivy kompilátoru a funkce knihovny. Funkce popsané v tomto dokumentu se souhrnně označuje jako *OpenMP C/C++ rozhraní API (Application Program)*. Cílem této specifikaci je zajistit model pro paralelní programování, který umožňuje programu, který má být přenosná v architekturách sdílené paměti od různých výrobců. Rozhraní API jazyka C/C++ OpenMP bude podporovat kompilátory od více dodavatelů. Další informace o OpenMP, včetně *OpenMP Fortran aplikační programovací rozhraní*, naleznete na následujícím webu:  
  
 [http://www.OpenMP.org](http://www.openmp.org)  
  
 Direktivy, funkce knihovny a proměnné definované v tomto dokumentu vám umožní uživatelům vytvářet a spravovat paralelní programy při umožňující přenositelnost. Direktivy rozšířit C a C++ sekvenční programování modelu s jeden program víc dat (SPMD) konstrukce, konstrukce pro sdílení práce a konstrukce synchronizace a poskytují podporu pro sdílení a privatizace data. Kompilátory, které podporují OpenMP C a C++ API bude obsahovat možnost příkazového řádku pro kompilátor, která aktivuje a umožňuje výklad všechny direktivy kompilátoru OpenMP.