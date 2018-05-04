---
title: Import dat pomocí deklarace __declspec(dllimport) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9877c5a229c3cabcb7703dd2617d1d57e3512f0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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