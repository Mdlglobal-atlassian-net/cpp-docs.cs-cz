---
title: Závažná chyba C1017 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1017
dev_langs:
- C++
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc2cb8ef9c7c9fe8eea7c506e55c49878b9bd809
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108522"
---
# <a name="fatal-error-c1017"></a>Závažná chyba C1017

Neplatný celočíselný konstantní výraz

Výraz v `#if` direktiva neexistuje nebo neprovedl vyhodnocení na konstantu.

Konstanty definované pomocí `#define` musí mít hodnoty, která se vyhodnotí celočíselnou konstantu, pokud jsou použity v `#if`, `#elif`, nebo `#else` směrnice.

Následující ukázka generuje C1017:

```
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

Možná řešení:

```
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

Protože `CONSTANT_NAME` vyhodnocena jako řetězec a není celé číslo, `#if` – direktiva generuje závažná chyba C1017.

V ostatních případech preprocesor vyhodnotí undefined – konstanta jako nula. To může způsobit nežádoucí výsledky, jak je znázorněno v následujícím příkladu. `YES` není definováno, takže je vyhodnocen jako nula. Výraz `#if` `CONSTANT_NAME` vyhodnocena jako NEPRAVDA a kód pro použití na `YES` Odebereme preprocesorem. `NO` To je nedefinované (nula), také `#elif` `CONSTANT_NAME==NO` vyhodnotí jako true (`0 == 0`), způsobí preprocesor kódu v `#elif` část příkazu – přesně opakem zamýšlené chování.

```
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

Pokud chcete zobrazit, přesně jak kompilátor zpracovává direktivy preprocesoru, použijte [/P](../../build/reference/p-preprocess-to-a-file.md), [/E](../../build/reference/e-preprocess-to-stdout.md), nebo [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).