---
title: Chyba kompilátoru C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 9747b1edadc76ceeb502b2c6fd03496b91769f5a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208062"
---
# <a name="compiler-error-c2026"></a>Chyba kompilátoru C2026

řetězec je moc velký, koncové znaky se zkrátily.

Řetězec byl delší než limit 16380 znaků s jedním bajtem.

Před zřetězením sousedících řetězců nemůže být řetězec delší než 16380 znaků.

Tato chyba by vygenerovala řetězec Unicode přibližně o jedné polovině této délky.

Pokud máte definován řetězec takto, vygeneruje C2026:

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Můžete ho rozdělit následujícím způsobem:

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Můžete chtít ukládat výjimečně velké řetězcové literály (32 a více) do vlastního prostředku nebo externího souboru. Další informace najdete v tématu [Vytvoření nového vlastního prostředku nebo zdroje dat](../../windows/creating-a-new-custom-or-data-resource.md) .
