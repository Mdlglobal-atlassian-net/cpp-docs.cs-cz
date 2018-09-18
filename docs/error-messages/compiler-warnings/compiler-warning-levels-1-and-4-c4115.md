---
title: Upozornění (úrovně 1 a 4) C4115 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4115
dev_langs:
- C++
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c22e3c33f9ef2409c02f0e651473d566b4d2a74
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022523"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Kompilátor upozornění (úrovně 1 a 4) C4115

'type': Pojmenovaná definice typu v závorkách

Daný symbol se používá k definování struktury, sjednocení nebo výčtového typu uvnitř výraz v závorkách. Rozsahu této definice mohou neočekávané.

Definici ve volání funkce jazyka C, má globální obor. Ve volání jazyka C++ má tato definice ve stejném rozsahu jako volané funkce.

Toto upozornění může být také způsobeno deklarátory mezi kulaté závorky (například prototypů), které nejsou výrazy se závorkami.

Toto je upozornění úrovně 1 s programy v jazyce C++ a C programech zkompilovaných pod kompatibility ANSI (/Za). V opačném případě je úroveň 3.