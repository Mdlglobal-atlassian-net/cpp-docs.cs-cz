---
title: LoadLibrary a AfxLoadLibrary
ms.date: 05/24/2018
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: c7700dd865e320686a2ad8bd036f207b9ecee6ac
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493212"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary a AfxLoadLibrary

Procesy volají [LoadLibraryExA](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa) nebo [LoadLibraryExW](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) (nebo [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) pro explicitní propojení s knihovnou DLL. Pokud je funkce úspěšná, mapuje zadanou knihovnu DLL do adresního prostoru volajícího procesu a vrátí popisovač knihovny DLL, kterou lze použít s jinými funkcemi v explicitním propojení, například `GetProcAddress` a. `FreeLibrary`

`LoadLibrary`pokusí se najít knihovnu DLL pomocí stejné vyhledávací sekvence, která se používá pro implicitní propojení. Pokud systém nemůže najít knihovnu DLL nebo pokud funkce vstupního bodu vrátí hodnotu false, `LoadLibrary` vrátí hodnotu null. Pokud volání `LoadLibrary` určuje modul knihovny DLL, který je již namapován do adresního prostoru volajícího procesu, funkce vrátí popisovač knihovny DLL a zvýší počet odkazů modulu.

Pokud má knihovna DLL funkci vstupního bodu, operační systém zavolá funkci v kontextu vlákna, které volalo `LoadLibrary`. Funkce vstupního bodu není volána, pokud je knihovna DLL již připojena k procesu z důvodu předchozího volání `LoadLibrary` , které nemá odpovídající volání `FreeLibrary` funkce.

Pro aplikace MFC, které načítají knihovny DLL rozšíření knihovny MFC, doporučujeme `AfxLoadLibrary` použít `LoadLibrary`místo. `AfxLoadLibrary`zpracovává synchronizaci vlákna před voláním `LoadLibrary`. Rozhraní (prototyp funkce) na `AfxLoadLibrary` je stejné jako. `LoadLibrary`

Pokud systém Windows nemůže načíst knihovnu DLL, proces se může pokusit o zotavení z chyby. Proces může například uživateli oznamovat chybu a požádat uživatele, aby určil jinou cestu ke knihovně DLL.

> [!IMPORTANT]
> Nezapomeňte zadat úplnou cestu všech knihoven DLL. Při načtení souborů se nejprve vyhledá aktuální adresář. Pokud neurčíte cestu k souboru, může být načten soubor, který není zamýšleným souborem. Dalším způsobem, jak to zabránit, je použití možnosti linkeru [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) .

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Pořadí hledání dynamických propojených knihoven](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary a AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Viz také:

- [Vytváření C/C++ knihoven DLL v aplikaci Visual Studio](dlls-in-visual-cpp.md)
