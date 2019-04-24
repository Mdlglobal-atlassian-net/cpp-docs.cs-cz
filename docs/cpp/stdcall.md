---
title: __stdcall
ms.date: 10/10/2018
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
ms.openlocfilehash: b9efac6f729a78db945ff3bd9ab16ebe315b7a5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266956"
---
# <a name="stdcall"></a>__stdcall

**Microsoft Specific**

**__Stdcall** konvence volání se používá pro volání funkce rozhraní Win32 API. Volaný vyčistí zásobník, aby mohl kompilátor `vararg` funkce **__cdecl**. Funkce, které používají konvenci volání k vyžadování prototypu funkce.

## <a name="syntax"></a>Syntaxe

> *Návratový typ*  **\_ \_stdcall** *název funkce*[**(** *seznam argumentů* **)** ]

## <a name="remarks"></a>Poznámky

Následující seznam ukazuje implementaci této konvence volání.

|Prvek|Implementace|
|-------------|--------------------|
|Pořadí předávání argumentů|Zprava doleva.|
|Konvence předávání argumentů|Podle hodnoty Pokud je předán typ ukazatele nebo odkazu.|
|Odpovědnost za údržbu zásobníku|Volaná funkce vezme argumenty ze zásobníku.|
|Konvence pro vzhled názvu|Podtržítko (_) je předponou názvu. Následuje název zavináč (@) následovaným počtem bajtů (v desítkové soustavě) v seznamu argumentů. Proto se funkce deklarovaná jako `int func( int a, double b )` upravena takto: `_func@12`|
|Konvence pro posunutí|Žádné|

[/Gz](../build/reference/gd-gr-gv-gz-calling-convention.md) určuje – možnost kompilátoru **__stdcall** pro všechny funkce, které nejsou explicitně deklarovány pomocí jiné konvence volání.

Z důvodu kompatibility s předchozími verzemi **_stdcall** je synonymum pro **__stdcall** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) je zadat.

Funkce deklarované pomocí **__stdcall** modifikátor návratové hodnoty stejným způsobem jako funkce deklarovaná pomocí [__cdecl](../cpp/cdecl.md).

Na ARM a x64 procesory, **__stdcall** je přijato a ignorováno kompilátory; v ARM a x64 architektur, podle úmluvy argumenty předány v registrech, pokud je to možné a další argumenty jsou předány v zásobníku.

U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice. Při této definici třídy

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

je ekvivalentem tohoto

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>Příklad

V následujícím příkladu, využívání **__stdcall** výsledky ve všech `WINAPI` typů funkcí jako standardní volání:

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Viz také:

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)