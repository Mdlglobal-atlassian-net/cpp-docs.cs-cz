---
title: .MODEL
ms.date: 11/05/2019
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: 92f14a352e5c177d767232eed36a7e705fd155ce
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317627"
---
# <a name="model-32-bit-masm"></a>. MODEL (32-bit MASM)

Inicializuje model paměti programu. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> **. Model** *Memory – model* ⟦ __,__ *Language-Type*⟧ ⟦ __,__ *Stack-Option*⟧

### <a name="parameters"></a>Parametry

\ *modelu paměti*
Povinný parametr, který určuje velikost kódu a datových ukazatelů.

\ *typu jazyka*
Volitelný parametr, který nastaví konvence volání a pojmenování pro procedury a veřejné symboly.

\ *možností zásobníku*
Volitelný parametr.

*možnost Stack-* není použita, pokud je *model paměti* **plochý**.

Zadání **NEARSTACK** seskupí segment zásobníku do jednoho fyzického segmentu (**DGROUP**) spolu s daty. Předpokládá se, že registr segmentu zásobníku (**SS**) odpovídá stejné adrese jako u registru datových segmentů (**DS**). **FARSTACK** neseskupuje zásobník pomocí **DGROUP**; To znamená, že **SS** nerovná **DS**.

## <a name="remarks"></a>Poznámky

**. MODEL** se nepoužívá v [MASM pro x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

V následující tabulce jsou uvedeny možné hodnoty pro každý parametr při cílení na 16bitové a 32-bitové platformy:

|Parametr|32 – bitové hodnoty|16bitové hodnoty (podpora pro starší 16bitový vývoj)|
|---------------|--------------------|----------------------------------------------------------------|
|*model paměti*|**KOPIE**|**malá**, **malá**, **kompaktní**, **střední**, **Velká**, **velmi**velká, **plochá**|
|*typ jazyka*|**C**, **STDCALL**|**C**, **Basic**, **FORTRAN**, **Pascal**, **syscall**, **STDCALL**|
|*zásobník – možnost*|Nepoužívá se|**NEARSTACK**, **FARSTACK**|

## <a name="code"></a>Kód

Ukázky týkající se MASM najdete v ukázkách kompilátoru z [vizuálních C++ ukázek a v související dokumentaci k sadě Visual Studio 2010](https://go.microsoft.com/fwlink/p/?linkid=178749).

Následující příklad ukazuje použití direktivy `.MODEL`.

## <a name="example"></a>Příklad

```asm
; file simple.asm
; For x86 (32-bit), assemble with debug information:
;   ml -c -Zi simple.asm
; For x64 (64-bit), assemble with debug information:
;   ml64 -c -DX64 -Zi simple.asm
;
; In this sample, the 'X64' define excludes source not used
;  when targeting the x64 architecture

ifndef X64
.686p
.XMM
.model flat, C
endif

.data
; user data

.code
; user code

fxn PROC public
  xor eax, eax ; zero function return value
  ret
fxn ENDP

end
```

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
