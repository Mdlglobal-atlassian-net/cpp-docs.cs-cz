---
title: __lzcnt16, __lzcnt, __lzcnt64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __lzcnt64
- __lzcnt16
- __lzcnt
dev_langs: C++
helpviewer_keywords:
- __lzcnt intrinsic
- lzcnt instruction
- lzcnt16 intrinsic
- lzcnt intrinsic
- __lzcnt16 intrinsic
- lzcnt64 intrinsic
- __lzcnt64 intrinsic
ms.assetid: 412113e7-052e-46e5-8bfa-d5ad72abc10e
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5fcd699cd137e6adbb2cf08f5852970d009f745
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="lzcnt16-lzcnt-lzcnt64"></a>__lzcnt16, __lzcnt, __lzcnt64
**Konkrétní Microsoft**  
  
 Počty počet úvodní nuly v 16 – 32- a 64 bajtů celé číslo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned short __lzcnt16(  
   unsigned short value  
);  
unsigned int __lzcnt(  
   unsigned int value  
);  
unsigned __int64 __lzcnt64(  
   unsigned __int64 value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`value`  
 16 – 32- a celé číslo bez znaménka 64-bit kontrolovala úvodními nulami.  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet mezer na začátku nulový počet bitů `value` parametr. Pokud `value` rovná nule, je vrácenou hodnotu velikost vstupní operand (16, 32 nebo 64). Pokud bit významné `value` je 1, návratovou hodnotou je nulová.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__lzcnt16`|AMD: Pokročilé bitové manipulace (ABM)<br /><br /> Intel: Haswell|  
|`__lzcnt`|AMD: Pokročilé bitové manipulace (ABM)<br /><br /> Intel: Haswell|  
|`__lzcnt64`|AMD: Rozšířené Bit manipulaci (ABM) v režimu 64-bit.<br /><br /> Intel: Haswell|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Každý z těchto vnitřní funkce generuje `lzcnt` instrukcí.  Velikost hodnoty, `lzcnt` instrukce vrátí je stejná jako velikost jeho argumentem.  V 32bitovém režimu nejsou žádné 64-bit pro obecné účely registrů, proto žádné 64-bit `lzcnt`.  
  
 K určení podporu hardwaru pro `lzcnt` instrukce volání `__cpuid` vnitřní s `InfoType=0x80000001` a zkontrolovat bitu 5 `CPUInfo[2] (ECX)`. Tato verze bude 1, pokud je podporováno pokyn a 0 jinak. Pokud jste spustili kód, který používá tento vnitřní hardware, který nepodporuje `lzcnt` instrukce, nepředvídatelné výsledky.  
  
 Na procesory Intel, které nepodporují `lzcnt` instrukce, instrukce bajtů kódování se spustí jako `bsr` (bit zpětného kontroly). Pokud vám záleží hlavně přenositelnost kódu, zvažte použití `_BitScanReverse` vnitřní místo. Další informace najdete v tématu [_BitScanReverse _BitScanReverse64](../intrinsics/bitscanreverse-bitscanreverse64.md).  
  
## <a name="example"></a>Příklad  
  
```  
// Compile this test with: /EHsc  
#include <iostream>   
#include <intrin.h>   
using namespace std;   
  
int main()   
{  
  unsigned short us[3] = {0, 0xFF, 0xFFFF};  
  unsigned short usr;  
  unsigned int   ui[4] = {0, 0xFF, 0xFFFF, 0xFFFFFFFF};  
  unsigned int   uir;  
  
  for (int i=0; i<3; i++) {  
    usr = __lzcnt16(us[i]);  
    cout << "__lzcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __lzcnt(ui[i]);  
    cout << "__lzcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
```Output  
__lzcnt16(0x0) = 16  
__lzcnt16(0xff) = 8  
__lzcnt16(0xffff) = 0  
__lzcnt(0x0) = 32  
__lzcnt(0xff) = 24  
__lzcnt(0xffff) = 16  
__lzcnt(0xffffffff) = 0  
```  
  
**Konkrétní Microsoft END**  
 Části tohoto obsahu jsou Copyright 2007 Advanced Micro zařízení, Inc. Všechna práva vyhrazena. Opakuje se svolením Advanced Micro zařízení, Inc.  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)