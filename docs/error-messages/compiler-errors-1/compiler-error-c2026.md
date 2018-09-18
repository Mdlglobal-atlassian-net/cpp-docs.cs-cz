---
title: Chyba kompilátoru C2026 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2026
dev_langs:
- C++
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 055ac47d036a1027817aa6b3433bfe0e2e88570e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019546"
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