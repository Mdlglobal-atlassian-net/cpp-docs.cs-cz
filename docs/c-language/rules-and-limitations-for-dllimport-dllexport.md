---
title: Pravidla a omezení příkazů dllimport dllexport | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e39c3eb9a45c80ff5e855bd5aacbbef5a9533ef6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32388182"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>Pravidla a omezení příkazů dllimport/dllexport
**Konkrétní Microsoft**  
  
-   Pokud je deklarovat funkci bez **dllimport** nebo `dllexport` atribut funkce není považovány za součást rozhraní knihovny DLL. Proto definice funkce musí být v tomto modulu nebo v jiném modulu stejný program. Chcete-li funkce součástí rozhraní knihovny DLL, musí deklarovat definice funkce v modulu jako `dllexport`. Chyba linkerů, jinak hodnota vygeneruje, když je integrovaný klient.  
  
-   Pokud obsahuje jeden modul v programu **dllimport** a `dllexport` deklarace pro stejnou funkci, `dllexport` atribut má přednost před **dllimport** atribut. Upozornění kompilátoru ale generuje se. Příklad:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void );  
       DllExport void func1( void );   /* Warning; dllexport */  
                                       /* takes precedence. */  
  
    ```  
  
-   Nelze inicializovat ukazatel statických dat s adresou deklarovat s datový objekt **dllimport** atribut. Například následující kód vygeneruje chyby:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport int i;  
       .  
       .  
       .  
       int *pi = &i;                           /* Error */  
  
       void func2()  
       {  
          static int *pi = &i;                   /* Error */  
       }  
  
    ```  
  
-   Inicializace ukazatel na funkci statickou adresu funkce deklarovat s **dllimport** nastaví má ukazatel na adresu převodu import knihoven DLL (rámec kódu, který předává řízení funkce) namísto adresu funkce. Toto přiřazení nezobrazí žádnou chybovou zprávu:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void   
       .  
       .  
       .  
       static void ( *pf )( void ) = &func1;   /* No Error */  
  
       void func2()  
       {  
          static void ( *pf )( void ) = &func1;  /* No Error */  
       }  
  
    ```  
  
-   Vzhledem k tomu, že program, který obsahuje `dllexport` atribut v deklaraci objektu musíte zadat definici pro tento objekt, bude možné inicializovat globální nebo místní statické funkce ukazatel s adresou `dllexport` funkce. Podobně můžete inicializovat globální nebo místní statických dat ukazatel s adresou `dllexport` datový objekt. Příklad:  
  
    ```  
    #define DllImport   __declspec( dllimport )  
    #define DllExport   __declspec( dllexport )  
  
       DllImport void func1( void );  
       DllImport int i;  
  
       DllExport void func1( void );  
       DllExport int i;  
       .  
       .  
       .  
       int *pi = &i;                            /* Okay */  
       static void ( *pf )( void ) = &func1;    /* Okay */  
  
       void func2()  
       {  
          static int *pi = i;                     /* Okay */  
          static void ( *pf )( void ) = &func1;   /* Okay */  
       }  
  
    ```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Import a export funkcí knihovny DLL](../c-language/dll-import-and-export-functions.md)