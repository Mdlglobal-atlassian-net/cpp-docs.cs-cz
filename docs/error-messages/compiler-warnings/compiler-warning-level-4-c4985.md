---
title: Kompilátor upozornění (úroveň 4) C4985
ms.date: 11/04/2016
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 73abb166910cc421f042d22d67efc122e416bceb
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024436"
---
# <a name="compiler-warning-level-4-c4985"></a>Kompilátor upozornění (úroveň 4) C4985

'název symbolu': neexistují atributy pro předchozí deklaraci.

Microsoft zdrojového kódu poznámky jazyka (SAL) poznámky na aktuální metodu deklarace nebo definice liší od poznámky u starších deklarace. Definice a deklarace metody musí využívat stejnou poznámky SAL.

SAL poskytuje sadu poznámky, které můžete použít k popisu, jak funkce používá parametry, předpoklady, které provádí o nich a záruky, které provádí na dokončení. Poznámky jsou definovány v souboru hlaviček sal.h.

Všimněte si, že SAL makra nelze rozbalit, pokud projekt nemá [/ analyze](../../build/reference/analyze-code-analysis.md) příznak zadán. Pokud zadáte **/ analyze**, kompilátor může vyvolat C4985, i v případě, že žádná upozornění ani chyby zobrazovaly bez **/ analyze**.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Použijte stejné poznámky SAL v definici metody a všechny jeho deklarace.

## <a name="see-also"></a>Viz také:

[Poznámky SAL](../../c-runtime-library/sal-annotations.md)