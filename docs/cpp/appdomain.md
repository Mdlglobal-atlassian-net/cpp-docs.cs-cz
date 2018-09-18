---
title: doména AppDomain | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- appdomain_cpp
dev_langs:
- C++
helpviewer_keywords:
- appdomain __declspec keyword
- __declspec keyword [C++], appdomain
ms.assetid: 29d843cb-cb6b-4d1b-a48d-d928a877234d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8ef06751e1c9e478c7119dbffb242581f432b9e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111768"
---
# <a name="appdomain"></a>appdomain

Určuje, zda každá aplikační doména vaší spravované aplikace by měla mít svou vlastní kopii určité globální proměnné nebo statické členské proměnné. Zobrazit [aplikačních doménách a Visual C++](../dotnet/application-domains-and-visual-cpp.md) Další informace.

Každá doména aplikace má vlastní kopii proměnné na úrovni appdomain. Konstruktor třídy proměnnou domény aplikace se spustí, až je sestavení načteno do domény aplikace a destruktor je spuštěn, když je doména aplikace uvolněna.

Pokud chcete všechny domény aplikace uvnitř procesu v modulu common language runtime sdílet globální proměnné, použijte `__declspec(process)` modifikátor. `__declspec(process)` je používána ve výchozím nastavení v části [/CLR](../build/reference/clr-common-language-runtime-compilation.md). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

`__declspec(appdomain)` je platná pouze při některou **/CLR** – možnosti kompilátoru je používá. Může být označena pouze globální proměnné, statické členské proměnné nebo statické místní proměnné `__declspec(appdomain)`. Jedná se o chybu, chcete-li použít `__declspec(appdomain)` na statické členy třídy spravované typy, protože mají vždy toto chování.

Pomocí `__declspec(appdomain)` podobá se to používání [vlákna místní úložiště (TLS)](../parallel/thread-local-storage-tls.md). Vlákna mají své vlastní úložiště, jako tomu aplikačních doménách. Pomocí `__declspec(appdomain)` zajišťuje globální proměnná má své vlastní úložiště v jednotlivých doménách aplikace vytvořené pro tuto aplikaci.

Existují omezení směšování využívání podle procesu a proměnné domény aplikace; Zobrazit [procesu](../cpp/process.md) Další informace.

Při spuštění programu, například všechny proměnné na úrovni jednotlivého procesu se inicializují pak všechny proměnné na úrovni appdomain se inicializují. Proto při inicializaci proměnné na úrovni jednotlivého procesu ji nemůže záviset na hodnotu kterékoli proměnné na aplikační domény. Je špatný postup kombinovat použití (přiřazení) podle domény aplikace a proměnné procesu.

Informace o tom, jak volat funkci ve specifické aplikační doméně najdete v tématu [call_in_appdomain – funkce](../dotnet/call-in-appdomain-function.md).

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

## <a name="see-also"></a>Viz také:

[__declspec](../cpp/declspec.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)