---
title: sizeof – operátor
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: bc1165cf1df3933575013906d1b24673467f0b36
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178714"
---
# <a name="sizeof-operator"></a>sizeof – operátor

Vypočítá velikost svého operandu s ohledem na velikost typu **char**.

> [!NOTE]
>  Informace o operátoru `sizeof ...` naleznete v tématu [tři tečky a šablony variadické](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Syntaxe

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Poznámky

Výsledek operátoru **sizeof** je typu `size_t`, celočíselný typ definovaný v souboru include \<STDDEF. h >. Tento operátor vám umožní vyhnout se zadání velikosti dat závislých na počítači v programech.

Operandem **operátoru sizeof** může být jedna z následujících:

- Název typu. Chcete-li použít **sizeof** s názvem typu, musí být název uzavřen v závorkách.

- Výraz. Při použití s výrazem lze **operátor sizeof** zadat s nebo bez závorek. Výraz není vyhodnocen.

Je-li operátor **sizeof** použit pro objekt typu **char**, je výsledkem 1. Je-li operátor **sizeof** použit pro pole, je výsledkem celkový počet bajtů v tomto poli, nikoli velikost ukazatele reprezentovaného identifikátorem pole. Chcete-li získat velikost ukazatele reprezentovaného identifikátorem pole, předejte jej jako parametr funkci, která používá **sizeof**. Příklad:

## <a name="example"></a>Příklad

```cpp
#include <iostream>
using namespace std;

size_t getPtrSize( char *ptr )
{
   return sizeof( ptr );
}

int main()
{
   char szHello[] = "Hello, world!";

   cout  << "The size of a char is: "
         << sizeof( char )
         << "\nThe length of " << szHello << " is: "
         << sizeof szHello
         << "\nThe size of the pointer is "
         << getPtrSize( szHello ) << endl;
}
```

## <a name="sample-output"></a>Vzorový výstup

```Output
The size of a char is: 1
The length of Hello, world! is: 14
The size of the pointer is 4
```

Je-li operátor **sizeof** použit pro typ **třídy**, **struktury**nebo **sjednocení** , je výsledkem počet bajtů v objektu daného typu a jakékoli odsazení přidané pro zarovnání členů na hranici slova. Výsledek nemusí nutně odpovídat velikosti počítané přidáním požadavků na úložiště jednotlivých členů. Možnost kompilátoru [/zp](../build/reference/zp-struct-member-alignment.md) a direktiva pragma [balíčku](../preprocessor/pack.md) mají vliv na hranice zarovnání pro členy.

Operátor **sizeof** nikdy nevrací 0, ani pro prázdnou třídu.

Operátor **sizeof** nelze použít s těmito operandy:

- POZVYHLEDAT. (K ukazatelům na funkce se ale dá použít **sizeof** .)

- Bitová pole.

- Nedefinované třídy.

- Typ **void**.

- Dynamicky přidělená pole

- Externí pole.

- Neúplné typy

- Názvy neúplných typů jsou v závorkách.

Je-li operátor **sizeof** použit na odkaz, výsledek je stejný, jako kdyby byl použit operátor **sizeof** pro samotný objekt.

Pokud je pole s nenastavenou velikostí posledním prvkem struktury, operátor **sizeof** vrátí velikost struktury bez pole.

Operátor **sizeof** se často používá k výpočtu počtu prvků v poli pomocí výrazu ve tvaru:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
