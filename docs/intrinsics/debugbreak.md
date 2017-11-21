---
title: "__debugbreak – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- __debugbreak_cpp
- __debugbreak
dev_langs: C++
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7d067798f981e86edea1b83557925c41e8f8a3d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="debugbreak"></a>__debugbreak
**Konkrétní Microsoft**  
  
 Umístí do kódu zarážku, kde uživatel bude vyzván ke spuštění ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __debugbreak();  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|Záhlaví|  
|---------------|------------------|------------|  
|`__debugbreak`|x86 ARM,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|\<intrin.h >|  
  
## <a name="remarks"></a>Poznámky  
 `__debugbreak` Kompilátoru vnitřní, podobně jako [debugbreak –](http://msdn.microsoft.com/library/windows/desktop/ms679297.aspx), je portable Win32 způsob, jak způsobit zarážky.  
  
> [!NOTE]
>  Při kompilaci s **/CLR**, funkce obsahující `__debugbreak` se zkompiluje do MSIL. Klíčové slovo `asm int 3` zajistí zkompilování funkce jako nativní. Další informace najdete v tématu [__asm](../assembler/inline/asm.md).  
  
 Příklad:  
  
```  
main() {  
   __debugbreak();  
}  
```  
  
 je podobné kódu:  
  
```  
main() {  
   __asm {  
      int 3  
   }  
}  
```  
  
 na počítači architektury x86.  
  
 Tato rutina je k dispozici pouze jako vnitřní objekt.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)