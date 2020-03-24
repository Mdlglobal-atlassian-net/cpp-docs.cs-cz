---
title: dllexport, dllimport
ms.date: 11/04/2016
f1_keywords:
- dllimport_cpp
- dllexport_cpp
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
ms.openlocfilehash: 0a8d90770552b8b9ab9169378289108d91811216
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189452"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport

**Specifické pro společnost Microsoft**

Atributy třídy úložiště **dllexport** a **dllimport** jsou rozšířeními specifickými pro společnost Microsoft pro jazyky C C++ a. Můžete je použít k exportu a importu funkcí, dat a objektů do knihovny DLL nebo z ní.

## <a name="syntax"></a>Syntaxe

```
   __declspec( dllimport ) declarator
   __declspec( dllexport ) declarator
```

## <a name="remarks"></a>Poznámky

Tyto atributy explicitně definují rozhraní knihovny DLL pro jeho klienta, což může být spustitelný soubor nebo jiná knihovna DLL. Deklarování funkcí jako **dllexport** eliminuje potřebu souboru definice modulu (. def), přinejmenším v souvislosti se specifikací exportovaných funkcí. Atribut **dllexport** nahrazuje klíčové slovo **__export** .

Pokud je třída označena jako declspec (dllexport), jakékoli specializace šablon třídy v hierarchii tříd jsou implicitně označeny jako declspec (dllexport). To znamená, že šablony tříd jsou explicitně vytvořeny a členy třídy musí být definovány.

**dllexport** funkce zpřístupňuje funkci s dekorovaným názvem. V C++ případě funkcí to zahrnuje pozměnění názvu. V případě funkcí nebo funkcí jazyka C, které jsou deklarovány jako `extern "C"`, zahrnuje dekoraci specifické pro platformu, která je založena na konvenci volání. Informace o dekorace názvu v kódu C/C++ Code naleznete v tématu [dekorované názvy](../build/reference/decorated-names.md). Pro exportované funkce jazyka C nebo C++ funkce `extern "C"` pomocí `__cdecl` konvence volání nejsou použity žádné dekorace názvů.

Chcete-li exportovat nedekorovaný název, můžete propojit pomocí souboru definice modulu (. def), který definuje nedekorovaný název v oddílu EXPORTs. Další informace najdete v tématu [exporty](../build/reference/exports.md). Dalším způsobem exportu nedekorované názvu je použití direktivy `#pragma comment(linker, "/export:alias=decorated_name")` ve zdrojovém kódu.

Při deklaraci **dllexport** nebo **dllimport**je nutné použít [syntaxi rozšířeného atributu](../cpp/declspec.md) a klíčové slovo **__declspec** .

## <a name="example"></a>Příklad

```cpp
// Example of the dllimport and dllexport class attributes
__declspec( dllimport ) int i;
__declspec( dllexport ) void func();
```

Nebo pokud chcete, aby byl kód čitelnější, můžete použít definice maker:

```cpp
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllImport int j;
DllExport int n;
```

Další informace naleznete v tématu:

- [Definice a deklarace](../cpp/definitions-and-declarations-cpp.md)

- [Definování vložených funkcí jazyka C++ příkazy dllexport a dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

- [Obecná pravidla a omezení](../cpp/general-rules-and-limitations.md)

- [Používání příkazů dllimport a dllexport ve třídách jazyka C++](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
