---
title: Upozornění kompilátoru (úrovně 1 a 4) C4115
ms.date: 11/04/2016
f1_keywords:
- C4115
helpviewer_keywords:
- C4115
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
ms.openlocfilehash: 7e39e8c837d94776a804da2bf38643b453edb949
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198039"
---
# <a name="compiler-warning-levels-1-and-4-c4115"></a>Upozornění kompilátoru (úrovně 1 a 4) C4115

' type ': definice pojmenovaného typu v závorkách

Daný symbol slouží k definování struktury, sjednocení nebo výčtového typu uvnitř výrazu v závorce. Rozsah definice může být neočekávaný.

Ve volání funkce jazyka C má definice globální rozsah. V C++ volání má definice stejný obor jako volání funkce.

Toto upozornění může být také způsobeno deklarátory v závorkách (například prototypy), které nejsou výrazy v závorkách.

Toto je upozornění úrovně 1 s C++ programy a programy jazyka C zkompilované v rámci kompatibility ANSI (/za). V opačném případě je to úroveň 3.
