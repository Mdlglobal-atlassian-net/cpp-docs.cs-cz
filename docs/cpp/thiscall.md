---
title: __thiscall | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __thiscall
- __thiscall_cpp
dev_langs:
- C++
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4912628529ae0b47a5a5b938ab8e6d25a9099510
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704400"
---
# <a name="thiscall"></a>__thiscall

**Konkrétní Microsoft**

`__thiscall` Konvence volání se používá na členské funkce a konvence volání výchozí používané C++ členské funkce, které nepoužívají proměnné argumenty. V části `__thiscall`, volaného vyčistí zásobníku, což je znemožňuje, aby `vararg` funkce. Argumenty jsou vložena v zásobníku zprava doleva, se `this` ukazatel předávány prostřednictvím registrace ECX a ne v zásobníku, na x86 architektura.

Jedním z důvodů používat `__thiscall` v třídy, jejichž členské funkce použití `__clrcall` ve výchozím nastavení. V takovém případě můžete použít `__thiscall` , aby jednotlivými členy funkce volány z nativního kódu.

Při kompilaci s [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), jsou všechny funkce a ukazatelů na funkce `__clrcall` není uvedeno jinak. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Ve verzích před Visual C++ 2005 `__thiscall` konvence volání nelze zadat explicitně v programu, protože `__thiscall` nebyla klíčové slovo.

`vararg` Členské funkce pomocí `__cdecl` konvence volání. Všechny argumenty funkce jsou vložena do zásobníku, se `this` v zásobníku poslední umístit ukazatel

Protože tato konvence volání se vztahuje pouze na C++, neexistuje žádné schéma decoration název C.

Na ARM a x64 počítače, `__thiscall` je přijatá a ignorovat kompilátoru.

U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice.

**Konkrétní Microsoft END**

## <a name="see-also"></a>Viz také:

- [Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)
