---
title: Upozornění (úroveň 4) C4718 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4718
dev_langs:
- C++
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8736902f4c3a1cfac7313806fde65d1b253716b3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46054230"
---
# <a name="compiler-warning-level-4-c4718"></a>Kompilátor upozornění (úroveň 4) C4718

volání funkce: rekurzivní volání nemá žádné vedlejší efekty, odstraňuje se

Funkce obsahuje rekurzivní volání, ale jinak nemá žádné vedlejší účinky. Voláním této funkce se odstraňuje. Správnost program nemá vliv, ale je chování. Vzhledem k tomu byste museli opustit volání může vést k výjimce přetečení zásobníku modulu runtime, odstraněním volání dojde k odebrání této možnosti.