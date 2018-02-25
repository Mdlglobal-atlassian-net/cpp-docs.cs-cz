---
title: __popcnt16, __popcnt, __popcnt64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- __popcnt64
- __popcnt
- __popcnt16
dev_langs:
- C++
helpviewer_keywords:
- popcnt instruction
- __popcnt16
- __popcnt64
- __popcnt
ms.assetid: e525b236-adc8-42df-9b9b-8b7d8c245d3b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce622f6283036dc3bde24f526da4c5256474ce00
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="popcnt16-popcnt-popcnt64"></a>__popcnt16, __popcnt, __popcnt64
**Microsoft Specific**  
  
 Spočítá počet jeden bitů (počet naplnění) 16 – 32- a 64 bajtů celé číslo bez znaménka.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned short __popcnt16(  
   unsigned short value  
);  
unsigned int __popcnt(  
   unsigned int value  
);  
unsigned __int64 __popcnt64(  
   unsigned __int64 value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `value`  
 16 –, 32- nebo 64bitové celé číslo bez znaménka pro kterou chceme počet naplnění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet jeden bitů `value` parametr.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__popcnt16`|Pokročilé bitové manipulace|  
|`__popcnt`|Pokročilé bitové manipulace|  
|`__popcnt64`|Pokročilé bitové manipulace v režimu 64-bit.|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Každý z těchto vnitřní funkce generuje `popcnt` instrukcí.  Velikost hodnoty, `popcnt` instrukce vrátí je stejná jako velikost jeho argumentem.  V 32bitovém režimu nejsou žádné 64-bit pro obecné účely registrů, proto žádné 64-bit `popcnt`.  
  
 K určení podporu hardwaru pro `popcnt` instrukce, volání `__cpuid` vnitřní s `InfoType=0x00000001` a zkontrolujte bit 23 `CPUInfo[2] (ECX)`. Tato verze je 1, pokud je podporovaná pokyn a 0 jinak. Pokud jste spustili kód, který používá tento vnitřní hardware, který nepodporuje `popcnt` instrukce, nepředvídatelné výsledky.  
  
## <a name="example"></a>Příklad  
  
```  
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
    usr = __popcnt16(us[i]);  
    cout << "__popcnt16(0x" << hex << us[i] << ") = " << dec << usr << endl;  
  }  
  
  for (int i=0; i<4; i++) {  
    uir = __popcnt(ui[i]);  
    cout << "__popcnt(0x" << hex << ui[i] << ") = " << dec << uir << endl;  
  }  
}  
  
```  
  
```Output  
__popcnt16(0x0) = 0  
__popcnt16(0xff) = 8  
__popcnt16(0xffff) = 16  
__popcnt(0x0) = 0  
__popcnt(0xff) = 8  
__popcnt(0xffff) = 16  
__popcnt(0xffffffff) = 32  
```  
  
**Konkrétní Microsoft END**  
 Copyright 2007 pokročilé Micro zařízení, Inc. Všechna práva vyhrazena. Opakuje se svolením Advanced Micro zařízení, Inc.  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)
