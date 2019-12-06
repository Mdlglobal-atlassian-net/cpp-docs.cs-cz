---
title: Direktivy pragma a klíčové slovo __pragma
ms.date: 08/29/2019
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
ms.openlocfilehash: 6cfbcd325dc895719bad5dccc9c19bcda90cdaa0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858071"
---
# <a name="pragma-directives-and-the-__pragma-keyword"></a>Direktivy pragma a klíčové slovo __pragma

Direktivy pragma určují funkce kompilátoru specifické pro počítač nebo operační systém. Klíčové slovo **__pragma** , které je specifické pro kompilátor společnosti Microsoft, umožňuje kódovat direktivy pragma v rámci definice makra.

## <a name="syntax"></a>Syntaxe

> **#pragma** *řetězec tokenu*\
> **__pragma (** *token-String* **)**

## <a name="remarks"></a>Poznámky

Každá implementace jazyka C a C++ podporuje některé funkce, které jsou jedinečné pro daný hostitelský počítač nebo operační systém. Některé programy například musí mít přesnou kontrolu nad umístěním dat v paměti nebo určovat, jak některé funkce přijímají parametry. Direktivy **#pragma** nabízejí způsob, jakým každý kompilátor nabízí funkce specifické pro počítač a operační systém a přitom udržuje celkovou kompatibilitu s jazyky C a C++ .

Direktivy pragma jsou specifické pro počítač nebo operační systém podle definice a jsou obvykle odlišné pro každý kompilátor. Direktivy pragma lze použít v podmíněných direktivách, k poskytnutí nových funkcí preprocesoru nebo k poskytnutí informací určených k implementaci kompilátoru.

*Řetězec tokenu* je série znaků, které poskytují konkrétní instrukci a argumenty kompilátoru, pokud existují. Znak čísla ( **#** ) musí být první neprázdný znak na řádku, který obsahuje direktivu pragma. Prázdné znaky mohou oddělovat znaménko čísla a slovo "pragma". Po **#pragma**napište libovolný text, který Překladatel dokáže analyzovat jako tokeny předzpracování. Argument pro **#pragma** podléhá rozšíření makra.

Kompilátor vydá upozornění, když najde direktivu pragma, kterou nerozpozná, a pokračuje v kompilaci.

Kompilátory Microsoft C a C++ rozpoznají následující Pragma:

||||
|-|-|-|
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[vytvořena](../preprocessor/comment-c-cpp.md)|
|[component](../preprocessor/component.md)|[vyhovuje](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|
|[data_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|
|[slouží](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|
|[intrinsic](../preprocessor/intrinsic.md)|[smyčka](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|
|[starosti](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)|[omp](../preprocessor/omp.md)|
|[once](../preprocessor/once.md)|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|
|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|
|[region, endregion](../preprocessor/region-endregion.md)|[runtime_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|
|[setlocale](../preprocessor/setlocale.md)|[strict_gs_check](../preprocessor/strict-gs-check.md)|[spravovateln](../preprocessor/managed-unmanaged.md)|
|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|[warning](../preprocessor/warning.md)||

<sup>1</sup> podporuje se C++ jenom kompilátorem.

## <a name="pragmas-and-compiler-options"></a>Direktivy pragma a možnosti kompilátoru

Některé prvky pragma poskytují stejné funkce, jaké poskytují možnosti kompilátoru. Pokud se pragma vyskytne ve zdrojovém kódu, potlačí chování určené jinou možností kompilátoru. Pokud jste například zadali [/ZP8](../build/reference/zp-struct-member-alignment.md), můžete přepsat toto nastavení kompilátoru pro konkrétní oddíly kódu pomocí [balíčku](../preprocessor/pack.md):

```cmd
cl /Zp8 some_file.cpp
```

```cpp
// some_file.cpp - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8 again
// ...
```

## <a name="the-__pragma-keyword"></a>Klíčové slovo __pragma ()

Kompilátor také podporuje klíčové slovo **__pragma** specifické pro společnost Microsoft, které má stejné funkce jako direktiva **#pragma** . Rozdíl je, klíčové slovo **__pragma** je v definici makra použitelné jako vložené. Direktiva **#pragma** není použitelná v definici makra, protože kompilátor interpretuje znak čísla znaménka (#) v direktivě jako [operátor převodu (#)](../preprocessor/stringizing-operator-hash.md).

Následující příklad kódu ukazuje, jak lze použít klíčové slovo **__pragma** v makru. Tento kód je výňatkem z hlavičky mfcdual.h ve vzorku ACDUAL v "Vzorky podpory kompilátoru COM":

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

## <a name="see-also"></a>Viz také:

\ reference preprocesoru C [C++ ](../preprocessor/c-cpp-preprocessor-reference.md)
[Direktivy pragma jazyka C](../c-language/c-pragmas.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
