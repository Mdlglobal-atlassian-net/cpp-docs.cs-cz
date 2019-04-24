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
ms.openlocfilehash: 709e4fdbc24d6fbbac44944e686a6fecf8c9b8db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274037"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary a AfxFreeLibrary

Procesy, které explicitní propojení s voláním knihovny DLL [FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary) fungovat, když už modul knihovny DLL nepotřebujete. Tato funkce sníží počet odkazů modul a pokud počet odkazů je nula, zruší jeho mapování z adresního prostoru procesu.

V aplikaci MFC pomocí [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) místo `FreeLibrary` uvolnění rozšiřující knihovny DLL MFC. Rozhraní (prototyp funkce) pro `AfxFreeLibrary` je stejný jako `FreeLibrary`.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [LoadLibrary a AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Viz také:

[Knihovny DLL v jazyce Visual C++](dlls-in-visual-cpp.md)<br/>
[FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
