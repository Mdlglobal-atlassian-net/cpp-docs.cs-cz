---
title: Kompilátor upozornění (úroveň 4) C4985
ms.date: 11/04/2016
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 6f098b25848d4fca0431663bd61ad71646c8d644
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50661068"
---
# <a name="compiler-warning-level-4-c4985"></a>Kompilátor upozornění (úroveň 4) C4985

'název symbolu': neexistují atributy pro předchozí deklaraci.

Microsoft zdrojového kódu poznámky jazyka (SAL) poznámky na aktuální metodu deklarace nebo definice liší od poznámky u starších deklarace. Definice a deklarace metody musí využívat stejnou poznámky SAL.

SAL poskytuje sadu poznámky, které můžete použít k popisu, jak funkce používá parametry, předpoklady, které provádí o nich a záruky, které provádí na dokončení. Poznámky jsou definovány v souboru hlaviček sal.h.

Všimněte si, že SAL makra nelze rozbalit, pokud projekt nemá [/ analyze](../../build/reference/analyze-code-analysis.md) příznak zadán. Pokud zadáte **/ analyze**, kompilátor může vyvolat C4985, i v případě, že žádná upozornění ani chyby zobrazovaly bez **/ analyze**.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Použijte stejné poznámky SAL v definici metody a všechny jeho deklarace.

## <a name="see-also"></a>Viz také

[Poznámky SAL](../../c-runtime-library/sal-annotations.md)