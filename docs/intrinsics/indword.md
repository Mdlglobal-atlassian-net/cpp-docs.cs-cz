---
title: __indword | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __indword_cpp
- __indword
dev_langs:
- C++
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2dcfb321d526bb449335f87e7a83ba2a0aba7e60
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325536"
---
# <a name="indword"></a>__indword
**Konkrétní Microsoft**  
  
 Přečte jeden double aplikace word dat pomocí zadaný port `in` instrukcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned long __indword(  
   unsigned short Port  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `Port`  
 Port pro čtení z.  
  
## <a name="return-value"></a>Návratová hodnota  
 Slovo přečíst z portu.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`__indword`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)