---
title: Závažná chyba C1383 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1383
dev_langs:
- C++
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98f6fe881b2cdc46d4d2848d6faf850381f54c7b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062186"
---
# <a name="fatal-error-c1383"></a>Závažná chyba C1383

– možnost kompilátoru /GL je nekompatibilní s nainstalovanou verzí modulu common language runtime

C1383 nastane, pokud používáte předchozí verzi modulu common language runtime s novější kompilátorem a při kompilaci s **/CLR** a   **/GL.**

Pokud chcete vyřešit, buď nepoužívejte **/GL** s **/CLR** nebo nainstalovat verzi common language runtime, dodávané s kompilátoru.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).