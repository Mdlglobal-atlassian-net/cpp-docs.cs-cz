---
title: __stosw | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __stosw
dev_langs:
- C++
helpviewer_keywords:
- stosw instruction
- __stosw intrinsic
- rep stosw instruction
ms.assetid: 7620fd1d-dba5-40e3-8e07-01aa68895133
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a9f73b401d953c026c60d504fbb016838720b7c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329342"
---
# <a name="stosw"></a>__stosw
**Konkrétní Microsoft**  
  
 Generuje řetězcovou instrukci úložiště (`rep stosw`).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stosw(   
   unsigned short* Dest,   
   unsigned short Data,   
   size_t Count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `Dest`  
 Cíl operace.  
  
 [v] `Data`  
 Data, která k ukládání.  
  
 [v] `Count`  
 Délka bloku slova pro zápis.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__stosw`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Výsledkem je, že slovo `Data` jsou zapsána do bloku `Count` slova v `Dest` řetězec.  
  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
## <a name="example"></a>Příklad  
  
```  
// stosw.c  
// processor: x86, x64  
#include <stdio.h>  
#include <intrin.h>  
  
#pragma intrinsic(__stosw)  
  
int main()  
{  
    unsigned short val = 128;  
    unsigned short a[100];  
    memset(a, 0, sizeof(a));  
    __stosw(a+10, val, 2);  
    printf_s("%u %u %u %u", a[9], a[10], a[11], a[12]);     
}  
```  
  
```Output  
0 128 128 0  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)