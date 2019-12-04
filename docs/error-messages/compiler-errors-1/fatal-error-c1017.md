---
title: Závažná chyba C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: 0feda3bc4c3729d3101be356220aa0124ba85190
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756939"
---
# <a name="fatal-error-c1017"></a>Závažná chyba C1017

neplatný výraz konstanty typu Integer

Výraz v direktivě `#if` neexistuje nebo se nevyhodnotil jako konstanta.

Konstanty definované pomocí `#define` musí mít hodnoty, které se vyhodnotí na celočíselnou konstantu, pokud jsou použity v direktivě `#if`, `#elif`nebo `#else`.

Následující ukázka generuje C1017:

```cpp
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

Možné řešení:

```cpp
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

Vzhledem k tomu, že `CONSTANT_NAME` vyhodnocuje jako řetězec, nikoli celé číslo, direktiva `#if` vygeneruje závažnou chybu C1017.

V jiných případech preprocesor vyhodnocuje nedefinovanou konstantu jako nulu. To může způsobit neočekávané výsledky, jak je znázorněno v následující ukázce. `YES` není definován, takže se vyhodnotí jako nula. Výraz `#if` `CONSTANT_NAME` vyhodnotí jako false a kód, který se má použít na `YES`, je odebraný preprocesorem. `NO` je také nedefinované (nula), takže `#elif` `CONSTANT_NAME==NO` vyhodnocena jako true (`0 == 0`), což způsobuje, že preprocesor opouští kód v `#elif` části příkazu – přesně proti zamýšlenému chování.

```cpp
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

Chcete-li zobrazit přesně, jak kompilátor zpracovává direktivy preprocesoru, použijte příkaz [/p](../../build/reference/p-preprocess-to-a-file.md), [/e](../../build/reference/e-preprocess-to-stdout.md)nebo [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).
