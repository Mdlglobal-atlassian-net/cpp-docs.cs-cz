---
title: Zastaralé konvence volání
ms.date: 11/04/2016
f1_keywords:
- __fortran
- __pascal
- __syscall
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
ms.openlocfilehash: 86c75c779158d9f191dd015410cf16c9ce25690d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587990"
---
# <a name="obsolete-calling-conventions"></a>Zastaralé konvence volání

## <a name="microsoft-specific"></a>Specifické pro Microsoft

**__Pascal**, **__fortran**, a **__syscall** již nejsou podporovány konvence volání. Jejich funkce lze simulovat pomocí jedné z podporovaných konvencí volání a vhodné možnosti linkeru.

\<Windows.h > nyní podporuje makro WINAPI, které se přeloží na odpovídající konvenci volání pro cíl. Použití rozhraní WINAPI, kde jste dříve používali PASCAL nebo **__far \__pascal**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)