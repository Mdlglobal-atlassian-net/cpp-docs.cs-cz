---
title: __thiscall
ms.date: 05/22/2020
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: b9edc2cd8caa5fd5458f6a53c5fdb1f8a5e69914
ms.sourcegitcommit: 5bb421fdf61d290cac93a03e16a6a80959accf6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83854811"
---
# `__thiscall`

Konvence volání **specifická pro společnost Microsoft** **`__thiscall`** se používá pro členské funkce třídy jazyka C++ v architektuře x86. Je výchozí konvencí volání používaná členskými funkcemi, které nepoužívají argumenty proměnných ( `vararg` funkce).

V části **`__thiscall`** volaný vyčistí zásobník, který není pro funkce možný `vararg` . Argumenty jsou vloženy do zásobníku zprava doleva. **`this`** Ukazatel se předává přes Register ecx, nikoli v zásobníku.

V počítačích ARM, ARM64 a x64 **`__thiscall`** je kompilátorem přijat a ignorován. To je proto, že ve výchozím nastavení používají konvenci volání založené na registraci.

Jedním z důvodů použití **`__thiscall`** je v třídách, jejichž členské funkce používají **`__clrcall`** ve výchozím nastavení. V takovém případě můžete použít **`__thiscall`** k tomu, aby se jednotlivé členské funkce mohly volat z nativního kódu.

Při kompilování se [**`/clr:pure`**](../build/reference/clr-common-language-runtime-compilation.md) všemi funkcemi a ukazateli na funkce jsou, **`__clrcall`** Pokud není uvedeno jinak. **`/clr:pure`** **`/clr:safe`** Možnosti kompilátoru a jsou zastaralé v aplikaci visual Studio 2015 a nejsou podporovány v aplikaci visual Studio 2017.

`vararg`Členské funkce používají **`__cdecl`** konvenci volání. Všechny argumenty funkce jsou vloženy do zásobníku s **`this`** ukazatelem umístěným v zásobníku jako poslední.

Vzhledem k tomu, že tato konvence volání se vztahuje pouze na C++, nemá schéma dekorace názvu C.

Pokud definujete nestatickou členskou funkci třídy mimo řádek, zadejte modifikátor konvence volání pouze v deklaraci. Nemusíte ho zadávat znovu na definici mimo řádek. Kompilátor používá konvenci volání určenou během deklarace v bodě definice.

## <a name="see-also"></a>Viz také

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)
