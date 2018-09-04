---
title: MMWORD | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7314c6d0861195e312c7f72481d2e195e041965d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679231"
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