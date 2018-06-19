---
title: Definice a Declarations (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d44a98fee82e41252b27fa5a1605b04a15af9115
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383482"
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