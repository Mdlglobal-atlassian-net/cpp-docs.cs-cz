---
title: Explicitní uvolnění knihovny DLL s odloženým načtením | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- /DELAY:UNLOAD linker option
- DELAY:UNLOAD linker option
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 1c4c5172-fd06-45d3-9e4f-f12343176b3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ad52e8efde017ce7be6132594552e13584b38dc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705325"
---
# <a name="explicitly-unloading-a-delay-loaded-dll"></a>Explicitní uvolnění knihovny DLL načtené se zpožděním

[/Delay](../../build/reference/delay-delay-load-import-settings.md): unload – možnost linkeru umožňuje uvolnit knihovnu DLL, která byla zpožděné načtení. Ve výchozím nastavení, když váš kód uvolnění knihovny DLL (/ Delay: Unload pomocí a **__FUnloadDelayLoadedDLL2**), importy s odloženým načtením zůstanou v tabulky importních adres (IAT). Ale pokud používáte/delay: Unload příkazového řádku linkeru, pomocnou funkci budou podporovat explicitní uvolnění knihovny DLL, když IAT v původní podobě; Neplatný ukazatele se přepíšou. Je pole v IAT [ImgDelayDescr](../../build/reference/calling-conventions-parameters-and-return-type.md) , který obsahuje adresu kopii původní IAT (pokud existuje).

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

```
// link with /link /DELAYLOAD:MyDLL.dll /DELAY:UNLOAD
#include <windows.h>
#include <delayimp.h>
#include "MyDll.h"
#include <stdio.h>

#pragma comment(lib, "delayimp")
#pragma comment(lib, "MyDll")
int main()
{
    BOOL TestReturn;
    // MyDLL.DLL will load at this point
    fnMyDll();

    //MyDLL.dll will unload at this point
    TestReturn = __FUnloadDelayLoadedDLL2("MyDll.dll");

    if (TestReturn)
        printf_s("\nDLL was unloaded");
    else
        printf_s("\nDLL was not unloaded");
}
```

### <a name="comments"></a>Komentáře

Důležité poznámky k uvolnění odloženě zaváděné knihovny DLL:

- Můžete najít implementaci **__FUnloadDelayLoadedDLL2** funkce v souboru \VC7\INCLUDE\DELAYHLP. CPP.

- Název parametru **__FUnloadDelayLoadedDLL2** funkce musí přesně odpovídat (včetně případu) co knihovnu importu obsahuje (tj. řetězec také v tabulce import na obrázku). Můžete zobrazit obsah s importovanou knihovnou [DUMPBIN /DEPENDENTS](../../build/reference/dependents.md). Pokud je shoda nerozlišuje velikost písmen řetězců, můžete aktualizovat **__FUnloadDelayLoadedDLL2** chcete použít jeden z řetězcové funkce CRT nebo volání Windows API.

Zobrazit [uvolnění knihovny DLL Delay-Loaded](../../build/reference/unloading-a-delay-loaded-dll.md) Další informace.

## <a name="see-also"></a>Viz také

[Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)