---
title: "Postupy: diagnostikovat a opravit problémy s kompatibilitou sestavení (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 297c71e3-04a8-4d24-a5dc-b04a2c5cc6fb
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a175705bd5d303187a11bf3e7779669a3a30e483
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-diagnose-and-fix-assembly-compatibility-problems-ccli"></a>Postupy: Diagnostikování a odstranění potíží s kompatibilitou sestavení (C++/CLI)
Toto téma vysvětluje, co může dojít v případě verze odkazovaného sestavení v čase kompilace se neshoduje verze sestavení odkazuje za běhu a jak se tomuto problému vyhnout.  
  
 Při sestavení, mohou být odkazována ostatních sestavení pomocí `#using` syntaxe. Během kompilace jsou tyto sestavení přístup kompilátoru. Informace z těchto sestavení se používá při rozhodování optimalizace.  
  
 Ale pokud je odkazované sestavení změnil a překompilovat, a není znovu zkompiluje odkazující sestavení, které je na ní závislé, sestavení může není nadále kompatibilní. Optimalizace rozhodnutí, která byla platná na první nemusí být správný s ohledem na novou verzi sestavení. Kvůli těmto problémům s kompatibilitou může dojít k různých chybám za běhu. Neexistuje žádná konkrétní výjimka, která bude vytvořena v takových případech. Způsob, jakým selhání je nahlášeno za běhu závisí na povaze změny kódu, která způsobila problém.  
  
 Tyto chyby by neměl být problém ve finální produkčním kódu tak dlouho, dokud bude celá aplikace se znovu sestavit pro vydanou verzi produktu. Sestavení, které byly vydané veřejnosti by měl být označen s číslem oficiální verze, která zajistí, že se tak předejde tyto problémy. Další informace najdete v tématu [Správa verzí sestavení](/dotnet/framework/app-domains/assembly-versioning).  
  
### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnostika a oprava chyby nekompatibility  
  
1.  Pokud dojde k výjimky za běhu nebo jiné chybové podmínky, ke kterým došlo v kód, který odkazuje na jiné sestavení a mít žádné jiné identifikované příčiny, může být plánování práce s aktuální sestavení.  
  
2.  Nejprve izolovat a reprodukujte výjimku nebo jiný chybový stav. Problém, ke kterému dochází kvůli zastaralé výjimce by měl být reprodukovatelnou.  
  
3.  Zkontrolujte časové razítko žádné sestavení odkazovaných ve vaší aplikaci.  
  
4.  Pokud jsou všechny odkazované sestavení časová razítka pozdější než časové razítko poslední kompilace vaší aplikace, aplikace je zastaralý. Pokud k tomu dojde, znovu zkompiluje aplikaci s nejnovější sestavení a proveďte potřebné změny kódu.  
  
5.  Znovu spusťte aplikaci, proveďte kroky, které reprodukování problému a ověřte, že výjimka nedojde.  
  
## <a name="example"></a>Příklad  
 Následující program znázorňuje problém, snížením usnadnění metody a pokusu o přístup k dané metody v jiném sestavení bez nutnosti rekompilace. Zkuste kompilování `changeaccess.cpp` první. Toto je odkazované sestavení, které se změní. Potom zkompilovat `referencing.cpp`. Kompilace úspěšné. Nyní snižte usnadnění vyvolání metody. Znovu zkompiluje `changeaccess.cpp` s příznakem `/DCHANGE_ACCESS`. Díky tomu metodu protected, nikoli privátní, tak jej již nelze volat právními předpisy. Bez nutnosti rekompilace `referencing.exe`, znovu spusťte aplikaci. Výjimku <xref:System.MethodAccessException> způsobí.  
  
```  
// changeaccess.cpp  
// compile with: /clr:safe /LD  
// After the initial compilation, add /DCHANGE_ACCESS and rerun  
// referencing.exe to introduce an error at runtime. To correct  
// the problem, recompile referencing.exe  
  
public ref class Test {  
#if defined(CHANGE_ACCESS)  
protected:  
#else  
public:  
#endif  
  
  int access_me() {  
    return 0;  
  }  
  
};  
  
```  
  
```  
// referencing.cpp  
// compile with: /clr:safe   
#using <changeaccess.dll>  
  
// Force the function to be inline, to override the compiler's own  
// algorithm.  
__forceinline  
int CallMethod(Test^ t) {  
  // The call is allowed only if access_me is declared public  
  return t->access_me();  
}  
  
int main() {  
  Test^ t = gcnew Test();  
  try  
  {  
    CallMethod(t);  
    System::Console::WriteLine("No exception.");  
  }  
  catch (System::Exception ^ e)  
  {  
    System::Console::WriteLine("Exception!");  
  }  
  return 0;  
}  
  
```  
  
## <a name="see-also"></a>Viz také  
 [#using – direktiva](../preprocessor/hash-using-directive-cpp.md)   
 [Spravované typy (C++/CLI)](../dotnet/managed-types-cpp-cli.md)