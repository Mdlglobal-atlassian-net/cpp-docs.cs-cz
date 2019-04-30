---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: 951760d7f9566c084bbe3d5a574d006020576c61
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345009"
---
# <a name="naked-c"></a>naked (C++)

**Microsoft Specific**

Pro funkce deklarované s **naked** atribut, kompilátor generuje kód bez kódu prologu a epilogu. Tuto funkci lze použít pro psaní vlastních sekvencí kódu epilogu nebo prologu pomocí vloženého kódu assembleru. Neviditelné funkce jsou zvláště užitečné při psaní ovladačů virtuálních zařízení.  Všimněte si, že **naked** atribut je platný jenom pro x86 a ARM a není k dispozici na x64.

## <a name="syntax"></a>Syntaxe

```
__declspec(naked) declarator
```

## <a name="remarks"></a>Poznámky

Protože **naked** atribut platí pouze pro definici funkce a není modifikátorem typu, musí neviditelné funkce používají rozšířenou syntaxi atributů a [__declspec](../cpp/declspec.md) – klíčové slovo.

Kompilátor nemůže generovat vložené funkce pro funkci s atributem naked i v případě, že funkce je také označena [__forceinline](inline-functions-cpp.md) – klíčové slovo.

Kompilátor vyvolá chybu, pokud **naked** atributu se použije na jinou hodnotu než definicí metody bez členů.

## <a name="examples"></a>Příklady

Tento kód definuje funkci s **naked** atribut:

```
__declspec( naked ) int func( formal_parameters ) {}
```

Nebo alternativně:

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

**Naked** atribut ovlivňuje pouze povahu generování kódu kompilátoru pro sekvence prologu a epilogu funkce. Neovlivňuje kód, který je generován pro volání těchto funkcí. Proto **naked** atribut není považován za součást typu funkce a ukazatele funkce nemohou mít **naked** atribut. Kromě toho **naked** atribut nejde použít s definicí data. Například tato ukázka kódu generuje chybu:

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

**Naked** atribut je relevantní pouze pro definici funkce a nelze zadat v prototypu funkce. Například tato deklarace generuje chybu kompilátoru:

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Volání holé funkce](../cpp/naked-function-calls.md)