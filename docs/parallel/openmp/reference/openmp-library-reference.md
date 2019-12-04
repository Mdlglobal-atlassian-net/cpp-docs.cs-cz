---
title: OpenMP – Referenční dokumentace knihoven
ms.date: 12/02/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: b61eb356b782b3cd17557827734a706e0761a2a8
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810748"
---
# <a name="openmp-library-reference"></a>OpenMP – Referenční dokumentace knihoven

Obsahuje odkazy na konstrukce používané v rozhraní OpenMP API.

Visual C++ implementace standardu OpenMP zahrnuje následující konstrukce.

|Konstrukce|Popis|
|---------------|-----------------|
|[Direktivy](openmp-directives.md)|Obsahuje odkazy na direktivy používané v rozhraní OpenMP API.|
|[Klauzule](openmp-clauses.md)|Obsahuje odkazy na klauzule používané v rozhraní OpenMP API.|
|[Funkce](openmp-functions.md)|Obsahuje odkazy na funkce používané v rozhraní OpenMP API.|
|[Proměnné prostředí](openmp-environment-variables.md)|Obsahuje odkazy na proměnné prostředí používané v rozhraní OpenMP API.|

Funkce běhové knihovny jazyka Visual C++ OpenMP jsou obsaženy v následujících knihovnách.

|Knihovna run-time OpenMP|Charakteristika|
|------------------------------|---------------------|
|VCOMP. Knihovna|Multithreading, dynamické propojení (import knihovny pro VCOMP140. DLL).|
|VCOMPD.LIB|Multithreading, dynamické propojení (import knihovny pro VCOMP140D. DLL) (ladění)|

Pokud je v kompilaci definováno _DEBUG a je-li `#include <omp.h>` ve zdrojovém kódu, VCOMPD. LIB bude výchozí lib, jinak VCOMP. Použije se LIB.

Můžete použít [/NODEFAULTLIB (Ignorovat knihovny)](../../../build/reference/nodefaultlib-ignore-libraries.md) k odebrání výchozí knihovny LIB a explicitní propojení s knihovnou dle vašeho výběru.

Knihovny DLL OpenMP jsou ve Visual C++ Redistributable adresáři a je nutné je distribuovat s aplikacemi, které používají OpenMP.

## <a name="see-also"></a>Viz také:

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
