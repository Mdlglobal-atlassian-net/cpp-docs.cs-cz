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
ms.openlocfilehash: 3e7cd4b1202ee717abf9a9767785ed8abe96bd69
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627361"
---
# <a name="fastcall"></a>__fastcall

**Specifické pro Microsoft**

**__Fastcall** konvence volání Určuje, že argumenty funkcí mají být předány v registrech, pokud je to možné. Tato konvence volání se vztahuje pouze x86 architektury. Následující seznam ukazuje implementaci této konvence volání.

|Prvek|Implementace|
|-------------|--------------------|
|Pořadí předávání argumentů|První dvě DWORD nebo menší argumenty, které se nacházejí v seznamu argumentů zleva doprava jsou předány v registrech ECX a EDX; všechny argumenty jsou předány v zásobníku zprava doleva.|
|Odpovědnost za údržbu zásobníku|Volaná funkce vezme argumenty ze zásobníku.|
|Konvence pro vzhled názvu|Zavináč (\@) je předponou názvů; zavináče následovaný počtem bajtů (v desítkové soustavě) v parametru seznam je přidán k názvům.|
|Konvence pro posunutí|Neprovádí se žádné posunutí.|

> [!NOTE]
> Budoucí verze kompilátoru mohou používat různé registry k uložení parametrů.

Použití [GR](../build/reference/gd-gr-gv-gz-calling-convention.md) – možnost kompilátoru způsobí, že každá funkce v modulu je kompilována jako **__fastcall** Pokud není funkce deklarována s konfliktním atributem použitím nebo název funkce `main` .

**__Fastcall** – klíčové slovo je přijato a ignorováno kompilátory, které se zaměřují ARM a x64 architektury; x x64 čip, podle úmluvy první čtyři argumenty předány v registrech, pokud je to možné a další argumenty jsou předány v zásobníku. Další informace najdete v tématu [x64 konvence volání](../build/x64-calling-convention.md). Čipu ARM až čtyři celočíselné argumenty a osm argumentů s plovoucí desetinnou čárkou mohou být předány v registrech a další argumenty jsou předány v zásobníku.

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

Z důvodu kompatibility s předchozími verzemi **_fastcall** je synonymum pro **__fastcall** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) je zadat.

## <a name="example"></a>Příklad

V následujícím příkladu se funkce `DeleteAggrWrapper` předány argumenty v registrech:

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)