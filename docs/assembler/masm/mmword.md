---
title: MMWORD
ms.date: 12/17/2019
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: fd3b9f40b7ff9fa4dae570e0ed906c13a9456424
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75311920"
---
# <a name="mmword"></a>MMWORD

Používá se pro 64é multimediální operandy s pokyny MMX a SSE (XMM).

## <a name="syntax"></a>Syntaxe

> **MMWORD**

## <a name="remarks"></a>Poznámky

**MMWORD** je typ.  Před přidáním **MMWORD** do MASM bylo možné dosáhnout ekvivalentních funkcí:

```asm
    mov mm0, qword ptr [ebx]
```

I když obě instrukce fungují na 64 bitových operandech, je hodnota **QWORD** typem pro 64 nepodepsaných celých čísel a **MMWORD** je typ hodnoty pro 64, který je v multimediální hodnotě.

**MMWORD** má představovat stejný typ jako [__m64](../../cpp/m64.md).

## <a name="example"></a>Příklad

```asm
    movq     mm0, mmword ptr [ebx]
```

## <a name="see-also"></a>Viz také

[Gramatika BNF MASM](masm-bnf-grammar.md)
