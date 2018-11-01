---
title: Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: eaa742fc2738ef4aeeb54bb8fd2b0da923ac57de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667425"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C

Pokud máte funkce v knihovně DLL, napsaný v jazyce C++, které chcete získat přístup z modulu jazyka C, by měla deklarovat tyto funkce s C-linkage místo propojení jazyka C++. Pokud není uvedeno jinak, kompilátor C++ používá C++ bezpečnost typů (označované také jako dekorování názvů) pojmenování a konvence volání C++, které může být obtížné volat z c

Chcete-li zadat C-linkage, zadejte `extern "C"` pro deklarace funkce. Příklad:

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++ – jazyk](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určit, kterou exportovací metodu použít](../build/determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Dekorované názvy](../build/reference/decorated-names.md)

- [Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](../build/exporting-from-a-dll.md)