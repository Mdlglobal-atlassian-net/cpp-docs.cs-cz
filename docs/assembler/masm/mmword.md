---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: 1205338f9140c74a3a6e0b4bce57983edc80862e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50541115"
---
# <a name="mmword"></a>MMWORD

Použít 64-bit multimediální operandů s instrukce MMX a SSE (XMM).

## <a name="syntax"></a>Syntaxe

> MMWORD

## <a name="remarks"></a>Poznámky

`MMWORD` je typem.  Před MMWORD přidávaný do MASM ekvivalentní funkce by bylo dosaženo pomocí:

```asm
    mov mm0, qword ptr [ebx]
```

Obě pokyny práci na 64-bit operandy `QWORD` je typem pro 64bitová celá čísla bez znaménka a `MMWORD` je typ hodnoty multimediální 64-bit.

`MMWORD` slouží k reprezentaci stejného typu jako [__m64](../../cpp/m64.md).

## <a name="example"></a>Příklad

```asm
    movq     mm0, mmword ptr [ebx]
```