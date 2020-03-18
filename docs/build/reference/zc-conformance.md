---
title: /Zc (shoda)
ms.date: 03/06/2018
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 4422524deab2a749c96d5e967bc3223d0c9c9873
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438667"
---
# <a name="zc-conformance"></a>/Zc (shoda)

Můžete použít možnosti kompilátoru **/Zc** k určení chování kompilátoru standardní nebo specifické pro společnost Microsoft.

## <a name="syntax"></a>Syntaxe

> **/Zc:** _možnost_{,_možnost_}

## <a name="remarks"></a>Poznámky

Pokud aplikace Visual Studio implementovala rozšíření pro C nebo C++ , které není kompatibilní se standardem, můžete použít možnost shody `/Zc` k určení chování specifického pro vyhovujícího standardu nebo pro konkrétního společnosti Microsoft. Pro některé možnosti je výchozím chováním specifické pro společnost Microsoft, aby se zabránilo rozsáhlým velkým změnám v existujícím kódu. V ostatních případech je výchozím chováním standardní chování, kde vylepšení zabezpečení, výkonu nebo kompatibility převažují náklady na zásadní změny. V novějších verzích sady Visual Studio se může změnit výchozí nastavení pro každou možnost shody. Další informace o jednotlivých možnostech dodržování shody naleznete v tématu pro konkrétní možnost. Možnost kompilátoru [/Permissive-](permissive-standards-conformance.md) implicitně nastavuje možnosti dodržování předpisů, které nejsou nastavené ve výchozím nastavení, do jejich vyhovujícího nastavení.

Jedná se o možnosti kompilátoru `/Zc`:

|Možnost|Chování|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|Povolit dynamické přidělování zarovnaných na úrovni C++ 17 (ve výchozím nastavení zapnuté C++ 17).|
|[Automatické\[-\]](zc-auto-deduce-variable-type.md)|Vyvynuťte nový standardní C++ význam pro `auto` (ve výchozím nastavení zapnutý).|
|[__cplusplus\[-\]](zc-cplusplus.md)|Povolit, aby makro **__cplusplus** nahlásilo podporované Standard (ve výchozím nastavení vypnuté).|
|[externConstexpr\[-\]](zc-externconstexpr.md)|Povolit vnější propojení pro proměnné `constexpr` (ve výchozím nastavení vypnuté).|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|Vynutila pravidla oboru standardní C++ `for` (ve výchozím nastavení zapnuté).|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|Povolit implicitní `noexcept` u požadovaných funkcí (ve výchozím nastavení zapnuté).|
|[vložené\[-\]](zc-inline-remove-unreferenced-comdat.md)|Odebrat neodkazovaná funkce nebo data, pokud je COMDAT nebo má pouze vnitřní vazbu (ve výchozím nastavení vypnuté).|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|Vynutilo C++ 17 s výjimkou pravidel (ve výchozím nastavení v C++ 17 a novějších).|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|Dočasný typ UDT se nebude navazovat na odkaz nekonstantní hodnoty lvalue (ve výchozím nastavení vypnutý).|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|Vynutil C++ standardní explicitní pravidla převodu typu (ve výchozím nastavení vypnuté).|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|Povolit funkce dealokace globálních velikostí C++ 14 (ve výchozím nastavení zapnuté)|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|Zakáže řetězcový literál pro `char*` nebo převod `wchar_t*` (ve výchozím nastavení vypnuté).|
|[Ternární\[-\]](zc-ternary.md)|Vynutil pravidla podmíněného operátoru u typů operandů (ve výchozím nastavení vypnuté).|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|Povolit místní statickou inicializaci bezpečnou pro přístup z více vláken (ve výchozím nastavení zapnuté).|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|Předpokládat, že `operator new` vyvolá chybu (ve výchozím nastavení vypnuté).|
|[trigraphs\[-\]](zc-trigraphs-trigraphs-substitution.md)|Povolit trigraphs (zastaralé, vypnuté ve výchozím nastavení).|
|[twoPhase](zc-twophase.md)|Použijte chování analýzy nevyhovujících šablon (ve výchozím nastavení je vyhovující).|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` je nativní typ, nikoli typedef (ve výchozím nastavení zapnuté).|

Další informace o problémech s kompatibilitou ve vizuálu C++najdete v tématu [nestandardní chování](../../cpp/nonstandard-behavior.md).

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
