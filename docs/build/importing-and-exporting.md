---
title: Import a export | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c0727002e264f3b0cfe39b763c29fd70725b982
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="importing-and-exporting"></a>Import a export
Můžete importovat veřejné symboly do aplikace nebo funkce exportu z knihovny DLL pomocí dvou metod:  
  
-   Soubor definice (.def) modul použít při vytváření knihovny DLL  
  
-   Používat klíčová slova **deklarace __declspec(dllimport)** nebo **__declspec(dllexport)** v definici funkce v hlavní aplikaci  
  
## <a name="using-a-def-file"></a>Pomocí souborů .def  
 Soubor definice modulu (.def) je textový soubor obsahující jeden nebo více příkazů modulu, které popisují různé atributy knihovny DLL. Pokud nepoužijete **deklarace __declspec(dllimport)** nebo **__declspec(dllexport)** export funkcí knihovny DLL, knihovny DLL vyžaduje .def souboru.  
  
 Můžete použít soubory .def [importování do aplikace](../build/importing-using-def-files.md) nebo [export z knihovny DLL](../build/exporting-from-a-dll-using-def-files.md).  
  
## <a name="using-declspec"></a>Pomocí __declspec  
 Visual C++ používá **deklarace __declspec(dllimport)** a **__declspec(dllexport)** nahradit **__export** použil v 16bitové verzí aplikace Visual C++ – klíčové slovo.  
  
 Není potřeba použít **deklarace __declspec(dllimport)** pro váš kód mohl zkompilovat správně, ale tak umožňuje kompilátoru generovat lepší kód. Kompilátor je schopen generovat lepší kód, protože můžete určit, zda funkce existuje v knihovně DLL nebo Ne, což umožňuje kompilátoru vytvoření kód, který přeskočí úroveň dereference, které by normálně ve volání funkce, které překračuje hranice knihovny DLL. Ale musí používat **deklarace __declspec(dllimport)** import proměnné používané v knihovně DLL.  
  
 S oddílem export souboru správné .def **__declspec(dllexport)** se nevyžaduje. **__declspec(dllexport)** byla přidána do poskytují snadný způsob, jak funkce exportu ze souboru .exe nebo .dll bez použití souboru .def.  
  
 Formát přenosného spustitelného souboru Win32 je navržená k minimalizaci počet stránek, které musí být změněny opravit importy. K tomuto účelu umístí všechny adresy import pro žádné program na jednom místě názvem tabulky Import adres. To umožňuje zavaděči upravit pouze jednu nebo dvě stránky při přístupu k tyto importy.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Import do aplikace](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Export z knihovny DLL](../build/exporting-from-a-dll.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)