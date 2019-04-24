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

Pokud se rozhodnete použít **__declspec(dllimport)** spolu se souborem .def, měli byste změnit .def souboru na základě dat namísto – KONSTANTA snížit pravděpodobnost, že nesprávné kódování bude způsobovat problémy:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   DATA
```

V následující tabulce jsou uvedeny důvod, proč.

|Klíčové slovo|Vysílá v knihovně importu|Exporty|
|-------------|---------------------------------|-------------|
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|

Pomocí **__declspec(dllimport)** a oba seznamy – KONSTANTA `imp` verze a nedekorovaný název v lib knihovny DLL pro import knihovny, která je vytvořena umožňuje explicitní propojení. Pomocí **__declspec(dllimport)** a zobrazí DATA jenom `imp` verzí názvu.

Pokud používáte – KONSTANTA, následující konstrukce kódu lze použít pro přístup k `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/
if (ulDataInDll == 0L)   /*sample code fragment*/
```

\-or-

```
ULONG *ulDataInDll;      /*prototype*/
if (*ulDataInDll == 0L)  /*sample code fragment*/
```

Pokud používáte DATA v souboru .def, však můžete pouze kód zkompilovaný s následující definici přístup proměnné `ulDataInDll`:

```
__declspec(dllimport) ULONG ulDataInDll;

if (ulDataInDll == 0L)   /*sample code fragment*/
```

Použití – KONSTANTA je více nebezpečné, protože pokud zapomenete používat vyšší úroveň dereference, může potenciálně zpřístupnit tabulky importních adres ukazatel na proměnnou, není proměnná. Tento druh problému může často manifestovat jako narušení přístupu, protože tabulky importních adres se aktuálně jen pro čtení v kompilátoru a propojovacího programu.

Aktuální MSVC linker vydá upozornění, pokud nalezne CONSTANT v .def souboru pro tento případ. Pouze skutečný důvod pro použití – KONSTANTA je-li některý soubor objektu, kde hlavičkového souboru v seznamu nelze znovu zkompilovat **__declspec(dllimport)** na prototypu.

## <a name="see-also"></a>Viz také:

[Import do aplikace](importing-into-an-application.md)
