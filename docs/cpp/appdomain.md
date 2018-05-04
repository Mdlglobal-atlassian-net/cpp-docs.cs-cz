---
title: doména AppDomain | Microsoft Docs
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
ms.openlocfilehash: 14b6f23e5690c98553448c827fe287bd413d6f97
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="appdomain"></a>appdomain
Určuje, že každou doménu aplikace spravované aplikace musí mít svůj vlastní kopii konkrétní globální proměnné nebo statické členské proměnné. V tématu [domény aplikace a jazyk Visual C++](../dotnet/application-domains-and-visual-cpp.md) Další informace.  
  
 Každá doména aplikací má vlastní kopii proměnné na appdomain. Konstruktor proměnné objektu třídy appdomain je spuštěn, když je načteno do domény aplikace sestavení a destruktoru je spuštěn, když je odpojen domény aplikace.  
  
 Pokud chcete, aby všechny domény aplikace v rámci procesu v modulu common language runtime sdílet globální proměnné, použijte `__declspec(process)` modifikátor. `__declspec(process)` Výsledkem je ve výchozím nastavení v části [/CLR](../build/reference/clr-common-language-runtime-compilation.md). **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
 `__declspec(appdomain)` je platný pouze při mezi **/CLR** – možnosti kompilátoru se používá. Může být označen pouze globální proměnné, statické členské proměnné nebo statické místní proměnné `__declspec(appdomain)`. Jedná se o chybu použít `__declspec(appdomain)` pro statické členy spravované typy, protože mají vždy toto chování.  
  
 Pomocí `__declspec(appdomain)` je podobný používání [vláken místní úložiště (TLS)](../parallel/thread-local-storage-tls.md). Vlákna jsou vlastní úložiště, stejně jako domény aplikace. Pomocí `__declspec(appdomain)` zajišťuje globální proměnná má svou vlastní úložiště v každé doméně aplikace vytvořené pro tuto aplikaci.  
  
 Existují určitá omezení kombinování použití jednotlivých procesů a proměnných domény aplikace; v tématu [proces](../cpp/process.md) Další informace.  
  
 Při spuštění programu, například všechny proměnné na proces se inicializují a potom se inicializují všechny proměnné na appdomain. Proto když probíhá inicializace proměnné na proces, ho nemůže záviset na hodnotu žádné proměnné pro aplikační doménu. Je chybný zvykem kombinovat používání (přiřazení) jednotlivých appdomain a proces proměnné.  
  
 Informace o tom, jak volat funkci v doméně konkrétní aplikaci najdete v tématu [call_in_appdomain – funkce](../dotnet/call-in-appdomain-function.md).  
  
## <a name="example"></a>Příklad  
  
```  
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
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)