---
title: __cdecl
ms.date: 10/09/2018
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
ms.openlocfilehash: 8f2b2b0cea8ff30cc450aae534fbff0d7b77f457
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190091"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl** je výchozí konvencí volání pro C a C++ programy. Vzhledem k tomu, že je zásobník vyčištěn volajícím, může provádět `vararg` funkce. Konvence volání **__cdecl** vytváří větší spustitelné soubory než [__stdcall](../cpp/stdcall.md), protože vyžaduje každé volání funkce pro zahrnutí kódu pro vyčištění zásobníku. Následující seznam ukazuje implementaci této konvence volání. Modifikátor **__cdecl** je specifický pro společnost Microsoft.

|Prvek|Implementace|
|-------------|--------------------|
|Pořadí předávání argumentů|Zprava doleva.|
|Odpovědnost za údržbu zásobníku|Volání funkce vezme argumenty ze zásobníku (POP).|
|Konvence pro vzhled názvu|Znak podtržítka (_) je předponou názvů, kromě případů, kdy \__cdecl funkce, které používají propojení jazyka C, jsou exportovány.|
|Konvence pro posunutí|Neprovádí se žádné posunutí.|

> [!NOTE]
>  Související informace naleznete v tématu [dekorované názvy](../build/reference/decorated-names.md).

Před proměnnou nebo název funkce Umístěte modifikátor **__cdecl** . Vzhledem k tomu, že konvence pojmenování a volání jazyka C jsou výchozí, jediný čas, kdy je nutné použít **__cdecl** v kódu x86, je, že jste zadali možnost kompilátoru `/Gv` (vectorcall), `/Gz` (STDCALL) nebo `/Gr` (fastcall). Možnost kompilátoru [/GD](../build/reference/gd-gr-gv-gz-calling-convention.md) vynutí konvenci volání **__cdecl** .

V procesorech ARM a x64 je **__cdecl** přijatý, ale obvykle je kompilátor ignoruje. Podle konvence pro procesory ARM a x64 jsou argumenty předávány v registrech vždy, když je to možné, a následné argumenty jsou předávány na zásobníku. V kódu x64 použijte **__cdecl** k přepsání možnosti kompilátoru **/GV** a použijte výchozí konvenci volání x64.

U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice. Při této definici třídy:

```cpp
struct CMyClass {
   void __cdecl mymethod();
};
```

toto:

```cpp
void CMyClass::mymethod() { return; }
```

je ekvivalentem tohoto:

```cpp
void __cdecl CMyClass::mymethod() { return; }
```

Z důvodu kompatibility s předchozími verzemi jsou **CDECL** a **_cdecl** synonymem pro **__cdecl** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

## <a name="example"></a>Příklad

V následujícím příkladu je kompilátor vyzván k použití názvů C a konvencí volání pro funkci `system`.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Viz také

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
