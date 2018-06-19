---
title: Kompilátoru (úroveň 1) upozornění C4503 | Microsoft Docs
ms.custom: ''
ms.date: 05/14/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4503
dev_langs:
- C++
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f60fdb44c5368ccc5c5f089002614332d95a63fe
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34255671"
---
# <a name="compiler-warning-level-1-c4503"></a>Kompilátoru (úroveň 1) upozornění C4503

> '*identifikátor*': dekorované délka názvu překročí, název byl zkrácen.

## <a name="remarks"></a>Poznámky

Toto upozornění kompilátoru je zastaralá a nevygenerovala ve Visual Studio 2017 a novější kompilátory.

Upravený název byl delší než omezení kompilátoru (4096) a byla zkrácena. Aby se zabránilo toto upozornění a zkrácení, snižte počet argumentů nebo název délek identifikátory používané. Dekorované názvy, které jsou delší než omezení kompilátoru použita hodnota hash a nehrozí nebezpečí kolize názvů.

Pokud používáte starší verze sady Visual Studio, můžete objeví toto upozornění, pokud kód obsahuje šablony specializuje na šablony opakovaně. Například mapa mapy (ze standardní knihovna C++). V takovém případě můžete provést vaše definice TypeDef typu ( **struktura**, například), který obsahuje mapy.

Může se však rozhodnout není změny struktury kódu.  Je možné dodávat aplikaci, která generuje C4503, ale pokud dojde k chybám čas odkaz na zkrácený symbol, může být obtížné určit typ symbolu v chybě. Ladění také může být obtížnější; ladicí program je pravděpodobně vyskytnout potíže mapování názvu symbolu na název typu. Správnost programu, je však nemá vliv na zkrácený název.

## <a name="example"></a>Příklad

Následující ukázka generuje C4503 v kompilátory před Visual Studio 2017:

```cpp
// C4503.cpp
// compile with: /W1 /EHsc /c
// C4503 expected
#include <string>
#include <map>

class Field{};

typedef std::map<std::string, Field> Screen;
typedef std::map<std::string, Screen> WebApp;
typedef std::map<std::string, WebApp> WebAppTest;
typedef std::map<std::string, WebAppTest> Hello;
Hello MyWAT;
```

Tento příklad ukazuje jeden ze způsobů přepište kód vyřešit C4503:

```cpp
// C4503b.cpp
// compile with: /W1 /EHsc /c
#include <string>
#include <map>

class Field{};

struct Screen2 {
   std::map<std::string, Field> Element;
};

struct WebApp2 {
   std::map<std::string, Screen2> Element;
};

struct WebAppTest2 {
   std::map<std::string, WebApp2> Element;
};

struct Hello2 {
   std::map<std::string, WebAppTest2> Element;
};

Hello2 MyWAT2;
```