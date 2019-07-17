---
title: '&lt;nové&gt; operátory a výčty'
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: a3fd5b825fe1eaf3a07d9d001f03b9d0c64ffa31
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243683"
---
# <a name="ltnewgt-operators-and-enums"></a>&lt;nové&gt; operátory a výčty

## <a name="op_align_val_t"></a> align_val_t výčtu

```cpp
enum class align_val_t : size_t {};
```

## <a name="op_delete"></a> delete – operátor

Funkci volanou třídou výraz delete pro zrušení přidělení úložiště pro jednotlivé objekty.

```cpp
void operator delete(void* ptr) throw();
void operator delete(void *, void*) throw();
void operator delete(void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

*PTR*\
Ukazatel, jehož hodnota má být vykreslen odstraněním neplatný.

### <a name="remarks"></a>Poznámky

První funkce je volána výrazem odstranění k vykreslení hodnoty *ptr* neplatný. Program lze definovat funkci s Tento podpis funkce, která nahradí výchozí verze definované ve standardní knihovně jazyka C++. Požadované chování je tak, aby přijímal hodnotu *ptr* , který je null nebo který byl vrácen dřívějším volání [operátor new](../standard-library/new-operators.md#op_new)(**size_t**).

Výchozí chování pro hodnotu null z *ptr* se neprovede žádnou akci. Jakákoli jiná hodnota *ptr* musí být číslo vrácen voláním jak už bylo popsáno dříve. Výchozí chování pro neprázdné hodnoty z *ptr* je uvolnit úložiště přidělené v dřívějším volání. Je zadán, za jakých podmínek část nebo všechny tyto uvolňovaného úložiště je přidělena následných volání `operator new`(**size_t**), nebo k některým `calloc`( **size_t**), `malloc`( **size_t**), nebo `realloc`( **void**<strong>\*</strong>, **size_t**).

Druhá funkce je volána výrazem odstranit umístění odpovídající výraz new formuláře **nové**( **std::size_t**). To nemá žádný účinek.

Třetí funkce je volána výrazem odstranit umístění odpovídající výraz new formuláře **nové**( **std::size_t**, **conststd::nothrow_t &** ). Program lze definovat funkci s Tento podpis funkce, která nahradí výchozí verze definované ve standardní knihovně jazyka C++. Požadované chování je tak, aby přijímal hodnotu `ptr` , který je null nebo který byl vrácen dřívějším volání `operator new`( **size_t**). Výchozí chování je vyhodnotit **odstranit**(`ptr`).

### <a name="example"></a>Příklad

Naleznete v tématu [operátor new](../standard-library/new-operators.md#op_new) Příklad používající **operátor delete**.

## <a name="op_delete_arr"></a> Operator delete]

Funkci volanou třídou výraz delete se zrušit přidělení úložiště pro pole objektů.

```cpp
void operator delete[](void* ptr) throw();
void operator delete[](void *, void*) throw();
void operator delete[](void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

*PTR*\
Ukazatel, jehož hodnota má být vykreslen odstraněním neplatný.

### <a name="remarks"></a>Poznámky

První funkce je volána `delete[]` výraz k vykreslení hodnoty *ptr* neplatný. Funkce totiž replaceable programu lze definovat funkci s Tento podpis funkce, která nahradí výchozí verze definované ve standardní knihovně jazyka C++. Požadované chování je tak, aby přijímal hodnotu *ptr* , který je null nebo který byl vrácen dřívějším volání [operátor new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)(**size_t**). Výchozí chování pro hodnotu null z *ptr* se neprovede žádnou akci. Jakákoli jiná hodnota *ptr* musí být číslo vrácen voláním jak už bylo popsáno dříve. Výchozí chování pro tyto nenulovou hodnotou *ptr* je uvolnit úložiště přidělené v dřívějším volání. Je zadán, za jakých podmínek část nebo všechny tyto uvolňovaného úložiště je přidělena následných volání [operátor new](../standard-library/new-operators.md#op_new)(**size_t**), nebo k některým `calloc`(**size_t**), `malloc`(**size_t**), nebo `realloc`( **void**<strong>\*</strong>, **size_t**) .

Druhá funkce je volána umístění `delete[]` výraz odpovídá `new[]` výrazu v podobě `new[]`(**std::size_t**). To nemá žádný účinek.

Třetí funkce je volána umístění odstranit výraz odpovídá `new[]` výrazu v podobě `new[]`( **std::size_t**, **const std::nothrow_t &** ). Program lze definovat funkci s Tento podpis funkce, která nahradí výchozí verze definované ve standardní knihovně jazyka C++. Požadované chování je tak, aby přijímal hodnotu *ptr* , který je null nebo který byl vrácen dřívějším volání operátoru `new[]`(**size_t**). Výchozí chování je vyhodnotit `delete[]`( `ptr`).

### <a name="example"></a>Příklad

Zobrazit [operátor new&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) příklady použití `operator delete[]`.

## <a name="op_new"></a> new – operátor

Funkci volanou třídou výraz new k přidělení úložiště pro jednotlivé objekty.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);
void* operator new(std::size_t count, const std::nothrow_t&) throw();
void* operator new(std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>Parametry

*Počet*\
Počet bajtů je přiděleno úložiště.

*PTR*\
Ukazatel, který se má vrátit.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nejnižší bajt adresu nově přidělené úložiště. Nebo *ptr*.

### <a name="remarks"></a>Poznámky

Volá funkci první výraz new k přidělení `count` bajtů úložiště vhodně zarovnaný pro reprezentaci libovolného objektu této velikosti. Program můžete definovat alternativní funkce podpisem této funkce, která nahradí výchozí verze definované ve standardní knihovně jazyka C++ a proto je nahraditelné.

Požadované chování je nenulový ukazatel pouze v případě, že úložiště je možné přidělit požadovanou. Každé takové přidělení vrací ukazatel do úložiště nesouvislý z jiné přidělené úložiště. Pořadí a contiguity úložiště přidělené v následných voláních není zadána. Počáteční uloženou hodnotu neurčená. Vrácený ukazatel odkazuje na začátku (nejnižší bajt adresa) přidělené úložiště. Pokud je počet nula, vrácená hodnota není výsledkem porovnání rovna jiné hodnotě, vrácené funkcí.

K provedení smyčky je výchozí chování. V rámci smyčky funkce nejdřív pokusí se přidělit požadované úložiště. Zda pokus zahrnuje volání `malloc`( **size_t**) není zadána. Pokud je tento pokus úspěšný, funkce vrátí ukazatel do přidělené úložiště. V opačném případě volá funkci určené [novou obslužnou rutinu](../standard-library/new-typedefs.md#new_handler). Pokud volaná funkce vrátí, opakování cyklu. Smyčky ukončí, pokud je úspěšný pokus o přidělení požadované úložiště nebo pokud volaná funkce nevrací.

Požadované chování novou obslužnou rutinu je provést jednu z následujících operací:

- Proveďte další úložiště k dispozici pro přidělení a vraťte.

- Volání na buď **přerušit** nebo **ukončit**(`int`).

- Vyvolat objekt typu **bad_alloc –.**

Výchozí chování [novou obslužnou rutinu](../standard-library/new-typedefs.md#new_handler) je objekt typu vyvolání `bad_alloc`. Ukazatel s hodnotou null označuje výchozí novou obslužnou rutinu.

Pořadí a contiguity úložiště přidělené následná volání `operator new`(**size_t**) neurčená, jsou uloženy počáteční hodnoty.

Druhá funkce je volána výraz umístění new k přidělení `count` bajtů úložiště vhodně zarovnaný pro reprezentaci libovolného objektu této velikosti. Program můžete definovat alternativní funkce podpisem této funkce, která nahradí výchozí verze definované ve standardní knihovně jazyka C++ a proto je nahraditelné.

Výchozím chováním `operator new`(`count`) Pokud je funkce úspěšná. V opačném případě vrátí ukazatel s hodnotou null.

Třetí funkce je volána umístění **nové** výrazu v podobě **nové** ( *args*) T. Tady *args* se skládá z jednoho objektu ukazatele. To může být užitečné pro vytváření objektu na známé adrese. Funkce vrátí *ptr*.

Uvolnění úložiště přidělené **operátor new**, volání [operátor delete](../standard-library/new-operators.md#op_delete).

Informace o vyvolání nebo non-throwing. chování nové, najdete v tématu [nové a odstranit operátory](../cpp/new-and-delete-operators.md).

### <a name="example"></a>Příklad

```cpp
// new_op_new.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;

class MyClass
{
public:
   MyClass( )
   {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass( )
   {
      imember = 0; cout << "Destructing MyClass." << this << endl;
   };
   int imember;
};

int main( )
{
   // The first form of new delete
   MyClass* fPtr = new MyClass;
   delete fPtr;

   // The second form of new delete
   MyClass* fPtr2 = new( nothrow ) MyClass;
   delete fPtr2;

   // The third form of new delete
   char x[sizeof( MyClass )];
   MyClass* fPtr3 = new( &x[0] ) MyClass;
   fPtr3 -> ~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;
}
```

## <a name="op_new_arr"></a> new [] – operátor

Funkce přidělení volány výraz new k přidělení úložiště pro pole objektů.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);
void* operator new[](std::size_t count, const std::nothrow_t&) throw();
void* operator new[](std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>Parametry

*Počet*\
Počet bajtů úložiště, která bude přidělena pro objekt pole.

*PTR*\
Ukazatel, který se má vrátit.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nejnižší bajt adresu nově přidělené úložiště. Nebo *ptr*.

### <a name="remarks"></a>Poznámky

První funkce je volána `new[]` výraz přidělit `count` bajtů úložiště vhodně zarovnaný pro libovolný objekt pole, které představují nebo menší. Program lze definovat funkci s Tento podpis funkce, která nahradí výchozí verze definované ve standardní knihovně jazyka C++. Požadované chování je stejné jako v případě [operátor new](../standard-library/new-operators.md#op_new)(**size_t**). Výchozím chováním `operator new`( `count`).

Druhá funkce je volána umístění `new[]` výraz přidělit `count` bajtů úložiště vhodně zarovnaný pro reprezentaci libovolný objekt pole zadané velikosti. Program lze definovat funkci s Tento podpis funkce, která nahradí výchozí verze definované ve standardní knihovně jazyka C++. Výchozím chováním **operatornew**(`count`) Pokud je funkce úspěšná. V opačném případě vrátí ukazatel s hodnotou null.

Třetí funkce je volána umístění `new[]` výrazu v podobě **nové** ( *args*) **T**[ **N**]. Tady *args* se skládá z jednoho objektu ukazatele. Funkce vrátí `ptr`.

Uvolnění úložiště přidělené `operator new[]`, volání [operátor delete&#91;&#93;](../standard-library/new-operators.md#op_delete_arr).

Informace o vyvolání nebo nonthrowing chování nové, najdete v tématu [nové a odstranit operátory](../cpp/new-and-delete-operators.md).

### <a name="example"></a>Příklad

```cpp
// new_op_alloc.cpp
// compile with: /EHsc
#include <new>
#include <iostream>

using namespace std;

class MyClass {
public:
   MyClass() {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass() {
      imember = 0; cout << "Destructing MyClass." << this << endl;
      };
   int imember;
};

int main() {
   // The first form of new delete
   MyClass* fPtr = new MyClass[2];
   delete[ ] fPtr;

   // The second form of new delete
   char x[2 * sizeof( MyClass ) + sizeof(int)];

   MyClass* fPtr2 = new( &x[0] ) MyClass[2];
   fPtr2[1].~MyClass();
   fPtr2[0].~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;

   // The third form of new delete
   MyClass* fPtr3 = new( nothrow ) MyClass[2];
   delete[ ] fPtr3;
}
```
