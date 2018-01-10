---
title: "Import do aplikace pomocí deklarace __declspec(dllimport) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __declspec
- dllimport
dev_langs: C++
helpviewer_keywords:
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: edb4da4e-f83a-44cf-a668-9239d49dbe42
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9766c6088e3f99711b936b10db0443da49b52c6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="importing-into-an-application-using-declspecdllimport"></a>Import do aplikace s použitím deklarace __declspec(dllimport)
Program, který používá veřejné symboly definované knihovnou DLL říká, že je importovat. Když vytvoříte hlavičkových souborů pro aplikace, které používají váš knihovny DLL k sestavení, používat **deklarace __declspec(dllimport)** na prohlášení o veřejné symboly. Klíčové slovo **deklarace __declspec(dllimport)** funguje zda exportovat soubory .def nebo s **__declspec(dllexport)** – klíčové slovo.  
  
 Aby byl váš kód čitelnější, definujte makro pro **deklarace __declspec(dllimport)** a pak pomocí makro deklaraci každého importovaného symbol:  
  
```  
#define DllImport   __declspec( dllimport )  
  
DllImport int  j;  
DllImport void func();  
```  
  
 Pomocí **deklarace __declspec(dllimport)** je volitelné na funkce deklarací, ale kompilátor vytváří efektivnější kódu, pokud použijete toto klíčové slovo. Ale musí používat **deklarace __declspec(dllimport)** pro import spustitelný soubor pro přístup k symboly veřejná data a objekty knihovnu DLL. Všimněte si, že uživatelé vaší knihovny DLL stále potřeba propojit s knihovnu importu.  
  
 Můžete použít stejný soubor hlaviček pro knihovnu DLL a klientské aplikace. K tomu použijte speciální preprocesoru symbol, který určuje, zda jsou vytváření knihovny DLL nebo klientskou aplikaci. Příklad:  
  
```  
#ifdef _EXPORTING  
   #define CLASS_DECLSPEC    __declspec(dllexport)  
#else  
   #define CLASS_DECLSPEC    __declspec(dllimport)  
#endif  
  
class CLASS_DECLSPEC CExampleA : public CObject  
{ ... class definition ... };  
```  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [Import a export vložených funkcí](../build/importing-and-exporting-inline-functions.md)  
  
-   [Vzájemné importy](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Viz také  
 [Import do aplikace](../build/importing-into-an-application.md)