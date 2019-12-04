---
title: Upozornění kompilátoru (úroveň 4) C4985
ms.date: 11/04/2016
f1_keywords:
- C4985
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 75feda6fb2c88b663aa6ade0efdfffc7def1568f
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810734"
---
# <a name="compiler-warning-level-4-c4985"></a>Upozornění kompilátoru (úroveň 4) C4985

' název symbolu ': atributy nejsou přítomny u předchozí deklarace.

Poznámky jazyka Microsoft zdrojového kódu pro poznámky (SAL) na aktuální deklaraci nebo definici metody se liší od poznámek k předchozí deklaraci. V definici a deklaracích metody se musí použít stejné poznámky SAL.

SAL poskytuje sadu poznámek, které můžete použít k popsání toho, jak funkce používá své parametry, předpoklady, které o nich slouží, a zaručuje, že se bude dokončí. Poznámky jsou definovány v souboru hlaviček Sal. h.

Všimněte si, že makra SAL se nebudou rozšiřovat, pokud projekt nemá zadaný příznak [/analyze](../../build/reference/analyze-code-analysis.md) . Když zadáte **/analyze**, může kompilátor vyvolat C4985, i když nejsou k dispozici žádná upozornění nebo chyby bez **/analyze**.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Používejte stejné poznámky SAL na definici metody a všech jejích deklaracích.

## <a name="see-also"></a>Viz také:

[Poznámky SAL](../../c-runtime-library/sal-annotations.md)