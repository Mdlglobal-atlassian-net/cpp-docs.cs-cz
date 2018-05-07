---
title: C3345 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3345
dev_langs:
- C++
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3e6b3a021d9c747e4ec30278d8a22bde899cb39a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3345"></a>C3345 chyby kompilátoru
"identifikátor": Neplatný identifikátor pro název modulu  
  
 *Identifikátor* pro modul obsahuje jeden nebo více znaků, nemůže být přijata. Identifikátor je platný, pokud první znak podtržítko abecedně, nebo vysoké znak ANSI (0X80VYPNUTO) a všechny následné znak je alfanumerické znaky, podtržítka nebo vysokou znak ANSI.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že *identifikátor* neobsahuje prázdné nebo jiné nepřijatelné znaků.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu způsobí chybová zpráva C3345, protože `name` parametr `module` atribut obsahuje prázdné pole.  
  
```  
// cpp_attr_name_module.cpp  
// compile with: /LD /link /OPT:NOREF  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlwin.h>  
#include <atltypes.h>  
#include <atlctl.h>  
#include <atlhost.h>  
#include <atlplus.h>  
  
// C3345 expected  
[module(dll, name="My Library", version="1.2", helpfile="MyHelpFile")]   
// Try the following line instead  
//[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]   
// Module attribute now applies to this class  
class CMyClass {  
public:  
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {  
   // add your own code here  
   return __super::DllMain(dwReason, lpReserved);  
   }  
};  
```  
  
## <a name="see-also"></a>Viz také  
 [__iscsym –](../../c-runtime-library/reference/iscsym-functions.md)   
 [Klasifikace znaků](../../c-runtime-library/character-classification.md)   
 [Modul](../../windows/module-cpp.md)