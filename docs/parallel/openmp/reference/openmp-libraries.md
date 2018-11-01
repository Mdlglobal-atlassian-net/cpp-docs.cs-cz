---
title: OpenMP – knihovny
ms.date: 10/24/2018
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
ms.openlocfilehash: 75f772c953a2120a02f72d8bdfc73c1baaaef390
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530335"
---
# <a name="openmp-libraries"></a>OpenMP – knihovny

Tento článek popisuje soubory .lib, které tvoří OpenMP – knihovny runtime v jazyce Visual C++.

Následující knihovny obsahují funkce Visual C++ OpenMP – knihovny run-time.

|OpenMP – knihovny run-time|Vlastnosti|
|------------------------------|---------------------|
|VCOMP. LIB|Odkaz s více vlákny, dynamické (knihovnu importu VCOMP. LIB).|
|VCOMPD.LIB|Odkaz s více vlákny, dynamické (knihovnu importu VCOMPD. VÍKO) (ladění)|

Pokud _DEBUG je definována v kompilaci a `#include omp.h` je ve zdrojovém kódu, VCOMPD. Lib – bude výchozí lib. V opačném případě VCOMP. LIB se použije.

Můžete použít [: / NODEFAULTLIB (ignorování knihoven)](../../../build/reference/nodefaultlib-ignore-libraries.md) odebrat výchozí lib a explicitní propojení s lib podle vašeho výběru.

OpenMP – knihovny DLL v adresáři distribuovatelné součásti Visual C++ a potřebujete distribuovat s aplikací, které používají OpenMP.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace knihoven](openmp-library-reference.md)
