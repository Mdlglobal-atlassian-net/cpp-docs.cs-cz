---
title: Vnitřní objekty a vložené sestavení
ms.date: 11/04/2016
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
ms.openlocfilehash: 033225259c0a33414fe45eba313bb1f1c94eb379
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515099"
---
# <a name="intrinsics-and-inline-assembly"></a>Vnitřní objekty a vložené sestavení

Jeden omezení x64 kompilátoru je vložený assembler nepodporují. To znamená, že funkce, které nelze zapsat do jazyka C nebo C++ se buď musí být napsány podprogramy nebo jako vnitřní funkce podporovány kompilátorem. Některé funkce jsou citlivé na výkon, některé nikoli. Citlivé na výkon funkce by měla být implementována jako vnitřní funkce.

Vnitřní objekty podporovány kompilátorem jsou popsány v [vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md).

## <a name="see-also"></a>Viz také

[x64 – softwarové konvence](../build/x64-software-conventions.md)