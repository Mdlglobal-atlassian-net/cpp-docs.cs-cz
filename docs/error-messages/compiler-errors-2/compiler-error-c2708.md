---
title: Chyba kompilátoru C2708 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2708
dev_langs:
- C++
helpviewer_keywords:
- C2708
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c0accd68881cccad5e34530a6c157a4e8179b283
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111092"
---
# <a name="compiler-error-c2708"></a>Chyba kompilátoru C2708

'identifier': Skutečná délka parametrů v bajtech se liší od předchozího volání nebo odkazu

A [__stdcall](../../cpp/stdcall.md) funkce musí být předcházen prototypu. V opačném případě kompilátor interpretuje první volání funkce jako prototyp a k této chybě dochází, když kompilátor narazí volání, které se neshoduje.

Chcete-li vyřešit tuto chybu přidat prototypu funkce.