---
title: dllexport, dllimport | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- dllimport_cpp
- dllexport_cpp
dev_langs:
- C++
helpviewer_keywords:
- dllexport __declspec keyword
- __declspec keyword [C++], dllexport
- dllimport __declspec keyword
- __declspec keyword [C++], dllimport
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d57287723da1bb7fbe7f75dece05674142bd417
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport
**Konkrétní Microsoft**  
  
 `dllexport` a **dllimport** atributy třídy úložiště jsou specifické pro společnost Microsoft rozšíření pro jazyky C a C++. Můžete je používat pro export a import funkce, dat a objektů do nebo z knihovny DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   __declspec( dllimport ) declarator  
   __declspec( dllexport ) declarator  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto atributy explicitně definujte knihovnu DLL rozhraní jeho klientovi, který může být spustitelný soubor nebo jiné knihovny DLL. Deklarování funkcí jako `dllexport` alespoň eliminuje potřebu soubor definice modulu (.def) s ohledem na specifikace exportovaných funkcí. `dllexport` Atribut nahradí `__export` – klíčové slovo.  
  
 Pokud je třída označeno declspec(dllexport), všechny specializace šablon tříd v hierarchii tříd implicitně označeno declspec(dllexport). To znamená, že explicitně instance šablony třídy a členy třídy musí být definován.  
  
 `dllexport` Funkce zpřístupní funkce se jeho upravený název. U funkcí jazyka C++ to zahrnuje, úprava názvu. Funkce jazyka C nebo funkce, které jsou deklarovány jako `extern "C"`, jedná se o decoration specifické pro platformu, která je založená na konvence volání. Informace o dekorování názvů v kódu C/C++, najdete v části [dekorované názvy](../build/reference/decorated-names.md). Úprava bez názvu se použije pro exportovaných funkcí jazyka C nebo C++ `extern "C"` funkce pomocí `__cdecl` konvence volání.  
  
 Pokud chcete exportovat bez upraveného název, můžete propojit pomocí souboru definice modulu (.def), který definuje název bez upraveného v části Export. Další informace najdete v tématu [EXPORTUJE](../build/reference/exports.md). Jiný způsob, jak exportovat bez upraveného název je použít `#pragma comment(linker, "/export:alias=decorated_name")` direktivy ve zdrojovém kódu.  
  
 Když je deklarovat `dllexport` nebo **dllimport**, je nutné použít [rozšířené syntaxe atribut](../cpp/declspec.md) a `__declspec` – klíčové slovo.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// Example of the dllimport and dllexport class attributes  
__declspec( dllimport ) int i;  
__declspec( dllexport ) void func();  
```  
  
 Případně aby byl čitelnější kódu, můžete definice maker:  
  
```cpp  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllImport int j;  
DllExport int n;  
```  
  
 Další informace naleznete v tématu:  
  
-   [Definice a deklarace](../cpp/definitions-and-declarations-cpp.md)  
  
-   [Definování vložených funkcí jazyka C++ příkazy dllexport a dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)  
  
-   [Obecná pravidla a omezení](../cpp/general-rules-and-limitations.md)  
  
-   [Používání příkazů dllimport a dllexport ve třídách jazyka C++](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)