---
title: Pravidla a omezení příkazů dllimport / dllexport | Dokumentace Microsoftu
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
ms.openlocfilehash: 6819ad58e3814f7c632c44db4549321e0c6969e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038396"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>Pravidla a omezení příkazů dllimport/dllexport

**Specifické pro Microsoft**

- Pokud deklarujete funkci bez **dllimport** nebo `dllexport` atribut, funkce není považováno za součást rozhraní DLL. Definice funkce proto musí být k dispozici v modulu nebo v jiném modulu stejného programu. Chcete-li funkce součástí rozhraní DLL, je třeba deklarovat definice funkce v modulu jako `dllexport`. V opačném případě je přiřazena chyba linkeru se vygeneruje, když je postavená klienta.

- Pokud obsahuje jeden modul ve svém programu **dllimport** a `dllexport` deklarace pro stejnou funkci `dllexport` atribut má přednost před **dllimport** atribut. Však bude vyvoláno upozornění kompilátoru. Příklad:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllExport void func1( void );   /* Warning; dllexport */
                                       /* takes precedence. */

    ```

- Nelze inicializovat statický datový ukazatele s adresou datový objekt deklarovaný s **dllimport** atribut. Například následující kód vygeneruje chyby:

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

- Inicializace ukazatele na funkci statickou adresu funkce deklarovaná pomocí **dllimport** nastaví ukazatel na adresu převodní rutina importu knihovny DLL (provizorního kódu, který předává řízení funkci) místo adresy funkce. Toto přiřazení negeneruje chybová zpráva:

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

- Vzhledem k tomu, že program, který obsahuje `dllexport` atribut v deklaraci objektu musí poskytnout definici pro daný objekt, můžete inicializovat globální ani místní statická funkce ukazatel adresou `dllexport` funkce. Podobně můžete inicializovat globální ani místní statická data ukazatel adresou `dllexport` datový objekt. Příklad:

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

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Import a export funkcí knihovny DLL](../c-language/dll-import-and-export-functions.md)