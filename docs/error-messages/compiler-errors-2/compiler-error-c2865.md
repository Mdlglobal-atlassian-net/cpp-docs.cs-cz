---
title: Chyba kompilátoru C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: e95714f7a10c1c25562e8b12025ede486e66cff8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532730"
---
# <a name="compiler-error-c2865"></a>Chyba kompilátoru C2865

'function': Neplatné porovnání pro handle_or_pointer

Můžete porovnat odkazy na [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md) nebo spravované odkazové typy pouze pro rovnost zobrazíte, pokud se odkazují na stejný objekt (==) nebo k různým objektům (! =).

Nelze porovnávat je pro řazení, protože modul .NET runtime může být přesunout spravované objekty v okamžiku, změna výsledek testu.