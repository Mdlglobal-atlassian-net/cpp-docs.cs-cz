---
title: 'Postupy: zařazování VARIANTPRO technologii ADO.NET (C + +/ CLI) | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
ms.assetid: 67a180a7-5691-48ab-8d85-7f75a68dde91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b442dcce2cdde28de8db1610971dd72dba84ab52
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-a-variant-for-adonet-ccli"></a>Postupy: Zařazování VARIANTpro technologii ADO.NET (C++/CLI)
Ukazuje, jak přidat nativní `VARIANT` k databázi a jak přeuspořádat <xref:System.Object?displayProperty=fullName> z databáze na nativní `VARIANT`.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída DatabaseClass vytvořena pro interakci s technologie ADO.NET <xref:System.Data.DataTable> objektu. Všimněte si, že tato třída je nativní C++ `class` (ve srovnání s `ref class` nebo `value class`). To je nezbytné, protože jsme chcete použít tuto třídu z nativního kódu a spravovaných typů nelze použít v nativním kódu. Tato třída se zkompiluje do cílové CLR, jak je uvedené `#pragma managed` – direktiva předchází deklaraci třídy. Další informace o tato direktiva najdete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).  
  
 Všimněte si privátního člena třídy DatabaseClass: `gcroot<DataTable ^> table`. Vzhledem k tomu, že nativní typy nemohou obsahovat spravované typy `gcroot` – klíčové slovo je nezbytné. Další informace o `gcroot`, najdete v části [postupy: deklarace zpracovává v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Zbytek kód v tomto příkladu je nativní kód C++, jako je indikován `#pragma unmanaged` předchází `main`. V tomto příkladu jsme se vytváření novou instanci třídy DatabaseClass a volání její metody pro vytvoření tabulky a naplnit některé řádky v tabulce. Všimněte si, že nativní `VARIANT` typy jsou předávány jako hodnoty pro sloupec databáze ObjectCol. Uvnitř DatabaseClass jsou tyto `VARIANT` typy přeuspořádány na spravované objekty použití funkcionality v nalezen <xref:System.Runtime.InteropServices?displayProperty=fullName> oboru názvů. Konkrétně metoda <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> se používá k zařazování `VARIANT` k <xref:System.Object>a metodu <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> se používá k zařazování <xref:System.Object> k `VARIANT`.  
  
```  
// adonet_marshal_variant.cpp  
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
  
    void AddRow(VARIANT *objectColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["ObjectCol"] = Marshal::GetObjectForNativeVariant(  
            IntPtr(objectColValue));  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ObjectCol",  
            Type::GetType("System.Object"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, VARIANT *values,  
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
            // Marshal each column value from a managed object  
            // to a VARIANT.  
            Marshal::GetNativeVariantForObject(  
                rows[i][columnStr], IntPtr(&values[i]));  
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
  
    BSTR bstr1 = SysAllocString(L"This is a BSTR in a VARIANT.");  
    VARIANT v1;  
    v1.vt = VT_BSTR;  
    v1.bstrVal = bstr1;  
    db->AddRow(&v1);  
  
    int i = 42;  
    VARIANT v2;  
    v2.vt = VT_I4;  
    v2.lVal = i;  
    db->AddRow(&v2);  
  
    // Now retrieve the rows and display their contents.  
    VARIANT values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ObjectCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        switch (values[i].vt)  
        {  
            case VT_BSTR:  
                wcout << L"ObjectCol: " << values[i].bstrVal << endl;  
                break;  
            case VT_I4:  
                cout << "ObjectCol: " << values[i].lVal << endl;  
                break;  
            default:  
                break;  
        }  
  
    }  
  
    SysFreeString(bstr1);  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
ObjectCol: This is a BSTR in a VARIANT.  
ObjectCol: 42  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zkompilovat kód z příkazového řádku, uložte příklad kódu v souboru s názvem adonet_marshal_variant.cpp a zadejte následující příkaz:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp  
    ```  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Informace na problémy se zabezpečením zahrnující ADO.NET naleznete v tématu [zabezpečení aplikací ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices>   
 [Přístup k datům s použitím technologie ADO.NET (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Vzájemná funkční spolupráce](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)