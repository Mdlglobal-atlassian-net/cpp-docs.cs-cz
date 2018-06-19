---
title: __writemsr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writemsr
dev_langs:
- C++
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 76131f4d07dec1713c80b4cd4f98f729b9ecf07b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323521"
---
# <a name="writemsr"></a>__writemsr
**Konkrétní Microsoft**  
  
 Generuje zápis modelu konkrétní zaregistrovat (`wrmsr`) instrukcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __writemsr(   
   unsigned long Register,   
   unsigned __int64 Value   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `Register`  
 Konkrétní registrace modelu.  
  
 [v] `Value`  
 Hodnota pro zápis  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__writemsr`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tuto funkci lze použít pouze v režimu jádra a tato rutina je pouze k dispozici jako vnitřní.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)