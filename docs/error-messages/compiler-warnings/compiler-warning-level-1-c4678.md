---
title: Kompilátor upozornění (úroveň 1) C4678
ms.date: 11/04/2016
f1_keywords:
- C4678
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
ms.openlocfilehash: 9e61d919f08bbbf4f3e74da7ba4f2388516d3152
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374518"
---
# <a name="compiler-warning-level-1-c4678"></a>Kompilátor upozornění (úroveň 1) C4678

Základní třída 'base_type' je méně dostupný než "derived_type"

Veřejný typ je odvozen od typu privátní. Pokud dojde k vytvoření veřejný typ v odkazovaném sestavení, členové privátní základního typu nebudou přístupné.

C4678 dosažitelný pouze pomocí možnosti kompilátoru zastaralé **oldSyntax**. Jedná se o chybu, při použití **/CLR**, mít základní třídu, která je méně dostupný, její odvozené třídy.
