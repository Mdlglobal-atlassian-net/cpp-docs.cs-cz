---
title: Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], exporting
- functions [C], C or C++ executables and
- __cplusplus macro
- exporting DLLs [C++], C functions in C++ executables
- exporting functions [C++], C functions in C++ executables
ms.assetid: b51d6e5e-37cf-4c1c-b0bf-fcf188c82f00
ms.openlocfilehash: b7ba2ed30615efb3b05e71cecf0ea69898feb8ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273570"
---
# <a name="exporting-c-functions-for-use-in-c-or-c-language-executables"></a>Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++

Pokud máte funkce v knihovně DLL napsané v jazyce C, ke kterým chcete přistupovat z jazyka C nebo modulu jazyka C++, měli byste použít **__cplusplus** makro preprocesoru k určení, který jazyk je kompilován, a poté deklarovat tyto funkce s propojením jazyka c, pokud je používán z modulu jazyka C++. Použijete-li tuto techniku a zadáte soubory hlaviček pro knihovnu DLL, mohou být tyto funkce používány uživateli jazyka C a C++ bez jakýchkoli změn.

Následující kód ukazuje hlavičkový soubor, který mohou používat klientské aplikace C a C++:

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

Pokud potřebujete propojit funkce jazyka C s vaším spustitelným souborem jazyka C++ a soubory hlaviček deklarace funkce nepoužily výše uvedenou techniku, proveďte v zdrojovém souboru jazyka C++ následující postup, který zabrání kompilátoru v upravení názvů funkcí jazyka C:

```cpp
extern "C" {
#include "MyCHeader.h"
}
```

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů. def](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializovat knihovnu DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Dekorované názvy](reference/decorated-names.md)

- [Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](exporting-from-a-dll.md)
