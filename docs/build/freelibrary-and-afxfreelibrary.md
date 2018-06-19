---
title: FreeLibrary a AfxFreeLibrary | Microsoft Docs
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
ms.openlocfilehash: f1e1bf5f1a05438ddf89af86c9b0d12e7885b901
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367508"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary a AfxFreeLibrary
Procesy, které explicitně propojit volání knihovny DLL [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188) fungovat, když už není potřeba modul knihovny DLL. Tato funkce sníží počet odkazů modul a, pokud počet odkazů rovná nule, zruší jeho mapování z adresního prostoru procesu.  
  
 V aplikaci MFC použít [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) místo `FreeLibrary` se uvolnit knihovnu DLL. Rozhraní (prototyp funkce) pro `AfxFreeLibrary` je stejný jako `FreeLibrary`.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Postup propojení implicitně s knihovny DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Rozhodování o způsobu vytváření použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [LoadLibrary a AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)   
 [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)   
 [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)