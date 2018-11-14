---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: e4ebaa9d47a569bc9cf7d843d3ddb54ca5d713a0
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328224"
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
    movq     mm0, mmword ptr [ebx]
```