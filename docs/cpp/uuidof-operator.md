---
title: __uuidof – operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
dev_langs:
- C++
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 70731665ca2a2eba739f139678e0f7eaface2b85
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="uuidof-operator"></a>__uuidof – operátor
**Konkrétní Microsoft**  
  
 Získá identifikátor GUID připojený k výrazu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      __uuidof (  
   expression   
)  
```  
  
## <a name="remarks"></a>Poznámky  
 *Výraz* může být název typu, ukazatelů, reference nebo pole daného typu, šablonu specializuje na těchto typů, nebo proměnnou z těchto typů. Argument je platný, pokud jej kompilátor může použít k vyhledání připojeného identifikátoru GUID.  
  
 Zvláštním případem tomto vnitřní je při buď **0** nebo **NULL** je zadaný jako argument. V tomto případě identifikátor `__uuidof` vrátí identifikátor GUID, který je tvořen nulami.  
  
 Pomocí tohoto klíčového slova je možné extrahovat identifikátor GUID připojený k:  
  
-   Objekt pomocí [uuid](../cpp/uuid-cpp.md) rozšířených atributů.  
  
-   Blok knihovny vytvořené pomocí [modulu](../windows/module-cpp.md) atribut.  
  
> [!NOTE]
>  V sestavení ladění identifikátor `__uuidof` vždy inicializuje objekt dynamicky (za běhu). V sestavení pro vydání může identifikátor `__uuidof` inicializovat objekt staticky (v době kompilace).  
  
## <a name="example"></a>Příklad  
 Následující kód (zkompilován s knihovnou ole32.lib) zobrazí identifikátor uuid vytvořeného bloku knihovny s atributem module:  
  
```  
// expre_uuidof.cpp  
// compile with: ole32.lib  
#include "stdio.h"  
#include "windows.h"  
  
[emitidl];  
[module(name="MyLib")];  
[export]  
struct stuff {  
   int i;  
};  
  
int main() {  
   LPOLESTR lpolestr;  
   StringFromCLSID(__uuidof(MyLib), &lpolestr);  
   wprintf_s(L"%s", lpolestr);  
   CoTaskMemFree(lpolestr);  
}  
```  
  
## <a name="comments"></a>Komentáře  
 V případech, kdy je název knihovny už v oboru, můžete použít __LIBID\_ místo `__uuidof`. Příklad:  
  
```  
StringFromCLSID(__LIBID_, &lpolestr);  
```  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)