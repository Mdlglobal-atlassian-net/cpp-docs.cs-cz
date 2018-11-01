---
title: Podpora plovoucí desetinné čárky ve starším kódu (Visual C++)
ms.date: 11/04/2016
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
ms.openlocfilehash: 2340a4d136dee3438a47ce06793ed9274035250d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509640"
---
# <a name="floating-point-support-for-older-code-visual-c"></a>Podpora plovoucí desetinné čárky ve starším kódu (Visual C++)

MMX a registry zásobníku s plovoucí desetinnou čárkou (MM0-MM7/ST0-ST7) jsou zachovány v kontextu.  Neexistuje žádné explicitní konvenci volání pro tyto registry.  Použití těchto registrů je přísně zakázáno v kódu v režimu jádra.

## <a name="see-also"></a>Viz také

[Konvence volání](../build/calling-convention.md)