---
title: FreeLibrary a AfxFreeLibrary | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
dev_langs:
- C++
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a86300b4814c8712f3cf88f91421dc1d0842e8a7
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081517"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary a AfxFreeLibrary

Procesy, které explicitní propojení s voláním knihovny DLL [FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary) fungovat, když už modul knihovny DLL nepotřebujete. Tato funkce sníží počet odkazů modul a pokud počet odkazů je nula, zruší jeho mapování z adresního prostoru procesu.

V aplikaci MFC pomocí [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) místo `FreeLibrary` uvolnění rozšiřující knihovny DLL MFC. Rozhraní (prototyp funkce) pro `AfxFreeLibrary` je stejný jako `FreeLibrary`.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Jak implicitní propojení s knihovnou DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Určit, kterou propojovací metodu použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [LoadLibrary a AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)

- [GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>Viz také

[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)<br/>
[FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)
[AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)