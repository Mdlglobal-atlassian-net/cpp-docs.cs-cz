---
title: __fastcall
ms.date: 12/17/2018
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
ms.openlocfilehash: d4b650542a3a85c8f0008374abef02686c5491a3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188919"
---
# <a name="__fastcall"></a>__fastcall

**Specifické pro společnost Microsoft**

Konvence volání **__fastcall** určuje, že argumenty funkcí mají být předány v registrech, pokud je to možné. Tato konvence volání se vztahuje pouze na architekturu x86. Následující seznam ukazuje implementaci této konvence volání.

|Prvek|Implementace|
|-------------|--------------------|
|Pořadí předávání argumentů|První dva argumenty DWORD nebo menší argumenty, které se nacházejí v seznamu argumentů zleva doprava, jsou předány v registrech ECX a EDX; všechny ostatní argumenty jsou předány v zásobníku zprava doleva.|
|Odpovědnost za údržbu zásobníku|Volaná funkce převezme argumenty ze zásobníku.|
|Konvence pro vzhled názvu|Na znaménko (\@) je předpona názvů; u znaménka následovaných počtem bajtů (v desítkové soustavě) v seznamu parametrů je přípona na názvy.|
|Konvence pro posunutí|Neprovádí se žádné posunutí.|

> [!NOTE]
> Budoucí verze kompilátoru mohou pro ukládání parametrů použít různé registry.

Použití možnosti kompilátoru [/gr](../build/reference/gd-gr-gv-gz-calling-convention.md) způsobí, že každá funkce v modulu má být zkompilována jako **__fastcall** , pokud není funkce deklarována pomocí kolidujícího atributu nebo pokud je název funkce `main`.

Klíčové slovo **__fastcall** je přijato a ignorováno kompilátory, které cílí na architektury ARM a x64. v případě čipu x64, podle úmluvy, jsou první čtyři argumenty předány v registrech, pokud je to možné, a další argumenty jsou předány do zásobníku. Další informace naleznete v tématu [konvence volání x64](../build/x64-calling-convention.md). V případě čipu ARM může být v registrech předán až čtyři celočíselné argumenty a osm argumentů s plovoucí desetinnou čárkou a další argumenty jsou předány do zásobníku.

U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice. Při této definici třídy:

```cpp
struct CMyClass {
   void __fastcall mymethod();
};
```

toto:

```cpp
void CMyClass::mymethod() { return; }
```

je ekvivalentem tohoto:

```cpp
void __fastcall CMyClass::mymethod() { return; }
```

Z důvodu kompatibility s předchozími verzemi je **_fastcall** synonymem pro **__fastcall** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Příklad

V následujícím příkladu je funkce `DeleteAggrWrapper` předána argumenty v registrech:

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
