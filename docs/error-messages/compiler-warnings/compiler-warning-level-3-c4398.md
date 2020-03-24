---
title: Upozornění kompilátoru (úroveň 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 041bf9f6bfce17b16f301604bb8706be30095c13
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198663"
---
# <a name="compiler-warning-level-3-c4398"></a>Upozornění kompilátoru (úroveň 3) C4398

> '*Variable*': globální objekt na úrovni procesu nemusí fungovat správně s několika doménami AppDomains; Zvažte použití __declspec (AppDomain)

## <a name="remarks"></a>Poznámky

Virtuální funkce s konvencí volání [__clrcall](../../cpp/clrcall.md) v nativním typu způsobí vytvoření domény vtable pro doménu aplikace. Tato proměnná se nemusí správně opravovat při použití ve více doménách aplikace.

Toto upozornění můžete vyřešit explicitním označením `__declspec(appdomain)`proměnné. Ve verzích sady Visual Studio před sadou Visual Studio 2017 můžete vyřešit toto upozornění kompilací s možností **/clr: Pure**, která ve výchozím nastavení zpřístupňuje globální proměnné pro aplikaci AppDomain. Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017.

Další informace naleznete v tématu [AppDomain](../../cpp/appdomain.md) a [domény aplikace a Visual C++ ](../../dotnet/application-domains-and-visual-cpp.md).

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
