---
title: PŘÍKAZ GOTO (MASM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0be678e2d39389cbc551c386c1890f799124b5b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691249"
---
# <a name="goto-masm"></a>GOTO (MASM)

Přenese sestavení na řádek označený **:**_macrolabel_.

## <a name="syntax"></a>Syntaxe

> **Příkaz GOTO** *macrolabel*

## <a name="remarks"></a>Poznámky

**Příkaz GOTO** smí obsahovat pouze uvnitř [– makro](macro.md), [pro](for-masm.md), [FORC](forc.md), [OPAKUJTE](repeat.md), a [při](while-masm.md)bloky. *Macrolabel* cíl musí být pouze – direktiva v řádku a musí být předcházen přední dvojtečka.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>
