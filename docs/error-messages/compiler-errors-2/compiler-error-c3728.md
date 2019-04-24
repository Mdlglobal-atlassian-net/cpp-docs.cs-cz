---
title: Chyba kompilátoru C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 68aa23843b0470f15f409b6f3b58624f979ccfae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328104"
---
# <a name="compiler-error-c3728"></a>Chyba kompilátoru C3728

'událost': událost nemá metodu raise

Metadata vytvořené pomocí jazyka, jako je C#, který neumožňuje událost vyvolána z vně třídy, ve kterém byl definován, je součástí [#using](../../preprocessor/hash-using-directive-cpp.md) směrnice a program Visual C++ pomocí CLR programování došlo k pokusu vyvolání události.

K vyvolání události aplikace vyvinuté v jazyce, jako je C#, je potřeba také definovat veřejnou metodu, která vyvolává událost třídy obsahující události.