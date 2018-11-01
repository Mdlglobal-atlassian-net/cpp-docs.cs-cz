---
title: Použití dynamických přístupových objektů
ms.date: 10/18/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
ms.openlocfilehash: 4539247894c3980464e744c76cea450324372382
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649719"
---
# <a name="using-dynamic-accessors"></a>Použití dynamických přístupových objektů

Dynamické přístupové objekty umožňují přístup ke zdroji dat, když nemají žádné informace o schématu databáze (podkladová struktura). Šablony technologie OLE DB knihovna poskytuje několik tříd můžete.

[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) příklad ukazuje způsob použití tříd dynamického přístupového objektu získat informace o sloupci a dynamicky se vytvářejí přistupující objekty.

## <a name="using-cdynamicaccessor"></a>CDynamicAccessor – použití

[CDynamicAccessor –](../../data/oledb/cdynamicaccessor-class.md) umožňuje přístup ke zdroji dat, když nemají žádné informace o schématu databáze (základní strukturu vaší databáze). `CDynamicAccessor` metody získat informace o sloupci, jako jsou názvy sloupců, počet a typ dat. Informace o tomto sloupci použijete k vytvoření přistupující objekt dynamicky za běhu. Informace o sloupci je uložená ve vyrovnávací paměti, který je vytvořen a spravován společností tuto třídu. Získání dat z vyrovnávací paměti pomocí [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) metody.

## <a name="example"></a>Příklad

```cpp
// Using_Dynamic_Accessors.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );

    CDataSource ds;
    CSession ss;

    CTable<CDynamicAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            DBTYPE type;
            rs.GetColumnType(i, &type );
            printf_s( "Column %d [%S] is of type %d\n",
                      i, rs.GetColumnName(i ), type );

            switch(type )
            {
                case DBTYPE_WSTR:
                    printf_s( "value is %S\n",
                              (WCHAR*)rs.GetValue(i ) );
                break;
                case DBTYPE_STR:
                    printf_s( "value is %s\n",
                              (CHAR*)rs.GetValue(i ) );
                default:
                    printf_s( "value is %d\n",
                              *(long*)rs.GetValue(i ) );
            }
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

    return 0;
}
```

## <a name="using-cdynamicstringaccessor"></a>CDynamicStringAccessor – použití

[CDynamicStringAccessor –](../../data/oledb/cdynamicstringaccessor-class.md) funguje jako [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), s výjimkou jedním ze způsobů důležité. Zatímco `CDynamicAccessor` vyžádá data v nativním formátu hlášené poskytovatelem, `CDynamicStringAccessor` požadavků, že zprostředkovatel načíst všechna data z úložiště dat jako řetězce data. Proces je zvláště užitečná pro jednoduché úlohy, které nevyžadují výpočet hodnot v úložišti dat, jako je například zobrazení nebo tisk obsah datového úložiště.

Použití `CDynamicStringAccessor` metody k získání informace o sloupci. Informace o tomto sloupci použijete k vytvoření přistupující objekt dynamicky za běhu. Informace o sloupci je uložená do vyrovnávací paměti, vytvářet a spravovat touto třídou. Získání dat z vyrovnávací paměti pomocí [CDynamicStringAccessor::GetString](../../data/oledb/cdynamicstringaccessor-getstring.md) nebo je uložit do vyrovnávací paměti pomocí [CDynamicStringAccessor::SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).

## <a name="example"></a>Příklad

```cpp
// Using_Dynamic_Accessors_b.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );
    if (hr != S_OK)
    {
        exit (-1);
    }

    CDataSource ds;
    CSession ss;

    CTable<CDynamicStringAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            printf_s( "column %d value is %s\n",
                      i, rs.GetString(i ) );
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

   return 0;
}
```

## <a name="using-cdynamicparameteraccessor"></a>CDynamicParameterAccessor – použití

[CDynamicParameterAccessor –](../../data/oledb/cdynamicparameteraccessor-class.md) je podobný [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), s tím rozdílem, že `CDynamicParameterAccessor` získá informace o parametrech nastavit voláním [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) rozhraní. Zprostředkovatel musí podporovat `ICommandWithParameters` pro spotřebitele pro tuto třídu používají.

Parametr informace jsou uloženy ve vyrovnávací paměti, vytvářet a spravovat touto třídou. Získat data parametrů z vyrovnávací paměti s použitím [CDynamicParameterAccessor::GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) a [CDynamicParameterAccessor::GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Příklad ukazuje, jak použít tuto třídu pro spuštění systému SQL Server uložené procedury a získat hodnoty výstupních parametrů, najdete v článku [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) ukázkový kód v [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) úložišti na Githubu.

## <a name="see-also"></a>Viz také:

[Použití přístupových objektů](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor – třída](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[Příklad DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)
