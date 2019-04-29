---
title: 'Postupy: Rozšíření knihovny zařazování'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: f289539807b1e9499cef51427d3f6a494545cc60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387302"
---
# <a name="how-to-extend-the-marshaling-library"></a>Postupy: Rozšíření knihovny zařazování

Toto téma vysvětluje, jak rozšíření knihovny zařazování poskytnout další převody mezi datovými typy. Uživatelé můžou rozšíření knihovny zařazování pro všechny převody dat není aktuálně podporovaná knihovny.

Můžete rozšíření knihovny zařazování v jednom ze dvou způsobů - s nebo bez něj [marshal_context Class](../dotnet/marshal-context-class.md). Zkontrolujte [Overview of Marshaling in C++](../dotnet/overview-of-marshaling-in-cpp.md) tématu k určení, zda nový převod vyžaduje kontext.

V obou případech se nejprve vytvořit soubor pro nové zařazování převody. Uděláte zachování integrity standard zařazování soubory knihovny. Pokud chcete přenést do projektu do jiného počítače nebo jiné programátora, musíte zkopírovat nový zařazování soubor se zbytkem projektu. Tímto způsobem uživatel, který obdrží projektu budou zaručovat přijímat nové převody a nebude mít úprava všech souborech knihoven.

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>K rozšíření knihovny zařazování se převod, který nevyžaduje, aby kontext

1. Vytvořte soubor pro uložení nové zařazování funkce, například MyMarshal.h.

1. Zahrnout jednu nebo více souborů knihovny zařazování:

   - Marshal.h základních typů.

   - marshal_windows.h pro datové typy systému windows.

   - marshal_cppstd.h pro C++ datové typy standardní knihovny.

   - marshal_atl.h ATL datových typů.

1. Pomocí kódu na konci tyto kroky pro zápis funkce pro převod. V tomto kódu je typ, který chcete převést, od je typ, který chcete převést, a `from` je parametr, který má být převeden.

1. Nahraďte kód, který převede komentář o převod logiku `from` parametru do objektu na typ a vrátí objekt převedený.

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

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>K rozšíření knihovny zařazování se převod, který vyžaduje kontext

1. Vytvořit soubor pro uložení nové zařazování funkce, například MyMarshal.h

1. Zahrnout jednu nebo více souborů knihovny zařazování:

   - Marshal.h základních typů.

   - marshal_windows.h pro datové typy systému windows.

   - marshal_cppstd.h pro C++ datové typy standardní knihovny.

   - marshal_atl.h ATL datových typů.

1. Pomocí kódu na konci tyto kroky pro zápis funkce pro převod. V tomto kódu je typ, který chcete převést, od je typ, který chcete převést, `toObject` je ukazatel, ve kterém k ukládání výsledků, a `fromObject` je parametr, který má být převeden.

1. Nahraďte komentář o inicializaci pomocí kód pro inicializaci `toPtr` odpovídající prázdnou hodnotu. Například pokud je ukazatel, nastavte ho na `NULL`.

1. Nahraďte kód, který převede komentář o převod logiku `from` parametru do objektu *na* typu. Převedený objekt se uloží v `toPtr`.

1. Nahraďte komentáře týkající se nastavení `toObject` pomocí kódu pro nastavení `toObject` převedený objekt.

1. Nahraďte komentář o čištění nativní prostředky s kód pro uvolnění paměti přidělené `toPtr`. Pokud `toPtr` přidělila paměť pomocí `new`, použijte `delete` uvolnit paměť.

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

Následující příklad rozšiřuje zařazovací knihovna se převod, který nevyžaduje kontextu. V tomto příkladu kód převede informace o zaměstnancích z nativního datového typu na typ spravovaná data.

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

V předchozím příkladu `marshal_as` vrátí funkce popisovač převedená data. To se dělá jako prevence vytváření další kopie dat. Vrací proměnnou přímo by mít náklady na zbytečně výkon přidruženo.

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>Příklad

Následující příklad převádí informace o zaměstnancích z typu spravovaných dat do nativního datového typu. Tento převod vyžaduje zařazování kontext.

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

## <a name="see-also"></a>Viz také:

[Přehled zařazování v jazyce C++](../dotnet/overview-of-marshaling-in-cpp.md)
