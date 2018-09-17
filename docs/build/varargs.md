---
title: Funkce VarArgs | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8305eaddf87a2e67b797bedff1944dbcbbbdbd41
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45713645"
---
# <a name="varargs"></a>Vararg

Pokud parametry jsou předány prostřednictvím vararg (například tlačítko se třemi tečkami argumenty), v podstatě normální předávání parametrů platí včetně přesahu páté a následné argumenty. Zodpovídá znovu volaného argumenty s výpisem paměti, které adresu. Pouze hodnoty s plovoucí desetinnou čárkou celé číslo a registr s plovoucí desetinnou čárkou obsahovat hodnoty typu float v případě, že volaný očekává, že hodnota v registrech celé číslo.

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)