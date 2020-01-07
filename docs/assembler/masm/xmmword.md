---
title: XMMWORD
ms.date: 12/17/2019
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: 1116729883bf9b1b9342b30332bab5de6ba59015
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75319109"
---
# <a name="xmmword"></a>XMMWORD

Používá se pro 128é multimediální operandy s pokyny MMX a SSE (XMM).

## <a name="syntax"></a>Syntaxe

> **XMMWORD**

## <a name="remarks"></a>Poznámky

**XMMWORD** má představovat stejný typ jako [__m128](../../cpp/m128.md).

## <a name="example"></a>Příklad

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```

## <a name="see-also"></a>Viz také

[Gramatika BNF MASM](masm-bnf-grammar.md)
