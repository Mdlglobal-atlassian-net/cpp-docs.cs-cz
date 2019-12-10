---
title: 'Postupy: Rozšíření knihovny zařazování'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- Marshaling Library, extending
ms.assetid: 4c4a56d7-1d44-4118-b85f-f9686515e6e9
ms.openlocfilehash: ab3b17638e07a54189803c83163db67c5ebf82a5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988487"
---
# <a name="how-to-extend-the-marshaling-library"></a>Postupy: Rozšíření knihovny zařazování

Toto téma vysvětluje, jak rozšiřuje zařazovací knihovnu tak, aby poskytovala více převodů mezi datovými typy. Uživatelé mohou rozšířenou knihovnu zařazování pro všechny převody dat, které nejsou aktuálně podporovány knihovnou.

Zařazování knihovny můžete roztáhnout jedním ze dvou způsobů – s nebo bez [Marshal_context třídy](../dotnet/marshal-context-class.md). Projděte si [Přehled zařazování v C++ ](../dotnet/overview-of-marshaling-in-cpp.md) tématu, abyste zjistili, zda nový převod vyžaduje kontext.

V obou případech nejprve vytvoříte soubor pro nové převody zařazování. To uděláte tak, abyste zachovali integritu standardních souborů knihoven. Chcete-li přenést projekt na jiný počítač nebo na jiný programátora, je nutné zkopírovat nový soubor zařazování společně se zbytkem projektu. Tímto způsobem bude uživatel, který obdrží projekt, zaručit, že obdrží nové převody a nebude muset upravovat žádné soubory knihovny.

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-does-not-require-a-context"></a>Postup rozšiřování zařazovací knihovny s převodem, který nevyžaduje kontext

1. Vytvořte soubor pro uložení nových funkcí zařazování, například MyMarshal. h.

1. Zahrnout jeden nebo více souborů zařazovací knihovny:

   - zařazování. h pro základní typy

   - marshal_windows. h pro datové typy Windows.

   - marshal_cppstd. h pro C++ standardní datové typy knihovny.

   - marshal_atl. h pro datové typy knihovny ATL.

1. Použijte kód na konci těchto kroků k zápisu funkce pro převod. V tomto kódu na je typ pro převod na, od je typ, ze kterého se má převést, a `from` je parametr, který má být převeden.

1. Nahraďte komentář o logice převodu kódem pro převedení `from` parametru na objekt typu na typ a vraťte převedený objekt.

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

### <a name="to-extend-the-marshaling-library-with-a-conversion-that-requires-a-context"></a>Postup rozšiřování zařazovací knihovny s převodem, který vyžaduje kontext

1. Vytvořte soubor pro uložení nových funkcí zařazování, například MyMarshal. h.

1. Zahrnout jeden nebo více souborů zařazovací knihovny:

   - zařazování. h pro základní typy

   - marshal_windows. h pro datové typy Windows.

   - marshal_cppstd. h pro C++ standardní datové typy knihovny.

   - marshal_atl. h pro datové typy knihovny ATL.

1. Použijte kód na konci těchto kroků k zápisu funkce pro převod. V tomto kódu na je typ, na který chcete převést, od je typ, ze kterého se má převést, `toObject` je ukazatel, do kterého se má výsledek uložit, a `fromObject` je parametr, který má být převeden.

1. Nahraďte komentář o inicializaci pomocí kódu pro inicializaci `toPtr` k odpovídající prázdné hodnotě. Pokud je například ukazatel, nastavte jej na `NULL`.

1. Nahraďte komentář o logice převodu kódem pro převedení `from` *parametru na objekt typu.* Tento převedený objekt bude uložen v `toPtr`.

1. Nahraďte komentář o nastavení `toObject` kódem pro nastavení `toObject` převedeného objektu.

1. Nahraďte komentář o čištění nativních prostředků kódem pro uvolnění paměti přidělené `toPtr`. Pokud `toPtr` přidělenou paměť pomocí `new`, použijte `delete` k uvolnění paměti.

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

Následující příklad rozšiřuje zařazovací knihovnu s převodem, který nevyžaduje kontext. V tomto příkladu kód převede informace o zaměstnanci z nativního datového typu na spravovaný datový typ.

```cpp
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

V předchozím příkladu funkce `marshal_as` vrací popisovač pro převedená data. To bylo provedeno, aby se zabránilo vytvoření další kopie dat. Vrácení proměnné přímo do by mělo být spojeno s zbytečnými náklady na výkon.

```Output
Managed name: Jeff Smith
Managed address: 123 Main Street
Managed zip code: 98111
```

## <a name="example"></a>Příklad

Následující příklad převede informace o zaměstnanci ze spravovaného datového typu na nativní datový typ. Tento převod vyžaduje zařazovací kontext.

```cpp
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
