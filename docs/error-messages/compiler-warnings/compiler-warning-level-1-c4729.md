---
title: Upozornění (úroveň 1) C4729 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4729
dev_langs:
- C++
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d1f5b4fe452937ce74e56886a5214ff92f44af7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096077"
---
# <a name="compiler-warning-level-1-c4729"></a>Kompilátor upozornění (úroveň 1) C4729

upozornění založená na funkce je moc velká pro graf toku

Toto upozornění se vygeneruje, když funkce je moc velké, aby se dalo kompilovat s reliable kontrolu pro situace, které se vygeneruje upozornění. Toto upozornění je pouze generován, když [/Od](../../build/reference/od-disable-debug.md) – možnost kompilátoru použít.

Pokud chcete vyřešit toto upozornění, rozdělte funkce na menší funkce.