---
title: XMMWORD
ms.date: 08/30/2018
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: a248c9318764cd632fed2afd8481ee2b2102fe31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479779"
---
# <a name="xmmword"></a>XMMWORD

Použít 128bitové multimediální operandů s instrukce MMX a SSE (XMM).

## <a name="syntax"></a>Syntaxe

> XMMWORD

## <a name="remarks"></a>Poznámky

`XMMWORD` slouží k reprezentaci stejného typu jako [__m128](../../cpp/m128.md).

## <a name="example"></a>Příklad

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```