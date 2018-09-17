---
title: Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C++ nebo C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88d9b18620c2e648ab519a59745876569b66ec30
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708094"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++

Pokud máte funkce v knihovně DLL napsané v C, které chcete získat přístup z jazyka C nebo modulu jazyka C++, byste měli použít **__cplusplus** preprocesor makro určit jazyk, který je kompilován a pak tyto deklarace funkce s C-linkage, pokud je používán z modulu jazyka C++. Pokud používáte tento postup a zadejte soubory hlaviček pro vaši knihovnu DLL, lze tyto funkce jazyka C a C++ uživatelé beze změny.

Následující kód ukazuje soubor hlaviček, které mohou využívat klientské aplikace C a C++:

```h
// MyCFuncs.h
#ifdef __cplusplus
extern "C" {  // only need to export C interface if
              // used by C++ source code
#endif

__declspec( dllimport ) void MyCFunc();
__declspec( dllimport ) void AnotherCFunc();

#ifdef __cplusplus
}
#endif
```

Pokud budete potřebovat odkázat funkcí jazyka C vašeho spustitelného jazyka c++ a soubory hlaviček deklarace funkce nepoužili techniky popsané výše ve zdrojovém souboru jazyka C++, proveďte následující příkaz pro zabránění kompilátoru upravení názvy funkcí jazyka C:

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Určit, kterou exportovací metodu použít](../build/determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Dekorované názvy](../build/reference/decorated-names.md)

- [Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](../build/exporting-from-a-dll.md)