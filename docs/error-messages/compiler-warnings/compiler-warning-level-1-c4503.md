---
title: Kompilátor upozornění (úroveň 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 94c88511d87c3adf3cf5687a94948c83ebc5b3d5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459784"
---
# <a name="compiler-warning-level-1-c4503"></a>Kompilátor upozornění (úroveň 1) C4503

> "*identifikátor*': délka názvu decorated-překročí, název se zkrátil

## <a name="remarks"></a>Poznámky

Toto upozornění kompilátoru je zastaralá a není generován v sadě Visual Studio 2017 a novější kompilátory.

Upravený název delší než omezení kompilátoru (4096) a byla zkrácena. Abyste toto upozornění a zkrácení snížíte počet argumentů nebo název délek identifikátory používané. Dekorované názvy, které jsou déle, než omezení kompilátoru mají hodnotu hash použít a nehrozí nebezpečí kolize názvů.

Pokud používáte starší verzi sady Visual Studio, můžete toto upozornění vydána, když váš kód obsahuje šablony specializované pro šablony opakovaně. Například mapa mapy (ze standardní knihovny C++). V takovém případě můžete provést vaší definice TypeDef typu ( **struktura**, například), která obsahuje mapu.

Může se však rozhodnout není změny struktury kódu.  Je možné dodávat aplikace, která generuje C4503, ale pokud dojde k chybám čas odkaz na zkrácený symbol, může být obtížné určit typ symbolu v chybě. Také ladění může být obtížnější; ladicí program může mít problémy mapování názvu symbol pro název typu. Správnost program, je však neovlivněna zkrácený název.

## <a name="example"></a>Příklad

Následující ukázka generuje C4503 v kompilátorech před Visual Studio 2017:

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

Tento příklad ukazuje jeden způsob, jak revize kódu řešení C4503:

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