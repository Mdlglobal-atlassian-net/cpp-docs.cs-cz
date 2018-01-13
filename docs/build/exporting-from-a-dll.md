---
title: Export z knihovny DLL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting DLLs [C++], about exporting from DLLs
- exporting functions [C++], DLLs (exporting from)
- exporting DLLs [C++]
- DLLs [C++], exporting from
- DLL exports [C++]
- functions [C++], exporting
- exports table [C++]
ms.assetid: a08f86c4-5996-460b-ae54-da2b764045f0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64571a0f648c0e33635990d9ca57744877429049
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exporting-from-a-dll"></a>Export z knihovny DLL  
  
Soubor DLL má velmi podobné na soubor .exe s jedním důležité rozdílem rozložení – soubor knihovny DLL obsahuje exportní tabulka. Exportní tabulka obsahuje název každé funkce, který exportuje knihovnu DLL pro další spustitelné soubory. Tyto funkce jsou vstupní body do knihovny DLL; podle další spustitelné soubory jsou přístupné pouze tyto funkce v tabulce exportuje. Jiných funkcí v knihovně DLL jsou privátní na knihovnu DLL. Exportní tabulka knihovny DLL lze zobrazit pomocí [DUMPBIN](../build/reference/dumpbin-reference.md) nástroj s parametrem/EXPORTS.  
  
 Funkce můžete exportovat z knihovny DLL pomocí dvou metod:  
  
-   Vytvořte soubor modulu definice (.def) a při vytváření knihovny DLL pomocí souborů .def. Tuto metodu použijte, pokud chcete [export funkcí z knihovny DLL podle pořadových nikoli podle názvu](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).  
  
-   Použití klíčového slova **__declspec(dllexport)** v definici funkcí.  
  
 Při exportu funkce pomocí některé z metod, nezapomeňte použít [__stdcall](../cpp/stdcall.md) konvence volání.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Export z knihovny DLL pomocí souborů .def](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Export z knihovny DLL pomocí deklarace __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Export a import pomocí třídy AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo jazyka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Export funkcí z knihovny DLL podle pořadových nikoli podle názvu](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)  
  
-   [Určení použité metody exportu](../build/determining-which-exporting-method-to-use.md)  
  
-   [Rozhodování o způsobu vytváření použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
-   [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Import do aplikace](../build/importing-into-an-application.md)  
  
-   [Import a export vložených funkcí](../build/importing-and-exporting-inline-functions.md)  
  
-   [Vzájemné importy](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Viz také  
 [Import a export](../build/importing-and-exporting.md)