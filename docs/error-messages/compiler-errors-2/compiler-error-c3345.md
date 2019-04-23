---
title: Chyba kompilátoru C3345
ms.date: 11/04/2016
f1_keywords:
- C3345
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
ms.openlocfilehash: eb1d15a12bfebbf44f7335a848d68c367c285586
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027537"
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

## <a name="see-also"></a>Viz také:

[__iscsym](../../c-runtime-library/reference/iscsym-functions.md)<br/>
[Klasifikace znaků](../../c-runtime-library/character-classification.md)<br/>
[module](../../windows/module-cpp.md)