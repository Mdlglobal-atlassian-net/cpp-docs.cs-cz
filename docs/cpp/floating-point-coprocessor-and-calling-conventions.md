---
title: Koprocesor plovoucí desetinné čárky a konvence volání
ms.date: 11/04/2016
helpviewer_keywords:
- floating-point numbers [C++]
- floating-point coprocessor
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
ms.openlocfilehash: 7e9184d66bde26ab0e2b345f8f10c2e28619fd2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625105"
---
# <a name="floating-point-coprocessor-and-calling-conventions"></a>Koprocesor plovoucí desetinné čárky a konvence volání

Při psaní sestavení koprocesor pro plovoucí rutiny, musíte zachovat plovoucí bodu řídicí slovo a vyčistit zásobník koprocesoru, pokud se vrátí **float** nebo **double** hodnotu (která funkce by měla vrátit v ST(0)).

## <a name="see-also"></a>Viz také:

[Konvence volání](../cpp/calling-conventions.md)