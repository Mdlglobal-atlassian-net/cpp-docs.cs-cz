---
title: Upozornění (úroveň 4) C4985 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d67b7394ef9bd38409ca45abe6ed7d347f5a37d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092660"
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