---
title: Obecná pravidla a omezení | Microsoft Docs
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
ms.openlocfilehash: 218bd2fb58ccc4d3a3c2e1d297be930350577d18
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="general-rules-and-limitations"></a>Obecná pravidla a omezení
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
  
-   Pokud deklarace funkce nebo objektu bez **dllimport** nebo `dllexport` atributu, funkce nebo objektu není považovány za součást rozhraní knihovny DLL. Proto definici funkce nebo objektu musí být v tomto modulu nebo v jiném modulu stejný program. Chcete-li funkce nebo objektu součástí rozhraní knihovny DLL, musí deklarovat definici funkce nebo objektu v modulu jako `dllexport`. Chyba linkerů, jinak se generuje.  
  
     Pokud deklarace funkce nebo objektu s `dllexport` atribut, jeho definice musí být v některých modulu stejný program. Chyba linkerů, jinak se generuje.  
  
-   Pokud obsahuje jeden modul v programu i **dllimport** a `dllexport` deklarace pro stejné funkce nebo objekt, `dllexport` atribut má přednost před **dllimport** atribut. Upozornění kompilátoru ale generuje se. Příklad:  
  
    ```  
    __declspec( dllimport ) int i;  
    __declspec( dllexport ) int i;   // Warning; inconsistent;  
                                     // dllexport takes precedence.  
    ```  
  
-   V jazyce C++, bude možné inicializovat ukazatel globálně deklarované nebo statické místní data nebo s adresou deklarovat s datový objekt **dllimport** atribut, který generuje chybu v C. Navíc můžete inicializovat ukazatel na funkci statické místní adresu funkce deklarovat s **dllimport** atribut. Takové přiřazení v jazyce C, nastaví má ukazatel na adresu převodu import knihoven DLL (rámec kódu, který předává řízení funkce) namísto adresu funkce. V jazyce C++ nastaví ukazatel na adresu funkce. Příklad:  
  
    ```  
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
  
     Ale vzhledem k tomu, že program, který obsahuje `dllexport` atribut v deklaraci objektu musíte zadat definici pro tento objekt někde v programu, můžete inicializovat globální nebo místní statické funkce ukazatel s adresou `dllexport`funkce. Podobně můžete inicializovat globální nebo místní statických dat ukazatel s adresou `dllexport` datový objekt. Následující kód například negeneruje chyby v jazyka C nebo C++:  
  
    ```  
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
  
-   Pokud použijete `dllexport` na regulární třídu, která obsahuje základní třídu, která není označená jako `dllexport`, vygeneruje kompilátor C4275.  
  
     Kompilátor generuje stejné upozornění, pokud specializace šablony třídy základní třídy. Chcete-li tento problém obejít, označit základní třídy s `dllexport`. Problém s specializace šablony třídy je kam umístit **__declspec(dllexport)**; nejsou povoleny označit šablona třídy. Místo toho explicitní vytvoření instance šablony třídy a označit tento explicitní vytvoření instance s `dllexport`. Příklad:  
  
    ```  
    template class __declspec(dllexport) B<int>;  
    class __declspec(dllexport) D : public B<int> {  
    // ...  
    ```  
  
     Toto řešení se nezdaří, pokud argument šablony je odvozená třída. Příklad:  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
     Vzhledem k tomu, že toto je běžný vzor se šablonami, kompilátor změnit sémantika `dllexport` při použití třídy, která má jeden nebo více základní třídy a specializace šablony tříd po nejméně jedna ze základních tříd. V takovém případě kompilátor implicitně platí `dllexport` k specializace šablon tříd. Můžete provést následující a není získat upozornění:  
  
    ```  
    class __declspec(dllexport) D : public B<D> {  
    // ...  
    ```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)