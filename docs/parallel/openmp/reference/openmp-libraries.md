---
title: OpenMP – knihovny | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9a4ccfefeaeb9446731027db44b849233bfefd6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391212"
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

## <a name="see-also"></a>Viz také

[Referenční dokumentace knihoven](../../../parallel/openmp/reference/openmp-library-reference.md)