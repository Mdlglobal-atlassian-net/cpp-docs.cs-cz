---
title: __addgsbyte __addgsword, __addgsdword __addgsqword | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __addgsdword
- __addgsqword
- __addgsword_cpp
- __addgsword
- __addgsbyte_cpp
- __addgsqword_cpp
- __addgsbyte
- __addgsdword_cpp
dev_langs:
- C++
helpviewer_keywords:
- __addgsword intrinsic
- __addgsqword intrinsic
- __addgsdword intrinsic
- __addgsbyte intrinsic
ms.assetid: 4fa03e69-d849-49ed-ba37-1d3aa23c2a21
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd5341dc4d47740410df01feadbd9e6aa3926a23
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721382"
---
# <a name="addgsbyte-addgsword-addgsdword-addgsqword"></a>__addgsbyte, __addgsword, __addgsdword, __addgsqword
**Specifické pro Microsoft**  
  
 Přidat hodnotu do umístění v paměti určený posun vzhledem k začátku `GS` segmentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __addgsbyte(   
   unsigned long Offset,   
   unsigned char Data   
);  
void __addgsword(   
   unsigned long Offset,   
   unsigned short Data   
);  
void __addgsdword(   
   unsigned long Offset,   
   unsigned long Data   
);  
void __addgsqword(   
   unsigned long Offset,   
   unsigned __int64 Data   
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Posun*<br/>
[in] Posun od začátku `GS`.  
  
*Data*<br/>
[in] Hodnota k přidání do umístění v paměti.  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní|Architektura|  
|---------------|------------------|  
|`__addgsbyte`|x64|  
|`__addgsword`|x64|  
|`__addgsdword`|x64|  
|`__addgsqword`|x64|  
  
## <a name="remarks"></a>Poznámky  
 Tyto vnitřní objekty jsou k dispozici v pouze v režimu jádra a tyto rutiny jsou dostupné jenom jako vnitřní funkce.  
  
**Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [__incgsbyte, \__incgsword, \__incgsdword, \__incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)   
 [__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)   
 [__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)