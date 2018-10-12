---
title: __stdcall | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/10/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
dev_langs:
- C++
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 06eafcd4303e01be523554f2a164e6cb14f79a26
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49162253"
---
# <a name="stdcall"></a>__stdcall

**Specifické pro Microsoft**

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