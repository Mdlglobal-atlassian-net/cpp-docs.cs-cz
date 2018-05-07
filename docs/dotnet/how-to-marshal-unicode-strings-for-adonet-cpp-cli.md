---
title: 'Postupy: Zařazování řetězců v kódu Unicode pro technologii ADO.NET (C + +/ CLI) | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
ms.assetid: 1da090ff-6b53-40be-841f-dc79dfe8ba10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 15cf9e9806c0820ea5a410a93419016c2f678c65
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-unicode-strings-for-adonet-ccli"></a>Postupy: Zařazování řetězců v kódu Unicode pro technologii ADO.NET (C++/CLI)
Ukazuje, jak přidat nativní řetězec znaků Unicode (`wchar_t *`) k databázi a jak přeuspořádat <xref:System.String?displayProperty=fullName> z databáze na nativní řetězec.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída DatabaseClass vytvořena pro interakci s technologie ADO.NET <xref:System.Data.DataTable> objektu. Všimněte si, že tato třída je nativní C++ `class` (ve srovnání s `ref class` nebo `value class`). To je nezbytné, protože jsme chcete použít tuto třídu z nativního kódu a spravovaných typů nelze použít v nativním kódu. Tato třída se zkompiluje do cílové CLR, jak je uvedené `#pragma managed` – direktiva předchází deklaraci třídy. Další informace o tato direktiva najdete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).  
  
 Všimněte si privátního člena třídy DatabaseClass: `gcroot<DataTable ^> table`. Vzhledem k tomu, že nativní typy nemohou obsahovat spravované typy `gcroot` – klíčové slovo je nezbytné. Další informace o `gcroot`, najdete v části [postupy: deklarace zpracovává v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Zbytek kód v tomto příkladu je nativní kód C++, jako je indikován `#pragma unmanaged` předchází `main`. V tomto příkladu jsme se vytváření novou instanci třídy DatabaseClass a volání její metody pro vytvoření tabulky a naplnit některé řádky v tabulce. Všimněte si, že řetězce Unicode C++ jsou předávány jako hodnoty pro sloupec databáze StringCol. Uvnitř DatabaseClass, tyto řetězce přeuspořádány na spravované řetězce použití funkcionality v nalezen <xref:System.Runtime.InteropServices?displayProperty=fullName> oboru názvů. Konkrétně metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> se používá k zařazování `wchar_t *` k <xref:System.String>a metodu <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> se používá k zařazování <xref:System.String> k `wchar_t *`.  
  
> [!NOTE]
>  Paměti přidělené <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> musí být navrácena voláním buď <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> nebo `GlobalFree`.  
  
```  
// adonet_marshal_string_wide.cpp  
// compile with: /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll  
#include <comdef.h>  
#include <gcroot.h>  
#include <iostream>  
using namespace std;  
  
#using <System.Data.dll>  
using namespace System;  
using namespace System::Data;  
using namespace System::Runtime::InteropServices;  
  
#define MAXCOLS 100  
  
#pragma managed  
class DatabaseClass  
{  
public:  
    DatabaseClass() : table(nullptr) { }  
  
    void AddRow(wchar_t *stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringUni(  
            (IntPtr)stringColValue);  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("StringCol",  
            Type::GetType("System.String"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, wchar_t **values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringUni(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a wchar_t *.  
            values[i] = (wchar_t *)Marshal::StringToHGlobalUni(  
                (String ^)rows[i][columnStr]).ToPointer();  
        }  
  
        return len;  
    }  
  
private:  
    // Using gcroot, you can use a managed type in  
    // a native class.  
    gcroot<DataTable ^> table;  
};  
  
#pragma unmanaged  
int main()  
{  
    // Create a table and add a few rows to it.  
    DatabaseClass *db = new DatabaseClass();  
    db->CreateAndPopulateTable();  
    db->AddRow(L"This is string 1.");  
    db->AddRow(L"This is string 2.");  
  
    // Now retrieve the rows and display their contents.  
    wchar_t *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"StringCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        wcout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToHGlobalUni.  
        GlobalFree(values[i]);  
    }  
  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
StringCol: This is string 1.  
StringCol: This is string 2.  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zkompilovat kód z příkazového řádku, uložte příklad kódu v souboru s názvem adonet_marshal_string_wide.cpp a zadejte následující příkaz:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp  
    ```  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Informace na problémy se zabezpečením zahrnující ADO.NET naleznete v tématu [zabezpečení aplikací ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices>   
 [Přístup k datům s použitím technologie ADO.NET (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Vzájemná funkční spolupráce](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)