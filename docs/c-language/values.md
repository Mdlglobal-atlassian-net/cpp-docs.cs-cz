---
title: Hodnoty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8bef044535d2f5a5b337823b1798feaea48745d7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106271"
---
# <a name="values"></a>Hodnoty

**ANSI 3.1.2.5** reprezentace a sady hodnot z různých typů čísel s plovoucí desetinnou čárkou

**Float** typ obsahuje 32 bity: 1 pro znaménko, 8 pro exponent a 23 pro mantisu. Jeho rozsah je +/-3.4E38 s alespoň 7 číslicemi přesnosti.

**Double** typ obsahuje 64 bitů: 1 pro znaménko, 11 pro exponent a 52 pro mantisu. Jeho rozsah je +/-1.7E308 s alespoň 15 číslicemi přesnosti.

**Long double** typ obsahuje 80 bity: 1 pro znaménko, 15 pro exponent a 64 pro mantisu. Jeho rozsah je +/-1.2E4932 s alespoň 19 číslic. Všimněte si, že kompilátor Microsoft C reprezentace typu **long double** je stejný jako typ **double**.

## <a name="see-also"></a>Viz také

[Matematika s plovoucí desetinnou čárkou](../c-language/floating-point-math.md)