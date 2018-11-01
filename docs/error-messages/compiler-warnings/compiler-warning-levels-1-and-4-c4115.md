---
title: Kompilátor upozornění (úrovně 1 a 4) C4115
ms.date: 11/04/2016
f1_keywords:
- C4115
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
ms.openlocfilehash: 20e44eba3b6f6079e6f37b7cf33fa530a996e829
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462956"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Kompilátor upozornění (úrovně 1 a 4) C4115

'type': Pojmenovaná definice typu v závorkách

Daný symbol se používá k definování struktury, sjednocení nebo výčtového typu uvnitř výraz v závorkách. Rozsahu této definice mohou neočekávané.

Definici ve volání funkce jazyka C, má globální obor. Ve volání jazyka C++ má tato definice ve stejném rozsahu jako volané funkce.

Toto upozornění může být také způsobeno deklarátory mezi kulaté závorky (například prototypů), které nejsou výrazy se závorkami.

Toto je upozornění úrovně 1 s programy v jazyce C++ a C programech zkompilovaných pod kompatibility ANSI (/Za). V opačném případě je úroveň 3.