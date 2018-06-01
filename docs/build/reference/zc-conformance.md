---
title: /Zc (shoda) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /zc
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b89744235a5a2302a6550b2ffa7100511ad2e59c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704838"
---
# <a name="zc-conformance"></a>/Zc (shoda)

Můžete použít **/Zc** – možnosti kompilátoru k určení chování kompilátoru standardní nebo specifické pro společnost Microsoft.

## <a name="syntax"></a>Syntaxe

> **/ Zc:**_možnost_{,_možnost_}

## <a name="remarks"></a>Poznámky

Po implementaci rozšíření do C nebo C++, který není kompatibilní se standardem Visual Studio můžete použít `/Zc` shody můžete určit chování standard vyhovující nebo specifické pro společnost Microsoft. Chování specifické pro společnost Microsoft pro některé možnosti, je výchozí nastavení, aby se zabránilo ve velkém měřítku nejnovější změny existujícího kódu. Výchozí hodnota je v ostatních případech standardní chování, kde vylepšení zabezpečení, výkonu a kompatibility převáží nad nákladů na nejnovější změny. V novějších verzích sady Visual Studio může změnit výchozí nastavení pro jednotlivé možnosti shoda. Další informace o jednotlivých možnostech shoda naleznete v tématu pro konkrétní možnosti. [/ Projektovou-](permissive-standards-conformance.md) – možnost kompilátoru implicitně nastaví shoda možnosti, které nejsou ve výchozím nastavení jejich vyhovující nastavení.

Jedná se o `/Zc` – možnosti kompilátoru:

|Možnost|Chování|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Povolit C ++ 17 přepsání zarovnaný dynamické přidělování (zapnuto ve výchozím nastavení v C ++ 17).|
|[Automaticky\[-\]](zc-auto-deduce-variable-type.md)|Vynutit nové standardní C++ význam pro `auto` (na ve výchozím nastavení).|
|[__cplusplus –\[-\]](zc-cplusplus.md)|Povolit **__cplusplus** makro nahlásit podporované standard (ve výchozím nastavení vypnuté).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Externí propojení pro povolení `constexpr` proměnné (ve výchozím nastavení vypnuté).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Vynutit standardní C++ `for` rozsahu pravidla (na ve výchozím nastavení).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Povolit implicitní `noexcept` na požadované funkce (na ve výchozím nastavení).|
|[Vložené\[-\]](zc-inline-remove-unreferenced-comdat.md)|Odebrat neodkazované funkce nebo data, pokud je sekvence COMDAT, nebo obsahuje pouze vnitřní propojení (ve výchozím nastavení vypnuté).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Vynutit C ++ 17 noexcept pravidla (na ve výchozím nastavení součástí C ++ 17 nebo novější).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|UDT dočasného nebude vytvořit vazbu odkazu lvalue bez const (ve výchozím nastavení vypnuté).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Vynucení pravidel převodu explicitního typu Standard C++ (ve výchozím nastavení vypnuté).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Povolit C ++ 14 globální velikostí navrácení funkce (na ve výchozím nastavení).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Zakázat řetězcový literál k `char*` nebo `wchar_t*` převodu (ve výchozím nastavení vypnuté).|
|[Ternární\[-\]](zc-ternary.md)|Vynutit podmíněný operátor pravidla pro typy operand (ve výchozím nastavení vypnuté).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Povolit místní statické inicializace vláken (na ve výchozím nastavení).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Předpokládejme `operator new` vyvolá při selhání (ve výchozím nastavení vypnuté).|
|[trigraph\[-\]](zc-trigraphs-trigraphs-substitution.md)|Povolte trigraphs (zastaralé, vypněte ve výchozím nastavení).|
|[twoPhase-](zc-twophase.md)|Šablona nonkonformní analýzy chování (který odpovídá ve výchozím nastavení).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` je nativní typ, není typedef (na ve výchozím nastavení).|

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](compiler-options.md)  
[Nastavení možností kompilátoru](setting-compiler-options.md)
