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
ms.openlocfilehash: b4a86c49880b0c40d402c7cec863f79e24bc4dc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371566"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl** je výchozí konvence volání pro programy Jazyka C a C++. Vzhledem k tomu, že zásobník je `vararg` vyčištěn volajícím, může dělat funkce. __cdecl **__cdecl** konvence volání vytvoří větší spustitelné soubory než [__stdcall](../cpp/stdcall.md), protože vyžaduje, aby každé volání funkce zahrnovalo kód vyčištění zásobníku. Následující seznam ukazuje implementaci této konvence volání. Modifikátor **__cdecl** je specifický pro společnost Microsoft.

|Prvek|Implementace|
|-------------|--------------------|
|Pořadí předávání argumentů|Zprava doleva.|
|Odpovědnost za údržbu zásobníku|Volání funkce vezme argumenty ze zásobníku (POP).|
|Konvence pro vzhled názvu|Znak podtržítka (_) je \_předponou na názvy, s výjimkou případů, kdy jsou exportovány _cdecl funkce, které používají propojení C.|
|Konvence pro posunutí|Neprovádí se žádné posunutí.|

> [!NOTE]
> Související informace naleznete v tématu [Dekorované názvy](../build/reference/decorated-names.md).

Umístěte **modifikátor __cdecl** před proměnnou nebo název funkce. Vzhledem k tomu, že konvence pojmenování a volání Jazyka C jsou výchozí, je `/Gv` nutné použít `/Gz` **pouze __cdecl** v kódu x86, pokud jste zadali možnost kompilátoru (vectorcall), (stdcall) nebo `/Gr` (fastcall). Možnost kompilátoru [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) vynutí **__cdecl** konvence volání.

Na procesorech ARM a x64 je **__cdecl** přijata, ale obvykle je kompilátorem ignorována. Podle konvence pro procesory ARM a x64 jsou argumenty předávány v registrech vždy, když je to možné, a následné argumenty jsou předávány na zásobníku. V kódu x64 použijte **__cdecl** k přepsání možnosti kompilátoru **/Gv** a použijte výchozí konvenci volání x64.

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

Pro kompatibilitu s předchozími verzemi jsou **cdecl** a **_cdecl** synonymem pro **__cdecl** pokud není zadána možnost kompilátoru [ \(/Za Zakázat jazykové rozšíření).](../build/reference/za-ze-disable-language-extensions.md)

## <a name="example"></a>Příklad

V následujícím příkladu je kompilátor instruován k použití `system` c pojmenování a volání konvence pro funkci.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Viz také

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
