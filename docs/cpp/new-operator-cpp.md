---
title: new – operátor (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: 21e67f8d44673a15e5d3a5994597caae4cc01a2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161123"
---
# <a name="new-operator-c"></a>new – operátor (C++)

Přiděluje paměť pro objekt nebo pole objektů *typu Name* z volného úložiště a vrací vhodně zadaný nenulový ukazatel na objekt.

> [!NOTE]
>  Rozšíření C++ Microsoft Component Extensions poskytují podporu pro **nové** klíčové slovo pro přidání záznamů slotu vtable. Další informace najdete v tématu [New (New slot v tabulce vtable)](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) .

## <a name="syntax"></a>Syntaxe

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Poznámky

V případě neúspěchu vrátí funkce **New** hodnotu nula nebo vyvolá výjimku. Další informace najdete [v tématu operátory New a DELETE](../cpp/new-and-delete-operators.md) . Toto výchozí chování lze změnit zápisem vlastní rutiny zpracování výjimek a voláním funkce běhové knihovny [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) s názvem funkce jako argumentem.

Informace o tom, jak vytvořit objekt na spravované haldě, naleznete v tématu [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md).

Pokud **new** je k přidělení paměti pro objekt C++ třídy použit nový, konstruktor objektu je volán po přidělení paměti.

Pomocí operátoru [Delete](../cpp/delete-operator-cpp.md) Nadělte paměť přidělenou operátorem **New** .

Následující příklad přiděluje a pak uvolňuje dvourozměrné pole znaků velikosti `dim` 10. Při přidělování multidimenzionálního pole všechny dimenze kromě prvního musí být konstantní výrazy, které vyhodnocují kladné hodnoty; levé pole dimenze může být libovolný výraz, který je vyhodnocen jako kladná hodnota. Při přidělování pole pomocí operátoru **New** může být první dimenze nulová – operátor **New** vrací jedinečný ukazatel.

```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*Název typu* nemůže obsahovat deklarace **const**, **volatile**, třídy nebo výčty výčtu. Proto je následující výraz neplatný:

```cpp
volatile char *vch = new volatile char[20];
```

Operátor **New** nepřiřazuje typy odkazů, protože nejsou objekty.

Operátor **New** nelze použít k přidělení funkce, ale lze ji použít k přidělení ukazatelů na funkce. Následující příklad přiděluje a pak uvolní pole sedmi ukazatelů na funkce, které vracejí celá čísla.

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

Použijete-li operátor **New** bez dalších argumentů a zkompilujete s možností [/GX](../build/reference/gx-enable-exception-handling.md), [/EHa](../build/reference/eh-exception-handling-model.md)nebo [/EHS](../build/reference/eh-exception-handling-model.md) , kompilátor vygeneruje kód pro volání operátoru **Delete** , pokud konstruktor vyvolá výjimku.

Následující seznam popisuje gramatické prvky **nového**:

*stáž*<br/>
Poskytuje způsob předávání dalších argumentů při přetížení **nové**.

*název typu*<br/>
Určuje typ, který se má přidělit; může to být buď vestavěný, nebo uživatelsky definovaný typ. Pokud je specifikace typu složitá, může být ohraničena závorkami, aby vynutila pořadí vazeb.

*inicializátor*<br/>
Poskytuje hodnotu inicializovaného objektu. Inicializátory nelze pro pole zadat. Operátor **New** vytvoří pole objektů pouze v případě, že třída má výchozí konstruktor.

## <a name="example"></a>Příklad

Následující příklad kódu přiděluje pole znaků a objekt třídy `CName` a pak je uvolní.

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

Použijete-li nový **tvar operátoru new,** formulář s argumenty kromě velikosti přidělení, kompilátor nepodporuje formu umístění operátoru **Delete** , pokud konstruktor vyvolá výjimku. Příklad:

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

## <a name="initializing-object-allocated-with-new"></a>Inicializuje se objekt přidělený pomocí New.

Volitelné pole *inicializátoru* je zahrnuté v gramatice pro operátor **New** . To umožňuje nové objekty inicializovat konstruktory definovanými uživatelem. Další informace o tom, jak je inicializace provedena, naleznete v tématu [Inicializátory](../cpp/initializers.md). Následující příklad ukazuje, jak použít inicializační výraz s operátorem **New** :

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

V tomto příkladu je objekt `CheckingAcct` přidělen pomocí operátoru **New** , ale není zadána žádná výchozí inicializace. Proto je zavolán výchozí konstruktor třídy `Acct()`. Poté je objekt `SavingsAcct` přiřazen stejným způsobem s tím rozdílem, že je explicitně inicializován na hodnotu 34,98. Vzhledem k tomu, že 34,98 je typu **Double**, konstruktor, který přijímá argument tohoto typu, je volán pro zpracování inicializace. Nakonec je netřídní typ `HowMuch` inicializován na hodnotu 43,0.

Pokud je objekt typu třídy a tato třída má konstruktory (jako v předchozím příkladu), lze objekt inicializovat pomocí operátoru **New** pouze v případě, že je splněna jedna z těchto podmínek:

- Argumenty zadané v inicializátoru souhlasí s argumenty konstruktoru.

- Třída má výchozí konstruktor (konstruktor, který lze volat bez argumentů).

Při přidělování polí pomocí operátoru **New** se dá provést žádná explicitní inicializace na element. je volán pouze výchozí konstruktor, pokud je k dispozici. Další informace najdete v tématu [výchozí argumenty](../cpp/default-arguments.md) .

Pokud není přidělení paměti úspěšné (**operátor New** vrátí hodnotu 0), neprovede se žádná inicializace. Je to ochrana proti pokusům o inicializaci neexistujících dat.

Stejně jako u volání funkcí není definováno pořadí, ve kterém jsou inicializované výrazy vyhodnoceny. Takže byste se neměli spoléhat, že jsou před provedením přidělení paměti tyto výrazy zcela vyhodnoceny. Pokud není přidělení paměti úspěšné a operátor **New** vrátí hodnotu nula, některé výrazy v inicializátoru nemusí být zcela vyhodnoceny.

## <a name="lifetime-of-objects-allocated-with-new"></a>Doba života objektů přidělených novému

Objekty přidělené s operátorem **New** nejsou zničeny, je-li obor, ve kterém jsou definovány, ukončen. Vzhledem k tomu, že operátor **New** vrací ukazatel na objekty, které přiděluje, musí program definovat ukazatel s vhodným oborem pro přístup k těmto objektům. Příklad:

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

## <a name="how-new-works"></a>Jak funguje nový

*Výraz alokace* – výraz obsahující operátor **New** – provede tři věci:

- Vyhledává a vyhrazuje úložiště pro objekt nebo objekty, které mají být přiděleny. Po dokončení této fáze je přidělen správný objem úložiště, ale není to ještě objekt.

- Inicializuje objekt(y). Po dokončení inicializace je k dispozici dostatek informací pro přidělené úložiště, aby byl vytvořen objekt.

- Vrací ukazatel na objekt (y) typu ukazatele odvozeného z *nového názvu typu* nebo názvu *typu*. Program používá tento ukazatel pro přístup k nově přidělenému objektu.

Operátor **New** vyvolá **operátor funkce New**. Pro pole libovolného typu a pro objekty, které nejsou typu **třídy**, **struktury**nebo **sjednocení** , je pro přidělení úložiště volána globální funkce **:: operator new**. Objekty typu třídy mohou definovat vlastní **operátor nové** statické členské funkce na základě třídy.

Když kompilátor narazí na operátor **New** pro přidělení objektu **typu, vyvolá**volání `type` **:: operator new (sizeof (** `type` **))** nebo, pokud není definován uživatelsky definovaný **operátor new** , **:: operator new (sizeof (** `type` **))** . Proto operátor **New** může přidělit správné množství paměti objektu.

> [!NOTE]
>  Argument pro **operátor New** je typu `size_t`. Tento typ je definovaný v \<Direct. h >, \<\ STDDEF. h >, \<paměť. h >, \<Search. h >, \<. h >, \<stdio. h >, \<Stdlib. h >, \<String. h > a \<Time. h >.

Možnost gramatiky umožňuje určení *umístění* (viz gramatika pro [operátor New](../cpp/new-operator-cpp.md)). Parametr *umístění* lze použít pouze pro uživatelem definované implementace **operátoru new**; umožňuje předat další informace **operátorovi New**. Výraz s polem *umístění* , jako je například `T *TObject = new ( 0x0040 ) T;` je přeložen na `T *TObject = T::operator new( sizeof( T ), 0x0040 );`, pokud třída t má operátor member New, jinak `T *TObject = ::operator new( sizeof( T ), 0x0040 );`.

Původní záměr pole *umístění* umožňoval, aby byly objekty závislé na hardwaru přiděleny na uživatelem zadané adresy.

> [!NOTE]
>  Přestože předchozí příklad ukazuje pouze jeden argument v poli *umístění* , neexistuje žádné omezení na to, kolik dalších argumentů lze předat **operátoru novým** tímto způsobem.

I v případě, že byl pro typ třídy definován **operátor New** , lze použít globální operátor pomocí formuláře v tomto příkladu:

```cpp
T *TObject =::new TObject;
```

Operátor rozlišení oboru (`::`) vynutí použití globálního operátoru **New** .

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[operátory New a DELETE](../cpp/new-and-delete-operators.md)
