---
title: "#<a name=\"using-directive-cclr--microsoft-docs\"></a>Using – direktiva (C + +/ CLR) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- friend_as_cpp
- '#using'
- friend_as
- '#using_cpp'
dev_langs: C++
helpviewer_keywords:
- using directive (#using)
- '#using directive'
- LIBPATH environment variable
- preprocessor, directives
ms.assetid: 870b15e5-f361-40a8-ba1c-c57d75c8809a
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8a73eb8e9b5c3f3ba67e4466a6e7138010fd430
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-directive-cclr"></a>#using – direktiva (C + +/ CLR)
Importuje metadata do aplikace, kompilovat s [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#using file [as_friend]  
```  
  
#### <a name="parameters"></a>Parametry  
 `file`  
 Knihovna DLL, .exe, .netmodule, nebo .obj jazyka MSIL. Například  
  
 `#using <MyComponent.dll>`  
  
 as_friend  
 Určuje, že jsou všechny typy v `file` k dispozici.  Další informace najdete v tématu [přátelských sestavení (C++)](../dotnet/friend-assemblies-cpp.md).  
  
## <a name="remarks"></a>Poznámky  
 `file` může být soubor jazyka MSIL (Microsoft Intermediate Language), který je importován pro své spravované konstrukce a spravovaná data. Pokud soubor s příponou DLL obsahuje manifest sestavení potom všech knihoven DLL, kterou se odkazuje v manifestu importují a zobrazí seznam sestavení vytváříte *souboru* v metadatech jako odkaz na sestavení.  
  
 Pokud `file` neobsahuje sestavení (Pokud `file` je modul) a pokud jste neměli v úmyslu použít informace o typu z modulu v aktuální aplikaci (sestavení), máte možnost právě označující, že modul je součástí sestavení; použijte [/ASSEMBLYMODULE](../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md). Typy z modulu pak budou k dispozici pro všechny aplikace, které odkazují na sestavení.  
  
 Alternativu k použití `#using` je [/FU](../build/reference/fu-name-forced-hash-using-file.md) – možnost kompilátoru.  
  
 Předaný .exe sestavení `#using` by měl být zkompilovány pomocí jedné z kompilátory .NET Visual Studio (Visual Basic nebo Visual C#, např.).  Probíhá pokus o import metadat ze sestavení .exe kompilovat s **/CLR** bude mít za následek výjimku zatížení souborů.  
  
> [!NOTE]
>  Komponentu, která je odkazována pomocí `#using`, lze spustit s jinou verzí souboru v době kompilace, což způsobí, že klientská aplikace poskytne neočekávané výsledky.  
  
 Je-li nutné, aby kompilátor rozpoznával typ v sestavení (ne modul), je zapotřebí jej donutit k přeložení typu, což lze provést například definováním instance daného typu. Existují jiné způsoby přeložení názvů typů pro kompilátor v sestavení, název typu se například stane pro kompilátor známým, pokud je zděděn z typu v sestavení.  
  
 Při importu metadat ze zdrojového kódu, který používá [__declspec(thread)](../cpp/thread.md), nejsou v metadatech trvalé sémantiku přístup z více vláken. Například proměnná definovaná s **__declspec(thread)**, kompilované v programu, který je sestavení pro modul common language runtime rozhraní .NET Framework a poté importovat prostřednictvím `#using`, nebude mít **__declspec ( vlákno)** sémantiku na proměnnou.  
  
 Všechny importované typy (spravované a nativní) v souboru, který je odkazován pomocí `#using`, jsou k dispozici, ale kompilátor zpracovává nativní typy jako deklarace, nikoli definice.  
  
 mscorlib.dll se automaticky odkazuje, když kompilujete s **/CLR**.  
  
 Proměnná prostředí LIBPATH určuje adresáře, které budou prohledány, jakmile se kompilátor pokusí přeložit názvy souborů předaných pomocí `#using`.  
  
 Kompilátor bude hledat odkazy v následující cestě:  
  
-   Cesta zadaná v příkazu `#using`.  
  
-   Aktuální adresář.  
  
-   Systémový adresář rozhraní .NET Framework.  
  
-   Adresáře se přidaly [/AI](../build/reference/ai-specify-metadata-directories.md) – možnost kompilátoru.  
  
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