---
title: 1. Úvod
ms.date: 11/04/2016
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
ms.openlocfilehash: b365ff828fd7dc2b7d9d3136a4fbfb68c43902ce
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554710"
---
# <a name="1-introduction"></a>1. Úvod

Tento dokument určuje kolekci direktivy kompilátoru knihovních funkcí a proměnných prostředí, které lze použít k určení paralelismu sdílené paměti v aplikacích jazyka C a C++. Funkce popsané v tomto dokumentu se souhrnně říká *OpenMP – C/C++ rozhraní API (Application Program)*. Cílem této specifikace je k poskytnutí modelu pro paralelní programování umožňuje aplikaci mít přenosné mezi architekturami sdílené paměti od různých dodavatelů. Kompilátory od mnoha dodavatelů bude podporovat rozhraní API OpenMP – C/C++. Další informace o OpenMP, včetně *OpenMP až po Fortran Application Program Interface*, najdete na následujícím webu:

[http://www.openmp.org](http://www.openmp.org)

Direktivy, knihovních funkcí a proměnných prostředí definovaných v tomto dokumentu vám umožní uživatelům vytvářet a spravovat paralelních programů při umožňující přenositelnost. Direktivy rozšíření jazyka C a sekvenční programování C++ model jedné programu více dat (SPMD) konstrukce, konstrukce pro sdílení práce a konstrukce synchronizace a poskytují podporu pro sdílení a privatizace data. Kompilátory, které podporují OpenMP – C a C++ API bude zahrnovat možnost příkazového řádku pro kompilátor, který aktivuje a umožňuje výklad všechny direktivy OpenMP kompilátoru.