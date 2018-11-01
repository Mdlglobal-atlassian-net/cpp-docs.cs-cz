---
title: Chyba kompilátoru C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: da4c03c681f95efaa5edb159869315b41d027e99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657119"
---
# <a name="compiler-error-c2026"></a>Chyba kompilátoru C2026

řetězec je moc velký, koncové znaky se oříznou

Řetězec je delší než limit 16380 jednobajtové znaky.

Před sousední řetězců jsou zřetězeny nemůže být delší než 16380 jednobajtové znaky řetězce.

Řetězec znaků Unicode přibližně polovina této délky také vygeneruje tuto chybu.

Pokud máte řetězec definovaná následujícím způsobem, generuje C2026:

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Vám může jej rozdělte následujícím způsobem:

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Můžete ukládat mimořádně velkou řetězcových literálů (32 kB nebo déle) ve vlastní prostředek nebo externí soubor. Zobrazit [vytvoření nového vlastního prostředku nebo prostředku dat](../../windows/creating-a-new-custom-or-data-resource.md) Další informace.