---
title: Obecná pravidla a omezení
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 1adbaf9d9be3a0fc0724603e01b81700554839bc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188586"
---
# <a name="general-rules-and-limitations"></a>Obecná pravidla a omezení

**Specifické pro společnost Microsoft**

- Pokud deklarujete funkci nebo objekt bez atributu **dllimport** nebo **dllexport** , funkce nebo objekt není považován za součást rozhraní dll. Proto musí být definice funkce nebo objektu přítomna v modulu nebo jiném modulu stejného programu. Chcete-li vytvořit součást funkce nebo objektu v rozhraní knihovny DLL, je nutné deklarovat definici funkce nebo objektu v jiném modulu jako **dllexport**. V opačném případě je vygenerována chyba linkeru.

   Pokud deklarujete funkci nebo objekt s atributem **dllexport** , jeho definice se musí objevit v některém modulu stejného programu. V opačném případě je vygenerována chyba linkeru.

- Pokud jeden modul v programu obsahuje deklarace **dllimport** i **dllexport** pro stejnou funkci nebo objekt, má atribut **dllexport** přednost před atributem **dllimport** . Vygeneruje se ale upozornění kompilátoru. Příklad:

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- V C++můžete inicializovat globálně deklarovaný nebo statický ukazatel místní dat nebo s adresou datového objektu deklarovaného s atributem **dllimport** , který generuje chybu v jazyce C. Kromě toho můžete inicializovat statický ukazatel místní funkce s adresou funkce deklarované s atributem **dllimport** . V jazyce C taková přiřazení nastaví ukazatel na adresu knihovny DLL import převodní rutiny (kód stub kódu, který přenáší řízení na funkci), nikoli adresu funkce. V C++systému nastaví ukazatel na adresu funkce. Příklad:

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

   Protože však program, který obsahuje atribut **dllexport** v deklaraci objektu, musí poskytnout definici pro daný objekt někde v programu, můžete inicializovat globální nebo místní ukazatel na statickou funkci s adresou funkce **dllexport** . Podobně lze inicializovat globální nebo místní ukazatel statických dat s adresou datového objektu **dllexport** . Například následující kód negeneruje chyby v C nebo C++:

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

- Použijete-li **dllexport** na regulární třídu, která má základní třídu, která není označena jako **dllexport**, kompilátor vygeneruje C4275.

   Kompilátor generuje stejné upozornění, pokud je základní třída specializací šablony třídy. Chcete-li se tomuto problému vyhnout, označte základní třídu pomocí příkazu **dllexport**. Problém s specializací šablony třídy je místo, kam umístit **__declspec (dllexport)** ; nemůžete označit šablonu třídy. Místo toho explicitně vytvořte instanci šablony třídy a označte tuto explicitní instanci pomocí příkazu **dllexport**. Příklad:

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

   Toto řešení se nepovede, pokud je argument šablony odvozenou třídou. Příklad:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

   Vzhledem k tomu, že se jedná o společný vzor se šablonami, kompilátor změnil sémantiku **dllexport** při použití na třídu, která má jednu nebo více základních tříd a v případě, že jedna nebo více základních tříd je specializací šablony třídy. V tomto případě kompilátor implicitně aplikuje **dllexport** na specializace šablon tříd. Můžete provést následující akce a nedostávat upozornění:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
