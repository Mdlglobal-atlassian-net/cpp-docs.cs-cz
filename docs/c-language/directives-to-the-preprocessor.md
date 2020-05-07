---
title: Direktivy pro preprocesor
ms.date: 11/04/2016
ms.assetid: adc6251e-cf6b-4508-bdbb-55f446c838d3
ms.openlocfilehash: 520d181c3a58ee2c626678a3afd9126f1ef183cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234137"
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
