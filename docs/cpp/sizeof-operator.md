---
title: sizeof – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- sizeof_cpp
dev_langs:
- C++
helpviewer_keywords:
- sizeof operator
ms.assetid: 8bc3b6fb-54a1-4eb7-ada0-05f8c5efc532
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6445fb834982cd13348c9e94def4b75fe31c02e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058809"
---
# <a name="sizeof-operator"></a>sizeof – operátor

Vrátí velikost svého operandu s ohledem na velikost typu **char**.

> [!NOTE]
>  Informace o tom, `sizeof ...` operátoru, naleznete v tématu [tři tečky a Variadické šablony](../cpp/ellipses-and-variadic-templates.md).

## <a name="syntax"></a>Syntaxe

```
sizeof unary-expression
sizeof  ( type-name )
```

## <a name="remarks"></a>Poznámky

Výsledkem **sizeof** operátor je typu `size_t`, celočíselný typ definovaný v souboru zahrnutí \<stddef.h >. Tento operátor umožňuje vyhnout zadávání velikosti dat závislé na počítače ve svých programech.

Operand **sizeof** může být jedna z následujících akcí:

- Název typu. Chcete-li použít **sizeof** pomocí názvu typu, musí být uzavřena v závorkách.

- Výraz. Při použití s výrazem, **sizeof** se dá nastavit s nebo bez závorek. Výraz není vyhodnocen.

Když **sizeof** operátor použit objekt typu **char**, bude vrácen 1. Když **sizeof** operátor je použit na pole, bude vrácen celkový počet bajtů v poli, nikoli velikost ukazatele reprezentovaného tímto identifikátorem pole. K získání velikosti ukazatele reprezentovaného tímto identifikátorem pole, předat ji jako parametr funkce, která používá **sizeof**. Příklad:

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

Když **sizeof** je použit operátor **třídy**, **– struktura**, nebo **sjednocení** typ výsledku je počet bajtů v objektu, který typ, a navíc všechny odsazení přidány pro zarovnání členů na hranicích slov. Výsledek nemusí nutně odpovídat velikosti vypočítané přidáním požadavky na úložiště jednotlivých členů. [/Zp](../build/reference/zp-struct-member-alignment.md) – možnost kompilátoru a [pack](../preprocessor/pack.md) – Direktiva pragma ovlivnit hranice pro zarovnání členů.

**Sizeof** operátor nikdy dává 0, a to i pro prázdnou třídu.

**Sizeof** operátor nelze použít s operandy následující:

- Funkce. (Ale **sizeof** lze použít u ukazatelů na funkce.)

- Bitová pole.

- Nedefinovaný třídy.

- Typ **void**.

- Dynamicky přiřazeného pole.

- Externí pole.

- Neúplné typy.

- Názvy v závorkách nekompletní typy.

Když **sizeof** operátor se použijí na odkaz, výsledek je stejný jako **sizeof** použili odkaz sám na sebe.

Pokud pole bez velikosti je posledním prvkem struktury, **sizeof** operátor vrátí velikost struktury bez tohoto pole.

**Sizeof** operátor se často používá k výpočtu počtu prvků v poli vlastnosti autorefresh pomocí výrazu ve formátu:

```cpp
sizeof array / sizeof array[0]
```

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)