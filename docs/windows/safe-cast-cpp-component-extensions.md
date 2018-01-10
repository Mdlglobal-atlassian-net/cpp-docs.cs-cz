---
title: "safe_cast (rozšíření komponent C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
dev_langs: C++
helpviewer_keywords: safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14bcf198d527fae51a579a2aa6e072a4c57424f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="safecast-c-component-extensions"></a>safe_cast (rozšíření komponent C++)
`safe_cast` Operace v případě úspěchu vrátí zadaný výraz jako zadaný typ; jinak vyvolá `InvalidCastException`.  
  
## <a name="all-runtimes"></a>Všechny moduly runtime  
 (Používají se žádné poznámky pro tuto funkci jazyka, které platí pro všechny moduly runtime.)  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>Parametry  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="windows-runtime"></a>prostředí Windows Runtime  
 `safe_cast`Umožňuje změnit typ zadaného výrazu. V situacích, kdy plně očekáváte proměnné nebo parametru být převoditelná na určitý typ můžete použít safe_cast bez bloku try-catch – ke zjištění programovací chyby během vývoje. Další informace najdete v tématu [přetypování (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh755802.aspx).  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
[default]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>Parametry  
 *id typu*  
 Typ převést *výraz* k. Obslužná rutina se odkaz na typ hodnoty, typ hodnoty nebo sledovací odkaz na typ hodnotou nebo odkazem.  
  
 *výraz*  
 Výraz, který se vyhodnotí jako popisovač pro odkaz nebo typ hodnoty, typ hodnoty nebo sledovací odkaz na typ hodnotou nebo odkazem.  
  
### <a name="remarks"></a>Poznámky  
 `safe_cast`Vyvolá `InvalidCastException` Pokud nemůže převést *výraz* na typ určený *id typu*. K zachycení `InvalidCastException`, zadejte [/EH (Model zpracování výjimek)](../build/reference/eh-exception-handling-model.md) – možnost kompilátoru a použijte příkaz try/catch.  
  
### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru: **/ZW**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Následující příklad kódu ukazuje, jak používat `safe_cast` pomocí prostředí Windows Runtime.  
  
```cpp#  
// safe_cast_ZW.cpp  
// compile with: /ZW /EHsc  
  
using namespace default;  
using namespace Platform;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main(Array<String^>^ args) {  
   I1^ i1 = ref new X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.  
   }   
   catch(InvalidCastException^ ic) {  
     wprintf(L"Caught expected exception: %s\n", ic->Message);  
   }  
}  
```  
  
 **Output**  
  
```Output  
Caught expected exception: InvalidCastException  
```  
  
## <a name="common-language-runtime"></a>CLR (Common Language Runtime) 
 `safe_cast`Umožňuje změnit typ výrazu a generovat ověřitelný kód MSIL.  
  
### <a name="syntax"></a>Syntaxe  
  
```cpp  
[cli]:: safe_cast<  
type-id  
>(  
expression  
)  
  
```  
  
### <a name="parameters"></a>Parametry  
 *id typu*  
 Obslužná rutina se odkaz na typ hodnoty, typ hodnoty nebo sledovací odkaz na typ hodnotou nebo odkazem.  
  
 *výraz*  
 Výraz, který se vyhodnotí jako popisovač pro odkaz nebo typ hodnoty, typ hodnoty nebo sledovací odkaz na typ hodnotou nebo odkazem.  
  
### <a name="remarks"></a>Poznámky  
 Výraz `safe_cast<` *id typu*`>(`*výraz* `)` převede operand výrazu na objekt typu id typu.  
  
 Kompilátor bude přijímat [static_cast](../cpp/static-cast-operator.md) ve většině míst, na které bude přijímat `safe_cast`.  Ale `safe_cast` záruku, že se k vytvoření ověřitelných MSIL, přičemž `static_cast` by mohla vést k neověřitelný MSIL.  V tématu [prázdná a ověřitelný kód (C + +/ CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md) a [Peverify.exe (Nástroj PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) Další informace o ověřitelný kód.  
  
 Jako `static_cast`, `safe_cast` vyvolá uživatelem definované převody.  
  
 Další informace o přetypování najdete v tématu [operátory přetypování](../cpp/casting-operators.md).  
  
 `safe_cast`se nevztahuje **const_cast –** (přetypovat rychle **const**).  
  
 `safe_cast`je v oboru názvů rozhraní příkazového řádku.  V tématu [Platform, default a rozhraní příkazového řádku obory názvů](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md) Další informace.  
  
 Další informace o **safe_cas**t, najdete v části:  
  
-   [Přetypování ve stylu jazyka pomocí možnosti/CLR (C + +/ CLI)](../windows/c-style-casts-with-clr-cpp-cli.md)  
  
-   [Postupy: Používání operátoru safe_cast v jazyce C++/CLI](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)  

### <a name="requirements"></a>Požadavky  
 – Možnost kompilátoru:   **/CLR**  
  
### <a name="examples"></a>Příklady  
 **Příklad**  
  
 Jeden příklad kde nebude přijímat kompilátor `static_cast` , ale bude přijímat `safe_cast` je pro přetypování mezi typy nesouvisejícími rozhraní.  S `safe_cast`, kompilátor nevydá Chyba převodu a provede kontrolu za běhu, zda je možné přetypování  
  
```cpp  
// safe_cast.cpp  
// compile with: /clr  
using namespace System;  
  
interface class I1 {};  
interface class I2 {};  
interface class I3 {};  
  
ref class X : public I1, public I2 {};  
  
int main() {  
   I1^ i1 = gcnew X;  
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X  
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead  
   try {  
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type  
   }   
   catch(InvalidCastException^) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 **Output**  
  
```Output  
Caught expected exception  
```  
  
## <a name="see-also"></a>Viz také  
 [Přípony komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)