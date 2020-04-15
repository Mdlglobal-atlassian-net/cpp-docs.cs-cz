---
title: Přístup k datům s použitím technologie ADO.NET (C++/CLI)
ms.date: 11/04/2016
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
ms.openlocfilehash: 35633449c4c01f5c103dcd54b81c0d6aa7c08cdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364415"
---
# <a name="data-access-using-adonet-ccli"></a>Přístup k datům s použitím technologie ADO.NET (C++/CLI)

ADO.NET je rozhraní .NET Framework API pro přístup k datům a poskytuje napájení a snadné použití neodpovídající předchozím řešením pro přístup k datům. Tato část popisuje některé problémy týkající se ADO.NET, které jsou jedinečné pro uživatele visual c++, jako je například zařazování nativních typů.

ADO.NET běží pod společným jazykem Runtime (CLR). Proto všechny aplikace, která spolupracuje s ADO.NET musí také cílit clr. To však neznamená, že nativní aplikace nelze použít ADO.NET. Tyto příklady ukazují, jak pracovat s ADO.NET databáze z nativního kódu.

## <a name="marshal-ansi-strings-for-adonet"></a><a name="marshal_ansi"></a>Maršál ANSI řetězce pro ADO.NET

Ukazuje, jak přidat nativní`char *`řetězec ( ) do <xref:System.String?displayProperty=fullName> databáze a jak zařadit z databáze do nativního řetězce.

### <a name="example"></a>Příklad

V tomto příkladu je třída DatabaseClass vytvořena <xref:System.Data.DataTable> pro interakci s objektem ADO.NET. Všimněte si, že tato `class` třída je nativní `ref class` `value class`C++ (ve srovnání s nebo). To je nezbytné, protože chceme použít tuto třídu z nativního kódu a spravované typy nelze použít v nativním kódu. Tato třída bude zkompilován cíl clr, jak `#pragma managed` je uvedeno ve směrnici předcházející deklaraci třídy. Další informace o této směrnici naleznete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).

Všimněte si, že soukromý `gcroot<DataTable ^> table`člen třídy DatabaseClass: . Vzhledem k tomu, že `gcroot` nativní typy nemohou obsahovat spravované typy, klíčové slovo je nezbytné. Další informace `gcroot`o tématu naleznete v [tématu How to: Declare handles in Native Types](../dotnet/how-to-declare-handles-in-native-types.md).

Zbytek kódu v tomto příkladu je nativní kód jazyka `#pragma unmanaged` C++, jak je uvedeno v předchozí směrnici `main`. V tomto příkladu vytváříme novou instanci DatabaseClass a voláme její metody k vytvoření tabulky a naplnění některých řádků v tabulce. Všimněte si, že nativní řetězce Jazyka C++ jsou předávány jako hodnoty pro sloupec databáze StringCol. Uvnitř DatabaseClass jsou tyto řetězce zařazeny do spravovaných řetězců <xref:System.Runtime.InteropServices?displayProperty=fullName> pomocí funkce zařazování nalezené v oboru názvů. <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> Konkrétně metoda se používá k `char *` zařazování a do , <xref:System.String>a metoda <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> se používá k zařazování a <xref:System.String> do . `char *`

> [!NOTE]
> Paměť přidělená <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> podle musí být vyrovnány voláním buď <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> nebo `GlobalFree`.

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

- Chcete-li zkompilovat kód z příkazového řádku, uložte příklad kódu do souboru s názvem adonet_marshal_string_native.cpp a zadejte následující příkaz:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-bstr-strings-for-adonet"></a><a name="marshal_bstr"></a>Maršál BSTR řetězce pro ADO.NET

Ukazuje, jak přidat řetězec`BSTR`COM ( ) do databáze <xref:System.String?displayProperty=fullName> a jak `BSTR`zařadit z databáze do .

### <a name="example"></a>Příklad

V tomto příkladu je třída DatabaseClass vytvořena <xref:System.Data.DataTable> pro interakci s objektem ADO.NET. Všimněte si, že tato `class` třída je nativní `ref class` `value class`C++ (ve srovnání s nebo). To je nezbytné, protože chceme použít tuto třídu z nativního kódu a spravované typy nelze použít v nativním kódu. Tato třída bude zkompilován cíl clr, jak `#pragma managed` je uvedeno ve směrnici předcházející deklaraci třídy. Další informace o této směrnici naleznete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).

Všimněte si, že soukromý `gcroot<DataTable ^> table`člen třídy DatabaseClass: . Vzhledem k tomu, že `gcroot` nativní typy nemohou obsahovat spravované typy, klíčové slovo je nezbytné. Další informace `gcroot`o tématu naleznete v [tématu How to: Declare handles in Native Types](../dotnet/how-to-declare-handles-in-native-types.md).

Zbytek kódu v tomto příkladu je nativní kód jazyka `#pragma unmanaged` C++, jak je uvedeno v předchozí směrnici `main`. V tomto příkladu vytváříme novou instanci DatabaseClass a voláme její metody k vytvoření tabulky a naplnění některých řádků v tabulce. Všimněte si, že řetězce COM jsou předávány jako hodnoty pro sloupec databáze StringCol. Uvnitř DatabaseClass jsou tyto řetězce zařazeny do spravovaných řetězců <xref:System.Runtime.InteropServices?displayProperty=fullName> pomocí funkce zařazování nalezené v oboru názvů. <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> Konkrétně metoda se používá k `BSTR` zařazování a do , <xref:System.String>a metoda <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> se používá k zařazování a <xref:System.String> do . `BSTR`

> [!NOTE]
> Paměť přidělená <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> podle musí být vyrovnány voláním buď <xref:System.Runtime.InteropServices.Marshal.FreeBSTR%2A> nebo `SysFreeString`.

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

- Chcete-li zkompilovat kód z příkazového řádku, uložte příklad kódu do souboru s názvem adonet_marshal_string_native.cpp a zadejte následující příkaz:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_native.cpp
    ```

## <a name="marshal-unicode-strings-for-adonet"></a><a name="marshal_unicode"></a>Maršál Unicode řetězce pro ADO.NET

Ukazuje, jak přidat nativní řetězec`wchar_t *`Unicode ( ) do <xref:System.String?displayProperty=fullName> databáze a jak zařadit a z databáze do nativního řetězce Unicode.

### <a name="example"></a>Příklad

V tomto příkladu je třída DatabaseClass vytvořena <xref:System.Data.DataTable> pro interakci s objektem ADO.NET. Všimněte si, že tato `class` třída je nativní `ref class` `value class`C++ (ve srovnání s nebo). To je nezbytné, protože chceme použít tuto třídu z nativního kódu a spravované typy nelze použít v nativním kódu. Tato třída bude zkompilován cíl clr, jak `#pragma managed` je uvedeno ve směrnici předcházející deklaraci třídy. Další informace o této směrnici naleznete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).

Všimněte si, že soukromý `gcroot<DataTable ^> table`člen třídy DatabaseClass: . Vzhledem k tomu, že `gcroot` nativní typy nemohou obsahovat spravované typy, klíčové slovo je nezbytné. Další informace `gcroot`o tématu naleznete v [tématu How to: Declare handles in Native Types](../dotnet/how-to-declare-handles-in-native-types.md).

Zbytek kódu v tomto příkladu je nativní kód jazyka `#pragma unmanaged` C++, jak je uvedeno v předchozí směrnici `main`. V tomto příkladu vytváříme novou instanci DatabaseClass a voláme její metody k vytvoření tabulky a naplnění některých řádků v tabulce. Všimněte si, že unicode C++ řetězce jsou předávány jako hodnoty pro sloupec databáze StringCol. Uvnitř DatabaseClass jsou tyto řetězce zařazeny do spravovaných řetězců <xref:System.Runtime.InteropServices?displayProperty=fullName> pomocí funkce zařazování nalezené v oboru názvů. <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> Konkrétně metoda se používá k `wchar_t *` zařazování a do , <xref:System.String>a metoda <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> se používá k zařazování a <xref:System.String> do . `wchar_t *`

> [!NOTE]
> Paměť přidělená <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalUni%2A> podle musí být vyrovnány voláním buď <xref:System.Runtime.InteropServices.Marshal.FreeHGlobal%2A> nebo `GlobalFree`.

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

- Chcete-li zkompilovat kód z příkazového řádku, uložte příklad kódu do souboru s názvem adonet_marshal_string_wide.cpp a zadejte následující příkaz:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_string_wide.cpp
    ```

## <a name="marshal-a-variant-for-adonet"></a><a name="marshal_variant"></a>Zařazuji variantu pro ADO.NET

Ukazuje, jak přidat `VARIANT` nativní do databáze a <xref:System.Object?displayProperty=fullName> jak zařazovat z databáze nativní `VARIANT`.

### <a name="example"></a>Příklad

V tomto příkladu je třída DatabaseClass vytvořena <xref:System.Data.DataTable> pro interakci s objektem ADO.NET. Všimněte si, že tato `class` třída je nativní `ref class` `value class`C++ (ve srovnání s nebo). To je nezbytné, protože chceme použít tuto třídu z nativního kódu a spravované typy nelze použít v nativním kódu. Tato třída bude zkompilován cíl clr, jak `#pragma managed` je uvedeno ve směrnici předcházející deklaraci třídy. Další informace o této směrnici naleznete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).

Všimněte si, že soukromý `gcroot<DataTable ^> table`člen třídy DatabaseClass: . Vzhledem k tomu, že `gcroot` nativní typy nemohou obsahovat spravované typy, klíčové slovo je nezbytné. Další informace `gcroot`o tématu naleznete v [tématu How to: Declare handles in Native Types](../dotnet/how-to-declare-handles-in-native-types.md).

Zbytek kódu v tomto příkladu je nativní kód jazyka `#pragma unmanaged` C++, jak je uvedeno v předchozí směrnici `main`. V tomto příkladu vytváříme novou instanci DatabaseClass a voláme její metody k vytvoření tabulky a naplnění některých řádků v tabulce. Všimněte `VARIANT` si, že nativní typy jsou předávány jako hodnoty pro sloupec databáze ObjectCol. Uvnitř DatabaseClass `VARIANT` tyto typy jsou zařazeny do spravovaných <xref:System.Runtime.InteropServices?displayProperty=fullName> objektů pomocí zařazování funkce nalezené v oboru názvů. Konkrétně <xref:System.Runtime.InteropServices.Marshal.GetObjectForNativeVariant%2A> metoda se používá k `VARIANT` zařazování <xref:System.Runtime.InteropServices.Marshal.GetNativeVariantForObject%2A> a na <xref:System.Object> <xref:System.Object>, `VARIANT`a metoda se používá k zařazování do .

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

- Chcete-li zkompilovat kód z příkazového řádku, uložte příklad kódu do souboru s názvem adonet_marshal_variant.cpp a zadejte následující příkaz:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_variant.cpp
    ```

## <a name="marshal-a-safearray-for-adonet"></a><a name="marshal_safearray"></a>Maršál SAFEARRAY pro ADO.NET

Ukazuje, jak přidat `SAFEARRAY` nativní do databáze a jak zařazovat `SAFEARRAY`spravované pole z databáze do nativní .

### <a name="example"></a>Příklad

V tomto příkladu je třída DatabaseClass vytvořena <xref:System.Data.DataTable> pro interakci s objektem ADO.NET. Všimněte si, že tato `class` třída je nativní `ref class` `value class`C++ (ve srovnání s nebo). To je nezbytné, protože chceme použít tuto třídu z nativního kódu a spravované typy nelze použít v nativním kódu. Tato třída bude zkompilován cíl clr, jak `#pragma managed` je uvedeno ve směrnici předcházející deklaraci třídy. Další informace o této směrnici naleznete v tématu [spravované, nespravované](../preprocessor/managed-unmanaged.md).

Všimněte si, že soukromý `gcroot<DataTable ^> table`člen třídy DatabaseClass: . Vzhledem k tomu, že `gcroot` nativní typy nemohou obsahovat spravované typy, klíčové slovo je nezbytné. Další informace `gcroot`o tématu naleznete v [tématu How to: Declare handles in Native Types](../dotnet/how-to-declare-handles-in-native-types.md).

Zbytek kódu v tomto příkladu je nativní kód jazyka `#pragma unmanaged` C++, jak je uvedeno v předchozí směrnici `main`. V tomto příkladu vytváříme novou instanci DatabaseClass a voláme její metody k vytvoření tabulky a naplnění některých řádků v tabulce. Všimněte `SAFEARRAY` si, že nativní typy jsou předávány jako hodnoty pro sloupec databáze ArrayIntsCol. Uvnitř DatabaseClass `SAFEARRAY` tyto typy jsou zařazeny do spravovaných <xref:System.Runtime.InteropServices?displayProperty=fullName> objektů pomocí zařazování funkce nalezené v oboru názvů. Konkrétně <xref:System.Runtime.InteropServices.Marshal.Copy%2A> metoda se používá k `SAFEARRAY` zařazování a do spravovaného <xref:System.Runtime.InteropServices.Marshal.Copy%2A> pole celáčísla a metoda se používá `SAFEARRAY`k zařazování spravované pole celáčísla na .

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

- Chcete-li zkompilovat kód z příkazového řádku, uložte příklad kódu do souboru s názvem adonet_marshal_safearray.cpp a zadejte následující příkaz:

    ```
    cl /clr /FU System.dll /FU System.Data.dll /FU System.Xml.dll adonet_marshal_safearray.cpp
    ```

## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework

Informace o problémech se zabezpečením týkajícími se ADO.NET naleznete v [tématu Zabezpečení ADO.NET aplikací](/dotnet/framework/data/adonet/securing-ado-net-applications).

## <a name="related-sections"></a>Související oddíly

|Sekce|Popis|
|-------------|-----------------|
|[ADO.NET](/dotnet/framework/data/adonet/index)|Poskytuje přehled ADO.NET, sada tříd, které zveřejňují služby přístupu k datům programátoru .NET.|

## <a name="see-also"></a>Viz také

[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

[Nativní funkce a vzájemná funkční spolupráce rozhraní .NET](../dotnet/native-and-dotnet-interoperability.md)

<xref:System.Runtime.InteropServices>

[Interoperabilita](/dotnet/framework/interop/index)
