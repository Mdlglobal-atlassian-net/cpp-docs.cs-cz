---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: 8772159dca71bb7605af5e5919425065423d503d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188152"
---
# <a name="__thiscall"></a>__thiscall

**Specifické pro společnost Microsoft**

Konvence volání **__thiscall** se používá pro členské funkce a je výchozí konvencí volání používaná C++ členskými funkcemi, které nepoužívají argumenty proměnných. V části **__thiscall**volaný vyčistí zásobník, což není možné pro funkce `vararg`. Argumenty jsou vloženy do zásobníku zprava doleva, s **tímto** ukazatelem předávaným pomocí Register ecx, nikoli v zásobníku, v architektuře x86.

Jedním z důvodů použití **__thiscall** je v třídách, jejichž členské funkce používají `__clrcall` ve výchozím nastavení. V takovém případě můžete použít **__thiscall** k tomu, aby se jednotlivé členské funkce mohly volat z nativního kódu.

Při kompilaci s možností [/clr: Pure](../build/reference/clr-common-language-runtime-compilation.md)jsou všechny funkce a ukazatele funkce `__clrcall`, pokud není uvedeno jinak. Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

V rámci vydání sady Visual Studio 2005 nebylo možné explicitně zadat konvenci volání **__thiscall** v programu, protože **__thiscall** nebyla klíčovým slovem.

`vararg` členské funkce používají konvenci volání **__cdecl** . Všechny argumenty funkce jsou vloženy do zásobníku s **tímto** ukazatelem umístěným v zásobníku jako poslední.

Vzhledem k tomu, že se tato C++konvence volání vztahuje pouze na, neexistuje žádné schéma dekorace názvu C.

V počítačích s procesorem ARM a x64 je **__thiscall** přijat a ignorován kompilátorem.

U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)
