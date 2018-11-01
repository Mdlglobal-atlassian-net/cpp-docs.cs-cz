---
title: /Zc (shoda)
ms.date: 03/06/2018
f1_keywords:
- /zc
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: b1f612040eea0078b0f27cf72327db94fe9e2939
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50665428"
---
# <a name="zc-conformance"></a>/Zc (shoda)

Můžete použít **/Zc** – možnosti kompilátoru k určení chování kompilátoru standardního nebo specifické pro společnost Microsoft.

## <a name="syntax"></a>Syntaxe

> **/ Zc:**_možnost_{,_možnost_}

## <a name="remarks"></a>Poznámky

Po implementaci rozšíření jazyka C nebo C++, který není kompatibilní se standardem sady Visual Studio můžete použít `/Zc` shody můžete určit chování splňují standard nebo specifické pro společnost Microsoft. Chování specifické pro společnost Microsoft pro některé možnosti, je výchozí, aby se zabránilo ve velkém měřítku rozbíjející změny stávajícího kódu. Výchozí hodnota je v jiných případech standardní chování, kde vylepšení zabezpečení, výkonu a kompatibility převažují nad náklady na nejnovější změny. V novějších verzích sady Visual Studio může změnit výchozí nastavení jednotlivých možností shody. Další informace o jednotlivých možnostech přizpůsobení naleznete v tématu pro konkrétní možnosti. [/ Permissive-](permissive-standards-conformance.md) – možnost kompilátoru implicitně nastaví možnosti přizpůsobení, které nejsou ve výchozím nastavení jejich splňující podmínky nastavení.

Jedná se o `/Zc` – možnosti kompilátoru:

|Možnost|Chování|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Povolení C ++ 17 nadbytečně zarovnané dynamického přidělování (zapnuto ve výchozím nastavení v C ++ 17).|
|[Automaticky\[-\]](zc-auto-deduce-variable-type.md)|Vynutit nový význam jazyka Standard C++ pro `auto` (na ve výchozím nastavení).|
|[__cplusplus\[-\]](zc-cplusplus.md)|Povolit **__cplusplus** – makro hlášení podporované standard (ve výchozím nastavení vypnuté).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Povolit vnější propojení pro `constexpr` proměnné (ve výchozím nastavení vypnuté).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Vynutit Standard C++ `for` pravidel oboru (na ve výchozím nastavení).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Povolit implicitní `noexcept` pro požadované funkce (na ve výchozím nastavení).|
|[vložené\[-\]](zc-inline-remove-unreferenced-comdat.md)|Odebrat neodkazovaný funkci nebo data, pokud je COMDAT nebo má jenom vnitřní vazby (ve výchozím nastavení vypnuté).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Vynutit pravidla C ++ 17 noexcept (v ve výchozím nastavení v C ++ 17 nebo novější).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|UDT dočasné se nebudou vázat k odkazu na nekonstantní l-hodnota (ve výchozím nastavení vypnuté).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Vynucení pravidel převodu explicitního typu Standard C++ (ve výchozím nastavení vypnuté).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Povolení C ++ 14 globální velikostí dealokace funkcí (na ve výchozím nastavení).|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Zakázat string-literal na `char*` nebo `wchar_t*` převod (ve výchozím nastavení vypnuté).|
|[Ternární\[-\]](zc-ternary.md)|Vynutit pravidla podmíněného operátoru na typy operandů (ve výchozím nastavení vypnuté).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Povolit lokální statická inicializace bezpečná pro vlákno (na ve výchozím nastavení).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Předpokládejme `operator new` při selhání vyvolá výjimku (ve výchozím nastavení vypnuté).|
|[Trigraphs\[-\]](zc-trigraphs-trigraphs-substitution.md)|Povolte sekvence (zastaralé, vypnuto ve výchozím nastavení).|
|[twoPhase-](zc-twophase.md)|Šablona nonkonformní analýza chování (který odpovídá ve výchozím nastavení).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` je nativní typ, ne typedef (na ve výchozím nastavení).|

Další informace o problémech přizpůsobení v aplikaci Visual C++, naleznete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru](compiler-options.md)<br/>
[Nastavení možností kompilátoru](setting-compiler-options.md)
