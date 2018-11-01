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
ms.openlocfilehash: 7c0b63d80a8b4b03b55d6e50af6c08a8de0937de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596541"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary a AfxLoadLibrary

Procesy volají [LoadLibraryExA](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) nebo [LoadLibraryExW](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexw)(nebo [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) pro explicitní propojení ke knihovně DLL. Pokud funkce uspěje, namapuje určenou knihovnu DLL do adresového prostoru volajícího procesu a vrátí popisovač do knihovny DLL, který lze použít s jinými funkcemi v explicitním propojení – například `GetProcAddress` a `FreeLibrary`.

`LoadLibrary` pokusí se vyhledat knihovnu DLL pomocí stejné vyhledávací sekvence použité pro implicitní propojení. Pokud systém nemůže najít knihovnu DLL nebo funkci vstupního bodu vrátí hodnotu FALSE, `LoadLibrary` vrátí hodnotu NULL. Pokud volání `LoadLibrary` Určuje modul knihovny DLL, která je již mapovaný do adresového prostoru volajícího procesu, vrátí funkce popisovač knihovny DLL a zvýší hodnotu referenčního počtu modulu.

Pokud má knihovna DLL funkci vstupního bodu, operační systém zavolá funkci v kontextu vlákna, která volá `LoadLibrary`. Funkce vstupního bodu není volána, pokud knihovna DLL již připojena k procesu z důvodu předchozího volání `LoadLibrary` , který má bez odpovídajícího volání `FreeLibrary` funkce.

Pro aplikace MFC, které načítají rozšiřující knihovny MFC DLL, doporučujeme použít `AfxLoadLibrary` místo `LoadLibrary`. `AfxLoadLibrary` zpracovává synchronizaci vlákna před voláním `LoadLibrary`. Rozhraní (prototyp funkce) pro `AfxLoadLibrary` je stejný jako `LoadLibrary`.

Pokud Windows nemůže načíst knihovnu DLL, proces se může pokusit obnovit z chyby. Například proces by mohl oznámit uživateli chybu a požádat uživatele o určení jiné cesty k souboru DLL.

> [!IMPORTANT]
> Nezapomeňte zadat úplnou cestu všech knihoven DLL. Aktuální adresář je nejprve prohledán, když jsou soubory načteny. Pokud nemáte kvalifikovanou cestu k souboru, může být načten soubor, který není určený. Dalším způsobem, jak tomu je použít [/DEPENDENTLOADFLAG](../build/reference/dependentloadflag.md) – možnost linkeru.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Jak implicitní propojení s knihovnou DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Určit, kterou propojovací metodu použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [Pořadí hledání knihoven DLL](/windows/desktop/Dlls/dynamic-link-library-search-order)

- [FreeLibrary a AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>Viz také:

- [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)
