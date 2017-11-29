---
title: "Import a export vložených funkcí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exporting functions [C++], inline functions
- inline functions [C++], importing
- DLLs [C++], importing
- importing functions [C++]
- DLLs [C++], exporting from
- importing inline functions [C++]
- inline functions [C++], exporting
- functions [C++], importing
- functions [C++], exporting
ms.assetid: 89f488f8-b078-40fe-afd7-80bd7840057b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7753660b38d67b410927ce831b936a998353e622
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="importing-and-exporting-inline-functions"></a>Import a export vložených funkcí
Importované funkce může být definován jako vložené. Efekt je přibližně stejná jako definice vloženě standardní funkce; volání funkce jsou rozšířit do vloženého kódu, podobně jako makra. To je užitečné především jako způsob podpory C++ třídy v knihovně DLL může přímo tady některé své členské funkce pro efektivitu.  
  
 Jednu funkci importované vložené funkce je, že může trvat adresy v jazyce C++. Kompilátor vrátí adresu kopie vložené funkce, které se nacházejí v knihovně DLL. Další funkce importovaných vložených funkcí je, že můžete inicializovat statické místní data importované funkce, na rozdíl od globální importovaných dat.  
  
> [!CAUTION]
>  Jste měli být opatrní při poskytování importu vložených funkcí, protože mohou vytvářet možné konflikty verzí. Vložená funkce je rozšířena do kódu aplikace; Proto pokud později přepíšete funkce, se neaktualizuje Pokud znovu zkompiluje vlastní aplikace. (Obvykle, funkcí knihovny DLL můžete aktualizovat bez nutnosti opětovného sestavení aplikace, které je používají.)  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Export z knihovny DLL](../build/exporting-from-a-dll.md)  
  
-   [Export z knihovny DLL pomocí. DEF soubory](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Export z knihovny DLL pomocí deklarace __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Export a import pomocí třídy AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Určení použité metody exportu](../build/determining-which-exporting-method-to-use.md)  
  
-   [Import do aplikace pomocí deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
## <a name="see-also"></a>Viz také  
 [Import a export](../build/importing-and-exporting.md)