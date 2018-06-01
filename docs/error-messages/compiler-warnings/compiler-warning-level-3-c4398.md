---
title: Kompilátoru (úroveň 3) upozornění C4398 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4398
dev_langs:
- C++
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c38ade6b75242fdd5144481e3415e914cb6773c5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704611"
---
# <a name="compiler-warning-level-3-c4398"></a>C4398 kompilátoru upozornění (úroveň 3)

> '*proměnná*': globální objektu na proces nemusí pracovat správně s více domén; zvažte použití __declspec(appdomain)

## <a name="remarks"></a>Poznámky

Virtuální funkce s [__clrcall](../../cpp/clrcall.md) konvence volání v nativním typu způsobí, že vytvoření za vtable domény aplikace. Tuto proměnnou nemusí správně opravit, pokud se používá ve více doménách aplikace.

Toto upozornění můžete vyřešit explicitní označení proměnnou `__declspec(appdomain)`. Ve verzích sady Visual Studio před Visual Studio 2017, můžete vyřešit toto upozornění kompilujete s **/CLR: pure**, takže globální proměnné jednotlivé domény aplikace ve výchozím nastavení. **/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

Další informace najdete v tématu [appdomain](../../cpp/appdomain.md) a [domény aplikace a jazyk Visual C++](../../dotnet/application-domains-and-visual-cpp.md).

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