---
title: __outbytestring | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outbytestring
dev_langs:
- C++
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55dc6492faea101df40c2901ced24321822f36e8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465484"
---
# <a name="outbytestring"></a>__outbytestring
**Specifické pro Microsoft**  
  
 Generuje `rep outsb` instrukce, která odesílá první `Count` bajtů dat, na které odkazuje `Buffer` na port určený `Port`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __outbytestring(   
   unsigned short Port,   
   unsigned char* Buffer,   
   unsigned long Count   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Port`  
 Port pro odesílání dat na.  
  
 [in] `Buffer`  
 Data, která mají být odeslány zadaný port.  
  
 [in] `Count`  
 Počet bajtů dat k odeslání.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__outbytestring`|x86, x64|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)