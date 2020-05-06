---
title: Import pomocí souborů DEF
ms.date: 11/04/2016
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
ms.openlocfilehash: 13a6a375d6200f73dd9845d057d1954c2b65485c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273414"
---
# <a name="importing-using-def-files"></a>Import pomocí souborů DEF

Pokud se rozhodnete použít **__declspec (dllimport)** spolu se souborem. def, měli byste změnit soubor. def tak, aby používal data namísto konstanty, aby se snížila pravděpodobnost, že při nesprávném kódování dojde k problému:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

V následující tabulce je uveden důvod.

|Klíčové slovo|Generuje v knihovně importu.|Vývozních|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

Pomocí **__declspec (dllimport)** a konstanta uvádí jak `imp` verzi, tak i neupravený název v knihovně importu knihovny DLL, která je vytvořena za účelem umožnění explicitního propojení. Použití **__declspec (dllimport)** a seznamů dat je `imp` pouze verze názvu.

Použijete-li KONSTANTu, lze použít kteroukoli z následujících konstrukcí kódu pro přístup `ulDataInDll`k:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-ani

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Pokud však použijete DATA v souboru. def, bude mít přístup k proměnné `ulDataInDll`pouze kód kompilovaný s následující definicí:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

Použití KONSTANTy je více riskantní, protože pokud zapomenete použít vyšší úroveň dereference, můžete potenciálně získat přístup k proměnné v tabulce importních adres, nikoli na proměnné samotné. Tento typ problému se může často manifestovat jako porušení přístupu, protože je v současnosti pro kompilátor a linker aktuálně vytvořená tabulka importních adres.

Aktuální linker MSVC vydá upozornění, pokud se v souboru. def zobrazí jako pro účet v tomto případě jako KONSTANTa. Jediný skutečný důvod pro použití KONSTANTy je, pokud nemůžete znovu kompilovat soubor s hlavičkou, kde hlavičkový soubor neobsahoval **__declspec (dllimport)** na prototypu.

## <a name="see-also"></a>Viz také

[Import do aplikace](importing-into-an-application.md)
