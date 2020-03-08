---
title: '&lt;nové&gt; operátory a výčty'
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: a3fd5b825fe1eaf3a07d9d001f03b9d0c64ffa31
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854931"
---
# <a name="ltnewgt-operators-and-enums"></a>&lt;nové&gt; operátory a výčty

## <a name="op_align_val_t"></a>align_val_t výčtu

```cpp
enum class align_val_t : size_t {};
```

## <a name="op_delete"></a>delete – operátor

Funkce volaná výrazem delete pro zrušení přidělení úložiště pro jednotlivé objekty.

```cpp
void operator delete(void* ptr) throw();
void operator delete(void *, void*) throw();
void operator delete(void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

\ *PTR*
Ukazatel, jehož hodnota má být vygenerována neplatným odstraněním.

### <a name="remarks"></a>Poznámky

První funkce je volána výrazem delete pro vykreslení hodnoty *PTR* není platná. Program může definovat funkci s touto signaturou funkce, která nahrazuje výchozí verzi definovanou C++ standardní knihovnou. Požadované chování je přijmout hodnotu *PTR* , která má hodnotu null nebo která byla vrácena starším voláním [operátoru new](../standard-library/new-operators.md#op_new)(**size_t**).

Výchozí chování pro hodnotu null typu *PTR* je nedělat nic. Jakákoli jiná hodnota *PTR* musí být hodnota vrácená dříve voláním, jak je popsáno výše. Výchozím chováním pro takovou nenulovou hodnotu *PTR* je uvolnit úložiště přidělené dřívějším voláním. Není stanoveno, za jakých podmínek se část nebo veškeré takové uvolněné úložiště přidělí následným voláním `operator new`(**size_t**) nebo do některého `calloc`( **size_t**) `malloc`( **size_t**) nebo `realloc`( **void** <strong>\*</strong>, **size_t**).

Druhá funkce je volána výrazem pro odstranění umístění odpovídajícím novému výrazu formuláře **New**( **std:: size_t**). Neprovádí žádnou akci.

Třetí funkce je volána umístěním odstranění výrazu odpovídajícím novému výrazu formuláře **New**( **std:: size_t**, **conststd:: nothrow_t &** ). Program může definovat funkci s touto signaturou funkce, která nahrazuje výchozí verzi definovanou C++ standardní knihovnou. Požadované chování je přijmout hodnotu `ptr`, která má hodnotu null nebo byla vrácena starším voláním `operator new`( **size_t**). Výchozím chováním je vyhodnotit **odstranění**(`ptr`).

### <a name="example"></a>Příklad

Příklad, který používá **operátor delete**, najdete v části [operator new](../standard-library/new-operators.md#op_new) .

## <a name="op_delete_arr"></a>DELETE [] – operátor

Funkce volaná výrazem delete pro zrušení přidělení úložiště pro pole objektů.

```cpp
void operator delete[](void* ptr) throw();
void operator delete[](void *, void*) throw();
void operator delete[](void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>Parametry

\ *PTR*
Ukazatel, jehož hodnota má být vygenerována neplatným odstraněním.

### <a name="remarks"></a>Poznámky

První funkce je volána výrazem `delete[]` pro vykreslení hodnoty *PTR* není platná. Funkce je nahraditelný, protože program může definovat funkci s touto signaturou funkce, která nahrazuje výchozí verzi definovanou C++ standardní knihovnou. Požadované chování je přijmout hodnotu *PTR* , která má hodnotu null nebo která byla vrácena starším voláním [operátoru New&#91;](../standard-library/new-operators.md#op_new_arr)(**size_t**). Výchozí chování pro hodnotu null typu *PTR* je nedělat nic. Jakákoli jiná hodnota *PTR* musí být hodnota vrácená dříve voláním, jak je popsáno výše. Výchozím chováním pro takovou hodnotu typu *PTR* , která není null, je uvolnění úložiště přiděleného dřívějším voláním. Není určena za to, jaké podmínky část nebo veškeré takové uvolněné úložiště jsou přiděleny následným voláním [operátoru new](../standard-library/new-operators.md#op_new)(**size_t**), nebo do jakéhokoli `calloc`(**size_t**), `malloc`(**size_t**) nebo `realloc`( **void** <strong>\*</strong>, **size_t**).

Druhá funkce je volána `delete[]` výrazem umístění odpovídajícím `new[]`mu výrazu `new[]`formuláře (**std:: size_t**). Neprovádí žádnou akci.

Třetí funkce je volána pomocí výrazu pro odstranění umístění odpovídajícího `new[]`mu výrazu `new[]`formuláře ( **std:: size_t**, **const std:: nothrow_t &** ). Program může definovat funkci s touto signaturou funkce, která nahrazuje výchozí verzi definovanou C++ standardní knihovnou. Požadované chování je přijmout hodnotu *PTR* , která je null nebo vrácená starším voláním operátoru `new[]`(**size_t**). Výchozím chováním je vyhodnotit `delete[]`(`ptr`).

### <a name="example"></a>Příklad

Příklady použití `operator delete[]`naleznete v části [operator new&#91; ](../standard-library/new-operators.md#op_new_arr) .

## <a name="op_new"></a>New – operátor

Funkce volaná novým výrazem k přidělení úložiště pro jednotlivé objekty.

```cpp
void* operator new(std::size_t count) throw(bad_alloc);
void* operator new(std::size_t count, const std::nothrow_t&) throw();
void* operator new(std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>Parametry

*počet*\
Počet bajtů úložiště, které mají být přiděleny.

\ *PTR*
Ukazatel, který má být vrácen.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nejnižší bajtovou adresu nově přiděleného úložiště. Nebo *PTR*.

### <a name="remarks"></a>Poznámky

První funkce je volána novým výrazem pro přidělení `count`ch bajtů úložiště vhodně zarovnané k reprezentaci libovolného objektu této velikosti. Program může definovat alternativní funkci s touto signaturou funkce, která nahrazuje výchozí verzi definovanou C++ standardní knihovnou, a takže je možné ji nahradit.

Vyžadováno chování je vrátit ukazatel, který není null, pokud je možné přidělit úložiště podle požadavků. Každé takové přidělení poskytuje ukazatel na úložiště nesouvislý z jakéhokoli jiného přiděleného úložiště. Pořadí a contiguity úložiště přidělené po sobě jdoucí volání nejsou specifikovány. Počáteční uložená hodnota není specifikována. Vrácený ukazatel ukazuje na začátek (nejnižší bajtovou adresu) přiděleného úložiště. Pokud je počet nula, vrácená hodnota se nerovná s žádnou jinou hodnotou vrácenou funkcí.

Výchozím chováním je spuštění smyčky. V rámci smyčky se funkce nejprve pokusí přidělit požadované úložiště. Bez ohledu na to, zda se pokus týká volání `malloc`( **size_t**) není určen. Pokud je pokus úspěšný, funkce vrátí ukazatel na přidělené úložiště. V opačném případě funkce volá určenou [novou obslužnou rutinu](../standard-library/new-typedefs.md#new_handler). Pokud se volaná funkce vrátí, opakuje se smyčka. Smyčka se ukončí, když se pokus o přidělení požadovaného úložiště úspěšně nebo když volaná funkce nevrátí.

Požadované chování nové obslužné rutiny je provedení jedné z následujících operací:

- Uvolněte úložiště k dispozici pro přidělení a pak se vraťte.

- Zavolejte buď **Abort** , nebo **Exit**(`int`).

- Vyvolejte objekt typu **bad_alloc.**

Výchozím chováním [nové obslužné rutiny](../standard-library/new-typedefs.md#new_handler) je vyvolání objektu typu `bad_alloc`. Ukazatel s hodnotou null označuje výchozí novou obslužnou rutinu.

Pořadí a contiguity úložiště přidělené po sobě jdoucí volání `operator new`(**size_t**) nejsou určeny, stejně jako počáteční hodnoty, které zde jsou uloženy.

Druhá funkce je volána umístěním nový výraz pro přidělení `count`ch bajtů úložiště vhodně zarovnané, aby představovaly libovolný objekt této velikosti. Program může definovat alternativní funkci s touto signaturou funkce, která nahrazuje výchozí verzi definovanou C++ standardní knihovnou, a takže je možné ji nahradit.

Výchozím chováním je vrácení `operator new`(`count`), pokud je tato funkce úspěšná. V opačném případě vrátí ukazatel s hodnotou null.

Třetí funkce je volána umístěním **Nový** výraz na formuláři **New** ( *args*) T. Zde jsou *argumenty* tvořeny jediným ukazatelem objektu. To může být užitečné při vytváření objektu na známé adrese. Funkce vrátí *PTR*.

Chcete-li uvolnit úložiště přidělené **operátorem New**, zavolejte [operátor delete](../standard-library/new-operators.md#op_delete).

Informace o vyvolání nebo nevyvolávání chování nové naleznete v tématu [operátory New a DELETE](../cpp/new-and-delete-operators.md).

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

## <a name="op_new_arr"></a>New [] – operátor

Funkce přidělení volaná novým výrazem k přidělení úložiště pro pole objektů.

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);
void* operator new[](std::size_t count, const std::nothrow_t&) throw();
void* operator new[](std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>Parametry

*počet*\
Počet bajtů úložiště, které se má přidělit objektu pole.

\ *PTR*
Ukazatel, který má být vrácen.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na nejnižší bajtovou adresu nově přiděleného úložiště. Nebo *PTR*.

### <a name="remarks"></a>Poznámky

První funkce je volána výrazem `new[]` k přidělení `count` bajtů úložiště vhodně zarovnaného na hodnotu, která představuje libovolný objekt pole této velikosti nebo menší. Program může definovat funkci s touto signaturou funkce, která nahrazuje výchozí verzi definovanou C++ standardní knihovnou. Požadované chování je stejné jako u [operátoru new](../standard-library/new-operators.md#op_new)(**size_t**). Výchozím chováním je vrácení `operator new`(`count`).

Druhá funkce je volána umístěním `new[]` výraz pro přidělení `count` bajtů úložiště vhodně zarovnané k reprezentování všech objektů pole této velikosti. Program může definovat funkci s touto signaturou funkce, která nahrazuje výchozí verzi definovanou C++ standardní knihovnou. Výchozím chováním je vrácení **operatornew**(`count`), pokud je tato funkce úspěšná. V opačném případě vrátí ukazatel s hodnotou null.

Třetí funkce je volána umístěním `new[]` výrazem v podobě **New** ( *args*) **t**[ **N**]. Zde jsou *argumenty* tvořeny jediným ukazatelem objektu. Funkce vrátí `ptr`.

Chcete-li uvolnit úložiště přidělené `operator new[]`, zavolejte [operátor delete&#91;](../standard-library/new-operators.md#op_delete_arr).

Informace o vyvolávání nebo nevyvolávání chování nové naleznete v tématu [operátory New a DELETE](../cpp/new-and-delete-operators.md).

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
