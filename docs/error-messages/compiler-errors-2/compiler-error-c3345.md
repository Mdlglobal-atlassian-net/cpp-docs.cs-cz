---
title: Chyba kompilátoru C3345
ms.date: 11/04/2016
f1_keywords:
- C3345
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
ms.openlocfilehash: e6962e5c127a92acc5dfdad580c7bc89fa134751
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753442"
---
# <a name="compiler-error-c3345"></a>Chyba kompilátoru C3345

' identifier ': neplatný identifikátor pro název modulu

*Identifikátor* pro modul obsahuje jeden nebo více nepřijatelných znaků. Identifikátor je platný, pokud je první znak abecední, podtržítko nebo high ANSI (0x80-FF) a jakýkoli další znak je alfanumerický znak, podtržítko nebo high ANSI.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Ujistěte se, že *identifikátor* neobsahuje prázdné znaky ani jiné nepřijmoutelné znaky.

## <a name="example"></a>Příklad

Následující příklad kódu způsobí, že se zobrazí chybová zpráva C3345, protože parametr `name` atributu `module` obsahuje prázdnou hodnotu.

```cpp
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
