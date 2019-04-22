---
title: Chyba kompilátoru C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: e80fa62db9795838980c63e113300a554afabef3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59040858"
---
# <a name="compiler-error-c3535"></a>Chyba kompilátoru C3535

nejde odvodit typ pro 'type1' z 'type2'

Typ proměnná deklarovaná příkazem `auto` – klíčové slovo nemůže být odvozen od typu vráceného výrazu inicializace. Například k této chybě dochází, pokud je vyhodnocen jako výraz inicializace `void`, který není typem.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ujistěte se, že není typ výrazu inicializace `void`.

1. Ujistěte se, že deklarace není ukazatel na základní typ. Další informace najdete v tématu [základní typy](../../cpp/fundamental-types-cpp.md).

1. Ujistěte se, že pokud deklarace je ukazatel na typ, se inicializační výraz typu ukazatele.

## <a name="example"></a>Příklad

Následující příklad provede C3535, protože inicializace výraz je vyhodnocen jako `void`.

```
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>Příklad

Následující příklad provede C3535, protože příkaz deklaruje proměnnou `x` jako ukazatel na odvozeným typem, ale typ inicializátoru je výraz double. V důsledku toho kompilátor nemůže odvodit typ proměnné.

```
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>Příklad

Následující příklad provede C3535, protože proměnná `p` deklaruje ukazatel na odvozeným typem, ale výraz inicializace není typem ukazatele.

```
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>Viz také:

[Auto – klíčové slovo](../../cpp/auto-keyword.md)<br/>
[Základní typy](../../cpp/fundamental-types-cpp.md)