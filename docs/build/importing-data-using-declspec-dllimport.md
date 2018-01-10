---
title: "Import dat pomocí deklarace __declspec(dllimport) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: dllimport
dev_langs: C++
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ebbc91b9144a7fe8025a34e9c1476ab23b604c46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="importing-data-using-declspecdllimport"></a>Import dat pomocí deklarace __declspec(dllimport)
V případě dat, pomocí **deklarace __declspec(dllimport)** je užitečný položka, která odebere úroveň dereference. Pokud importujete data z knihovny DLL, máte stále projít tabulku importních adres. Před **deklarace __declspec(dllimport)**, vynutila si museli pamatovat, abyste provedli vyšší úroveň dereference při přístupu k datům exportovat z knihovny DLL:  
  
```  
// project.h  
#ifdef _DLL   // If accessing the data from inside the DLL  
   ULONG ulDataInDll;  
  
#else         // If accessing the data from outside the DLL  
   ULONG *ulDataInDll;  
#endif  
```  
  
 By pak exportovat data ve vašem. DEF soubor:  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   CONSTANT  
```  
  
 a k němu přístup mimo knihovnu DLL:  
  
```  
if (*ulDataInDll == 0L)   
{  
   // Do stuff here  
}  
```  
  
 Pokud označíte data jako **deklarace __declspec(dllimport)**, kompilátor automaticky generuje dereferenční kód za vás. Už máte starat o výše uvedených kroků. Jak jsme uvedli dříve, nepoužívejte **deklarace __declspec(dllimport)** deklaraci na základě dat při vytváření knihovny DLL. Funkce v rámci knihovny DLL nepoužívají tabulku importních adres pro přístup k objektu dat; proto nebude mít další úroveň dereference.  
  
 Chcete-li automaticky exportovat data z knihovny DLL, použijte tuto deklaraci:  
  
```  
__declspec(dllexport) ULONG ulDataInDLL;  
```  
  
## <a name="see-also"></a>Viz také  
 [Import do aplikace](../build/importing-into-an-application.md)