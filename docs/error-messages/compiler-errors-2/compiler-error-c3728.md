---
title: Chyba kompilátoru C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 68aa23843b0470f15f409b6f3b58624f979ccfae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454584"
---
# <a name="compiler-error-c3728"></a>Chyba kompilátoru C3728

'událost': událost nemá metodu raise

Metadata vytvořené pomocí jazyka, jako je C#, který neumožňuje událost vyvolána z vně třídy, ve kterém byl definován, je součástí [#using](../../preprocessor/hash-using-directive-cpp.md) směrnice a program Visual C++ pomocí CLR programování došlo k pokusu vyvolání události.

K vyvolání události aplikace vyvinuté v jazyce, jako je C#, je potřeba také definovat veřejnou metodu, která vyvolává událost třídy obsahující události.