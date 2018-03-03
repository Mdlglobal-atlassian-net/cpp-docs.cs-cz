---
title: "New – operátor (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 68843f0619b5ebc057f83bdb4f49807a15fb86a1
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="new-operator-c"></a>new – operátor (C++)
Přidělí paměť pro objekt nebo pole objektů *název typu* z volné úložiště a vrátí vhodně typové, nenulové hodnoty ukazatele k objektu.  
  
> [!NOTE]
>  Rozšíření komponent C++ Microsoft poskytuje podporu pro `new` – klíčové slovo pro přidání položek vtable slot. Další informace najdete v tématu [new (nový slot v tabulce vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[::] new [placement] new-type-name [new-initializer]  
[::] new [placement] ( type-name ) [new-initializer]  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud je úspěšné, **nové** vrátí nula nebo vyvolá výjimku, zjistit [nové a odstraňte operátory](../cpp/new-and-delete-operators.md) Další informace. Toto výchozí chování můžete změnit psaní vlastní rutiny zpracování výjimek a volání [_set_new_handler –](../c-runtime-library/reference/set-new-handler.md) funkce běhové knihovny s názvem vaší funkce jako její argument.  
  
 Informace o tom, jak vytvořit objekt na spravovaná halda najdete v tématu [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
 Když **nové** se používá k přidělení paměti pro objekt třídy C++, objektu volání konstruktoru po je paměť přidělená.  
  
 Použití [odstranit](../cpp/delete-operator-cpp.md) operátor se zrušit přidělení paměti přidělené s **nové** operátor.  
  
 V následujícím příkladu přiděluje a pak uvolní dvourozměrná pole znaků velikosti `dim` podle 10. Při přidělování multidimenzionálního pole, všechny dimenze kromě prvního musí být konstantní výrazy, která se vyhodnotí jako kladné hodnoty; dimenze krajní levé pole může být jakýkoli výraz, jehož výsledkem je kladné celé číslo. Při přidělování pole pomocí **nové** operátor, první dimenze může být nula – **nové** operátor vrátí jedinečný ukazatel.  
  
```  
char (*pchar)[10] = new char[dim][10];  
delete [] pchar;  
```  
  
 *Název typu* nemůže obsahovat **const**, `volatile`, deklarace tříd nebo deklarace výčtů. Následující výraz je proto neplatný:  
  
```  
volatile char *vch = new volatile char[20];  
```  
  
 **Nové** operátor nepřidělí odkazové typy, protože nejsou objekty.  
  
 **Nové** operátor nelze použít k přidělení funkce, ale může sloužit k přidělení ukazatelé na funkce. V následujícím příkladu přiděluje a pak uvolní pole sedm ukazatele na funkce, které vrací celá čísla.  
  
```  
int (**p) () = new (int (*[7]) ());  
delete *p;  
```  
  
 Pokud používáte operátor **nové** bez jakékoli další argumenty a kompilaci s [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md), nebo [/EHs](../build/reference/eh-exception-handling-model.md) možnost, bude kompilátor generování kódu pro volání operátor **odstranit** Pokud konstruktoru vyvolá výjimku.  
  
 Následující seznam popisuje elementy gramatika **nové**:  
  
 *placement*  
 Poskytuje způsob předat další argumenty, pokud jste přetížení **nové**.  
  
 *type-name*  
 Určuje typ přidělování; může být buď předdefinovaných nebo uživatelem definovaný typ. Pokud specifikace typu je složitá, může být obklopená závorkách vynutit pořadí vazby.  
  
 *Inicializátor*  
 Obsahuje hodnotu pro objekt inicializovaný. Inicializátory nelze zadat pro pole. **Nové** operátor vytvoří pole objektů, pouze v případě, že má třída výchozí konstruktor.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu přiděluje pole znaků a třída objektu `CName` a pak je uvolní.  
  
```  
// expre_new_Operator.cpp  
// compile with: /EHsc  
#include <string.h>  
  
class CName {  
public:  
   enum {  
      sizeOfBuffer = 256  
   };  
  
   char m_szFirst[sizeOfBuffer];  
   char m_szLast[sizeOfBuffer];  
  
public:  
   void SetName(char* pszFirst, char* pszLast) {  
     strcpy_s(m_szFirst, sizeOfBuffer, pszFirst);  
     strcpy_s(m_szLast, sizeOfBuffer, pszLast);  
   }  
  
};  
  
int main() {  
   // Allocate memory for the array  
   char* pCharArray = new char[CName::sizeOfBuffer];  
   strcpy_s(pCharArray, CName::sizeOfBuffer, "Array of characters");  
  
   // Deallocate memory for the array  
   delete [] pCharArray;             
   pCharArray = NULL;  
  
   // Allocate memory for the object  
   CName* pName = new CName;  
   pName->SetName("Firstname", "Lastname");  
  
   // Deallocate memory for the object  
   delete pName;  
   pName = NULL;  
}  
```  
  
## <a name="example"></a>Příklad  
 Pokud používáte nové formě umístění **nové** operátor, formu přidělení, kompilátor s argumenty kromě velikost nepodporuje umístění formu **odstranit** operátor Pokud konstruktor, vyvolá výjimku. Příklad:  
  
```  
// expre_new_Operator2.cpp  
// C2660 expected  
class A {  
public:  
   A(int) { throw "Fail!"; }  
};  
void F(void) {  
   try {  
      // heap memory pointed to by pa1 will be deallocated  
      // by calling ::operator delete(void*).  
      A* pa1 = new A(10);  
   } catch (...) {  
   }  
   try {  
      // This will call ::operator new(size_t, char*, int).  
      // When A::A(int) does a throw, we should call  
      // ::operator delete(void*, char*, int) to deallocate  
      // the memory pointed to by pa2.  Since  
      // ::operator delete(void*, char*, int) has not been implemented,  
      // memory will be leaked when the deallocation cannot occur.  
  
      A* pa2 = new(__FILE__, __LINE__) A(20);  
   } catch (...) {  
   }  
}  
  
int main() {  
   A a;  
}  
```  
  
## <a name="initializing-object-allocated-with-new"></a>Inicializaci objektu přiřazen výraz new  
 Volitelný *inicializátoru* pole je součástí gramatika pro **nové** operátor. To umožňuje nové objekty inicializovat konstruktory definovanými uživatelem. Další informace o tom, jak se provádí inicializace najdete v tématu [inicializátory](../cpp/initializers.md). Následující příklad ukazuje, jak pomocí výrazu inicializace s **nové** operátor:  
  
```  
// expre_Initializing_Objects_Allocated_with_new.cpp  
class Acct  
{  
public:  
    // Define default constructor and a constructor that accepts  
    //  an initial balance.  
    Acct() { balance = 0.0; }  
    Acct( double init_balance ) { balance = init_balance; }  
private:  
    double balance;  
};  
  
int main()  
{  
    Acct *CheckingAcct = new Acct;  
    Acct *SavingsAcct = new Acct ( 34.98 );  
    double *HowMuch = new double ( 43.0 );  
    // ...  
}  
```  
  
 V tomto příkladu objekt `CheckingAcct` je přidělen s použitím **nové** je zadán operátor však žádné výchozí inicializace. Proto je zavolán výchozí konstruktor třídy `Acct()`. Poté je objekt `SavingsAcct` přiřazen stejným způsobem s tím rozdílem, že je explicitně inicializován na hodnotu 34,98. Protože je typu 34.98 **dvojité**, konstruktor, který přebírá argument tohoto typu je volána pro zpracování inicializace. Nakonec je netřídní typ `HowMuch` inicializován na hodnotu 43,0.  
  
 Pokud je objekt typu třídy a třídy obsahuje konstruktorů (jako v předchozím příkladu), můžete objekt inicializovat pomocí **nové** operátor pouze v případě, že je splněna jedna z těchto podmínek:  
  
-   Argumenty zadané v inicializátoru souhlasí s argumenty konstruktoru.  
  
-   Třída má výchozí konstruktor (konstruktor, který lze volat bez argumentů).  
  
 Žádné explicitní za element inicializace lze provést při přidělování maticových pomocí **nové** operátor; pouze výchozí konstruktor, pokud existuje, je volána. V tématu [výchozí argumenty](../cpp/default-arguments.md) Další informace.  
  
 Pokud dojde k selhání přidělení paměti (`operator new` vrátí hodnotu 0), není inicializace provedena. Je to ochrana proti pokusům o inicializaci neexistujících dat.  
  
 Stejně jako u volání funkcí není definováno pořadí, ve kterém jsou inicializované výrazy vyhodnoceny. Takže byste se neměli spoléhat, že jsou před provedením přidělení paměti tyto výrazy zcela vyhodnoceny. Pokud se nezdaří přidělování paměti a **nové** operátor vrátí hodnotu 0, nemusí některé výrazy v inicializátoru vyhodnotí úplně.  
  
## <a name="lifetime-of-objects-allocated-with-new"></a>Doba životnosti objektů přiřazen výraz new  
 Objekty přidělený **nové** operátor nejsou zničený, když je byl ukončen oboru, ve kterém jsou definovány. Protože **nové** operátor vrací ukazatel na objekty přiděluje, program musí definovat ukazatel s vhodný rozsah pro přístup k těmto objektům. Příklad:  
  
```  
// expre_Lifetime_of_Objects_Allocated_with_new.cpp  
// C2541 expected  
int main()  
{  
    // Use new operator to allocate an array of 20 characters.  
    char *AnArray = new char[20];  
  
    for( int i = 0; i < 20; ++i )  
    {  
        // On the first iteration of the loop, allocate  
        //  another array of 20 characters.  
        if( i == 0 )  
        {  
            char *AnotherArray = new char[20];  
        }  
    }  
  
    delete [] AnotherArray; // Error: pointer out of scope.  
    delete [] AnArray;      // OK: pointer still in scope.  
}  
```  
  
 Jakmile ukazatel `AnotherArray` v příkladu překročí obor, nelze již objekt odstranit.  
  
## <a name="how-new-works"></a>Jak funguje výraz new  
 *Přidělení výraz* – výraz obsahující **nové** operátor – provádí tři věci:  
  
-   Vyhledává a vyhrazuje úložiště pro objekt nebo objekty, které mají být přiděleny. Po dokončení této fáze je přidělen správný objem úložiště, ale není to ještě objekt.  
  
-   Inicializuje objekt(y). Po dokončení inicializace je k dispozici dostatek informací pro přidělené úložiště, aby byl vytvořen objekt.  
  
-   Vrátí ukazatel na vybrané objekty typu ukazatele odvozené od *nový název typu* nebo *název typu*. Program používá tento ukazatel pro přístup k nově přidělenému objektu.  
  
 **Nové** operátor volá funkci `operator new`. Pro pole libovolného typu a pro objekty, které nejsou **třída**, `struct`, nebo **sjednocení** typy, globální funkce **:: new – operátor**, nazývá se přidělit úložiště. Objekty typu třídy mohou definovat svou vlastní funkci statického člena `operator new` na základě každé třídy.  
  
 Když kompilátor narazí **nové** operátor přidělit objekt typu `type`, vystavuje volání `type` **:: new – operátor (sizeof (** `type` **))**  nebo, pokud ne, uživatelem definované `operator new` je definován **:: new – operátor (sizeof (** `type` **))**. Proto **nové** operátor můžete přidělit správné množství paměti pro objekt.  
  
> [!NOTE]
>  Argument `operator new` je typu **size_t –**. Tento typ je definována v \<direct.h >, \<malloc.h >, \<memory.h >, \<search.h >, \<stddef.h >, \<stdio.h >, \<stdlib.h >, \<string.h >, a \<time.h >.  
  
 Možnost v gramatiky umožňuje specifikaci *umístění* (viz gramatika pro [operátor new](../cpp/new-operator-cpp.md)). *Umístění* parametr lze použít pouze pro uživatelem definované implementace `operator new`; umožňuje doplňující informace, které mají být předány `operator new`. Výraz s *umístění* pole, jako `T *TObject = new ( 0x0040 ) T;` převádějí na `T *TObject = T::operator new( sizeof( T ), 0x0040 );` Pokud T je třídu operátor členů nové, jinak `T *TObject = ::operator new( sizeof( T ), 0x0040 );`.  
  
 Původní záměrem *umístění* bylo pole umožňující související s hardwarem objektů být přidělené adresy, které zadaného uživatelem.  
  
> [!NOTE]
>  I když v předchozím příkladu zobrazuje pouze jeden argument *umístění* pole neexistuje žádné omezení na tom, kolik další argumenty se dá předat do `operator new` tímto způsobem.  
  
 I když byl člen `operator new` definován pro typ třídy, lze pomocí formuláře v tomto příkladu použít globální operátor:  
  
```  
T *TObject =::new TObject;  
```  
  
 Operátor řešení rozsahu (`::`) vynutí použití na globální **nové** operátor.  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)   
 [nové a odstraňte operátory](../cpp/new-and-delete-operators.md)