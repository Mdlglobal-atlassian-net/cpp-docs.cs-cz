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
ms.openlocfilehash: 3abd1d020e4181a42a7bc38319e5e17e69ef0507
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178535"
---
# <a name="__stdcall"></a>__stdcall

Konvence volání **__stdcall** slouží k volání funkcí Win32 API. Volaný vyčistí zásobník, takže kompilátor vytvoří `vararg` Functions **__cdecl**. Funkce, které používají tuto konvenci volání, vyžadují prototyp funkce. Modifikátor **__stdcall** je specifický pro společnost Microsoft.

## <a name="syntax"></a>Syntaxe

> *návratový typ* **\_\_STDCALL** *– název funkce*[ **(** *argument-seznam* **)** ]

## <a name="remarks"></a>Poznámky

Následující seznam ukazuje implementaci této konvence volání.

|Prvek|Implementace|
|-------------|--------------------|
|Pořadí předávání argumentů|Zprava doleva.|
|Konvence předávání argumentů|Podle hodnoty, pokud není předán typ ukazatele nebo odkazu.|
|Odpovědnost za údržbu zásobníku|Volaná funkce převezme své vlastní argumenty ze zásobníku.|
|Konvence pro vzhled názvu|Podtržítko (_) je předponou názvu. Za názvem následuje znak @ (@) následovaný počtem bajtů (v desítkové soustavě) v seznamu argumentů. Proto je funkce deklarovaná jako `int func( int a, double b )` upravena takto: `_func@12`|
|Konvence pro posunutí|Žádné|

Možnost kompilátoru [/GZ](../build/reference/gd-gr-gv-gz-calling-convention.md) Určuje **__stdcall** pro všechny funkce, které nejsou explicitně deklarovány s jinou konvencí volání.

Z důvodu kompatibility s předchozími verzemi je **_stdcall** synonymem pro **__stdcall** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

Funkce deklarované pomocí modifikátoru **__stdcall** vrací hodnoty stejným způsobem jako funkce deklarované pomocí [__cdecl](../cpp/cdecl.md).

V procesorech ARM a x64 je **__stdcall** přijat a ignorován kompilátorem; v architekturách ARM a x64 jsou podle úmluvy předány argumenty v registrech, pokud je to možné, a další argumenty jsou předány do zásobníku.

U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice. Daná definice třídy

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

tohoto provozu

```cpp
void CMyClass::mymethod() { return; }
```

je ekvivalentem tohoto

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>Příklad

V následujícím příkladu použití **__stdcall** má za následek, že jsou všechny typy funkcí `WINAPI` zpracovávány jako standardní volání:

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Viz také

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
