---
title: __popcnt16 __popcnt, __popcnt64 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34063223addb433a94c877ad56cf410f189e6681
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724731"
---
# <a name="popcnt16-popcnt-popcnt64"></a>__popcnt16 __popcnt, __popcnt64

**Specifické pro Microsoft**  
  
 Spočítá počet jednu službu bits (počet naplnění) v 16, 32 nebo 64bajtové číslo bez znaménka.  
  
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
*value*<br/>
[in] 16 - 32 a 64-bit znaménka, pro kterou chceme, aby počet naplnění.  
  
## <a name="return-value"></a>Návratová hodnota  
 Počet bitů, jeden v `value` parametru.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__popcnt16`|Pokročilé bitové manipulace|  
|`__popcnt`|Pokročilé bitové manipulace|  
|`__popcnt64`|Pokročilé zpracování Bit v 64bitovém režimu.|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto vnitřních objektů vygeneruje `popcnt` instrukce.  Velikost hodnoty, který `popcnt` instrukce vrátí je stejná jako velikost svého argumentu.  V 32bitovém režimu nejsou žádné 64-bit pro obecné účely registry, tedy ne 64-bit `popcnt`.  
  
 K určení hardwarovou podporu `popcnt` instrukce, volání `__cpuid` vnitřní s `InfoType=0x00000001` a zkontrolujte bit 23 `CPUInfo[2] (ECX)`. Tato verze je 1, pokud podporované instrukce a 0 jinak. Pokud jste spustili kód, který používá tuto vnitřní hardware, který není podporován `popcnt` instrukce, výsledky nepředvídatelné.  
  
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
  
**Specifické pro END Microsoft**  

Copyright 2007 pokročilé zařízení Micro, Inc. Všechna práva vyhrazena. Reprodukovat se svolením rozšířené Micro zařízení, Inc.  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)
