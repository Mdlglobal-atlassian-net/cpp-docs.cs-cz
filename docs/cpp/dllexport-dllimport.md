---
title: dllexport, dllimport | Dokumentace Microsoftu
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
ms.openlocfilehash: a330ecf221d210134425c4bf39c17bac0f5006dc
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940531"
---
# <a name="dllexport-dllimport"></a>dllexport, dllimport
**Specifické pro Microsoft**  
  
 **Dllexport** a **dllimport** jsou atributy třídy úložiště specifické pro společnost Microsoft rozšíření pro jazyky C a C++. Můžete využít k exportu a importu funkce, data a objekty do nebo z knihovny DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   __declspec( dllimport ) declarator  
   __declspec( dllexport ) declarator  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto atributy explicitně definují rozhraní DLL svému klientu, který může být spustitelný soubor nebo jiné knihovně DLL. Deklarace funkcí jako **dllexport** eliminuje potřebu souboru definice modulu (.def), alespoň jde o specifikaci exportovaných funkcí. **Dllexport** atribut nahradí **__export** – klíčové slovo.  
  
 Pokud má třída označení declspec(dllexport), jakékoli specializace šablony třídy v hierarchii třídy jsou implicitně označeny jako declspec(dllexport). To znamená, že šablony třídy explicitně vytvoří instanci a členy tříd musí být definován.  
  
 **dllexport** funkce vystavuje funkci s jejím upraveným názvem. Pro funkce jazyka C++ to zahrnuje pozměnění názvu. Funkce jazyka C nebo funkce, které jsou deklarovány jako `extern "C"`, jedná se o platformě závislou dekoraci, která je založena na konvenci volání. Informace o dekorování názvů v kódu C/C++, naleznete v tématu [dekorované názvy](../build/reference/decorated-names.md). Žádné dekorování názvů u exportovaných funkcí jazyka C nebo C++ `extern "C"` funkce používající `__cdecl` konvence volání.  
  
 Pokud chcete exportovat nedekorovaný název, můžete propojit pomocí souboru definice modulu (.def), který definuje nedekorovaný název v oddílu EXPORTY. Další informace najdete v tématu [EXPORTY](../build/reference/exports.md). Dalším způsobem, jak exportovat nedekorovaný název je použít `#pragma comment(linker, "/export:alias=decorated_name")` směrnice ve zdrojovém kódu.  
  
 Pokud deklarujete **dllexport** nebo **dllimport**, je nutné použít [rozšířené syntaxe atributů](../cpp/declspec.md) a **__declspec** – klíčové slovo.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// Example of the dllimport and dllexport class attributes  
__declspec( dllimport ) int i;  
__declspec( dllexport ) void func();  
```  
  
 Další možností aby váš kód lépe čitelný, můžete použít definice makra:  
  
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
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)