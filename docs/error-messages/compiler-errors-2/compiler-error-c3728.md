---
title: Chyba kompilátoru C3728 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3728
dev_langs:
- C++
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e412824bd2afdadfc21d71b73f38eb8ba5ace82d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108414"
---
# <a name="compiler-error-c3728"></a>Chyba kompilátoru C3728

'událost': událost nemá metodu raise

Metadata vytvořené pomocí jazyka, jako je C#, který neumožňuje událost vyvolána z vně třídy, ve kterém byl definován, je součástí [#using](../../preprocessor/hash-using-directive-cpp.md) směrnice a program Visual C++ pomocí CLR programování došlo k pokusu vyvolání události.

K vyvolání události aplikace vyvinuté v jazyce, jako je C#, je potřeba také definovat veřejnou metodu, která vyvolává událost třídy obsahující události.