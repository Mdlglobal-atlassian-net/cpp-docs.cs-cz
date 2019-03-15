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
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814017"
---
# <a name="exporting-c-functions-for-use-in-c-language-executables"></a>Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C

Pokud máte funkce v knihovně DLL, napsaný v jazyce C++, které chcete získat přístup z modulu jazyka C, by měla deklarovat tyto funkce s C-linkage místo propojení jazyka C++. Pokud není uvedeno jinak, kompilátor C++ používá C++ bezpečnost typů (označované také jako dekorování názvů) pojmenování a konvence volání C++, které může být obtížné volat z c

Chcete-li zadat C-linkage, zadejte `extern "C"` pro deklarace funkce. Příklad:

```
extern "C" __declspec( dllexport ) int MyFunc(long parm1);
```

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí souborů .def](exporting-from-a-dll-using-def-files.md)

- [Export z knihovny DLL pomocí __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++ – jazyk](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určit, kterou exportovací metodu použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializace knihovny DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Dekorované názvy](reference/decorated-names.md)

- [Používání příkazu extern pro specifikaci propojení](../cpp/using-extern-to-specify-linkage.md)

## <a name="see-also"></a>Viz také:

[Export z knihovny DLL](exporting-from-a-dll.md)
