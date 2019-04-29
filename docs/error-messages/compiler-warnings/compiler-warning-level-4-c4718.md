---
title: Kompilátor upozornění (úroveň 4) C4718
ms.date: 11/04/2016
f1_keywords:
- C4718
helpviewer_keywords:
- C4718
ms.assetid: 29507f8a-b024-42c1-a3b8-f35d1f2641f3
ms.openlocfilehash: c313e26af5f5b17db9c7d001a705ff7211461c2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395167"
---
# <a name="compiler-warning-level-4-c4718"></a>Kompilátor upozornění (úroveň 4) C4718

volání funkce: rekurzivní volání nemá žádné vedlejší efekty, odstraňuje se

Funkce obsahuje rekurzivní volání, ale jinak nemá žádné vedlejší účinky. Voláním této funkce se odstraňuje. Správnost program nemá vliv, ale je chování. Vzhledem k tomu byste museli opustit volání může vést k výjimce přetečení zásobníku modulu runtime, odstraněním volání dojde k odebrání této možnosti.