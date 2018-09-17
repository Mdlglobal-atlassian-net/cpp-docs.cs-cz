---
title: Uvolnění knihovny DLL s odloženým načtením | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- __FUnloadDelayLoadedDLL2
- delayed loading of DLLs, unloading
ms.assetid: 6463bc71-020e-4aff-a4ca-90360411c54e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa7b9652c37b6c4e841a798dae3cfeb69779b5ff
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45719924"
---
# <a name="unloading-a-delay-loaded-dll"></a>Uvolnění knihovny DLL s odloženým načtením

Zadaný výchozí odloženě zaváděné pomocné zkontroluje, zkontrolujte, jestli popisovače zpožděného načtení ukazatel a kopii původní tabulky importních adres (IAT) v poli pUnloadIAT. Pokud ano, se uloží ukazatel na seznam do popisovače zpoždění importu. To umožňuje pomocnou funkci k nalezení knihovny DLL podle názvu pro podporu explicitně uvolnění této knihovny DLL.

Tady jsou přidružené strukturách a funkcích pro explicitní uvolnění odloženě zaváděné knihovny DLL:

```cpp
//
// Unload support from delayimp.h
//

// routine definition; takes a pointer to a name to unload

ExternC
BOOL WINAPI
__FUnloadDelayLoadedDLL2(LPCSTR szDll);

// structure definitions for the list of unload records
typedef struct UnloadInfo * PUnloadInfo;
typedef struct UnloadInfo {
    PUnloadInfo     puiNext;
    PCImgDelayDescr pidd;
    } UnloadInfo;

// from delayhlp.cpp
// the default delay load helper places the unloadinfo records in the
// list headed by the following pointer.
ExternC
PUnloadInfo __puiHead;
```

Struktura UnloadInfo je implementováno pomocí C++ třídu, která používá **LocalAlloc** a **LocalFree** implementace jako jeho operátor **nové** a operátor  **Odstranit** v uvedeném pořadí. Tyto možnosti jsou uloženy v standardní odkazovaného seznamu pomocí __puiHead jako první pozice v seznamu.

__FUnloadDelayLoadedDLL volání funkce se pokusí najít název zadáte v seznamu načtené knihovny DLL (přesná shoda se vyžaduje). Pokud je nalezen, je zkopírován kopii IAT v pUnloadIAT přes horní spuštěné IAT obnovit ukazatele převodní rutina knihovny uvolněna pomocí **FreeLibrary**, odpovídající **UnloadInfo** záznamu je byl odpojen od v seznamu a odstranit a nastavena hodnota TRUE je vrácena.

Argument funkce __FUnloadDelayLoadedDLL2 je velká a malá písmena. Například zadali byste:

```cpp
__FUnloadDelayLoadedDLL2("user32.DLL");
```

a ne:

```cpp
__FUnloadDelayLoadedDLL2("User32.DLL");.
```

## <a name="see-also"></a>Viz také

[Základní informace o podpůrné funkci](understanding-the-helper-function.md)