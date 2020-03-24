---
title: Upozornění kompilátoru (úroveň 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: 48452ed53b93d7cd89daadd3f7ab3a69b453e1a1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198156"
---
# <a name="compiler-warning-level-4-c4718"></a>Upozornění kompilátoru (úroveň 4) C4718

volání funkce: rekurzivní volání nemá žádné vedlejší efekty, odstraňuje se

Funkce obsahuje rekurzivní volání, ale v opačném případě nemá žádné vedlejší účinky. Probíhá odstraňování volání této funkce. Správnost tohoto programu není ovlivněna, ale chování je. Vzhledem k tomu, že ukončení volání může způsobit výjimku přetečení zásobníku modulu runtime, odstranění tohoto volání odebere tuto možnost.
