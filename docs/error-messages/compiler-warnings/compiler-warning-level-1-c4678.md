---
title: Kompilátor upozornění (úroveň 1) C4678
ms.date: 11/04/2016
f1_keywords:
- C4678
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
ms.openlocfilehash: 9e61d919f08bbbf4f3e74da7ba4f2388516d3152
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624624"
---
# <a name="compiler-warning-level-1-c4678"></a>Kompilátor upozornění (úroveň 1) C4678

Základní třída 'base_type' je méně dostupný než "derived_type"

Veřejný typ je odvozen od typu privátní. Pokud dojde k vytvoření veřejný typ v odkazovaném sestavení, členové privátní základního typu nebudou přístupné.

C4678 dosažitelný pouze pomocí možnosti kompilátoru zastaralé **oldSyntax**. Jedná se o chybu, při použití **/CLR**, mít základní třídu, která je méně dostupný, její odvozené třídy.
