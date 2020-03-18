---
title: Import dat pomocí deklarace __declspec(dllimport)
ms.date: 11/04/2016
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
ms.openlocfilehash: c9dce798572a91bcb9721f022393abb669970131
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440455"
---
# <a name="importing-data-using-__declspecdllimport"></a>Import dat pomocí deklarace __declspec(dllimport)

V případě dat je použití **__declspec (dllimport)** pohodlnou položkou, která odebere vrstvu dereference. Při importu dat z knihovny DLL je stále nutné projít tabulku importních adres. Před **__declspec (dllimport)** to znamenalo, že jste si museli při přístupu k datům exportovaným z knihovny DLL udělat další úroveň nepřímých odkazů:

```
// project.h
#ifdef _DLL   // If accessing the data from inside the DLL
   ULONG ulDataInDll;

#else         // If accessing the data from outside the DLL
   ULONG *ulDataInDll;
#endif
```

Data pak můžete exportovat v. DEF soubor:

```
// project.def
LIBRARY project
EXPORTS
   ulDataInDll   CONSTANT
```

a přístup k němu mimo knihovnu DLL:

```
if (*ulDataInDll == 0L)
{
   // Do stuff here
}
```

Když označíte data jako **__declspec (dllimport)** , kompilátor automaticky generuje nepřímý kód pro vás. Už si nemusíte dělat starosti s výše uvedenými kroky. Jak bylo uvedeno dříve, při sestavování knihovny DLL nepoužívejte pro data deklaraci **__declspec (dllimport)** . Funkce v rámci knihovny DLL nepoužívají pro přístup k datovému objektu tabulku importních adres. Proto nebudete mít k dispozici další úroveň nepřímých odkazů.

Pokud chcete data exportovat automaticky z knihovny DLL, použijte tuto deklaraci:

```
__declspec(dllexport) ULONG ulDataInDLL;
```

## <a name="see-also"></a>Viz také

[Import do aplikace](importing-into-an-application.md)
