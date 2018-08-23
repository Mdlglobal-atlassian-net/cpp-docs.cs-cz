---
title: __outword | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outword
dev_langs:
- C++
helpviewer_keywords:
- __outword intrinsic
- out instruction
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d118c26e79a462723f87e76672b2d9b9c1a76cb2
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465759"
---
# <a name="outword"></a>__outword
**Specifické pro Microsoft**  
  
 Generuje `out` instrukce, která odesílá slovo `Data` portu vstupně-výstupní operace určené `Port`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __outword(   
   unsigned short Port,   
   unsigned short Data   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Port`  
 Port pro odesílání dat na.  
  
 [in] `Data`  
 Data, která má být odeslána.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__outword`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)