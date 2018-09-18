---
title: Direktivy pro preprocesor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1ddecf1e205cc9a6d7f09a27fbf243417540e49
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033560"
---
# <a name="directives-to-the-preprocessor"></a>Direktivy pro preprocesor

„Direktiva“ dává pokyn preprocesoru jazyka C k provedení konkrétní akce týkající se textu programu před kompilací. [Direktivy preprocesoru](../preprocessor/preprocessor-directives.md) jsou plně popsány v *odkazu preprocesoru*. V tomto příkladu je použita direktiva preprocesoru `#define`:

```
#define MAX 100
```

Tento příkaz sděluje kompilátoru, že před kompilací je třeba všechny výskyty `MAX` nahradit `100`. Mezi direktivy preprocesoru kompilátoru jazyka C patří:

|#define – direktiva|#endif – direktiva|#ifdef|#line – direktiva|
|--------------|-------------|-------------|------------|
|`#elif`|`#error`|**#ifndef**|**#pragma**|
|`#else`|`#if`|`#include`|`#undef`|

## <a name="see-also"></a>Viz také

[Zdrojové soubory a zdrojové programy](../c-language/source-files-and-source-programs.md)