---
title: Kompilátoru (úroveň 4) upozornění C4985 | Microsoft Docs
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
ms.openlocfilehash: c8f0b62a72d61ee061fd996f93638acba9e7ebb0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301087"
---
# <a name="compiler-warning-level-4-c4985"></a>C4985 kompilátoru upozornění (úroveň 4)
"název symbol": atributy není k dispozici na předchozí deklarace.  
  
 Jazyk (SAL) poznámky Microsoft zdrojového kódu poznámky na aktuální metoda deklarace a definice se liší od poznámky u starších deklarace. Stejné poznámky SAL musí být používány definice a deklarace metody.  
  
 SAL poskytuje sadu poznámky, které lze použít k popisu, jak funkce používá jeho parametrů, předpoklady, které provádí o nich a záruky, které provádí na dokončení. Poznámky jsou definovány v záhlaví souboru sal.h.  
  
 Všimněte si, že makra SAL nelze rozbalit, pokud tento projekt [/ analyze](../../build/reference/analyze-code-analysis.md) příznak. Pokud zadáte **/ analyze**, kompilátor můžete vyvolat C4985, i v případě, že žádná varování nebo chyby zobrazovaly bez **/ analyze**.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Použijte stejné poznámky SAL v definici metody a všechny jeho deklarace.  
  
## <a name="see-also"></a>Viz také  
 [Poznámky SAL](../../c-runtime-library/sal-annotations.md)