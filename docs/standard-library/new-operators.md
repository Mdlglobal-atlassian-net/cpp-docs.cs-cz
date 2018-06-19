---
title: '&lt;nové&gt; operátory | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: 0520b2f45f9f87009b61ded8a5c420c837d1333d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33861367"
---
# <a name="ltnewgt-operators"></a>&lt;nové&gt; operátory

||||
|-|-|-|
|[delete – operátor](#op_delete)|[delete [] – operátor](#op_delete_arr)|[new – operátor](#op_new)|
|[new [] – operátor](#op_new_arr)|

## <a name="op_delete"></a>  delete – operátor

Odstranění výrazem se zrušit přidělení úložiště pro jednotlivé objekty volaná funkce.

```cpp
void operator delete(void* ptr) throw();

void operator delete(void *,
    void*) throw();

void operator delete(void* ptr,
    const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

`ptr` Ukazatel, jehož hodnota je k odstranění vykreslení neplatný.

### <a name="remarks"></a>Poznámky

Volá funkci první výraz delete k vykreslení hodnotu `ptr` neplatný. Program můžete definovat funkce podpisem této funkce, která nahradí výchozí verze definované standardní knihovna C++. Požadované chování je tak, aby přijímal hodnotu `ptr` tedy vrátila hodnotu null nebo který starší voláním [new – operátor](../standard-library/new-operators.md#op_new)( **size_t –**).

Výchozí chování pro hodnotu null `ptr` je se nic nestane. Jakákoli jiná hodnota `ptr` musí být hodnota vrácený volání výše popsané výše. Výchozí chování pro nenulový hodnotu z `ptr` má uvolnit úložiště přidělené starší voláním. Je tento parametr, za jakých podmínek část nebo všechny tyto regenerovaný úložiště je přidělena následných volání `operator new`( **size_t –**), nebo k některým `calloc`( **size_t –**), `malloc`( **size_t –**), nebo `realloc`( **void\***, **size_t –**).

Druhý funkce je volána výrazem odstranit umístění odpovídající výraz nového formuláře **nové**( **std::size_t**). Neprovede žádnou akci.

Třetí funkce je volána výrazem odstranit umístění odpovídající výraz nového formuláře **nové**( **std::size_t**, **conststd::nothrow_t &**). Program můžete definovat funkce podpisem této funkce, která nahradí výchozí verze definované standardní knihovna C++. Požadované chování je tak, aby přijímal hodnotu `ptr` tedy vrátila hodnotu null nebo který starší voláním `operator new`( **size_t –**). Výchozí chování je vyhodnotit **odstranit**( `ptr`).

### <a name="example"></a>Příklad

V tématu [new – operátor](../standard-library/new-operators.md#op_new) příklad použijte `operator delete`.

## <a name="op_delete_arr"></a>  delete [] – operátor

Funkci nazvanou odstranění výrazem se zrušit přidělení úložiště pro pole objektů.

```cpp
void operator delete[](void* ptr) throw();

void operator delete[](void *,
    void*) throw();

void operator delete[](void* ptr,
    const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

`ptr` Ukazatel, jehož hodnota je k odstranění vykreslení neplatný.

### <a name="remarks"></a>Poznámky

První funkce je volána `delete[]` výraz k vykreslení hodnotu `ptr` neplatný. Funkce je replaceable, protože program můžete definovat funkce podpisem této funkce, která nahradí výchozí verze definované standardní knihovna C++. Požadované chování je tak, aby přijímal hodnotu `ptr` tedy vrátila hodnotu null nebo který starší voláním [new – operátor&#91;&#93;](../standard-library/new-operators.md#op_new_arr)( **size_t –**). Výchozí chování pro hodnotu null `ptr` je se nic nestane. Jakákoli jiná hodnota `ptr` musí být hodnota vrácený volání výše popsané výše. Výchozí chování pro nenulový hodnotu z `ptr` má uvolnit úložiště přidělené starší voláním. Je tento parametr, za jakých podmínek část nebo všechny tyto regenerovaný úložiště je přidělena následných volání [new – operátor](../standard-library/new-operators.md#op_new)( **size_t –**), nebo k některým `calloc`( **size_t –**), `malloc`( **size_t –**), nebo `realloc`( **void\***, **size_t –**).

Umístění je volána funkce second `delete[]` odpovídající výraz `new[]` výrazu ve formátu `new[]`( **std::size_t**). Neprovede žádnou akci.

Třetí funkce je volána umístění odstranit výraz odpovídající `new[]` výrazu ve formátu `new[]`( **std::size_t**, **const std::nothrow_t &**). Program můžete definovat funkce podpisem této funkce, která nahradí výchozí verze definované standardní knihovna C++. Požadované chování je tak, aby přijímal hodnotu `ptr` tedy vrátila hodnotu null nebo který starší voláním operátor `new[]`( **size_t –**). Výchozí chování je vyhodnotit `delete[]`( `ptr`).

### <a name="example"></a>Příklad

V tématu [new – operátor&#91; &#93; ](../standard-library/new-operators.md#op_new_arr) příklady použití `operator delete[]`.

## <a name="op_new"></a>  new – operátor

Nový-výrazem se přidělit úložiště pro jednotlivé objekty volaná funkce.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);

void* operator new(std::size_t count,
    const std::nothrow_t&) throw();

void* operator new(std::size_t count,
    void* ptr) throw();
```

### <a name="parameters"></a>Parametry

`count` Počet bajtů úložišť, která bude přidělena.

`ptr` Ukazatel má být vrácen.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na adresu nejnižší bajtů nově přidělené úložiště. Nebo `ptr.`

### <a name="remarks"></a>Poznámky

První funkce je volána nové výrazem přidělit `count` bajtů úložišť vhodně zarovnán představují libovolného objektu této velikosti. Program můžete definovat alternativní funkci podpisem této funkce, která nahradí výchozí verze definované ve standardní knihovně C++ a stejně tak replaceable.

Požadované chování je vrátit nenulový ukazatel pouze v případě, že úložiště může být přidělen podle požadavku. Každé takové přidělení poskytuje ukazatel na úložiště nesouvislý z jiných úložiště přidělené. Pořadí a contiguity úložiště přidělené následných voláních není zadáno. Počáteční uložené hodnoty neurčené. Vrácený ukazatel odkazuje na spuštění úložiště přidělené (nejnižší adresu bajtů). Pokud je počet nula, hodnota vrácená nelze použít k porovnání rovna jakoukoli jinou hodnotu vráceným funkcí.

Výchozí chování je provést smyčku. V rámci smyčky funkce nejprve pokusí se přidělit požadované úložiště. Zda pokus zahrnuje volání `malloc`( **size_t –**) není zadáno. Pokud je úspěšné, vrátí funkce do úložiště přidělené ukazatel. Jinak zavolá funkci určené [novou obslužnou rutinu](../standard-library/new-typedefs.md#new_handler). Pokud volané funkce vrátí hodnotu, že opakování ve smyčce opakuje. Po úspěšné alokovat požadovaný úložiště, nebo když volaná funkce nevrací se ukončuje smyčky.

Požadované chování novou obslužnou rutinu je provést jednu z následujících operací:

- Proveďte další úložiště k dispozici pro přidělení a vraťte.

- Volání buď **abort** nebo **ukončete**( `int`).

- Throw objekt typu **bad_alloc.**

Výchozí chování [novou obslužnou rutinu](../standard-library/new-typedefs.md#new_handler) je throw objekt typu `bad_alloc`. Ukazatele null označí nový výchozí obslužnou rutinu.

Pořadí a contiguity úložiště přidělené následná volání `operator new`( **size_t –**) není zadáno, jako jsou počáteční hodnoty v ní uloženy.

Volá funkci druhý výraz nové umístění přidělit `count` bajtů úložišť vhodně zarovnán představují libovolného objektu této velikosti. Program můžete definovat alternativní funkci podpisem této funkce, která nahradí výchozí verze definované ve standardní knihovně C++ a stejně tak replaceable.

Výchozí chování je vrátit `operator new`( `count`) je-li tuto funkci úspěšné. Jinak vrátí hodnotu null. ukazatel.

Volá funkci třetí umístění **nové** výrazu ve formátu **nové** ( *argumentů*) T. Zde *argumentů* se skládá z jednoho objektu ukazatel. To může být užitečné pro vytváření objektu na známou adresu. Funkce vrátí hodnotu *ptr*.

Chcete-li uvolnit úložiště přidělené `operator new`, volání [delete – operátor](../standard-library/new-operators.md#op_delete).

Informace o vyvolání nebo nonthrowing chování nové, viz [nové a odstraňte operátory](../cpp/new-and-delete-operators.md).

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

## <a name="op_new_arr"></a>  new [] – operátor

Funkce přidělení volá nový výraz se přidělit úložiště pro pole objektů.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);

void* operator new[](std::size_t count,
    const std::nothrow_t&) throw();

void* operator new[](std::size_t count,
    void* ptr) throw();
```

### <a name="parameters"></a>Parametry

`count` Počet bajtů úložiště, která bude přidělena pro objekt array.

`ptr` Ukazatel má být vrácen.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na adresu nejnižší bajtů nově přidělené úložiště. Nebo `ptr.`

### <a name="remarks"></a>Poznámky

První funkce volá `new[]` výraz přidělit `count` bajtů úložišť vhodně zarovnaný představují libovolného pole objektu této velikosti nebo menší. Program můžete definovat funkce podpisem této funkce, která nahradí výchozí verze definované standardní knihovna C++. Požadované chování je stejné jako u [new – operátor](../standard-library/new-operators.md#op_new)( **size_t –**). Výchozí chování je vrátit `operator new`( `count`).

Umístění je volána funkce second `new[]` výraz přidělit `count` bajtů úložišť vhodně zarovnán představují libovolného pole objektu této velikosti. Program můžete definovat funkce podpisem této funkce, která nahradí výchozí verze definované standardní knihovna C++. Výchozí chování je vrátit **operatornew**( `count`) je-li tuto funkci úspěšné. Jinak vrátí hodnotu null. ukazatel.

Volá funkci třetí umístění `new[]` výrazu ve formátu **nové** ( *argumentů*) **T**[ **N**]. Zde *argumentů* se skládá z jednoho objektu ukazatel. Funkce vrátí hodnotu `ptr`.

Chcete-li uvolnit úložiště přidělené `operator new[]`, volání [delete – operátor&#91;&#93;](../standard-library/new-operators.md#op_delete_arr).

Informace o vyvolání nebo nonthrowing chování nové, viz [nové a odstraňte operátory](../cpp/new-and-delete-operators.md).

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

## <a name="see-also"></a>Viz také

[\<Nový >](../standard-library/new.md)<br/>
