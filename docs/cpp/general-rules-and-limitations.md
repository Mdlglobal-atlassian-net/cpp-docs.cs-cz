---
title: Obecná pravidla a omezení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9a2a21de2cade8eb0d8776b340123df3535c36f4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034392"
---
# <a name="general-rules-and-limitations"></a>Obecná pravidla a omezení

## <a name="microsoft-specific"></a>Specifické pro Microsoft

- Je-li deklarovat funkci nebo objekt bez **dllimport** nebo **dllexport** atribut, funkce nebo objektu není považováno za součást rozhraní DLL. Definice funkce nebo objektu, proto musí být k dispozici v modulu nebo v jiném modulu stejného programu. Chcete-li funkce nebo objektu součástí rozhraní DLL, je třeba deklarovat definice funkce nebo objektu v modulu jako **dllexport**. V opačném případě je generována chyba linkeru.

     Je-li deklarovat funkci nebo objektu **dllexport** atribut, jeho definice musí být uvedena v některých modulu stejného programu. V opačném případě je generována chyba linkeru.

- Pokud obsahuje jeden modul ve svém programu **dllimport** a **dllexport** deklarace pro stejné funkce nebo objektu, **dllexport** atribut má přednost před přes **dllimport** atribut. Však bude vyvoláno upozornění kompilátoru. Příklad:

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- V jazyce C++ lze inicializovat ukazatel globálně deklarované nebo statická místní data nebo adresou datový objekt deklarovaný s **dllimport** atribut, který generuje chybu v jazyce C. Kromě toho můžete inicializovat statické lokální funkce ukazatel adresou funkce deklarovaná pomocí **dllimport** atribut. V jazyce C nastaví tato přiřazení ukazatel na adresu převodní rutina importu knihovny DLL (provizorního kódu, který předává řízení funkci) místo adresu funkce. V jazyce C++ nastaví ukazatel na adresu funkce. Příklad:

    ```cpp
    __declspec( dllimport ) void func1( void );
    __declspec( dllimport ) int i;

    int *pi = &i;                             // Error in C
    static void ( *pf )( void ) = &func1;     // Address of thunk in C,
                                              // function in C++

    void func2()
    {
       static int *pi = &i;                  // Error in C
       static void ( *pf )( void ) = &func1; // Address of thunk in C,
                                             // function in C++
    }
    ```

     Ale vzhledem k tomu program, který zahrnuje **dllexport** atribut v deklaraci objektu musí poskytnout definici pro daný objekt někde v programu, můžete inicializovat ukazatel globální ani místní statické funkce s Adresa **dllexport** funkce. Podobně můžete inicializovat globální ani místní statická data ukazatel adresou **dllexport** datový objekt. Následující kód například nevygeneruje chyby v jazyce C nebo C++:

    ```cpp
    __declspec( dllexport ) void func1( void );
    __declspec( dllexport ) int i;

    int *pi = &i;                              // Okay
    static void ( *pf )( void ) = &func1;      // Okay

    void func2()
    {
        static int *pi = &i;                   // Okay
        static void ( *pf )( void ) = &func1;  // Okay
    }
    ```

- Pokud použijete **dllexport** do běžné třídy, který má základní třída, která není označena jako **dllexport**, bude kompilátor generovat C4275.

     Kompilátor generuje stejné upozornění, pokud základní třída je specializace šablony třídy. Chcete-li tento problém obejít, označit základní třídy s **dllexport**. Problém s specializace šablony třídy je kam umístit **__declspec(dllexport)**; nemáte oprávnění k označení šablony třídy. Místo toho explicitně vytvořit instanci šablony třídy a označit tento explicitní vytváření instancí s **dllexport**. Příklad:

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

     Toto řešení selže, pokud je odvozená třída argument šablony. Příklad:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

     Protože to je běžný vzor se šablonami, kompilátor změnil sémantika **dllexport** při použití na třídu, která má jeden nebo více základních tříd, a pokud jeden nebo více základních tříd je specializace šablony třídy . V tomto případě kompilátor implicitně platí **dllexport** do specializace šablony třídy. Můžete takto a ne se vám upozornění:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[dllexport, dllimport](../cpp/dllexport-dllimport.md)