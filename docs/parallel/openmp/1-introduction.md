---
title: 1. Úvod | Dokumentace Microsoftu
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
ms.openlocfilehash: 4ce963d312d145e26567a5902f32e45735eb1d89
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438415"
---
# <a name="1-introduction"></a>1. Úvod

Tento dokument určuje kolekci direktivy kompilátoru knihovních funkcí a proměnných prostředí, které lze použít k určení paralelismu sdílené paměti v aplikacích jazyka C a C++. Funkce popsané v tomto dokumentu se souhrnně říká *OpenMP – C/C++ rozhraní API (Application Program)*. Cílem této specifikace je k poskytnutí modelu pro paralelní programování umožňuje aplikaci mít přenosné mezi architekturami sdílené paměti od různých dodavatelů. Kompilátory od mnoha dodavatelů bude podporovat rozhraní API OpenMP – C/C++. Další informace o OpenMP, včetně *OpenMP až po Fortran Application Program Interface*, najdete na následujícím webu:

[http://www.openmp.org](http://www.openmp.org)

Direktivy, knihovních funkcí a proměnných prostředí definovaných v tomto dokumentu vám umožní uživatelům vytvářet a spravovat paralelních programů při umožňující přenositelnost. Direktivy rozšíření jazyka C a sekvenční programování C++ model jedné programu více dat (SPMD) konstrukce, konstrukce pro sdílení práce a konstrukce synchronizace a poskytují podporu pro sdílení a privatizace data. Kompilátory, které podporují OpenMP – C a C++ API bude zahrnovat možnost příkazového řádku pro kompilátor, který aktivuje a umožňuje výklad všechny direktivy OpenMP kompilátoru.