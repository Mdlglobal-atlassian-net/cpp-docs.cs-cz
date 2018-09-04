---
title: VYVOLÁNÍ | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- Invoke
dev_langs:
- C++
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e5698acf9986903a1d6d731c1047484a0ce6904
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676514"
---
# <a name="invoke"></a>INVOKE

Volá podle postupu na adrese dán *výraz*, předány argumenty v zásobníku nebo v registrech podle standardní konvence volání jazyka typu.

## <a name="syntax"></a>Syntaxe

> INVOKE *výraz* [[, *argumenty*]]

## <a name="remarks"></a>Poznámky

Každý argument předaný do procedury může být výraz, pár registr nebo výraz adresy (předcházet párový příkaz výrazu `ADDR`).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>