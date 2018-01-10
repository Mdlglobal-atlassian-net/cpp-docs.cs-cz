---
title: Definice a Declarations (C) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4886ee6a8bce115c2f7676124477ec81e71b16d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="definitions-and-declarations-c"></a>Definice a deklarace (C)
**Konkrétní Microsoft**  
  
 Odkazuje na knihovnu DLL rozhraní pro všechny položky (funkce a data), které jsou známé exportovat některé programem v systému. To znamená, všechny položky, které jsou deklarované jako **dllimport** nebo `dllexport`. Všechny deklarace, které jsou součástí rozhraní knihovny DLL musí být buď **dllimport** nebo `dllexport` atribut. Však definici lze zadat pouze `dllexport` atribut. Následující definice funkce například vygeneruje chybu kompilátoru:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllImport int func()    /* Error; dllimport prohibited in */  
                        /* definition. */  
{  
   return 1;  
}  
```  
  
 Tento kód také vygeneruje chybu:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllImport int i = 10;      /* Error; this is a definition. */  
```  
  
 Tato syntaxe je však správná:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport int i = 10;      /* Okay: this is an export definition. */  
```  
  
 Použití `dllexport` znamená definici, zatímco **dllimport** znamená deklaraci. Klíčové slovo `extern` je nutné použít spolu s atributem `dllexport` k vynucení deklarace. V opačném případě se předpokládá definice.  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
extern DllImport int k;   /* These are correct and imply */  
Dllimport int j;          /* a declaration. */      
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Import a export funkcí knihovny DLL](../c-language/dll-import-and-export-functions.md)