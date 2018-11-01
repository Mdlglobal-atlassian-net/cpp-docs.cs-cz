---
title: Chyba kompilátoru C2873
ms.date: 11/04/2016
f1_keywords:
- C2873
helpviewer_keywords:
- C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
ms.openlocfilehash: 69be18e5f3e06392d4f2fa11c6343a07298b84bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455169"
---
# <a name="compiler-error-c2873"></a>Chyba kompilátoru C2873

'symbol': symbol nejde používat v deklarace using

A `using` chybí direktiva [obor názvů](../../cpp/namespaces-cpp.md) – klíčové slovo. To způsobí, že kompilátor interpretuje jako kód [using – deklarace](../../cpp/using-declaration.md) spíše než [direktiva using](../../cpp/namespaces-cpp.md#using_directives).