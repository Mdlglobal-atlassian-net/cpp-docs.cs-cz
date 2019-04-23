---
title: OpenMP – Referenční dokumentace knihoven
ms.date: 03/20/2019
ms.assetid: a25188c6-edde-43d0-84b5-780e797b08fc
ms.openlocfilehash: 6f4bbeca54bff1fc44a3576362edca9c30926d5a
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124691"
---
# <a name="openmp-library-reference"></a>OpenMP – Referenční dokumentace knihoven

Obsahuje odkazy na objektů, které používá v rozhraní API OpenMP.

Implementace jazyka Visual C++, OpenMP úrovně Standard zahrnuje následující konstrukce.

|Konstrukce|Popis|
|---------------|-----------------|
|[Direktivy](openmp-directives.md)|Obsahuje odkazy na direktivy použité v rozhraní API OpenMP.|
|[Klauzule](openmp-directives.md)|Obsahuje odkazy na použité v rozhraní API OpenMP – klauzule.|
|[Funkce](openmp-functions.md)|Obsahuje odkazy na funkcí používaných v rozhraní API OpenMP.|
|[Proměnné prostředí](openmp-environment-variables.md)|Obsahuje odkazy na proměnné prostředí použít v rozhraní API OpenMP.|

Vizuál C++ OpenMP – knihovny run-time funkcí je obsažena v následujících knihoven.

|OpenMP – knihovny run-time|Vlastnosti|
|------------------------------|---------------------|
|VCOMP. LIB|Odkaz s více vlákny, dynamické (knihovnu importu VCOMP. LIB).|
|VCOMPD.LIB|Odkaz s více vlákny, dynamické (knihovnu importu VCOMPD. VÍKO) (ladění)|

Pokud _DEBUG je definována v kompilaci a `#include omp.h` je ve zdrojovém kódu, VCOMPD. Lib – bude výchozí lib, v opačném případě VCOMP. LIB se použije.

Můžete použít [: / NODEFAULTLIB (ignorování knihoven)](../../../build/reference/nodefaultlib-ignore-libraries.md) odebrat výchozí lib a explicitní propojení s lib podle vašeho výběru.

OpenMP – knihovny DLL v adresáři distribuovatelné součásti Visual C++ a potřebujete distribuovat s aplikací, které používají OpenMP.

## <a name="see-also"></a>Viz také:

[OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)