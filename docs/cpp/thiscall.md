---
title: klíčové slovo __thiscall | Dokumentace Microsoftu
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
ms.openlocfilehash: d1b7718e4c6d270536f5d7973a1b5a3ec0e61f28
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37941584"
---
# <a name="thiscall"></a>__thiscall

**Specifické pro Microsoft**

**Klíčové slovo __thiscall** konvence volání se používá pro členské funkce a je výchozí konvenci volání členských funkcí jazyka C++, které nepoužívají proměnné argumenty používá. V části **klíčové slovo __thiscall**, volaný vyčistí zásobník, který je možné `vararg` funkce. Argumenty jsou posunuty v zásobníku zprava doleva, se **to** ukazatel předávána prostřednictvím registrace ECX a ne na zásobník, v případě x86 architektury.

Jedním z důvodů použití **klíčové slovo __thiscall** je do třídy, jejíž členské funkce pomocí `__clrcall` ve výchozím nastavení. V takovém případě můžete použít **klíčové slovo __thiscall** aby jednotliví členové funkce volat z nativního kódu.

Při kompilaci s [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), všechny funkce a ukazatelů na funkce jsou `__clrcall` není uvedeno jinak. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Ve verzích před Visual C++ 2005 **klíčové slovo __thiscall** konvence volání nelze zadat explicitně v aplikaci, protože **klíčové slovo __thiscall** nebyla klíčové slovo.

`vararg` Členské funkce použijte **__cdecl** konvence volání. Všechny argumenty funkce jsou vloženy do zásobníku s **to** ukazatel umístěny na zásobník, poslední

Protože tato konvence volání se vztahuje pouze na C++, neexistuje žádné schéma dekorace názvu C.

Na ARM a x64 počítače, **klíčové slovo __thiscall** je přijato a ignorováno kompilátory.

U funkcí nestatické třídy platí, že je-li funkce definovaná mimo řádek, modifikátor konvence volání není nutné určit na definici mimo řádek. To znamená, že pro členské nestatické metody třídy se konvence volání zadaná během deklarace přejme během definice.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

- [Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)
