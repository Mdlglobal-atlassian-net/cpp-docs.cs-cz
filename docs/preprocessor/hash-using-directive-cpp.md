---
title: '#Using – direktiva (C + +/ CLI) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
dev_langs:
- C++
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2255f5de9cc26505bb07110da6368a039009c6c
ms.sourcegitcommit: b8b1cba85ff423142d73c888be26baa8c33f3cdc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093030"
---
# <a name="using-directive-ccli"></a>#using – direktiva (C + +/ CLI)
Importuje metadata do programu kompilovaného s [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#using file [as_friend]  
```  
  
#### <a name="parameters"></a>Parametry  
 `file`  
 Knihovna DLL, .exe, .netmodule, nebo .obj jazyka MSIL. Například  
  
 `#using <MyComponent.dll>`  
  
 as_friend  
 Určuje, že jsou všechny typy v `file` k dispozici.  Další informace najdete v tématu [přátelská sestavení (C++)](../dotnet/friend-assemblies-cpp.md).  
  
## <a name="remarks"></a>Poznámky  
 `file` může být soubor jazyka MSIL (Microsoft Intermediate Language), který je importován pro své spravované konstrukce a spravovaná data. Pokud soubor DLL obsahuje manifest sestavení, potom jsou importovány všechny odkazované sestavované a zobrazí se seznam sestavení, kterou vytváříte *souboru* v metadatech jako odkaz na sestavení.  
  
 Pokud `file` neobsahuje sestavení (Pokud `file` je modul) a pokud je nemáte v úmyslu použít informace o typu z modulu v aktuální aplikaci (sestavení), máte možnost pouze označující, že modul je součástí sestavení; použijte [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Typy z modulu pak budou k dispozici pro všechny aplikace, které odkazují na sestavení.  
  
 Alternativou k použití `#using` je [/FU](../build/reference/fu-name-forced-hash-using-file.md) – možnost kompilátoru.  
  
 sestavení .exe předaná `#using` by měl být zkompilován pomocí jedné z kompilátorů aplikace Visual Studio .NET (Visual Basic nebo Visual C#, například).  Pokus o import metadat ze sestavení .exe kompilovaného s **/CLR** povede k výjimce načítání souboru.  
  
> [!NOTE]
>  Komponentu, která je odkazována pomocí `#using`, lze spustit s jinou verzí souboru v době kompilace, což způsobí, že klientská aplikace poskytne neočekávané výsledky.  
  
 Je-li nutné, aby kompilátor rozpoznával typ v sestavení (ne modul), je zapotřebí jej donutit k přeložení typu, což lze provést například definováním instance daného typu. Existují jiné způsoby přeložení názvů typů pro kompilátor v sestavení, název typu se například stane pro kompilátor známým, pokud je zděděn z typu v sestavení.  
  
 Při importu metadat ze zdrojového kódu, který používá [__declspec(thread)](../cpp/thread.md), sémantika vláken nejsou zachované v metadatech. Například proměnná deklarovaná pomocí **__declspec(thread)** zkompilovaná v programu, který je sestaven pro modul common language runtime rozhraní .NET Framework a poté importována pomocí `#using`, už nebude mít **__declspec () vlákno)** sémantiky pro proměnnou.  
  
 Všechny importované typy (spravované a nativní) v souboru, který je odkazován pomocí `#using`, jsou k dispozici, ale kompilátor zpracovává nativní typy jako deklarace, nikoli definice.  
  
 soubor mscorlib.dll je při kompilaci s automaticky odkazována **/CLR**.  
  
 Proměnná prostředí LIBPATH určuje adresáře, které budou prohledány, jakmile se kompilátor pokusí přeložit názvy souborů předaných pomocí `#using`.  
  
 Kompilátor bude hledat odkazy v následující cestě:  
  
-   Cesta zadaná v příkazu `#using`.  
  
-   Aktuální adresář.  
  
-   Systémový adresář rozhraní .NET Framework.  
  
-   Adresáře přidané pomocí [/AI](../build/reference/ai-specify-metadata-directories.md) – možnost kompilátoru.  
  
-   Adresáře dle proměnné prostředí LIBPATH.  
  
## <a name="example"></a>Příklad  
 Při vytvoření sestavení (C) a odkázání na sestavení (B), které odkazuje na jiné sestavení (A), nebude explicitně odkazováno na sestavení A, pokud nebude v sestavení C explicitně použit jeden z typů sestavení A.  
  
```  
// using_assembly_A.cpp  
// compile with: /clr /LD  
public ref class A {};  
```  
  
## <a name="example"></a>Příklad  
  
```  
// using_assembly_B.cpp  
// compile with: /clr /LD  
#using "using_assembly_A.dll"  
public ref class B {  
public:  
   void Test(A a) {}  
   void Test() {}  
};  
  
```  
  
## <a name="example"></a>Příklad  
 V následující ukázce se nevyskytuje žádná chyba kompilátoru v souvislosti s neodkazováním na using_assembly_A.dll, protože program nepoužívá žádné typy definované v using_assembly_A.cpp.  
  
```  
// using_assembly_C.cpp  
// compile with: /clr  
#using "using_assembly_B.dll"  
int main() {  
   B b;  
   b.Test();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)
