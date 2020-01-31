---
title: FreeLibrary a AfxFreeLibrary
ms.date: 11/04/2016
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
ms.openlocfilehash: 0b530aca2ab036de186ff3fdb11be23f41e12d05
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821548"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary a AfxFreeLibrary

Procesy, které explicitně odkazují na knihovnu DLL, volají funkci [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary) , pokud již modul knihovny DLL nepotřebujete. Tato funkce snižuje počet odkazů modulu. A pokud je počet odkazů nula, je odmapována z adresního prostoru procesu.

V aplikaci knihovny MFC použijte [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) namísto `FreeLibrary` k uvolnění knihovny DLL rozšíření knihovny MFC. Rozhraní (prototyp funkce) pro `AfxFreeLibrary` je stejné jako `FreeLibrary`.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [LoadLibrary a AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Viz také:

[Vytvoření C/C++ knihoven DLL v aplikaci Visual Studio](dlls-in-visual-cpp.md)\
\ [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
