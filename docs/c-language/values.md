---
title: Hodnoty
ms.date: 11/04/2016
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
ms.openlocfilehash: a745b9cc45ed3e58cab4ec7355707d93a0557c04
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343154"
---
# <a name="values"></a>Hodnoty

**ANSI 3.1.2.5** reprezentace a sady hodnot z různých typů čísel s plovoucí desetinnou čárkou

**Float** typ obsahuje 32 bitů: 1 pro znaménko, 8 pro exponent a 23 pro mantisu. Jeho rozsah je +/-3.4E38 s alespoň 7 číslicemi přesnosti.

**Double** typ obsahuje 64 bitů: 1 pro znaménko, 11 pro exponent a 52 pro mantisu. Jeho rozsah je +/-1.7E308 s alespoň 15 číslicemi přesnosti.

**Long double** typ obsahuje 80 bitů: 1 pro znaménko, 15 pro exponent a 64 pro mantisu. Jeho rozsah je +/-1.2E4932 s alespoň 19 číslic. Všimněte si, že kompilátor Microsoft C reprezentace typu **long double** je stejný jako typ **double**.

## <a name="see-also"></a>Viz také:

[Matematika s plovoucí desetinnou čárkou](../c-language/floating-point-math.md)
