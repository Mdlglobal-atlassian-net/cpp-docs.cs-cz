---
title: Hodnoty
ms.date: 11/04/2016
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
ms.openlocfilehash: e0a200bfea8c0a0a06f064b280dad320da25550c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534053"
---
# <a name="values"></a>Hodnoty

**ANSI 3.1.2.5** reprezentace a sady hodnot z různých typů čísel s plovoucí desetinnou čárkou

**Float** typ obsahuje 32 bity: 1 pro znaménko, 8 pro exponent a 23 pro mantisu. Jeho rozsah je +/-3.4E38 s alespoň 7 číslicemi přesnosti.

**Double** typ obsahuje 64 bitů: 1 pro znaménko, 11 pro exponent a 52 pro mantisu. Jeho rozsah je +/-1.7E308 s alespoň 15 číslicemi přesnosti.

**Long double** typ obsahuje 80 bity: 1 pro znaménko, 15 pro exponent a 64 pro mantisu. Jeho rozsah je +/-1.2E4932 s alespoň 19 číslic. Všimněte si, že kompilátor Microsoft C reprezentace typu **long double** je stejný jako typ **double**.

## <a name="see-also"></a>Viz také

[Matematika s plovoucí desetinnou čárkou](../c-language/floating-point-math.md)