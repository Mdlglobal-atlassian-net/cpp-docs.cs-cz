---
title: Spravované typy (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data types [C++], managed
- managed data types [C++]
- .NET Framework [C++], managed types
- data types [C++], .NET feature access
- main function, in managed applications
- managed code, main() function
- .NET Framework [C++], C++ equivalents
- __nogc type declarations
- __value keyword, issues when nesting
- equality, testing for
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 679b8ed3-d966-4a0c-b627-2a3f3ec96b74
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a14b217df2bdc8aec8e8d823df7661e8b4754b38
ms.sourcegitcommit: b8b1cba85ff423142d73c888be26baa8c33f3cdc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39092991"
---
# <a name="managed-types-ccli"></a>Spravované typy (C++/CLI)
Visual C++ umožňuje přístup k funkcím .NET prostřednictvím spravované typy, které poskytují podporu pro funkce common language runtime a řídí, jaké výhody a omezení modulu runtime se.  
  
## <a name="main_functions"></a> Spravované typy a hlavní funkce
Při psaní aplikace s využitím **/CLR**, argumenty **main()** spravovaného typu nemůže být funkce.  
  
 Je například správný podpis:  
  
```cpp  
// managed_types_and_main.cpp  
// compile with: /clr  
int main(int, char*[], char*[]) {}  
```  

## <a name="dotnet"></a> .NET framework – ekvivalenty k nativním typům C++
V následující tabulce jsou uvedeny klíčová slova pro předdefinované typy jazyka Visual C++, které jsou aliasy předdefinovaných typů v **systému** oboru názvů.  
  
|Typ Visual C++|Typ rozhraní .NET Framework|  
|-----------------------|-------------------------|  
|**bool**|**System.Boolean**|  
|**podepsané char** (viz [/J](../build/reference/j-default-char-type-is-unsigned.md) Další informace)|**System.SByte**|  
|**unsigned char**|**System.Byte**|  
|**wchar_t**|**System.Char**|  
|**dvojité** a **long double**|**System.Double**|  
|**float**|**System.Single**|  
|**int**, **znaménkem**, **dlouhé**, a **podepsané dlouho**|**System.Int32**|  
|**unsigned int** a **unsigned long**|**System.UInt32**|  
|**__int64** a **signed __int64**|**System.Int64**|  
|**unsigned __int64**|**System.UInt64**|  
|**krátký** a **podepsané krátké**|**System.Int16**|  
|**short bez znaménka**|**System.UInt16**|  
|**void**|**System.Void.**|  
  
## <a name="version_issues"></a> Problémy s verzí u typů hodnot vnořených v nativních typech
Vezměte v úvahu komponentu sestavení podepsané (silný název) použitý k vytvoření sestavení klienta. Komponenta obsahuje hodnotový typ, který se používá v klientovi jako typ člena nativní sjednocení, třídy nebo pole. Pokud se v budoucích verzích komponenty změní velikost nebo rozložení typu hodnoty, klient musí zopakovat.  
  
 Vytvoření souboru keyfile s [sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`).  
  
### <a name="example"></a>Příklad  
 Následující ukázka je součástí.  
  
```cpp 
// nested_value_types.cpp  
// compile with: /clr /LD  
using namespace System::Reflection;  
[assembly:AssemblyVersion("1.0.0.*"),   
assembly:AssemblyKeyFile("mykey.snk")];  
  
public value struct S {  
   int i;  
   void Test() {  
      System::Console::WriteLine("S.i = {0}", i);  
   }  
};  
```  
  
### <a name="example"></a>Příklad  
 Tato ukázka je klienta:  
  
```cpp  
// nested_value_types_2.cpp  
// compile with: /clr  
#using <nested_value_types.dll>  
  
struct S2 {  
   S MyS1, MyS2;  
};  
  
int main() {  
   S2 MyS2a, MyS2b;  
   MyS2a.MyS1.i = 5;  
   MyS2a.MyS2.i = 6;  
   MyS2b.MyS1.i = 10;  
   MyS2b.MyS2.i = 11;  
  
   MyS2a.MyS1.Test();  
   MyS2a.MyS2.Test();  
   MyS2b.MyS1.Test();  
   MyS2b.MyS2.Test();  
}  
```  
  
### <a name="output"></a>Výstup  
  
```  
S.i = 5  
S.i = 6  
S.i = 10  
S.i = 11  
```  
  
### <a name="comments"></a>Komentáře  
 Ale pokud chcete přidat jiného člena pro `struct S` v nested_value_types.cpp (například `double d;`) a znovu zkompilovat komponenty bez opětovné kompilace klienta, výsledek je k neošetřené výjimce (typu <xref:System.IO.FileLoadException?displayProperty=fullName>).  

## <a name="test_equality"></a> Postupy: testování rovnosti
V následujícím příkladu je test rovnosti, který používá spravovaného rozšíření jazyka C++ podle úchyty odkazovat na.  
  
### <a name="example"></a>Příklad  
  
```cpp  
// mcppv2_equality_test.cpp  
// compile with: /clr /LD  
using namespace System;  
  
bool Test1() {  
   String ^ str1 = "test";  
   String ^ str2 = "test";  
   return (str1 == str2);  
}  
```  
  
 IL pro tento program ukazuje, že návratová hodnota je implementována pomocí volání op_Equality.  
  
```  
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,  
                                                               string)  
```  

## <a name="diagnose_fix"></a> Postupy: diagnostikování a odstranění potíží s kompatibilitou sestavení
Toto téma vysvětluje, co se může stát, pokud verze odkazovaného sestavení v době kompilace neodpovídá verzi sestavení odkazuje na modul runtime a o tom, abyste zabránili problémům.  
  
 Při kompilaci sestavení jiná sestavení mohou být odkazována pomocí `#using` syntaxe. Během kompilace jsou přístupné tato sestavení pomocí kompilátoru. Informace z těchto sestavení se používá k rozhodování optimalizace.  
  
 Nicméně pokud odkazované sestavení změní a znovu zkompilovat a nezkompilujete odkazující sestavení, které je na ní závislé, sestavení nemusí být kompatibilní. Optimalizační rozhodnutí, která byla platná na první nemusí být správné s ohledem na novou verzi sestavení. Z důvodu tyto nekompatibility může dojít k různých chybám modulu runtime. Neexistuje žádná konkrétní výjimky, který bude vytvořen v takových případech. Způsob, jakým selhání je nahlášeno za běhu závisí na povaze změny kódu, která způsobila problém.  
  
 Tyto chyby by neměl být problém v posledním produkční kód, tak dlouho, dokud bude celá aplikace je znovu sestavit pro vydanou verzi produktu. Sestavení, které jsou všeobecně dostupné pro veřejnost, by měly být označené oficiální verze číslo, které zajistí, že se vyhnout těmto problémům. Další informace najdete v tématu [Správa verzí sestavení](/dotnet/framework/app-domains/assembly-versioning).  
  
### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>Diagnostika a řešení nekompatibility chybě  
  
1.  Pokud narazíte na výjimky modulu CLR nebo další chybové stavy, které se vyskytují v kódu, který odkazuje na jiné sestavení a žádné jiné identifikovaný příčinu, může být Zabýváte se zastaralá sestavení.  
  
2.  Nejprve izolovat a reprodukovat výjimku nebo jiných chybový stav. Problém, který nastává z důvodu zastaralé výjimky by měla být reprodukovatelné.  
  
3.  Zkontrolujte časové razítko všech sestavení odkazuje ve vaší aplikaci.  
  
4.  Pokud jsou pozdější než časové razítko poslední kompilace aplikace časová razítka všech odkazovaných sestavení, vaše aplikace je zastaralá. Pokud k tomu dojde, znovu zkompilovat aplikaci s nejnovější sestavení a proveďte potřebné změny kódu.  
  
5.  Znovu spusťte aplikaci, proveďte kroky, které problém reprodukovat a ověřte, že výjimka nedojde.  
  
### <a name="example"></a>Příklad  
 Následující program ukazuje problém snížením usnadnění metody a pokusu o přístup k této metodě v jiném sestavení bez opětovné kompilace. Pokuste se zkompilovat `changeaccess.cpp` první. Toto je odkazovaná sestavení, které se změní. Potom zkompilujete `referencing.cpp`. Sestavení proběhne úspěšně. Nyní snížit přístupnost volané metody. Znovu zkompilovat `changeaccess.cpp` s příznakem `/DCHANGE_ACCESS`. Toto učiní metodu chráněné, spíše než soukromé, tak může už být volána ze zákona. Bez opětovné kompilace `referencing.exe`, spusťte aplikaci znovu. Výjimka <xref:System.MethodAccessException> dojde.  
  
```cpp  
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
  
```cpp  
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
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

 [Vzájemná funkční spolupráce s jinými jazyky rozhraní .NET (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)

 [Spravované typy (C++/CLI)](../dotnet/managed-types-cpp-cli.md)

 [#using – direktiva](../preprocessor/hash-using-directive-cpp.md) 
