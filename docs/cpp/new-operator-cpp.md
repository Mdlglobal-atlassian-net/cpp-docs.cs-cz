---
title: new – operátor (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: ac89bf37b8aaaa9d77393b714a233f8a4c998139
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367877"
---
# <a name="new-operator-c"></a>new – operátor (C++)

Přidělí paměť pro objekt nebo pole objektů *typu název* z volného úložiště a vrátí vhodně zadaný, nenulový ukazatel objektu.

> [!NOTE]
> Rozšíření součástí Microsoft C++ poskytuje podporu pro **nové** klíčové slovo pro přidání položek vtable slot. Další informace naleznete [v novém (nový slot in vtable)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

## <a name="syntax"></a>Syntaxe

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Poznámky

Pokud neúspěšné, **new** vrátí nulu nebo vyvolá výjimku; další informace naleznete [v tématu Nové a odstraňte operátory.](../cpp/new-and-delete-operators.md) Toto výchozí chování můžete změnit napsáním vlastní rutiny zpracování výjimek a voláním funkce knihovny [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) za běhu s názvem funkce jako argumentem.

Informace o tom, jak vytvořit objekt na spravované haldě, naleznete [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Při **new** se používá k přidělení paměti pro objekt třídy C++, konstruktor objektu je volána po přidělení paměti.

Pomocí operátoru [delete](../cpp/delete-operator-cpp.md) můžete navrátit paměť přidělenou **novému** operátoru.

Následující příklad přiděluje a potom uvolní dvojrozměrné `dim` pole znaků o velikosti 10. Při přidělování vícerozměrné pole, všechny dimenze s výjimkou první musí být konstantní výrazy, které vyhodnocují kladné hodnoty; dimenze pole nejvíce vlevo může být libovolný výraz, který je vyhodnocen na kladnou hodnotu. Při přidělování pole pomocí **nového** operátoru může být první dimenze nulová – **nový** operátor vrátí jedinečný ukazatel.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*Název typu* nemůže obsahovat **deklarace const**, **volatile**, class nebo enumeration. Proto je neplatný následující výraz:

```cpp
volatile char *vch = new volatile char[20];
```

**Nový** operátor nepřiděluje typy odkazů, protože nejsou objekty.

**Nový** operátor nelze použít k přidělení funkce, ale lze jej použít k přidělení ukazatelů na funkce. Následující příklad přiděluje a potom uvolní pole sedmi ukazatelů na funkce, které vracejí celá čísla.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

Pokud použijete operátor **new** bez dalších argumentů a zkompilujete s parametrem [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md)nebo [/EHs,](../build/reference/eh-exception-handling-model.md) kompilátor vygeneruje kód pro volání **operátoru delete,** pokud konstruktor vyvolá výjimku.

Následující seznam popisuje gramatické prvky **nového**:

*Umístění*<br/>
Poskytuje způsob předávání další argumenty, pokud přetížení **new**.

*název typu*<br/>
Určuje typ, který má být přidělen; může se jedná o vestavěný nebo uživatelem definovaný typ. Pokud je specifikace typu komplikovaná, může být obklopena závorky, aby se vynutilo pořadí vazby.

*Inicializátor*<br/>
Poskytuje hodnotu inicializovaného objektu. Inicializátory nelze zadat pro pole. **Nový** operátor vytvoří pole objektů pouze v případě, že třída má výchozí konstruktor.

## <a name="example"></a>Příklad

Následující příklad kódu přiděluje pole znaků `CName` a objekt třídy a pak je uvolní.

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

Pokud použijete umístění nového formuláře **nového** operátoru, formulář s argumenty kromě velikosti přidělení, kompilátor nepodporuje umístění formulář **delete** operátor, pokud konstruktor vyvolá výjimku. Příklad:

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

## <a name="initializing-object-allocated-with-new"></a>Inicializace objektu přidělená novým

Volitelné *pole inicializátoru* je zahrnuto v gramatice pro **nový** operátor. To umožňuje nové objekty inicializovat konstruktory definovanými uživatelem. Další informace o způsobu inicializace naleznete v tématu [Initializers](../cpp/initializers.md). Následující příklad ukazuje, jak použít inicializační výraz s **novým** operátorem:

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

V tomto příkladu `CheckingAcct` je objekt přidělen pomocí **nového** operátoru, ale není zadána žádná výchozí inicializace. Proto je zavolán výchozí konstruktor třídy `Acct()`. Poté je objekt `SavingsAcct` přiřazen stejným způsobem s tím rozdílem, že je explicitně inicializován na hodnotu 34,98. Protože 34.98 je typu **double**, konstruktor, který přebírá argument tohoto typu je volána ke zpracování inicializace. Nakonec je netřídní typ `HowMuch` inicializován na hodnotu 43,0.

Pokud je objekt typu třídy a tato třída má konstruktory (jako v předchozím příkladu), objekt může být inicializován **nový** operátor pouze v případě, že je splněna jedna z těchto podmínek:

- Argumenty zadané v inicializátoru souhlasí s argumenty konstruktoru.

- Třída má výchozí konstruktor (konstruktor, který lze volat bez argumentů).

Při přidělování polí pomocí **nového** operátoru nelze provést žádnou explicitní inicializaci za prvek; pouze výchozí konstruktor, pokud je k dispozici, se nazývá. Další informace naleznete [v tématu Výchozí argumenty.](../cpp/default-arguments.md)

Pokud se přidělení paměti nezdaří (**operátor new** vrátí hodnotu 0), neprovede se žádná inicializace. Je to ochrana proti pokusům o inicializaci neexistujících dat.

Stejně jako u volání funkcí není definováno pořadí, ve kterém jsou inicializované výrazy vyhodnoceny. Takže byste se neměli spoléhat, že jsou před provedením přidělení paměti tyto výrazy zcela vyhodnoceny. Pokud přidělení paměti selže a **nový** operátor vrátí nulu, některé výrazy v inicializátoru nemusí být zcela vyhodnoceny.

## <a name="lifetime-of-objects-allocated-with-new"></a>Životnost objektů přidělených novými

Objekty přidělené **s novým** operátorem nejsou zničeny při ukončení oboru, ve kterém jsou definovány. Vzhledem k tomu, že **nový** operátor vrátí ukazatel na objekty, které přiděluje, program musí definovat ukazatel s vhodným rozsahem pro přístup k těmto objektům. Příklad:

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

## <a name="how-new-works"></a>Jak funguje nové

*Allocation-expression* – výraz obsahující **nový** operátor – provádí tři věci:

- Vyhledává a vyhrazuje úložiště pro objekt nebo objekty, které mají být přiděleny. Po dokončení této fáze je přidělen správný objem úložiště, ale není to ještě objekt.

- Inicializuje objekt(y). Po dokončení inicializace je k dispozici dostatek informací pro přidělené úložiště, aby byl vytvořen objekt.

- Vrátí ukazatel na objekt (objekty) typu ukazatele odvozeného z *názvu nového typu* nebo *názvu typu*. Program používá tento ukazatel pro přístup k nově přidělenému objektu.

**Nový** operátor vyvolá operátor funkce **new**. Pro pole libovolného typu a pro objekty, které nejsou **třídy**, **struktury**, nebo **sjednocení** typy, globální funkce: **:operátor new**, se nazývá přidělení úložiště. Objekty typu třídy můžete definovat své vlastní **operátor nové** statické členské funkce na základě třídy.

Když kompilátor narazí na **nový** operátor pro **type**přidělení objektu typu `type`, vydá volání **::operator new( sizeof(** `type` **) nebo,** pokud není definován žádný uživatelem definovaný **operátor new,** **::operator new( sizeof(** `type` **) .** Proto **nový** operátor můžete přidělit správné množství paměti pro objekt.

> [!NOTE]
> Argument **operátor u nového** je typu `size_t`. Tento typ je \<definován v \<direct.h>, \<malloc.h \<>, memory.h>, \<search.h>, stddef.h>, \<stdio.h>, \<stdlib.h>, \<string.h> a \<time.h>.

Možnost v gramatice umožňuje specifikaci *umístění* (viz Gramatika pro [nový operátor](../cpp/new-operator-cpp.md)). Parametr *umístění* lze použít pouze pro uživatelem definované implementace **operátoru new**; umožňuje předání dodatečných informací **operátorovi nové**. Výraz s polem *umístění,* `T *TObject = new ( 0x0040 ) T;` například `T *TObject = T::operator new( sizeof( T ), 0x0040 );` přeložený do if class `T *TObject = ::operator new( sizeof( T ), 0x0040 );`T má operátor člena nový, jinak na .

Původním záměrem pole *umístění* bylo umožnit přidělení objektů závislých na hardwaru na adresy zadané uživatelem.

> [!NOTE]
> Přestože předchozí příklad ukazuje pouze jeden argument v poli *umístění,* neexistuje žádné omezení na kolik dalších argumentů může být **předáno operátoru nový** tímto způsobem.

I když **operátor new** byl definován pro typ třídy, globální operátor lze použít pomocí formuláře tohoto příkladu:

```cpp
T *TObject =::new TObject;
```

Operátor rozlišení oboru`::`( ) vynutí použití globálního **nového** operátoru.

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[nové a odstranit operátory](../cpp/new-and-delete-operators.md)
