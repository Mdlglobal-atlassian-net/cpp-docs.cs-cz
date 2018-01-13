---
title: "Vytváření knihovny DLL určené pouze | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dd65085c9a0ecc0479c7d22feb5587d1e94447de
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-resource-only-dll"></a>Vytvoření knihovny DLL obsahující pouze prostředky  
  
Knihovny DLL určené pouze se knihovny DLL obsahující pouze prostředky, např. ikony, rastrové obrázky, řetězce a dialogová okna. Použití knihovny DLL určené pouze je dobrý způsob, jak mají společnou sadu prostředků mezi více programy. Je také vhodné zajistit aplikace s prostředky lokalizovány pro více jazyků (viz [lokalizované prostředky v aplikacích MFC: satelitní knihovny DLL](../build/localized-resources-in-mfc-applications-satellite-dlls.md)).  
  
K vytvoření knihovny DLL určené pouze, vytvořte nový projekt Win32 DLL (mimo MFC) a přidat prostředky do projektu.  
  
-   Vyberte Win32 Projekt v **nový projekt** dialogové okno a zadejte typ projektu knihovny DLL v Průvodci projektu Win32.  
  
-   Vytvoření nového prostředku skript, který obsahuje prostředky (například řetězec nebo z nabídky) pro knihovnu DLL a uložte soubor.  
  
-   Na **projektu** nabídky, klikněte na tlačítko **přidat existující položku**a potom vložte nový soubor .rc do projektu.  
  
-   Zadejte [/NOENTRY](../build/reference/noentry-no-entry-point.md) – možnost linkeru. / NOENTRY brání odkaz na linkeru `_main` do knihovny DLL; je potřeba vytvořit knihovny DLL určené pouze tuto možnost.  
  
-   Vytvořte knihovnu DLL.  
  
Aplikace, která používá knihovny DLL určené pouze by měly volat [LoadLibrary](../build/loadlibrary-and-afxloadlibrary.md) explicitně propojení na knihovnu DLL. Pro přístup k prostředkům, volejte obecné funkce `FindResource` a `LoadResource`, která pracovat na jakýkoli druh prostředku nebo volání jednoho z následujících prostředků specifických funkcí:  
  
-   `FormatMessage`  
  
-   `LoadAccelerators`  
  
-   `LoadBitmap`  
  
-   `LoadCursor`  
  
-   `LoadIcon`  
  
-   `LoadMenu`  
  
-   `LoadString`  
  
Aplikace by měly volat `FreeLibrary` po dokončení pomocí prostředky.  
  
## <a name="see-also"></a>Viz také  
  
[Práce se zdrojovými soubory](../windows/working-with-resource-files.md)  
[Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)