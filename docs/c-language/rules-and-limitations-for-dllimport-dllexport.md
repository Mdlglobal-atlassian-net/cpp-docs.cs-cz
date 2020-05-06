---
title: Pravidla a omezení pro dllimport-dllexport
ms.date: 11/04/2016
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
ms.openlocfilehash: cc83a43fd09299710585fa104dbd4dc847036c68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158420"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>Pravidla a omezení příkazů dllimport/dllexport

**Specifické pro Microsoft**

- Pokud deklarujete funkci bez atributu **dllimport** nebo `dllexport` , funkce není považována za součást rozhraní dll. Proto musí být definice funkce přítomna v modulu nebo v jiném modulu stejného programu. Chcete-li provést funkci součásti rozhraní DLL, je nutné deklarovat definici funkce v jiném modulu jako `dllexport`. V opačném případě je při sestavení klienta generována chyba linkeru.

- Pokud jeden modul v programu obsahuje **dllimport** a `dllexport` deklarace pro stejnou funkci, má `dllexport` atribut přednost před atributem **dllimport** . Vygeneruje se ale upozornění kompilátoru. Příklad:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllExport void func1( void );   /* Warning; dllexport */
                                       /* takes precedence. */

    ```

- Nelze inicializovat ukazatel statických dat s adresou datového objektu deklarovaného s atributem **dllimport** . Například následující kód vygeneruje chyby:

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

- Inicializace ukazatele statické funkce s adresou funkce deklarované pomocí **atributu DllImport** nastaví ukazatel na adresu knihovny DLL import převodní rutiny (zástupná procedura kódu, která přenáší řízení na funkci), nikoli na adresu funkce. Toto přiřazení negeneruje chybovou zprávu:

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

- Vzhledem k tomu, že program `dllexport` , který obsahuje atribut v deklaraci objektu, musí poskytnout definici pro daný objekt, můžete inicializovat globální nebo místní ukazatel statické funkce s adresou `dllexport` funkce. Podobně můžete inicializovat globální nebo místní ukazatel statických dat s adresou `dllexport` datového objektu. Příklad:

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Import a export funkcí knihovny DLL](../c-language/dll-import-and-export-functions.md)
