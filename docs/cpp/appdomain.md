---
title: appdomain
ms.date: 11/04/2016
f1_keywords:
- appdomain_cpp
helpviewer_keywords:
- appdomain __declspec keyword
- __declspec keyword [C++], appdomain
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
ms.openlocfilehash: 7ac74e8774204b316712a15975f7af3fb8835a9e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181483"
---
# <a name="appdomain"></a>appdomain

Určuje, že každá doména aplikace vaší spravované aplikace by měla mít svou vlastní kopii konkrétní globální proměnné nebo statické členské proměnné. Další informace najdete v tématu věnovaném [doménám a C++ vizuálním aplikacím](../dotnet/application-domains-and-visual-cpp.md) .

Každá doména aplikace má svou vlastní kopii proměnné pro každou doménu AppDomain. Konstruktor proměnné AppDomain je spuštěn, když je sestavení načteno do domény aplikace a destruktor je spuštěn, když je doména aplikace uvolněna.

Chcete-li, aby všechny domény aplikace v rámci procesu v modulu Common Language Runtime sdílely globální proměnnou, použijte modifikátor `__declspec(process)`. `__declspec(process)` ve výchozím nastavení v rámci [/CLR](../build/reference/clr-common-language-runtime-compilation.md). Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

`__declspec(appdomain)` je platná pouze v případě, že je použita jedna z možností kompilátoru **/CLR** . Pomocí `__declspec(appdomain)`lze označit pouze globální proměnnou, statickou členskou proměnnou nebo statickou místní proměnnou. Použití `__declspec(appdomain)` pro statické členy spravovaných typů je chybné, protože mají vždy toto chování.

Použití `__declspec(appdomain)` je podobné jako při použití [místního úložiště (TLS) vlákna](../parallel/thread-local-storage-tls.md). Vlákna mají vlastní úložiště, stejně jako domény aplikace. Pomocí `__declspec(appdomain)` zajišťuje globální proměnná vlastní úložiště v každé doméně aplikace vytvořené pro tuto aplikaci.

Existují určitá omezení pro kombinování použití jednotlivých procesů a proměnných AppDomain. Další informace najdete v tématu o [procesu](../cpp/process.md) .

Například při spuštění programu jsou inicializovány všechny proměnné pro procesy, poté jsou inicializovány všechny proměnné pro doménu AppDomain. Proto když je inicializována proměnná pro proces, nemůže záviset na hodnotě jakékoli proměnné domény pro aplikaci. Je to špatný postup ke smíchání použití (přiřazení) pro každou doménu aplikace a proměnnou procesu.

Informace o tom, jak zavolat funkci v konkrétní doméně aplikace, naleznete v tématu [Call_in_appdomain Function](../dotnet/call-in-appdomain-function.md).

## <a name="example"></a>Příklad

```cpp
// declspec_appdomain.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

class CGlobal {
public:
   CGlobal(bool bProcess) {
      Counter = 10;
      m_bProcess = bProcess;
      Console::WriteLine("__declspec({0}) CGlobal::CGlobal constructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   ~CGlobal() {
      Console::WriteLine("__declspec({0}) CGlobal::~CGlobal destructor", m_bProcess ? (String^)"process" : (String^)"appdomain");
   }

   int Counter;

private:
   bool m_bProcess;
};

__declspec(process) CGlobal process_global = CGlobal(true);
__declspec(appdomain) CGlobal appdomain_global = CGlobal(false);

value class Functions {
public:
   static void change() {
      ++appdomain_global.Counter;
   }

   static void display() {
      Console::WriteLine("process_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         process_global.Counter);

      Console::WriteLine("appdomain_global value in appdomain '{0}': {1}",
         AppDomain::CurrentDomain->FriendlyName,
         appdomain_global.Counter);
   }
};

int main() {
   AppDomain^ defaultDomain = AppDomain::CurrentDomain;
   AppDomain^ domain = AppDomain::CreateDomain("Domain 1");
   AppDomain^ domain2 = AppDomain::CreateDomain("Domain 2");
   CrossAppDomainDelegate^ changeDelegate = gcnew CrossAppDomainDelegate(&Functions::change);
   CrossAppDomainDelegate^ displayDelegate = gcnew CrossAppDomainDelegate(&Functions::display);

   // Print the initial values of appdomain_global in all appdomains.
   Console::WriteLine("Initial value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   // Changing the value of appdomain_global in the domain and domain2
   // appdomain_global value in "default" appdomain remain unchanged
   process_global.Counter = 20;
   domain->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);
   domain2->DoCallBack(changeDelegate);

   // Print values again
   Console::WriteLine("Changed value");
   defaultDomain->DoCallBack(displayDelegate);
   domain->DoCallBack(displayDelegate);
   domain2->DoCallBack(displayDelegate);

   AppDomain::Unload(domain);
   AppDomain::Unload(domain2);
}
```

```Output
__declspec(process) CGlobal::CGlobal constructor
__declspec(appdomain) CGlobal::CGlobal constructor
Initial value
process_global value in appdomain 'declspec_appdomain.exe': 10
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 1': 10
appdomain_global value in appdomain 'Domain 1': 10
__declspec(appdomain) CGlobal::CGlobal constructor
process_global value in appdomain 'Domain 2': 10
appdomain_global value in appdomain 'Domain 2': 10
Changed value
process_global value in appdomain 'declspec_appdomain.exe': 20
appdomain_global value in appdomain 'declspec_appdomain.exe': 10
process_global value in appdomain 'Domain 1': 20
appdomain_global value in appdomain 'Domain 1': 11
process_global value in appdomain 'Domain 2': 20
appdomain_global value in appdomain 'Domain 2': 12
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(appdomain) CGlobal::~CGlobal destructor
__declspec(process) CGlobal::~CGlobal destructor
```

## <a name="see-also"></a>Viz také

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
