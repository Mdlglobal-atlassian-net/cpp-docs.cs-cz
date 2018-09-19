---
title: Chyba kompilátoru C3535 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3535
dev_langs:
- C++
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 215fa52f892cb569b32335ca439811eb07b28dc7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094075"
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

## <a name="see-also"></a>Viz také

[Auto – klíčové slovo](../../cpp/auto-keyword.md)<br/>
[Základní typy](../../cpp/fundamental-types-cpp.md)