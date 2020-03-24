---
title: Závažná chyba C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: 6c0be830cb56b760f1397ea2b2f81b42a87e9ba6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203083"
---
# <a name="fatal-error-c1383"></a>Závažná chyba C1383

možnost kompilátoru/GL není kompatibilní s nainstalovanou verzí modulu CLR (Common Language Runtime).

K C1383 dochází při použití předchozí verze modulu CLR (Common Language Runtime) s novějším kompilátorem a při kompilaci s možností **/CLR** a **/GL.** .

Chcete-li tuto chybu vyřešit, buď Nepoužívejte **/GL** s **/CLR** , nebo nainstalujte verzi modulu Common Language Runtime, který byl dodán s vaším kompilátorem.

Další informace naleznete v tématu [/CLR (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) a [/GL (celá optimalizace programu)](../../build/reference/gl-whole-program-optimization.md).
