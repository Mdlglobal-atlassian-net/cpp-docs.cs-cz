---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: cfe3631086515e4e31c7d4188d46e3a7440662b7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177947"
---
# <a name="naked-c"></a>naked (C++)

**Specifické pro společnost Microsoft**

Pro funkce deklarované s atributem **holé** generuje kompilátor kód bez kódu prologu a epilogu. Tuto funkci lze použít pro psaní vlastních sekvencí kódu epilogu nebo prologu pomocí vloženého kódu assembleru. Neviditelné funkce jsou zvláště užitečné při psaní ovladačů virtuálních zařízení.  Upozorňujeme, že **atribut s** atributy je platný jenom pro procesory x86 a ARM a není k dispozici na platformě x64.

## <a name="syntax"></a>Syntaxe

```
__declspec(naked) declarator
```

## <a name="remarks"></a>Poznámky

Vzhledem k tomu, že atribut **holé** je relevantní pouze pro definici funkce a není modifikátorem typu, musí holé funkce použít syntaxi rozšířeného atributu a klíčové slovo [__declspec](../cpp/declspec.md) .

Kompilátor nemůže vygenerovat vloženou funkci pro funkci označenou atributem holé, a to i v případě, že je funkce také označena klíčovým slovem [__forceinline](inline-functions-cpp.md) .

Kompilátor vystaví **chybu, pokud je atribut s** atributy atributu použit na jinou hodnotu než definice jiné než členské metody.

## <a name="examples"></a>Příklady

Tento kód definuje funkci s atributem **holé** :

```
__declspec( naked ) int func( formal_parameters ) {}
```

Nebo alternativně:

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

Atribut **s omezením má vliv** jenom na povahu generování kódu kompilátoru pro Prology a sekvence epilogu funkce. Neovlivňuje kód, který je generován pro volání těchto funkcí. Proto atribut s **pouhým** není považován za součást typu funkce a ukazatele funkce nemohou mít atribut **s atributy.** Kromě **toho atribut s** podmnožinou nelze použít pro definici dat. Například Tato ukázka kódu vygeneruje chybu:

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

Atribut **s atributy je relevantní** pouze pro definici funkce a nelze ji zadat v prototypu funkce. Například tato deklarace generuje chybu kompilátoru:

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Volání holé funkce](../cpp/naked-function-calls.md)
