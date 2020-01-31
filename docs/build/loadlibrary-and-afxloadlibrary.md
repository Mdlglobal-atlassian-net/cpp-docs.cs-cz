---
title: LoadLibrary a AfxLoadLibrary
description: Použití LoadLibrary a AfxLoadLibrary pro explicitní načítání knihoven DLL v MSVC.
ms.date: 01/28/2020
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: f803212c4485f7517dc42802f1ff581ffa4e609d
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821535"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>LoadLibrary a AfxLoadLibrary

Procesy volají funkci [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) nebo [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) k explicitnímu propojení s knihovnou DLL. (Aplikace MFC používají [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary) nebo [AfxLoadLibraryEx](../mfc/reference/application-information-and-management.md#afxloadlibraryex).) Pokud je funkce úspěšná, namapuje zadanou knihovnu DLL do adresního prostoru volajícího procesu a vrátí popisovač do knihovny DLL. Popisovač je vyžadován v dalších funkcích používaných pro explicitní propojení, například `GetProcAddress` a `FreeLibrary`. Další informace najdete v tématu [explicitní propojování](linking-an-executable-to-a-dll.md#linking-explicitly).

`LoadLibrary` se pokusí najít knihovnu DLL pomocí stejné vyhledávací sekvence, která se používá pro implicitní propojení. `LoadLibraryEx` nabízí větší kontrolu nad pořadím cesty pro hledání. Další informace najdete v tématu [pořadí hledání knihovny dynamického propojení](/windows/win32/dlls/dynamic-link-library-search-order). Pokud systém nemůže najít knihovnu DLL nebo pokud funkce vstupního bodu vrátí hodnotu FALSE, `LoadLibrary` vrátí hodnotu NULL. Pokud volání `LoadLibrary` určuje modul knihovny DLL, který je již namapován do adresního prostoru volajícího procesu, funkce vrátí popisovač knihovny DLL a zvýší počet odkazů modulu.

Pokud má knihovna DLL funkci vstupního bodu, operační systém zavolá funkci v kontextu vlákna, které se říká `LoadLibrary` nebo `LoadLibraryEx`. Funkce vstupního bodu není volána, je-li knihovna DLL již k procesu připojena. K tomu dojde v případě, že předchozí volání `LoadLibrary` nebo `LoadLibraryEx` pro knihovnu DLL nemá odpovídající volání funkce `FreeLibrary`.

Pro aplikace MFC, které načítají knihovny DLL rozšíření knihovny MFC, doporučujeme použít `AfxLoadLibrary` nebo `AfxLoadLibraryEx` namísto `LoadLibrary` nebo `LoadLibraryEx`. Funkce knihovny MFC zpracovává synchronizaci vláken před explicitním načtením knihovny DLL. Rozhraní (prototypy funkcí) pro `AfxLoadLibrary` a `AfxLoadLibraryEx` jsou stejná jako `LoadLibrary` a `LoadLibraryEx`.

Pokud systém Windows nemůže načíst knihovnu DLL, váš proces se může pokusit o zotavení z chyby. Například může uživatele s chybou informovat a pak požádat o další cestu k knihovně DLL.

> [!IMPORTANT]
> Nezapomeňte zadat úplnou cestu všech knihoven DLL. Při načítání souborů pomocí `LoadLibrary`se může aktuální adresář vyhledat jako první. Pokud plně neurčíte cestu k souboru, může být načten jiný soubor, než který je určen. Při vytváření knihovny DLL použijte možnost linkeru [/DEPENDENTLOADFLAG](reference/dependentloadflag.md) a určete pořadí vyhledávání staticky propojených ZÁVISLOSTÍ knihoven DLL. V rámci knihoven DLL použijte jak úplné cesty k explicitně načteny závislosti, a `LoadLibraryEx` nebo `AfxLoadLibraryEx` parametry volání pro určení pořadí hledání modulu. Další informace najdete v tématu [zabezpečení knihovny dynamického propojení](/windows/win32/dlls/dynamic-link-library-security) a [pořadí hledání dynamické knihovny](/windows/win32/dlls/dynamic-link-library-search-order).

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [Pořadí hledání dynamických propojených knihoven](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary a AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Viz také:

- [Vytváření C/C++ knihoven DLL v aplikaci Visual Studio](dlls-in-visual-cpp.md)
