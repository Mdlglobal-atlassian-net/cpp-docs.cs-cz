---
title: Chyba linkerů LNK2011
ms.date: 11/04/2016
f1_keywords:
- LNK2011
helpviewer_keywords:
- LNK2011
ms.assetid: 04991ef5-49d5-46c7-8eee-a9d1d3fc541e
ms.openlocfilehash: c8c62da6c1b4ea856f7a0854b998946893f2be63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299087"
---
# <a name="linker-tools-error-lnk2011"></a>Chyba linkerů LNK2011

předkompilovaný objekt není odkazovaný; bitové kopie se možná nespustí.

Použití předkompilovaných hlaviček vyžaduje odkaz, že všechny soubory objektů, které jsou vytvořené pomocí předkompilovaných hlaviček je potřeba propojit v. Pokud máte zdrojový soubor, který slouží k vytvoření předkompilovaných hlaviček pro použití s jiných zdrojových souborech, teď musíte zahrnout soubor objektu společně předkompilované hlavičky.

Pokud kompilujete soubor s názvem STUB.cpp k vytvoření předkompilovaných hlaviček pro použití s jiných zdrojových souborech, je třeba propojit s STUB.obj nebo tato chyba se zobrazí. V následujících příkazových řádků řádek jedna slouží k vytvoření předkompilovaných hlaviček, COMMON.pch, která se používá s PROG1.cpp a PROG2.cpp v řádcích, dva a tři. Soubor obsahuje pouze STUB.cpp `#include` řádky (stejné `#include` řádcích jako v PROG1.cpp a PROG2.cpp) a slouží jenom ke generování předkompilovaných hlaviček. Na posledním řádku STUB.obj je potřeba propojit v vyhnout LNK2011.

```
cl /c /Yccommon.h stub.cpp
cl /c /Yucommon.h prog1.cpp
cl /c /Yucommon.h prog2.cpp
link /out:prog.exe stub.obj prog1.obj prog2.obj
```