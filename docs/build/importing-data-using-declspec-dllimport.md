---
title: Import dat pomocí deklarace __declspec(dllimport)
ms.date: 11/04/2016
f1_keywords:
- dllimport
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: 7f4b9dcf7358e8301562fb5e856b9a3fd1cb42cd
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57419604"
---
# <a name="importing-data-using-declspecdllimport"></a>Import dat pomocí deklarace __declspec(dllimport)

V případě dat, pomocí **__declspec(dllimport)** položka pohodlí, které odstraní úroveň dereference. Při importu dat z knihovny DLL, máte stále procházejí tabulky importních adres. Před **__declspec(dllimport)**, to znamená, že jste museli pamatovat, abyste provedli vyšší úroveň dereference při přístupu k data exportovaná z knihovny DLL:

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

By pak exportovat data ve vašich. Soubor DEF:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

a k němu přístup mimo knihovnu DLL:

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Určíte-li data jako **__declspec(dllimport)**, kompilátor automaticky generuje kód dereference za vás. Už si nemusíte dělat starosti o výše uvedených kroků. Jak bylo uvedeno dříve, nepoužívejte **__declspec(dllimport)** deklarace dat při vytváření knihovny DLL. Funkce v rámci knihovny DLL nepoužívejte tabulky importních adres pro přístup k objektu data; proto nebude mít vyšší úroveň dereference.

Pokud chcete exportovat data automaticky z knihovny DLL, použijte tuto deklaraci:

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Viz také:

[Import do aplikace](../build/importing-into-an-application.md)
