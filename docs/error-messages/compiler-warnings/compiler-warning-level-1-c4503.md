---
title: Upozornění kompilátoru (úroveň 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 9077c448f3b5f1d70d18047b91dcf300e606c91f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186542"
---
# <a name="compiler-warning-level-1-c4503"></a>Upozornění kompilátoru (úroveň 1) C4503

> '*Identifier*': překročila se délka názvu dekorované, název byl zkrácen.

## <a name="remarks"></a>Poznámky

Toto upozornění kompilátoru je zastaralé a negeneruje se v kompilátorech Visual Studio 2017 a novějších.

Dekorovaný název byl delší než limit kompilátoru (4096) a byl zkrácen. Chcete-li se vyhnout tomuto upozornění a zkrácení, snižte počet argumentů nebo názvy používaných identifikátorů. Dekorované názvy, které jsou delší než omezení kompilátoru, mají použitu hodnotu hash a nejsou v nebezpečí kolizí názvů.

Při použití starší verze sady Visual Studio může být toto upozornění vystaveno, když váš kód obsahuje šablony specializované na šablony opakovaně. Například mapa map (ze C++ standardní knihovny). V této situaci můžete vytvořit definice typedef typ (například **strukturu**), která obsahuje mapu.

Můžete se ale rozhodnout nestrukturovat kód.  Je možné dodávat aplikaci, která generuje C4503, ale pokud dojde k chybám při propojování pro zkrácený symbol, může být obtížné určit typ symbolu v chybě. Ladění může být také obtížnější; ladicí program může mít obtížné mapování názvu symbolu na název typu. Správnost tohoto programu ale neovlivní zkrácený název.

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

Tento příklad ukazuje jeden ze způsobů, jak přepsat kód pro vyřešení C4503:

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
