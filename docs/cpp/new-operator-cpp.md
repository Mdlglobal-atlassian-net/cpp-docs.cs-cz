---
title: New – operátor (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae977f1f5388bd4a88c377ee8629f10130854108
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402988"
---
# <a name="new-operator-c"></a>new – operátor (C++)
Přiděluje paměť pro objekt nebo pole objektů *název typu* z volného úložiště a vrací vhodně typovaný nenulový ukazatel na objekt.  
  
> [!NOTE]
>  Rozšíření komponenty Microsoft C++ poskytuje podporu pro **nové** – klíčové slovo přidat položky vtable slot. Další informace najdete v tématu [new (nový slot v tabulce vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[::] new [placement] new-type-name [new-initializer]  
[::] new [placement] ( type-name ) [new-initializer]  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud není úspěšné, **nové** vrátí hodnotu 0 nebo vyvolá výjimku, naleznete v tématu [nové a odstranit operátory](../cpp/new-and-delete-operators.md) Další informace. Můžete změnit toto výchozí chování psaní vlastních rutin zpracování výjimek a volání [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) funkce knihovny run-time s názvem funkce jako svůj argument.  
  
 Informace o tom, jak vytvořit objekt na spravované haldě, naleznete v tématu [gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
 Když **nové** se používá k přidělení paměti pro objekt třídy jazyka C++, objekt konstruktoru se volá, když je přidělena paměť.  
  
 Použití [odstranit](../cpp/delete-operator-cpp.md) operátor přidělení paměti s **nové** operátor.  
  
 V následujícím příkladu se přiděluje a poté uvolněno dvourozměrné pole znaků velikost `dim` 10. Při přidělování multidimenzionálního pole, všechny dimenze s výjimkou prvního musí být konstantní výrazy, které vedou k pozitivním hodnotám; levé pole dimenze může být libovolný výraz, který je vyhodnocen jako kladná hodnota. Při přidělování pole pomocí **nové** operátoru, první dimenze může být nula – **nové** operátor vrací jedinečný ukazatel.  
  
```cpp 
char (*pchar)[10] = new char[dim][10];  
delete [] pchar;  
```  
  
 *Název typu* nemůže obsahovat **const**, **volatile**, deklarace tříd nebo deklarace výčtů. Proto je neplatný následující výraz:  
  
```cpp 
volatile char *vch = new volatile char[20];  
```  
  
 **Nové** operátor nepřidělí odkazové typy, protože nejsou objekty.  
  
 **Nové** operátor nelze použít k přidělení funkce, ale je možné přidělit ukazatele na funkce. V následujícím příkladu se přiděluje a poté uvolní pole sedmi ukazatelů na funkce, které vrací celá čísla.  
  
```cpp 
int (**p) () = new (int (*[7]) ());  
delete *p;  
```  
  
 Pokud použijete operátor **nové** bez dalších argumentů a kompilujete s [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md), nebo [/EHS](../build/reference/eh-exception-handling-model.md) možnost, kompilátor způsobí Generovat kód pro volání operátoru **odstranit** Pokud konstruktor vyvolá výjimku.  
  
 Následující seznam popisuje gramatické prvky parametru **nové**:  
  
 *umístění*  
 Poskytuje způsob předání dalších argumentů, pokud přetížíte **nové**.  
  
 *Název typu*  
 Určuje typ má být přidělen. může se jednat vestavěný nebo uživatelem definovaný typ. Pokud je specifikace typu složitá, může být uzavřen v závorkách k vynucení pořadí vazeb.  
  
 *Inicializátor*  
 Poskytuje hodnotu pro inicializaci objektu. Inicializátory nelze zadat pro pole. **Nové** operátor vytvoří pole objektů pouze v případě, třída nemá výchozí konstruktor.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu přiřazuje pole znaků a objekt třídy `CName` a poté je uvolní.  
  
```cpp 
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
 Používáte-li formu new z **nové** operátor, formu s argumenty kromě velikosti alokace, kompilátor nepodporuje formu umístění **odstranit** operátor-li konstruktor vyvolá výjimku. Příklad:  
  
```cpp 
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
  
## <a name="initializing-object-allocated-with-new"></a>Inicializace objektů, kterým je přiřazen výraz new  
 Volitelně *inicializátor* pole je součástí gramatiky **nové** operátor. To umožňuje nové objekty inicializovat konstruktory definovanými uživatelem. Další informace o průběhu inicializace naleznete v tématu [inicializátory](../cpp/initializers.md). Následující příklad ukazuje, jak použít výraz inicializace s **nové** operátor:  
  
```cpp 
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
  
 V tomto příkladu je objekt `CheckingAcct` je přidělena pomocí **nové** je zadán operátor, ale žádná výchozí inicializace. Proto je zavolán výchozí konstruktor třídy `Acct()`. Poté je objekt `SavingsAcct` přiřazen stejným způsobem s tím rozdílem, že je explicitně inicializován na hodnotu 34,98. Protože je 34,98 typu **double**, konstruktor, který přijímá argument tohoto typu je volána k inicializaci. Nakonec je netřídní typ `HowMuch` inicializován na hodnotu 43,0.  
  
 Pokud je objekt typu třídy a tato třída má konstruktory (jako v předchozím příkladu), lze objekt inicializovat pomocí **nové** operátor pouze pokud je splněna jedna z těchto podmínek:  
  
-   Argumenty zadané v inicializátoru souhlasí s argumenty konstruktoru.  
  
-   Třída má výchozí konstruktor (konstruktor, který lze volat bez argumentů).  
  
 Inicializace žádné explicitní na element lze provést při přidělování paměti polím nelze pomocí **nové** operátor; pouze výchozí konstruktor, pokud jsou k dispozici, je volána. Zobrazit [výchozí argumenty](../cpp/default-arguments.md) Další informace.  
  
 Pokud selhání přidělení paměti (**operátor new** vrátí hodnotu 0), není inicializace provedena. Je to ochrana proti pokusům o inicializaci neexistujících dat.  
  
 Stejně jako u volání funkcí není definováno pořadí, ve kterém jsou inicializované výrazy vyhodnoceny. Takže byste se neměli spoléhat, že jsou před provedením přidělení paměti tyto výrazy zcela vyhodnoceny. Pokud selhání přidělení paměti a **nové** operátor vrátí hodnotu 0, nemusí být některé výrazy v inicializátoru zcela vyhodnoceny.  
  
## <a name="lifetime-of-objects-allocated-with-new"></a>Doba života objektů, kterým je přiřazen výraz new  
 Přidělené objekty s **nové** operátor nejsou zničeny, když je byl ukončen oboru, ve kterém jsou definovány. Vzhledem k tomu, **nové** operátor vrací ukazatel na objekty přiděluje, program musí definovat ukazatel s vhodným oborem pro přístup k těmto objektům. Příklad:  
  
```cpp 
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
 *Allocation-expression* – obsahující **nové** operátor – dělá tři věci:  
  
-   Vyhledává a vyhrazuje úložiště pro objekt nebo objekty, které mají být přiděleny. Po dokončení této fáze je přidělen správný objem úložiště, ale není to ještě objekt.  
  
-   Inicializuje objekt(y). Po dokončení inicializace je k dispozici dostatek informací pro přidělené úložiště, aby byl vytvořen objekt.  
  
-   Vrátí ukazatel na objekt(y) typu ukazatele odvozený z *nové type-name* nebo *název typu*. Program používá tento ukazatel pro přístup k nově přidělenému objektu.  
  
 **Nové** operátor vyvolá funkci **operátor new**. Pro pole libovolného typu a pro objekty, které nejsou typu **třídy**, **struktura**, nebo **sjednocení** typy, globální funkce **:: operátor new**, je volá se, aby přidělení úložiště. Objekty typu třídy mohou definovat svou vlastní **operátor new** statickou členskou funkci na základě každé třídy.  
  
 Když kompilátor narazí **nové** operátor přidělit objekt typu **typ**, vydá volání `type` **:: operátor new (sizeof (** `type` **))** nebo když není definovaný uživatelem **operátor new** je definován, **:: operátor new (sizeof (** `type` **))**. Proto **nové** operátor můžete přidělit objektu správnou velikost paměti pro objekt.  
  
> [!NOTE]
>  Argument **operátor new** je typu `size_t`. Tento typ je definován v \<direct.h >, \<malloc.h >, \<memory.h >, \<search.h >, \<stddef.h >, \<stdio.h >, \<stdlib.h >, \<string.h >, a \<time.h >.  
  
 Možnost v gramatice umožňuje volbu specifikace *umístění* (viz gramatika [operátor new](../cpp/new-operator-cpp.md)). *Umístění* parametr lze použít pouze pro uživatelem definované implementací **operátor new**; umožňuje dodatečné informace, které se mají předat **operátor new**. Výraz s *umístění* pole jako `T *TObject = new ( 0x0040 ) T;` se přeloží na `T *TObject = T::operator new( sizeof( T ), 0x0040 );` li třída T členský operátor new, jinak k `T *TObject = ::operator new( sizeof( T ), 0x0040 );`.  
  
 Původní záměr *umístění* pole byl umožnit objektům závislým na hardwaru k přidělování na uživatelem zadaných adresách.  
  
> [!NOTE]
>  Ačkoli předchozí příklad ukazuje pouze jeden argument *umístění* pole, neexistuje žádné omezení na tom, kolik dalších argumentů lze předat **operátor new** tímto způsobem.  
  
 I když **operátor new** byla definována pro typ třídy, může pomocí formuláře v tomto příkladu použít globální operátor:  
  
```cpp 
T *TObject =::new TObject;  
```  
  
 Operátor rozlišení oboru (`::`) vynutí použití globálního **nové** operátor.  
  
## <a name="see-also"></a>Viz také:  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [klíčová slova](../cpp/keywords-cpp.md)   
 [nové a odstranit operátory](../cpp/new-and-delete-operators.md)