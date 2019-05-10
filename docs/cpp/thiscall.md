---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: e51879ae62b2881e0adadbe59859605f6cc58947
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221909"
---
# <a name="thiscall"></a>__thiscall

**Microsoft Specific**

**Klíčové slovo __thiscall** konvence volání se používá pro členské funkce a je jako výchozí konvenci volání C++ členské funkce, které nepoužívají proměnné argumenty. V části **klíčové slovo __thiscall**, volaný vyčistí zásobník, který je možné `vararg` funkce. Argumenty jsou posunuty v zásobníku zprava doleva, se **to** ukazatel předávána prostřednictvím registrace ECX a ne na zásobník, v případě x86 architektury.

Jedním z důvodů použití **klíčové slovo __thiscall** je do třídy, jejíž členské funkce pomocí `__clrcall` ve výchozím nastavení. V takovém případě můžete použít **klíčové slovo __thiscall** aby jednotliví členové funkce volat z nativního kódu.

Při kompilaci s [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), všechny funkce a ukazatelů na funkce jsou `__clrcall` není uvedeno jinak. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Ve verzích před Visual Studio 2005 **klíčové slovo __thiscall** konvence volání nelze zadat explicitně v aplikaci, protože **klíčové slovo __thiscall** nebyla klíčové slovo.

`vararg` Členské funkce použijte **__cdecl** konvence volání. Všechny argumenty funkce jsou vloženy do zásobníku s **to** ukazatel umístěny na zásobník, poslední

Protože tato konvence volání se vztahuje pouze na C++, neexistuje žádné schéma dekorace názvu C.

Na ARM a x64 počítače, **klíčové slovo __thiscall** je přijato a ignorováno kompilátory.

U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)