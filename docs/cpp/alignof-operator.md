---
title: __alignof – operátor
ms.date: 10/09/2018
f1_keywords:
- alignas_cpp
- __alignof_cpp
- alignof_cpp
- __alignof
- _alignof
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
ms.openlocfilehash: 391535d7d80b075149c797cbd00fa34d46ed677d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479492"
---
# <a name="alignof-operator"></a>__alignof – operátor

C ++ 11 zavádí **alignof** operátor, který vrátí zarovnání, v bajtech zadaného typu. Pro zajištění maximální přenositelnosti používali operátor alignof místo __alignof – operátor specifické pro společnost Microsoft.

**Specifické pro Microsoft**

Vrátí hodnotu typu `size_t` to znamená požadavek zarovnání typu.

## <a name="syntax"></a>Syntaxe

```cpp
  __alignof( type )
```

## <a name="remarks"></a>Poznámky

Příklad:

|Výraz|Hodnota|
|----------------|-----------|
|**__alignof (char)**|1|
|**__alignof (krátký)**|2|
|**__alignof (int).**|4|
|**__alignof ( \__int64)**|8|
|**__alignof (float)**|4|
|**__alignof (double)**|8|
|**__alignof (char\* )**|4|

**__Alignof** hodnota je stejná jako hodnota `sizeof` pro základní typy. Uvažme však tento příklad:

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

V takovém případě **__alignof** hodnota je požadavkem zarovnání největšího prvku ve struktuře.

Podobně pro

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` je rovno `32`.

Jedním použitím **__alignof** by bylo parametrem pro jednu z vlastních rutin přidělení paměti. Například s ohledem na následující definovanou strukturu `S` lze volat rutinu přidělení paměti s názvem `aligned_malloc` pro přidělení paměti na hranici určitého zarovnání.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

Z důvodu kompatibility s předchozími verzemi **_alignof** je synonymum pro **__alignof** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) je zadat.

Další informace o úpravách zarovnání naleznete v:

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md)

- [Příklady zarovnání struktur](../build/examples-of-structure-alignment.md) (x64 konkrétní)

Další informace o rozdílech v souladu v kódu pro x86 a x64 najdete v tématu:

- [Konflikty s kompilátorem x86](../build/conflicts-with-the-x86-compiler.md)

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)