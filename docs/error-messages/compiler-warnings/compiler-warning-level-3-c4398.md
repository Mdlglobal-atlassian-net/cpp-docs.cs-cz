---
title: Kompilátor upozornění (úroveň 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 4126a1267b41cdf9c0161c7e85a9057b2a301d77
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578461"
---
# <a name="compiler-warning-level-3-c4398"></a>Kompilátor upozornění (úroveň 3) C4398

> "*proměnnou*': globální objekt na úrovni jednotlivého procesu nemusí fungovat správně s více objektů třídy appdomains; zvažte použití možnosti __declspec(appdomain)

## <a name="remarks"></a>Poznámky

Virtuální funkce s [__clrcall](../../cpp/clrcall.md) konvence volání v nativním typu způsobí vytvoření za vtable domény aplikace. Tato proměnná nemusí opravte správně při použití ve více doménách aplikace.

Toto upozornění můžete vyřešit explicitní označení proměnné `__declspec(appdomain)`. Ve verzích sady Visual Studio před Visual Studio 2017, můžete vyřešit tato upozornění kompilace s **/CLR: pure**, který představuje globální proměnné na doménu aplikace ve výchozím nastavení. **/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [aplikačních doménách a Visual C++](../../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4398.

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```