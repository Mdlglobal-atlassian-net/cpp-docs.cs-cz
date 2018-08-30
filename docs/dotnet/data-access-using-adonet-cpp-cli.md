---
title: Přístup k datům pomocí technologie ADO.NET (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ADO.NET [C++]
- .NET Framework [C++], data access
- databases [C++], accessing in C++
- data access [C++], ADO.NET
- data [C++], ADO.NET
- native strings [C++]
- ADO.NET [C++], marshaling ANSI strings
- strings [C++], ADO.NET
- BSTRs, strings
- ADO.NET [C++], marshaling BSTR strings
- strings [C++], marshaling BSTR strings
- ADO.NET [C++], marshaling Unicode strings
- Unicode [C++], strings
- strings [C++], Unicode
- VARIANT, marshaling
- ADO.NET [C++], marshaling VARIANT types
- VARIANT
- SAFEARRAY, marshaling
- ADO.NET [C++], marshaling SAFEARRAY types
ms.assetid: b0cd987d-1ea7-4f76-ba01-cbd52503d06d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3d87d41b97f587f2546df246044eaf8df3bba373
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221975"
---
# <a name="data-access-using-adonet-ccli"></a>Přístup k datům s použitím technologie ADO.NET (C++/CLI)
ADO.NET je rozhraní API pro .NET Framework pro přístup k datům a zajišťuje výkon a snadnost použití bezkonkurenční pomocí předchozích řešení přístupu k data. Tato část popisuje některé z problémů týkajících se technologie ADO.NET, které jsou jedinečné pro uživatele jazyka Visual C++, jako je například zařazování nativní typy.  
  
 ADO.NET běží v části Common Language Runtime (CLR). Proto každou aplikaci, která komunikuje pomocí ADO.NET musí také cílit na modulu CLR. Ale to neznamená, že nemůžete použít nativních aplikací ADO.NET. Tyto příklady ukazují, jak pracovat s databází technologie ADO.NET z nativního kódu.  
  
## <a name="marshal_ansi"></a> Zařazování řetězců ANSI pro technologii ADO.NET
Ukazuje, jak přidat nativní řetězec (`char *`) k databázi a způsobu zařazení <xref:System.String?displayProperty=fullName> z databáze nativní řetězec.  
  
### <a name="example"></a>Příklad  
 V tomto příkladu je třída DatabaseClass vytvořena pro interakci s technologie ADO.NET <xref:System.Data.DataTable> objektu. Všimněte si, že tato třída je nativní kód C++ `class` (ve srovnání s `ref class` nebo `value class`). To je nezbytné, protože chceme použít tuto třídu z nativního kódu a spravovanými typy nelze používat v nativním kódu. Tato třída se zkompiluje do cílové CLR, jak je uvedeno ve `#pragma managed` směrnice předchozí deklaraci třídy. Další informace o této směrnice, naleznete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).  
  
 Všimněte si soukromému členu třídy DatabaseClass: `gcroot<DataTable ^> table`. Protože nativní typy nemůžou obsahovat spravované typy `gcroot` – klíčové slovo je nezbytné. Další informace o `gcroot`, naleznete v tématu [postupy: deklarování zpracovává v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Zbytek kódu v tomto příkladu je nativní kód C++, jako je indikován `#pragma unmanaged` předchází `main`. V tomto příkladu jsme se vytváří novou instanci třídy DatabaseClass a volání metody k vytvoření tabulky a naplňte několik řádků v tabulce. Všimněte si, že nativní C++ řetězce jsou předávány jako hodnoty pro sloupec databáze StringCol. Uvnitř DatabaseClass, tyto řetězce jsou zařazeny do spravované řetězce pomocí zařazování funkcemi produktu <xref:System.Runtime.InteropServices?displayProperty=fullName> oboru názvů. Konkrétně metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> použitý k zařazování `char *` k <xref:System.String>a metodu <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> použitý k zařazování <xref:System.String> k `char *`.  
  
> [!NOTE]
>  Přidělená paměť <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> musí uvolnit voláním buď <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> nebo `GlobalFree`.  
  
```cpp  
// adonet_marshal_string_native.cpp  
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
  
    void AddRow(char *stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringAnsi(  
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
  
    int GetValuesForColumn(char *dataColumn, char **values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringAnsi(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a char *.  
            values[i] = (char *)Marshal::StringToHGlobalAnsi(  
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
    db->AddRow("This is string 1.");  
    db->AddRow("This is string 2.");  
  
    // Now retrieve the rows and display their contents.  
    char *values[MAXCOLS];  
    int len = db->GetValuesForColumn(  
        "StringCol", values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        cout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToHGlobalAnsi.  
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
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Ke kompilaci kódu z příkazového řádku, uložit do souboru s názvem adonet_marshal_string_native.cpp příklad kódu a zadejte následující příkaz:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp  
    ```  

## <a name="marshal_bstr"></a> Zařazování řetězců BSTR pro technologii ADO.NET
Ukazuje, jak přidat řetězec modelu COM (`BSTR`) k databázi a způsobu zařazení <xref:System.String?displayProperty=fullName> z databáze `BSTR`.  
  
### <a name="example"></a>Příklad  
 V tomto příkladu je třída DatabaseClass vytvořena pro interakci s technologie ADO.NET <xref:System.Data.DataTable> objektu. Všimněte si, že tato třída je nativní kód C++ `class` (ve srovnání s `ref class` nebo `value class`). To je nezbytné, protože chceme použít tuto třídu z nativního kódu a spravovanými typy nelze používat v nativním kódu. Tato třída se zkompiluje do cílové CLR, jak je uvedeno ve `#pragma managed` směrnice předchozí deklaraci třídy. Další informace o této směrnice, naleznete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).  
  
 Všimněte si soukromému členu třídy DatabaseClass: `gcroot<DataTable ^> table`. Protože nativní typy nemůžou obsahovat spravované typy `gcroot` – klíčové slovo je nezbytné. Další informace o `gcroot`, naleznete v tématu [postupy: deklarování zpracovává v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Zbytek kódu v tomto příkladu je nativní kód C++, jako je indikován `#pragma unmanaged` předchází `main`. V tomto příkladu jsme se vytváří novou instanci třídy DatabaseClass a volání metody k vytvoření tabulky a naplňte několik řádků v tabulce. Všimněte si, že řetězců modelu COM jsou předávány jako hodnoty pro sloupec databáze StringCol. Uvnitř DatabaseClass, tyto řetězce jsou zařazeny do spravované řetězce pomocí zařazování funkcemi produktu <xref:System.Runtime.InteropServices?displayProperty=fullName> oboru názvů. Konkrétně metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> použitý k zařazování `BSTR` k <xref:System.String>a metodu <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> použitý k zařazování <xref:System.String> k `BSTR`.  
  
> [!NOTE]
>  Přidělená paměť <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> musí uvolnit voláním buď <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> nebo `SysFreeString`.  
  
``` cpp 
// adonet_marshal_string_bstr.cpp  
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
  
    void AddRow(BSTR stringColValue)  
    {  
        // Add a row to the table.  
        DataRow ^row = table->NewRow();  
        row["StringCol"] = Marshal::PtrToStringBSTR(  
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
  
    int GetValuesForColumn(BSTR dataColumn, BSTR *values,  
        int valuesLength)  
    {  
        // Marshal the name of the column to a managed  
        // String.  
        String ^columnStr = Marshal::PtrToStringBSTR(  
                (IntPtr)dataColumn);  
  
        // Get all rows in the table.  
        array<DataRow ^> ^rows = table->Select();  
        int len = rows->Length;  
        len = (len > valuesLength) ? valuesLength : len;  
        for (int i = 0; i < len; i++)  
        {  
            // Marshal each column value from a managed string  
            // to a BSTR.  
            values[i] = (BSTR)Marshal::StringToBSTR(  
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
  
    BSTR str1 = SysAllocString(L"This is string 1.");  
    db->AddRow(str1);  
  
    BSTR str2 = SysAllocString(L"This is string 2.");  
    db->AddRow(str2);  
  
    // Now retrieve the rows and display their contents.  
    BSTR values[MAXCOLS];  
    BSTR str3 = SysAllocString(L"StringCol");  
    int len = db->GetValuesForColumn(  
        str3, values, MAXCOLS);  
    for (int i = 0; i < len; i++)  
    {  
        wcout << "StringCol: " << values[i] << endl;  
  
        // Deallocate the memory allocated using  
        // Marshal::StringToBSTR.  
        SysFreeString(values[i]);  
    }  
  
    SysFreeString(str1);  
    SysFreeString(str2);  
    SysFreeString(str3);  
    delete db;  
  
    return 0;  
}  
```  
  
```Output  
StringCol: This is string 1.  
StringCol: This is string 2.  
```  
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Ke kompilaci kódu z příkazového řádku, uložit do souboru s názvem adonet_marshal_string_native.cpp příklad kódu a zadejte následující příkaz:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp  
    ```  

## <a name="marshal_unicode"></a> Zařazování řetězců kódování Unicode pro technologii ADO.NET
Ukazuje, jak přidat nativní řetězec znaků Unicode (`wchar_t *`) k databázi a způsobu zařazení <xref:System.String?displayProperty=fullName> z databáze nativní řetězec znaků Unicode.  
  
### <a name="example"></a>Příklad  
 V tomto příkladu je třída DatabaseClass vytvořena pro interakci s technologie ADO.NET <xref:System.Data.DataTable> objektu. Všimněte si, že tato třída je nativní kód C++ `class` (ve srovnání s `ref class` nebo `value class`). To je nezbytné, protože chceme použít tuto třídu z nativního kódu a spravovanými typy nelze používat v nativním kódu. Tato třída se zkompiluje do cílové CLR, jak je uvedeno ve `#pragma managed` směrnice předchozí deklaraci třídy. Další informace o této směrnice, naleznete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).  
  
 Všimněte si soukromému členu třídy DatabaseClass: `gcroot<DataTable ^> table`. Protože nativní typy nemůžou obsahovat spravované typy `gcroot` – klíčové slovo je nezbytné. Další informace o `gcroot`, naleznete v tématu [postupy: deklarování zpracovává v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Zbytek kódu v tomto příkladu je nativní kód C++, jako je indikován `#pragma unmanaged` předchází `main`. V tomto příkladu jsme se vytváří novou instanci třídy DatabaseClass a volání metody k vytvoření tabulky a naplňte několik řádků v tabulce. Všimněte si, že řetězce Unicode C++ jsou předávány jako hodnoty pro sloupec databáze StringCol. Uvnitř DatabaseClass, tyto řetězce jsou zařazeny do spravované řetězce pomocí zařazování funkcemi produktu <xref:System.Runtime.InteropServices?displayProperty=fullName> oboru názvů. Konkrétně metoda <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> použitý k zařazování `wchar_t *` k <xref:System.String>a metodu <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> použitý k zařazování <xref:System.String> k `wchar_t *`.  
  
> [!NOTE]
>  Přidělená paměť <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> musí uvolnit voláním buď <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> nebo `GlobalFree`.  
  
```cpp  
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
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Ke kompilaci kódu z příkazového řádku, uložit do souboru s názvem adonet_marshal_string_wide.cpp příklad kódu a zadejte následující příkaz:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp  
    ```  

## <a name="marshal_variant"></a> Zařazování VARIANTPRO technologii ADO.NET
Ukazuje, jak přidat nativní `VARIANT` k databázi a způsobu zařazení <xref:System.Object?displayProperty=fullName> z databáze na nativní `VARIANT`.  
  
### <a name="example"></a>Příklad  
 V tomto příkladu je třída DatabaseClass vytvořena pro interakci s technologie ADO.NET <xref:System.Data.DataTable> objektu. Všimněte si, že tato třída je nativní kód C++ `class` (ve srovnání s `ref class` nebo `value class`). To je nezbytné, protože chceme použít tuto třídu z nativního kódu a spravovanými typy nelze používat v nativním kódu. Tato třída se zkompiluje do cílové CLR, jak je uvedeno ve `#pragma managed` směrnice předchozí deklaraci třídy. Další informace o této směrnice, naleznete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).  
  
 Všimněte si soukromému členu třídy DatabaseClass: `gcroot<DataTable ^> table`. Protože nativní typy nemůžou obsahovat spravované typy `gcroot` – klíčové slovo je nezbytné. Další informace o `gcroot`, naleznete v tématu [postupy: deklarování zpracovává v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Zbytek kódu v tomto příkladu je nativní kód C++, jako je indikován `#pragma unmanaged` předchází `main`. V tomto příkladu jsme se vytváří novou instanci třídy DatabaseClass a volání metody k vytvoření tabulky a naplňte několik řádků v tabulce. Všimněte si, že nativní `VARIANT` typy jsou předávány jako hodnoty pro sloupec databáze ObjectCol. Uvnitř DatabaseClass tyto `VARIANT` typy, které jsou zařazeny do spravované objekty zařazování funkce součástí <xref:System.Runtime.InteropServices?displayProperty=fullName> oboru názvů. Konkrétně metoda <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> použitý k zařazování `VARIANT` k <xref:System.Object>a metodu <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> použitý k zařazování <xref:System.Object> k `VARIANT`.  
  
```cpp  
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
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Ke kompilaci kódu z příkazového řádku, uložit do souboru s názvem adonet_marshal_variant.cpp příklad kódu a zadejte následující příkaz:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp  
    ```  

## <a name="marshal_safearray"></a> Zařazování SAFEARRAY pro technologii ADO.NET
Ukazuje, jak přidat nativní `SAFEARRAY` k databázi a způsobu zařazení spravovaného pole z databáze na nativní `SAFEARRAY`.  
  
### <a name="example"></a>Příklad  
 V tomto příkladu je třída DatabaseClass vytvořena pro interakci s technologie ADO.NET <xref:System.Data.DataTable> objektu. Všimněte si, že tato třída je nativní kód C++ `class` (ve srovnání s `ref class` nebo `value class`). To je nezbytné, protože chceme použít tuto třídu z nativního kódu a spravovanými typy nelze používat v nativním kódu. Tato třída se zkompiluje do cílové CLR, jak je uvedeno ve `#pragma managed` směrnice předchozí deklaraci třídy. Další informace o této směrnice, naleznete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).  
  
 Všimněte si soukromému členu třídy DatabaseClass: `gcroot<DataTable ^> table`. Protože nativní typy nemůžou obsahovat spravované typy `gcroot` – klíčové slovo je nezbytné. Další informace o `gcroot`, naleznete v tématu [postupy: deklarování zpracovává v nativních typech](../dotnet/how-to-declare-handles-in-native-types.md).  
  
 Zbytek kódu v tomto příkladu je nativní kód C++, jako je indikován `#pragma unmanaged` předchází `main`. V tomto příkladu jsme se vytváří novou instanci třídy DatabaseClass a volání metody k vytvoření tabulky a naplňte několik řádků v tabulce. Všimněte si, že nativní `SAFEARRAY` typy jsou předávány jako hodnoty pro sloupec databáze ArrayIntsCol. Uvnitř DatabaseClass tyto `SAFEARRAY` typy, které jsou zařazeny do spravované objekty zařazování funkce součástí <xref:System.Runtime.InteropServices?displayProperty=fullName> oboru názvů. Konkrétně metoda <xref:System.Runtime.InteropServices.Marshal.Copy%2A> použitý k zařazování `SAFEARRAY` spravované pole celých čísel a metodu <xref:System.Runtime.InteropServices.Marshal.Copy%2A> použitý k zařazování spravovaného pole celých čísel na `SAFEARRAY`.  
  
```cpp  
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
  
### <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Ke kompilaci kódu z příkazového řádku, uložit do souboru s názvem adonet_marshal_safearray.cpp příklad kódu a zadejte následující příkaz:  
  
    ```  
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp  
    ```  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Informace týkající se zabezpečení zahrnující ADO.NET naleznete v tématu [zabezpečení aplikací ADO.NET](/dotnet/framework/data/adonet/securing-ado-net-applications).  

## <a name="related-sections"></a>Související oddíly  
  
|Oddíl|Popis|  
|-------------|-----------------|  
|[ADO.NET](/dotnet/framework/data/adonet/index)|Poskytuje přehled ADO.NET, sadu tříd, které zprostředkovávají služby data access services pro programátora rozhraní .NET.|  
  
## <a name="see-also"></a>Viz také  
 [Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
   
 [Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)

 <xref:System.Runtime.InteropServices>   

 [Interoperabilita](https://msdn.microsoft.com/afcc2e7d-3f32-48d2-8141-1c42acf29084)   
