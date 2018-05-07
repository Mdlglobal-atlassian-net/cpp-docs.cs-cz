---
title: 'Postupy: Zařazování SAFEARRAY pro technologii ADO.NET (C + +/ CLI) | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: 1034b9d7-ecf1-40f7-a9ee-53180e87a58c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ddd6250fac293fef58ccc21894661ddf32e3fa61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-a-safearray-for-adonet-ccli"></a>Postupy: Zařazování SAFEARRAY pro technologii ADO.NET (C++/CLI)
Ukazuje, jak přidat nativní `SAFEARRAY` k databázi a jak přeuspořádat spravované pole z databáze na nativní `SAFEARRAY`.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída DatabaseClass vytvořena pro interakci s technologie ADO.NET <xref:System.Data.DataTable> objektu. Všimněte si, že tato třída je nativní C++ `class` (ve srovnání s `ref class` nebo `value class`). To je nezbytné, protože jsme chcete použít tuto třídu z nativního kódu a spravovaných typů nelze použít v nativním kódu. Tato třída se zkompiluje do cílové CLR, jak je uvedené `#pragma managed` – direktiva předchází deklaraci třídy. Další informace o tato direktiva najdete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).  
  
 Všimněte si privátního člena třídy DatabaseClass: `gcroot<DataTable ^> table`. Vzhledem k tomu, že nativní typy nemohou obsahovat spravované typy `gcroot` – klíčové slovo je nezbytné. Další informace o `gcroot`, najdete v části [postupy: deklarace zpracovává v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Zbytek kód v tomto příkladu je nativní kód C++, jako je indikován `#pragma unmanaged` předchází `main`. V tomto příkladu jsme se vytváření novou instanci třídy DatabaseClass a volání její metody pro vytvoření tabulky a naplnit některé řádky v tabulce. Všimněte si, že nativní `SAFEARRAY` typy jsou předávány jako hodnoty pro sloupec databáze ArrayIntsCol. Uvnitř DatabaseClass jsou tyto `SAFEARRAY` typy přeuspořádány na spravované objekty použití funkcionality v nalezen <xref:System.Runtime.InteropServices?displayProperty=fullName> oboru názvů. Konkrétně metoda <xref:System.Runtime.InteropServices.Marshal.Copy%2A> se používá k zařazování `SAFEARRAY` na spravované pole celých čísel a metodu <xref:System.Runtime.InteropServices.Marshal.Copy%2A> se používá k přeuspořádat spravované pole celých čísel na `SAFEARRAY`.  
  
```  
// adonet_marshal_safearray.cpp  
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
  
    void AddRow(SAFEARRAY *arrayIntsColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        int len = arrayIntsColValue->rgsabound[0].cElements;  
        array<int> ^arr = gcnew array<int>(len);  
  
        int *pData;  
        SafeArrayAccessData(arrayIntsColValue, (void **)&pData);  
        Marshal::Copy(IntPtr(pData), arr, 0, len);  
        SafeArrayUnaccessData(arrayIntsColValue);  
  
        row["ArrayIntsCol"] = arr;  
        table->Rows->Add(row);  
    }  
  
    void CreateAndPopulateTable()  
    {  
        // Create a simple DataTable.  
        table = gcnew DataTable("SampleTable");  
  
        // Add a column of type String to the table.  
        DataColumn ^column1 = gcnew DataColumn("ArrayIntsCol",  
            Type::GetType("System.Int32[]"));  
        table->Columns->Add(column1);  
    }  
  
    int GetValuesForColumn(wchar_t *dataColumn, SAFEARRAY **values,  
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
            // Marshal each column value from a managed array  
            // of Int32s to a SAFEARRAY of type VT_I4.  
            values[i] = SafeArrayCreateVector(VT_I4, 0, 10);  
            int *pData;  
            SafeArrayAccessData(values[i], (void **)&pData);  
            Marshal::Copy((array<int> ^)rows[i][columnStr], 0,  
                IntPtr(pData), 10);  
            SafeArrayUnaccessData(values[i]);  
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
  
    // Create a standard array.  
    int originalArray[] = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
    // Create a SAFEARRAY.  
    SAFEARRAY *psa;  
    psa = SafeArrayCreateVector(VT_I4, 0, 10);  
  
    // Copy the data from the original array to the SAFEARRAY.  
    int *pData;  
    HRESULT hr = SafeArrayAccessData(psa, (void **)&pData);  
    memcpy(pData, &originalArray, 40);  
    SafeArrayUnaccessData(psa);  
    db->AddRow(psa);  
  
    // Now retrieve the rows and display their contents.  
    SAFEARRAY *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        L"ArrayIntsCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        int *pData;  
        SafeArrayAccessData(values[i], (void **)&pData);  
        for (int j = 0; j < 10; j++)  
        {  
            cout << pData[j] << " ";  
        }  
        cout << endl;  
        SafeArrayUnaccessData(values[i]);  
  
        // Deallocate the memory allocated using  
        // SafeArrayCreateVector.  
        SafeArrayDestroy(values[i]);  
    }  
  
    SafeArrayDestroy(psa);  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
0 1 2 3 4 5 6 7 8 9   
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zkompilovat kód z příkazového řádku, uložte příklad kódu v souboru s názvem adonet_marshal_safearray.cpp a zadejte následující příkaz:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp  
    ```  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Informace na problémy se zabezpečením zahrnující ADO.NET naleznete v tématu [zabezpečení aplikací ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices>   
 [Přístup k datům s použitím technologie ADO.NET (C + +/ CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)   
 [ADO.NET](/dotnet/framework/data/adonet/index)   
 [Vzájemná funkční spolupráce](http://msdn.microsoft.com/en-us/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
 [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)