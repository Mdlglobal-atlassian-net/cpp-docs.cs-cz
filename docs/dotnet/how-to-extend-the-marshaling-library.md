---
title: "Postupy: rozšíření knihovny zařazování | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ee919e1faa37959d25e8e42581c8cde80d640337
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-extend-the-marshaling-library"></a>Postupy: Rozšíření knihovny zařazování
Toto téma vysvětluje, jak rozšíření knihovny zařazování zajistit další převody mezi datovými typy. Uživatelé mohou rozšíření knihovny zařazování pro všechny převody dat není aktuálně podporovaná knihovny.  
  
 Můžete rozšíření knihovny zařazování v jednom ze dvou způsobů – bez ohledu [marshal_context – třída](../dotnet/marshal-context-class.md). Zkontrolujte [přehled zařazování v jazyku C++](../dotnet/overview-of-marshaling-in-cpp.md) tématu, které chcete zjistit, zda nový převod vyžaduje kontextu.  
  
 V obou případech nejprve vytvořte soubor pro nové zařazování převody. Je to provést pro zachování integrity standardní zařazování soubory knihovny. Pokud chcete k portu projektu do jiného počítače nebo jiným programátorům, musíte zkopírovat nový soubor zařazování společně s zbytek projektu. Tímto způsobem uživatel přijetí projektu bude zaručit přijímat nové převody a nebudete muset upravit všechny soubory knihoven.  
  
### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>K rozšíření knihovny zařazování s převodu, který nevyžaduje kontextu  
  
1.  Vytvořte soubor pro uložení nové zařazování funkce, například MyMarshal.h.  
  
2.  Zahrnout jeden nebo více souborů Knihovna zařazování:  
  
    -   Marshal.h pro základní typy.  
  
    -   marshal_windows.h pro datové typy systému windows.  
  
    -   marshal_cppstd.h pro standardní knihovna C++ datové typy.  
  
    -   marshal_atl.h pro ATL datové typy.  
  
3.  Použijte kód na konci těchto kroků k zápisu funkci pro převod. V tomto kódu je převést na typ, od je typ převést, a `from` je parametr, který má být převeden.  
  
4.  Nahraďte kód převést komentář o převod logiky `from` parametru do objektu na typ a vrátí převedený objekt.  
  
```  
namespace msclr {  
   namespace interop {  
      template<>  
      inline TO marshal_as<TO, FROM> (const FROM& from) {  
         // Insert conversion logic here, and return a TO parameter.  
      }  
   }  
}  
```  
  
### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>K rozšíření knihovny zařazování s převodu, který vyžaduje kontext  
  
1.  Vytvořit soubor pro uložení nové zařazování funkce, například MyMarshal.h  
  
2.  Zahrnout jeden nebo více souborů Knihovna zařazování:  
  
    -   Marshal.h pro základní typy.  
  
    -   marshal_windows.h pro datové typy systému windows.  
  
    -   marshal_cppstd.h pro standardní knihovna C++ datové typy.  
  
    -   marshal_atl.h pro ATL datové typy.  
  
3.  Použijte kód na konci těchto kroků k zápisu funkci pro převod. V tomto kódu je převést na typ, od je typ převést, `toObject` ukazatel do které chcete uložit výsledek a `fromObject` je parametr, který má být převeden.  
  
4.  Nahraďte komentář o inicializaci s kód pro inicializaci `toPtr` na odpovídající hodnotu prázdný. Například pokud je ukazatel, nastavte ji na `NULL`.  
  
5.  Nahraďte kód převést komentář o převod logiky `from` parametru do objektu *na* typu. Tento převedený objekt se uloží v `toPtr`.  
  
6.  Nahraďte komentář o nastavení `toObject` kódem nastavit `toObject` k převedený objekt.  
  
7.  Nahraďte komentář o vyčištění nativní prostředky s kódem uvolnit všechny přidělené paměti `toPtr`. Pokud `toPtr` přidělené paměti pomocí `new`, použijte `delete` k uvolnění paměti.  
  
```  
namespace msclr {  
   namespace interop {  
      template<>  
      ref class context_node<TO, FROM> : public context_node_base  
      {  
      private:  
         TO toPtr;  
      public:  
         context_node(TO& toObject, FROM fromObject)  
         {  
            // (Step 4) Initialize toPtr to the appropriate empty value.  
            // (Step 5) Insert conversion logic here.  
            // (Step 6) Set toObject to the converted parameter.  
         }  
         ~context_node()  
         {  
            this->!context_node();  
         }  
      protected:  
         !context_node()  
         {  
            // (Step 7) Clean up native resources.  
         }  
      };  
   }  
}   
```  
  
## <a name="example"></a>Příklad  
 Následující příklad rozšíření knihovny zařazování s převodu, který nevyžaduje kontextu. V tomto příkladu převede kód na spravovaný datový typ z nativní datový typ informace o zaměstnancích.  
  
```  
// MyMarshalNoContext.cpp  
// compile with: /clr  
#include <msclr/marshal.h>  
  
value struct ManagedEmp {  
   System::String^ name;  
   System::String^ address;  
   int zipCode;  
};  
  
struct NativeEmp {  
   char* name;  
   char* address;  
   int zipCode;  
};  
  
namespace msclr {  
   namespace interop {  
      template<>  
      inline ManagedEmp^ marshal_as<ManagedEmp^, NativeEmp> (const NativeEmp& from) {  
         ManagedEmp^ toValue = gcnew ManagedEmp;  
         toValue->name = marshal_as<System::String^>(from.name);  
         toValue->address = marshal_as<System::String^>(from.address);  
         toValue->zipCode = from.zipCode;  
         return toValue;  
      }  
   }  
}  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {   
   NativeEmp employee;  
  
   employee.name = "Jeff Smith";  
   employee.address = "123 Main Street";  
   employee.zipCode = 98111;  
  
   ManagedEmp^ result = marshal_as<ManagedEmp^>(employee);  
  
   Console::WriteLine("Managed name: {0}", result->name);  
   Console::WriteLine("Managed address: {0}", result->address);  
   Console::WriteLine("Managed zip code: {0}", result->zipCode);  
  
   return 0;  
}  
```  
  
 V předchozím příkladu `marshal_as` funkce vrátí popisovač převedená data. To se dělá jako prevence vytváření další kopie data. Vrací proměnnou přímo by mít nákladů na zbytečně výkon s ním spojená.  
  
```Output  
Managed name: Jeff Smith  
Managed address: 123 Main Street  
Managed zip code: 98111  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad převede na nativní datový typ informace o zaměstnancích ze spravovaných datového typu. Tento převod vyžaduje zařazování kontextu.  
  
```  
// MyMarshalContext.cpp  
// compile with: /clr  
#include <stdlib.h>  
#include <string.h>  
#include <msclr/marshal.h>  
  
value struct ManagedEmp {  
   System::String^ name;  
   System::String^ address;  
   int zipCode;  
};  
  
struct NativeEmp {  
   const char* name;  
   const char* address;  
   int zipCode;  
};  
  
namespace msclr {  
   namespace interop {  
      template<>  
      ref class context_node<NativeEmp*, ManagedEmp^> : public context_node_base  
      {  
      private:  
         NativeEmp* toPtr;  
         marshal_context context;  
      public:  
         context_node(NativeEmp*& toObject, ManagedEmp^ fromObject)  
         {  
            // Conversion logic starts here  
            toPtr = NULL;  
  
            const char* nativeName;  
            const char* nativeAddress;  
  
            // Convert the name from String^ to const char*.  
            System::String^ tempValue = fromObject->name;  
            nativeName = context.marshal_as<const char*>(tempValue);  
  
            // Convert the address from String^ to const char*.  
            tempValue = fromObject->address;  
            nativeAddress = context.marshal_as<const char*>(tempValue);  
  
            toPtr = new NativeEmp();  
            toPtr->name = nativeName;  
            toPtr->address = nativeAddress;  
            toPtr->zipCode = fromObject->zipCode;  
  
            toObject = toPtr;  
         }  
         ~context_node()  
         {  
            this->!context_node();  
         }  
      protected:  
         !context_node()  
         {  
            // When the context is deleted, it will free the memory  
            // allocated for toPtr->name and toPtr->address, so toPtr  
            // is the only memory that needs to be freed.  
            if (toPtr != NULL) {  
               delete toPtr;  
               toPtr = NULL;  
            }  
         }  
      };  
   }  
}   
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   ManagedEmp^ employee = gcnew ManagedEmp();  
  
   employee->name = gcnew String("Jeff Smith");  
   employee->address = gcnew String("123 Main Street");  
   employee->zipCode = 98111;  
  
   marshal_context context;  
   NativeEmp* result = context.marshal_as<NativeEmp*>(employee);  
  
   if (result != NULL) {  
      printf_s("Native name: %s\nNative address: %s\nNative zip code: %d\n",  
         result->name, result->address, result->zipCode);  
   }  
  
   return 0;  
}  
```  
  
```Output  
Native name: Jeff Smith  
Native address: 123 Main Street  
Native zip code: 98111  
```  
  
## <a name="see-also"></a>Viz také  
 [Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)