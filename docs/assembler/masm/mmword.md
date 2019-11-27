---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: d4378c1435df09f249fe7f55dabd4bd0f43f6100
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397178"
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
