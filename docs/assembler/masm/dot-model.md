---
title: . MODEL | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .MODEL
dev_langs: C++
helpviewer_keywords: .MODEL directive
ms.assetid: 057f00df-1515-4c55-852a-d936c8a34b53
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d4ea26a75d37e264344aaacfa660e6d66dc8d5e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="model"></a>.MODEL
Inicializuje modelu paměti programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.MODEL memorymodel [[, langtype]] [[, stackoption]]  
```  
  
#### <a name="parameters"></a>Parametry  
 `memorymodel`  
 Povinný parametr, který určuje velikost ukazatelů kód a data.  
  
 `langtype`  
 Volitelný parametr, který nastaví konvence volání a pojmenování postupy a veřejné symboly pro.  
  
 `stackoption`  
 Volitelný parametr.  
  
 `stackoption`se nepoužívá, pokud `memorymodel` je `FLAT`.  
  
 Určení `NEARSTACK` skupiny zásobníku segment do jednoho fyzického segmentu (`DGROUP`) spolu s daty. Registr segmentu zásobníku (`SS`) se předpokládá, že pro stejnou adresu jako registr segmentu dat (`DS`). `FARSTACK`neseskupuje zásobník s `DGROUP`; proto `SS` se nerovná `DS`.  
  
## <a name="remarks"></a>Poznámky  
 .`MODEL` nepoužívá se v [MASM pro x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
 Následující tabulka uvádí možné hodnoty pro každý parametr, pokud je cílem 16bitové a 32bitové verze platformy:  
  
|Parametr|32bitové hodnoty|16bitové hodnoty (podpora pro starší vývoj 16 bitů)|  
|---------------|--------------------|----------------------------------------------------------------|  
|`memorymodel`|`FLAT`|`TINY`, `SMALL`, `COMPACT`, `MEDIUM`, `LARGE`, `HUGE`, `FLAT`|  
|`langtype`|`C`, `STDCALL`|`C`, `BASIC`, `FORTRAN`, `PASCAL`, `SYSCALL`, `STDCALL`|  
|`stackoption`|Nepoužívá se|`NEARSTACK`, `FARSTACK`|  
  
## <a name="code"></a>Kód  
 Související MASM ukázky, stáhněte si ukázky kompilátoru z [Visual C++ – ukázky a související dokumentace pro Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=178749).  
  
 Následující příklad ukazuje použití `.MODEL` – direktiva.  
  
## <a name="example"></a>Příklad  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)   
 [Visual C++ – ukázky a související dokumentace pro Visual Studio 2010](http://go.microsoft.com/fwlink/?LinkID=178749)