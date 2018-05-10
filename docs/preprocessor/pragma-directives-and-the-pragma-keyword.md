---
title: Direktivy pragma a klíčové slovo __Pragma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '#pragma'
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b20a476e1701f58782b97f986ee6c3d4b310b566
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="pragma-directives-and-the-pragma-keyword"></a>Direktivy Pragma a klíčové slovo __Pragma
Direktivy pragma zadejte počítače nebo operačního – funkce specifické pro kompilátoru. `__pragma` – Klíčové slovo, která je specifická pro kompilátor Microsoft, vám umožňuje kód direktivy pragma v definicích maker.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      #pragma token-string  
__pragma(token-string)  
```  
  
## <a name="remarks"></a>Poznámky  
 Každý implementace C a C++ podporuje některé funkce, které jsou jedinečné pro jeho hostitelský počítač nebo operačního systému. Některé programy, například musí uplatňovat přesné řízení přes paměťové oblasti, kde je umístěna dat nebo k řízení způsobu určité funkce přijímat parametry. `#pragma` Direktivy nabízí způsob, jak každý kompilátoru nabízet počítače a operačního systému konkrétní funkce a přitom zachovat celkové kompatibilitu s jazyky C a C++.  
  
 Direktivy jsou počítače nebo operačního systému specifické podle definice a se obvykle liší u každé kompilátoru. Direktivy lze v podmíněné příkazy, nabízí nové funkce preprocesoru nebo poskytovat informace definované implementací kompilátoru.  
  
 `token-string` Je řady znaků, který dává pokyn konkrétní kompilátoru a argumenty, pokud existuje. Znaménko čísla (**#**) musí být první znak prázdné znaky na řádek, který obsahuje – Direktiva pragma; prázdné znaky můžete oddělit znaménko čísla a je slovo "– Direktiva pragma". Následující `#pragma`, zápis libovolný text, který překladač můžete analyzovat jako předzpracování tokeny. Argument `#pragma` podléhá makro rozšíření.  
  
 Pokud kompilátor najde – Direktiva pragma, který nelze rozpoznat, vydá upozornění a pokračuje v kompilaci.  
  
 Kompilátory jazyka Microsoft C a C++ rozpoznat následující direktivy:  
  
||||  
|-|-|-|  
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|  
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[Komentář](../preprocessor/comment-c-cpp.md)|  
|[component](../preprocessor/component.md)|[v souladu s](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|  
|[data_seg](../preprocessor/data-seg.md)|[deprecated](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|  
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|  
|[Funkce](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|  
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|  
|[intrinsic](../preprocessor/intrinsic.md)|[smyčky](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|  
|[Spravované](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)||  
|[omp](../preprocessor/omp.md)|[once](../preprocessor/once.md)||  
|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|[pointers_to_members –](../preprocessor/pointers-to-members.md) <sup>1</sup>|  
|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|[region, endregion](../preprocessor/region-endregion.md)|  
|[runtime_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|[setlocale](../preprocessor/setlocale.md)|  
|[strict_gs_check](../preprocessor/strict-gs-check.md)|[nespravované](../preprocessor/managed-unmanaged.md)|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|  
|[warning](../preprocessor/warning.md)|||  
  
 1. Podporuje pouze C++ compiler.  
  
## <a name="pragmas-and-compiler-options"></a>Direktivy pragma a možnosti kompilátoru  
 Některé direktivy poskytovat stejné funkce jako – možnosti kompilátoru. Pragma vyskytne ve zdrojovém kódu, přepíše nastavení chování kompilátoru možnosti. Například pokud jste zadali [/Zp8](../build/reference/zp-struct-member-alignment.md), můžete přepsat toto nastavení kompilátoru pro určité části kódu s [pack](../preprocessor/pack.md):  
  
```  
cl /Zp8 ...  
  
<file> - packing is 8  
// ...  
#pragma pack(push, 1) - packing is now 1  
// ...  
#pragma pack(pop) - packing is 8  
</file>  
```  
  
## <a name="the-pragma-keyword"></a>__Pragma() klíčové slovo  
 **Microsoft konkrétní**  
  
 Kompilátor podporuje také `__pragma` – klíčové slovo, který má stejné funkce jako `#pragma` – direktiva, ale mohou být použité vložené v definici makra. `#pragma` – Direktiva nelze použít v definici makra, protože kompilátor interpretuje v direktivě jako číslo přihlašovací znak (#) [operátor nastavení velikosti řetězce (#)](../preprocessor/stringizing-operator-hash.md).  
  
 Následující příklad kódu ukazuje, jak `__pragma` – klíčové slovo lze použít v makru. Tento kód je převzat webových stránek z hlavičky mfcdual.h v acdual – ukázka v "Ukázky podpory modelu COM kompilátoru":  
  
```  
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
  
 **Ukončení konkrétní Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [C/C++ – referenční dokumentace preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)   
 [Pragmas jazyka C](../c-language/c-pragmas.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)