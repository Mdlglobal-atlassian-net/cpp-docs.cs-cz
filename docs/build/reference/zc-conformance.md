---
title: -Zc (shoda) | Microsoft Docs
ms.custom: 
ms.date: 9/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /zc
dev_langs: C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 86b12604a5348c3a1aabb33c7e13a4e7a3c57932
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="zc-conformance"></a>/Zc (shoda)

Můžete použít **/Zc** – možnosti kompilátoru k určení chování kompilátoru standardní nebo specifické pro společnost Microsoft.

## <a name="syntax"></a>Syntaxe

> / Zc:_možnost_{,_možnost_}

## <a name="remarks"></a>Poznámky

Po implementaci rozšíření do C nebo C++, který není kompatibilní se standardem Visual Studio můžete použít `/Zc` shody můžete určit chování standard vyhovující nebo specifické pro společnost Microsoft. Chování specifické pro společnost Microsoft pro některé možnosti, je výchozí nastavení, aby se zabránilo ve velkém měřítku nejnovější změny existujícího kódu. Výchozí hodnota je v ostatních případech standardní chování, kde vylepšení zabezpečení, výkonu a kompatibility převáží nad nákladů na nejnovější změny. V novějších verzích sady Visual Studio může změnit výchozí nastavení pro jednotlivé možnosti shoda. Další informace o jednotlivých možnostech shoda naleznete v tématu pro konkrétní možnosti.

Jedná se o `/Zc` – možnosti kompilátoru:

|Možnost|Chování|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Povolit C ++ 17 přepsání zarovnaný dynamické přidělování (zapnuto ve výchozím nastavení v C ++ 17).|
|[automaticky\[-\]](zc-auto-deduce-variable-type.md)|Vynutit nové standardní C++ význam pro `auto` (na ve výchozím nastavení).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Externí propojení pro povolení `constexpr` proměnné (ve výchozím nastavení vypnuté).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Vynutit standardní C++ `for` rozsahu pravidla (na ve výchozím nastavení).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Povolit implicitní `noexcept` na požadované funkce (na ve výchozím nastavení).|
|[vložené\[-\]](zc-inline-remove-unreferenced-comdat.md)|Odebrat neodkazované funkce nebo data, pokud je sekvence COMDAT, nebo obsahuje pouze vnitřní propojení (ve výchozím nastavení vypnuté).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Vynutit C ++ 17 noexcept pravidla (na ve výchozím nastavení součástí C ++ 17 nebo novější).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|UDT dočasného nebude vytvořit vazbu odkazu lvalue bez const (ve výchozím nastavení vypnuté).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Vynucení pravidel převodu explicitního typu Standard C++ (ve výchozím nastavení vypnuté).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Povolit C ++ 14 globální velikostí navrácení funkce (na ve výchozím nastavení).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Zakázat řetězcový literál k `char*` nebo `wchar_t*` převodu (ve výchozím nastavení vypnuté).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Povolit místní statické inicializace vláken (na ve výchozím nastavení).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Předpokládejme `operator new` vyvolá při selhání (ve výchozím nastavení vypnuté).|
|[trigraph\[-\]](zc-trigraphs-trigraphs-substitution.md)|Povolte trigraphs (zastaralé, vypněte ve výchozím nastavení).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t`je nativní typ, není typedef (na ve výchozím nastavení).|

Další informace o problémech shoda v jazyce Visual C++, najdete v části [nestandardní chování](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](compiler-options.md)  
[Nastavení možností kompilátoru](setting-compiler-options.md)
