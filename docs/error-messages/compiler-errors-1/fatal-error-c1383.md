---
title: Závažná chyba C1383
ms.date: 11/04/2016
f1_keywords:
- C1383
helpviewer_keywords:
- C1383
ms.assetid: ca224d14-d687-4fd6-80c2-8b82f28924ea
ms.openlocfilehash: 4ab96c0516ee5593a969669c03ae22f0c211ae27
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208580"
---
# <a name="fatal-error-c1383"></a>Závažná chyba C1383

– možnost kompilátoru /GL je nekompatibilní s nainstalovanou verzí modulu common language runtime

C1383 nastane, pokud používáte předchozí verzi modulu common language runtime s novější kompilátorem a při kompilaci s **/CLR** a   **/GL.**

Pokud chcete vyřešit, buď nepoužívejte **/GL** s **/CLR** nebo nainstalovat verzi common language runtime, dodávané s kompilátoru.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) a [/GL (optimalizace celého programu)](../../build/reference/gl-whole-program-optimization.md).