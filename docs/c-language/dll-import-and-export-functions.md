---
title: Knihovna DLL Import a Export funkcí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3da47c4d6c5af518660b5799b3bf9ae3f512a6fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029218"
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