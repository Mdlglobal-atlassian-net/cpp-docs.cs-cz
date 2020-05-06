---
title: Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], C++ functions in C executables
- exporting DLLs [C++], C++ functions in C executables
- exporting functions [C++], C++ functions in C executables
- functions [C++], exporting
ms.assetid: 80b9e982-f52d-4312-a891-f73cc69f3c2b
ms.openlocfilehash: a694b77e3730ab82ec1698076cc66729ff115cdc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195231"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C

Pokud máte funkce v knihovně DLL napsané v jazyce C++, ke kterým chcete přistupovat z modulu jazyka C, měli byste tyto funkce deklarovat s propojením jazyka C namísto vazby C++. Není-li uvedeno jinak, kompilátor C++ používá pojmenování v jazyce c++ (označované také jako dekorace názvů) a konvence volání jazyka C++, které mohou být obtížné volat z jazyka C.

Chcete-li určit propojení jazyka `extern "C"` C, zadejte pro deklarace funkce. Příklad:

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů. def](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializovat knihovnu DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Dekorované názvy](reference/decorated-names.md)

- [Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](exporting-from-a-dll.md)
