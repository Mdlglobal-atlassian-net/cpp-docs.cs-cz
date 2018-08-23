---
title: __incgsbyte __incgsword, __incgsdword __incgsqword | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __incgsdword
- __incgsqword_cpp
- __incgsword_cpp
- __incgsword
- __incgsbyte
- __incgsbyte_cpp
- __incgsqword
- __incgsdword_cpp
dev_langs:
- C++
helpviewer_keywords:
- __incgsbyte intrinsic
- __incgsword intrinsic
- __incgsqword intrinsic
- __incgsdword intrinsic
ms.assetid: 06bfdf4f-7643-4fe0-8455-60ce3068073e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 74e1b74c95f143aac7a915b3f148a85da9c5a3d3
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42466118"
---
# <a name="incgsbyte-incgsword-incgsdword-incgsqword"></a>__incgsbyte __incgsword, __incgsdword, __incgsqword
**Specifické pro Microsoft**  
  
 Přidejte jej na hodnotu v paměti umístění určené posun vzhledem k začátku `GS` segmentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __incgsbyte(   
   unsigned long Offset   
);  
void __incgsword(   
   unsigned long Offset   
);  
void __incgsdword(   
   unsigned long Offset  
);  
void __incgsqword(   
   unsigned long Offset   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [in] `Offset`  
 Posun od začátku `GS`.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__incgsbyte`|x64|  
|`__incgsword`|x64|  
|`__incgsdword`|x64|  
|`__incgsqword`|x64|  
  
## <a name="remarks"></a>Poznámky  
 Tyto vnitřní objekty jsou dostupné jenom v režimu jádra a rutiny jsou dostupné jenom jako vnitřní funkce.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [__addgsbyte, \__addgsword, \__addgsdword, \__addgsqword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)   
 [__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)