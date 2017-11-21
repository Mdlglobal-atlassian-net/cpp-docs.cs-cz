---
title: "Načtení všech importů pro knihovnu DLL s odloženým načtením | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: __HrLoadAllImportsForDll linker option
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 842b23afe7aec4d66eaf0787976d8e0c5d9a7320
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="loading-all-imports-for-a-delay-loaded-dll"></a>Načtení všech importů pro knihovnu DLL se zpožděným načtením
**__HrLoadAllImportsForDll** linkeru načtení všech importů z knihovny DLL, která byla zadána s informacemi o funkci, která je definována v delayhlp.cpp, [/delayload](../../build/reference/delayload-delay-load-import.md) – možnost linkeru.  
  
 Načtení všech importů umožňuje vložit zpracování chyb v jednom místě ve vašem kódu a není nutné používat kolem skutečné volání importy zpracování výjimek. Zabraňuje také situace, kdy aplikace nejsou částečně procesem v důsledku kód pomocného objektu nedaří se načíst importu.  
  
 Volání metody **__HrLoadAllImportsForDll** nezmění chování háky a Chyba zpracování; najdete v části [zpracování chyb a oznámení](../../build/reference/error-handling-and-notification.md) Další informace.  
  
 Předaný název DLL **__HrLoadAllImportsForDll** bude porovnána s názvem uložený v knihovně DLL a je malá a velká písmena.  
  
 Následující příklad ukazuje způsob volání **__HrLoadAllImportsForDll**:  
  
```  
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {  
   printf ( "failed on snap load, exiting\n" );  
   exit(2);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora linkeru pro knihovny DLL s odloženým načtením](../../build/reference/linker-support-for-delay-loaded-dlls.md)