---
title: /DEPENDENTS
ms.date: 07/15/2019
f1_keywords:
- /dependents
helpviewer_keywords:
- -DEPENDENTS dumpbin option
- /DEPENDENTS dumpbin option
- DEPENDENTS dumpbin option
ms.assetid: 9b31da2a-75ac-4bbf-a3f1-adf8b0ecbbb4
ms.openlocfilehash: 88f0062a6bbca3f9199a12f739c2ade5f9d912cd
ms.sourcegitcommit: 7f5b29e24e1be9b5985044a030977485fea0b50c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2019
ms.locfileid: "68299744"
---
# <a name="dependents"></a>/DEPENDENTS

Vypíše názvy knihoven DLL, ze kterých obrázek importuje funkce. Seznam můžete použít k určení, které knihovny DLL se mají znovu distribuovat s vaší aplikací, nebo najít název chybějící závislosti.

## <a name="syntax"></a>Syntaxe

> **/DEPENDENTS**

Tato možnost se vztahuje na všechny spustitelné soubory zadané v příkazovém řádku. Nepřijímá žádné argumenty.

## <a name="remarks"></a>Poznámky

Možnost **/Dependents** přidá názvy knihoven DLL, ze kterých obrázek importuje funkce do výstupu. Tato možnost nevypíše názvy importovaných funkcí. Pokud chcete zobrazit názvy importovaných funkcí, použijte možnost [/Imports](imports-dumpbin.md) .

Pouze možnost DUMPBIN [/Headers](headers.md) je k dispozici pro použití v souborech vytvořených pomocí možnosti kompilátoru [/GL](gl-whole-program-optimization.md) .

## <a name="example"></a>Příklad

Tento příklad ukazuje výstup DUMPBIN pro možnost **/Dependents** ve spustitelném souboru klienta sestaveném v [návodu: Vytvoření a použití vlastní knihovny](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)dll:

```cmd
C:\Users\username\Source\Repos\MathClient\Debug>dumpbin /DEPENDENTS MathClient.exe
Microsoft (R) COFF/PE Dumper Version 14.16.27032.1
Copyright (C) Microsoft Corporation.  All rights reserved.


Dump of file MathClient1322.exe

File Type: EXECUTABLE IMAGE

  Image has the following dependencies:

    MathLibrary.dll
    MSVCP140D.dll
    VCRUNTIME140D.dll
    ucrtbased.dll
    KERNEL32.dll

  Summary

        1000 .00cfg
        1000 .data
        2000 .idata
        1000 .msvcjmc
        3000 .rdata
        1000 .reloc
        1000 .rsrc
        8000 .text
       10000 .textbss
```

## <a name="see-also"></a>Viz také:

[DUMPBIN – možnosti](dumpbin-options.md)
