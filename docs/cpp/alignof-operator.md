---
title: __alignof – operátor
ms.date: 12/17/2018
f1_keywords:
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
ms.openlocfilehash: 6bddce29dd97d965303a58cc72aa97dfe8cbd8d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181535"
---
# <a name="__alignof-operator"></a>__alignof – operátor

C++ 11 zavádí operátor **alignof** , který vrací zarovnání v bajtech zadaného typu. Pro maximální přenositelnost byste měli použít operátor alignof namísto operátoru __alignof specifického pro společnost Microsoft.

**Specifické pro společnost Microsoft**

Vrací hodnotu typu `size_t`, která je požadavkem na zarovnání typu.

## <a name="syntax"></a>Syntaxe

```cpp
  __alignof( type )
```

## <a name="remarks"></a>Poznámky

Příklad:

|Výraz|Hodnota|
|----------------|-----------|
|**__alignof (Char)**|1|
|**__alignof (krátký)**|2|
|**__alignof (int)**|4|
|**__alignof (\__int64)**|8|
|**__alignof (float)**|4|
|**__alignof (Double)**|8|
|**__alignof (Char\*)**|4|

Hodnota **__alignof** je stejná jako hodnota `sizeof` pro základní typy. Uvažme však tento příklad:

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

V tomto případě je hodnota **__alignof** požadavek na zarovnání největšího prvku ve struktuře.

Podobně pro

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` se rovná `32`.

Jedním z použití **__alignof** by byl jako parametr jedné z vlastních rutin pro přidělování paměti. Například s ohledem na následující definovanou strukturu `S` lze volat rutinu přidělení paměti s názvem `aligned_malloc` pro přidělení paměti na hranici určitého zarovnání.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

Z důvodu kompatibility s předchozími verzemi je **_alignof** synonymem pro **__alignof** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

Další informace o úpravách zarovnání naleznete v:

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (zarovnání členů struktury)](../build/reference/zp-struct-member-alignment.md)

- [Příklady zarovnání struktury](../build/x64-software-conventions.md#examples-of-structure-alignment) (specifické pro procesory x64)

Další informace o rozdílech v zarovnání v kódu pro x86 a x64 naleznete v tématu:

- [Konflikty s kompilátorem x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
