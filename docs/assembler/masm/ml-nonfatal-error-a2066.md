---
title: Závažná méně závažná chyba nástroje ML A2066 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2066
dev_langs:
- C++
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf5cbe7d5c77da7f129cbc40ffa97f4051afca6
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690249"
---
# <a name="ml-nonfatal-error-a2066"></a>Méně závažná chyba nástroje ML A2066

**nekompatibilní režim a segment velikost procesoru**

Byl proveden pokus o otevření segment s **USE16**, **USE32**, nebo **PLOCHÝ** atribut, který není kompatibilní se zadaným procesoru nebo změnit na 16-bit CPU v 32-bit Segment.

**USE32** a **PLOCHÝ** atributy musí být předcházen.386 nebo větší procesor směrnice.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>