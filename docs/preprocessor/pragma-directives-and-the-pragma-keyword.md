---
title: Direktivy Pragma a klíčové slovo __Pragma
ms.date: 11/04/2016
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
ms.openlocfilehash: b6c2ff579c6fafa78cbfd0a2879a71fca2bfaa01
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027438"
---
# <a name="pragma-directives-and-the-pragma-keyword"></a>Direktivy Pragma a klíčové slovo __Pragma

Direktivy pragma určují funkce kompilátoru nebo provozní specifické pro počítač. **__Pragma** – klíčové slovo, které jsou specifické pro kompilátor společnosti Microsoft, umožňuje kódovat direktivy pragma v rámci definice maker.

## <a name="syntax"></a>Syntaxe

```
#pragma token-string
__pragma(token-string)
```

## <a name="remarks"></a>Poznámky

Každá implementace jazyka C a C++ podporuje některé funkce, které jsou jedinečné pro daný hostitelský počítač nebo operační systém. Některé programy musí například vykonávat přesnou kontrolu paměťových oblastí dat nebo způsob, jak některé funkce přijímají parametry. **#Pragma** direktivy představují způsob, jakým každý kompilátor nabízí funkce závislé na počítače a operačního systému při zachování celkové kompatibility s jazyky C a C++.

Direktivy pragma jsou nebo operačního systému – specifické pro počítač podle definice a obvykle se různí pro každý kompilátor. Direktivy pragma je možné podmíněné příkazy a poskytnout tak preprocesoru nové funkce, nebo poskytnout informace definované implementací kompilátoru.

`token-string` Je posloupnost znaků, které poskytuje specifickému kompilátoru instrukce a argumenty, pokud existuje. Znak čísla (**#**) musí být první-neprázdný znak na řádku, který obsahuje pragma; mezerové znaky můžete oddělit znak čísla a slovo "pragma". Následující **#pragma**, napište libovolný text, který dokáže překladač analyzovat jako tokeny předzpracování. Argument **#pragma** se řídí podle rozšíření makra.

Pokud kompilátor najde pragma, které nebylo rozpoznáno, upozorní a pokračuje v kompilaci.

Kompilátory Microsoft C a C++ rozpoznají následující Pragma:

||||
|-|-|-|
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[comment](../preprocessor/comment-c-cpp.md)|
|[komponenta](../preprocessor/component.md)|[v souladu s](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|
|[data_seg](../preprocessor/data-seg.md)|[zastaralé](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|
|[ – funkce](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|
|[ – vnitřní funkce](../preprocessor/intrinsic.md)|[smyčka](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|
|[spravovaná](../preprocessor/managed-unmanaged.md)|[ – zpráva](../preprocessor/message.md)||
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||
|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|
|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|[region, endregion](../preprocessor/region-endregion.md)|
|[runtime_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|
|[strict_gs_check](../preprocessor/strict-gs-check.md)|[nespravovaná](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|
|[upozornění](../preprocessor/warning.md)|||

<sup>1</sup> podporovány pouze v kompilátoru jazyka C++.

## <a name="pragmas-and-compiler-options"></a>Direktivy pragma a možnosti kompilátoru

Některé prvky pragma poskytují stejné funkce jako možnosti kompilátoru. Pokud se pragma vyskytne ve zdrojovém kódu, potlačí chování určené jinou možností kompilátoru. Například, pokud jste zadali [/zp8](../build/reference/zp-struct-member-alignment.md), můžete přepsat toto nastavení kompilátoru pro určité části kódu s [pack](../preprocessor/pack.md):

```
cl /Zp8 ...

<file> - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8
</file>
```

## <a name="the-pragma-keyword"></a>Klíčové slovo __pragma()

**Specifické pro Microsoft**

Kompilátor podporuje také **__pragma** – klíčové slovo, který má stejné funkce jako **#pragma** směrnice, ale lze používat vložené v definici makra. **#Pragma** směrnice nelze použít v definici makra, protože kompilátor interpretuje znaménko pro číslo ('#') v direktivě [operátor převodu na řetězec (#)](../preprocessor/stringizing-operator-hash.md).

Následující příklad kódu ukazuje, jak **__pragma** – klíčové slovo lze použít v makru. Tento kód je výňatkem z hlavičky mfcdual.h ve vzorku acdual v "Vzorky podpory kompilátoru COM":

```cpp
#define CATCH_ALL_DUAL \
CATCH(COleException, e) \
{ \
_hr = e->m_sc; \
} \
AND_CATCH_ALL(e) \
{ \
__pragma(warning(push)) \
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \
AFX_MANAGE_STATE(pThis->m_pModuleState); \
__pragma(warning(pop)) \
_hr = DualHandleException(_riidSource, e); \
} \
END_CATCH_ALL \
return _hr; \
```

**Specifické pro end Microsoft**

## <a name="see-also"></a>Viz také:

[C/C++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
[Pragmas jazyka C](../c-language/c-pragmas.md)<br/>
[klíčová slova](../cpp/keywords-cpp.md)