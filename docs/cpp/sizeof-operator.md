---
title: sizeof – operátor
ms.date: 11/04/2016
f1_keywords:
- sizeof_cpp
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
ms.openlocfilehash: c9ae581b1b3bea522f2c1557b8be44ee1f32eef1
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032288"
---
# <a name="sizeof-operator"></a>sizeof – operátor

Výnosy velikost i jeho operandu vzhledem k velikosti typu **char**.

> [!NOTE]
> Informace o `sizeof ...` operátorovi naleznete v [tématu Tři tečky a variadické šablony](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Syntaxe

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Poznámky

Výsledkem **sizeof** operátor je `size_t`typ , integrální \<typ definovaný v include file stddef.h>. Tento operátor umožňuje vyhnout se určení velikosti dat závislých na počítači v programech.

Operand na **sizeof** může být jeden z následujících:

- Název typu. Chcete-li použít **sizeof** s názvem typu, musí být název uzavřen v závorcích.

- Výraz. Při použití s výrazem **sizeof** lze zadat s nebo bez závorky. Výraz není vyhodnocen.

Při **sizeof** operátor je použita na objekt typu **char**, dává 1. Při **sizeof** operátor je použita na pole, poskytuje celkový počet bajtů v tomto poli, nikoli velikost ukazatele reprezentované identifikátor pole. Chcete-li získat velikost ukazatele reprezentovaného identifikátorem pole, předajte jej jako parametr funkci, která používá **sizeof**. Příklad:

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

Při **sizeof** operátor je **použita**na třídu , **struktura**, nebo **typ sjednocení,** výsledkem je počet bajtů v objektu tohoto typu, plus všechny odsazení přidán zarovnat členy na hranice slova. Výsledek nemusí nutně odpovídat velikosti vypočtené přidáním požadavků na úložiště jednotlivých členů. Možnost kompilátoru [/Zp](../build/reference/zp-struct-member-alignment.md) a [pragma pack](../preprocessor/pack.md) ovlivňují hranice zarovnání pro členy.

**Sizeof** operator nikdy dává 0, i pro prázdnou třídu.

**Sizeof** operátor nelze použít s následujícíoperands:

- Funkce. (Velikost **velikosti** však lze použít na ukazatele na funkce.)

- Bitová pole.

- Nedefinované třídy.

- Typ **void**.

- Dynamicky přidělená pole.

- Externí pole.

- Neúplné typy.

- Názvy neúplných typů v závorce.

Při **sizeof** operátor je použita na odkaz, výsledek je stejný, jako kdyby **sizeof** byla použita na samotný objekt.

Pokud nevelké pole je poslední prvek struktury, **sizeof** operátor vrátí velikost struktury bez pole.

**Sizeof** operátor se často používá k výpočtu počtu prvků v poli pomocí výrazu formuláře:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
