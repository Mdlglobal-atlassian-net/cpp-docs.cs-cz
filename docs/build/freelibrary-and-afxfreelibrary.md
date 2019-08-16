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
ms.openlocfilehash: 9c657bb0d583270f81658afa53f36b1be6a4fd4a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493269"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary a AfxFreeLibrary

Procesy, které explicitně odkazují na knihovnu DLL, volají funkci [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary) , pokud již modul knihovny DLL nepotřebujete. Tato funkce sníží počet odkazů modulu a, pokud je počet odkazů nula, nemapuje ho z adresního prostoru procesu.

V aplikaci knihovny MFC použijte [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) namísto `FreeLibrary` uvolnění rozšiřující knihovny MFC DLL. Rozhraní (prototyp funkce) pro `AfxFreeLibrary` je stejné jako. `FreeLibrary`

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [LoadLibrary a AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Viz také:

[Vytváření C/C++ knihoven DLL v aplikaci Visual Studio](dlls-in-visual-cpp.md)<br/>
[FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)
