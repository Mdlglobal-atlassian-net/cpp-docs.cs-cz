---
title: Vnitřní objekty a vložené sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6a87e577af339099eda56a3b9d91929a05253a43
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716245"
---
# <a name="intrinsics-and-inline-assembly"></a>Vnitřní objekty a vložené sestavení

Jeden omezení x64 kompilátoru je vložený assembler nepodporují. To znamená, že funkce, které nelze zapsat do jazyka C nebo C++ se buď musí být napsány podprogramy nebo jako vnitřní funkce podporovány kompilátorem. Některé funkce jsou citlivé na výkon, některé nikoli. Citlivé na výkon funkce by měla být implementována jako vnitřní funkce.

Vnitřní objekty podporovány kompilátorem jsou popsány v [vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md).

## <a name="see-also"></a>Viz také

[x64 – softwarové konvence](../build/x64-software-conventions.md)