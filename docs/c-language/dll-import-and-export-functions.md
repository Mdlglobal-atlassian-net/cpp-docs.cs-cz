---
title: Import a export funkcí knihovny DLL
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
ms.openlocfilehash: b4f0674e68f2c7b8deeae663c42470b83777ac78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572381"
---
# <a name="dll-import-and-export-functions"></a>Import a export funkcí knihovny DLL

**Specifické pro Microsoft**

Nejvíce nejúplnější a nejaktuálnější informace k tomuto tématu najdete v [dllexport, dllimport](../cpp/dllexport-dllimport.md).

**Dllimport** a `dllexport` modifikátory třídy úložiště jsou rozšíření specifické pro společnost Microsoft pro jazyk C. Tyto modifikátory explicitně definují rozhraní DLL svému klientu (spustitelnému souboru nebo jiné knihovně DLL). Deklarace funkcí s modifikátorem `dllexport` odstraňuje potřebu souboru definice modulu (.DEF). Můžete také použít **dllimport** a `dllexport` modifikátory data a objekty.

**Dllimport** a `dllexport` modifikátory třídy úložiště je nutné použít s klíčovým slovem syntaxi rozšířeného atributu, `__declspec`, jak je znázorněno v tomto příkladu:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllExport int j;
DllExport int n;
```

Konkrétní informace o syntaxi pro rozšířené paměťové třídy modifikátory najdete v tématu [rozšířené atributy tříd úložiště](../c-language/c-extended-storage-class-attributes.md).

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)