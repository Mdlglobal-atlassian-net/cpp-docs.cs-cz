---
title: Upozornění (úroveň 1) C4678 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4678
dev_langs:
- C++
helpviewer_keywords:
- C4678
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 81eb7df618f97300c2654cc0f4f7a58d18215b26
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076096"
---
# <a name="compiler-warning-level-1-c4678"></a>Kompilátor upozornění (úroveň 1) C4678

Základní třída 'base_type' je méně dostupný než "derived_type"

Veřejný typ je odvozen od typu privátní. Pokud dojde k vytvoření veřejný typ v odkazovaném sestavení, členové privátní základního typu nebudou přístupné.

C4678 dosažitelný pouze pomocí možnosti kompilátoru zastaralé **oldSyntax**. Jedná se o chybu, při použití **/CLR**, mít základní třídu, která je méně dostupný, její odvozené třídy.
