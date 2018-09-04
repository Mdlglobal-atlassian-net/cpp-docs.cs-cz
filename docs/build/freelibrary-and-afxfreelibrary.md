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
ms.openlocfilehash: 063c858253c12cfedbf252a124029b8cbc16a691
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680960"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary a AfxFreeLibrary
Procesy, které explicitní propojení s voláním knihovny DLL [FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152(v=vs.85).aspx) fungovat, když už modul knihovny DLL nepotřebujete. Tato funkce sníží počet odkazů modul a pokud počet odkazů je nula, zruší jeho mapování z adresního prostoru procesu.  
  
 V aplikaci MFC pomocí [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) místo `FreeLibrary` uvolnění rozšiřující knihovny DLL MFC. Rozhraní (prototyp funkce) pro `AfxFreeLibrary` je stejný jako `FreeLibrary`.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Jak implicitní propojení s knihovnou DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Určit, kterou propojovací metodu použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?  
  
-   [LoadLibrary a AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)   
 [FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152(v=vs.85).aspx)   
 [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)