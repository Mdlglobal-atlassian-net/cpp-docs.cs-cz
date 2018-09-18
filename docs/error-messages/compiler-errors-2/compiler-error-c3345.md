---
title: Chyba kompilátoru C3345 | Dokumentace Microsoftu
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
ms.openlocfilehash: 191c2184d14f991ab62f439b492c7fd7f4a00be5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118944"
---
# <a name="compiler-error-c3345"></a>Chyba kompilátoru C3345

'identifier': Neplatný identifikátor pro název modulu

*Identifikátor* pro modul obsahuje jeden nebo více znaků nemůže být přijata. Identifikátor je platný, pokud je první znak abecedy, podtržítko nebo vysokou znaků ANSI (0x80 – FF) a libovolný následující znak je alfanumerické znaky, podtržítka nebo vysokou znaků ANSI.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ujistěte se, že *identifikátor* neobsahuje mezery nebo jiných nepřijatelné znaků.

## <a name="example"></a>Příklad

Následující příklad kódu způsobí chybové zprávy C3345, protože `name` parametr `module` atribut obsahuje prázdnou hodnotu.

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

[__iscsym](../../c-runtime-library/reference/iscsym-functions.md)<br/>
[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[Modul](../../windows/module-cpp.md)