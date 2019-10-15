---
title: OpenMP – Referenční dokumentace knihoven
ms.date: 07/30/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: c63ae5ba7f04d8ee6bd02418792804373fa71e6b
ms.sourcegitcommit: 170f5de63b0fec8e38c252b6afdc08343f4243a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72348227"
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

|Knihovna run-time OpenMP|Svých|
|------------------------------|---------------------|
|VCOMP. Knihovna|Multithreading, dynamické propojení (import knihovny pro VCOMP. LIB).|
|VCOMPD. Knihovna|Multithreading, dynamické propojení (import knihovny pro VCOMPD. VÍKA) (ladění)|

Pokud je v kompilaci definováno _DEBUG a pokud `#include <omp.h>` je ve zdrojovém kódu, VCOMPD. LIB bude výchozí lib, jinak VCOMP. Použije se LIB.

Můžete použít [/NODEFAULTLIB (Ignorovat knihovny)](../../../build/reference/nodefaultlib-ignore-libraries.md) k odebrání výchozí knihovny LIB a explicitní propojení s knihovnou dle vašeho výběru.

Knihovny DLL OpenMP jsou ve Visual C++ Redistributable adresáři a je nutné je distribuovat s aplikacemi, které používají OpenMP.

## <a name="see-also"></a>Viz také:

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)
