---
title: .MODEL
ms.date: 08/30/2018
f1_keywords:
- .MODEL
helpviewer_keywords:
- .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
ms.openlocfilehash: 5c7d5a1cfe16ef3cb1d79617133cd1ceccdfb78c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633506"
---
# <a name="model"></a>.MODEL

Inicializuje model paměti programu.

## <a name="syntax"></a>Syntaxe

> . MODEL memorymodel [[, langtype]] [[, stackoption]]

### <a name="parameters"></a>Parametry

*memorymodel*<br/>
Povinný parametr, který určuje velikost ukazatele na kód a data.

*langtype*<br/>
Volitelný parametr, který nastaví konvence pojmenování a volání procedury a veřejných symbolů.

*stackoption*<br/>
Volitelný parametr.

*stackoption* nepoužívá, pokud *memorymodel* je `FLAT`.

Určení `NEARSTACK` seskupí segmentu zásobníku do jednoho fyzického segmentu (`DGROUP`) spolu s daty. Registr segmentu zásobníku (`SS`) se předpokládá, že obsahovat stejné adrese jako registr segmentu dat (`DS`). `FARSTACK` neseskupuje do zásobníku s `DGROUP`; proto `SS` nerovná `DS`.

## <a name="remarks"></a>Poznámky

.`MODEL` není použit v [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

Následující tabulka uvádí možné hodnoty pro každý parametr při cílení na platformy 16bitová a 32bitová verze:

|Parametr|32bitové hodnoty|16bitové hodnoty (podpora pro vývoj starší 16 bitů)|
|---------------|--------------------|----------------------------------------------------------------|
|*memorymodel*|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|
|*langtype*|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|
|*stackoption*|Nepoužívá se|`NEARSTACK`, `FARSTACK`|

## <a name="code"></a>Kód

MASM související ukázky, stáhněte si ukázky kompilátoru z [Visual C++ – ukázky MFC a související dokumentaci pro sadu Visual Studio 2010](http://go.microsoft.com/fwlink/p/?linkid=178749).

Následující příklad ukazuje použití `.MODEL` směrnice.

## <a name="example"></a>Příklad

```asm
; file simple.asm
; For x86 (32-bit), assemble with debug information:
;   ml -c -Zi simple.asm
; For x64 (64-bit), assemble with debug information:
;   ml64 -c -DX64 -Zi simple.asm
;
; In this sample, the 'X64' define excludes source not used
;  when targeting the x64 architecture

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

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>

