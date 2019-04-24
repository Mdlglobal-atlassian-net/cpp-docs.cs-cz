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
ms.openlocfilehash: 298485d310ee4039b13781a8b5cd88a489af3b8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232399"
---
# <a name="cdecl"></a>__cdecl

**Microsoft Specific**

**__cdecl** je výchozí konvencí volání jazyka C a C++ programy. Vzhledem k tomu, že je zásobník vyčištěn volajícím, můžete provádět `vararg` funkce. **__Cdecl** konvence volání vytvoří větší spustitelné soubory než [__stdcall](../cpp/stdcall.md), protože vyžaduje, aby každé volání funkce obsahovalo kód pro vyčištění zásobníku. Následující seznam ukazuje implementaci této konvence volání.

|Prvek|Implementace|
|-------------|--------------------|
|Pořadí předávání argumentů|Zprava doleva.|
|Odpovědnost za údržbu zásobníku|Volání funkce vezme argumenty ze zásobníku (POP).|
|Konvence pro vzhled názvu|Znak podtržítka (_) je předponou názvů, kromě případů, kdy \__cdecl funkce, které používají C-linkage jsou exportovány.|
|Konvence pro posunutí|Neprovádí se žádné posunutí.|

> [!NOTE]
>  Související informace naleznete v tématu [dekorované názvy](../build/reference/decorated-names.md).

Místo **__cdecl** modifikátor před proměnnou nebo název funkce. Protože konvence pojmenování a volání jazyka C jsou standardem, jediný případ je nutné použít **__cdecl** x86 kód je Pokud jste určili `/Gv` (vectorcall), `/Gz` (stdcall) nebo `/Gr` (fastcall) – možnost kompilátoru. [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) vynutí – možnost kompilátoru **__cdecl** konvence volání.

Na ARM a x64 procesory, **__cdecl** přijme, ale obvykle ignoruje kompilátor. Podle konvence pro procesory ARM a x64 jsou argumenty předávány v registrech vždy, když je to možné, a následné argumenty jsou předávány na zásobníku. V x64 kódu, použijte **__cdecl** přepsání **/Gv** – možnost kompilátoru a použijte výchozí x64 konvenci volání.

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

Z důvodu kompatibility s předchozími verzemi **cdecl** a **_cdecl** jsou synonyma pro **__cdecl** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) určena.

## <a name="example"></a>Příklad

V následujícím příkladu je kompilátor nastaven na použití názvů C a konvencí pro volání `system` funkce.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Viz také:

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)