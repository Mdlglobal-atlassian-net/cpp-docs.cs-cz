---
title: "Použití dynamických přístupových objektů | Microsoft Docs"
ms.custom: 
ms.date: 02/14/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8f867a9a099c835550332822fa94c46046d07e2a
ms.sourcegitcommit: 8ae12a602244a5853e941e5e8806e3545d876844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2018
---
# <a name="using-dynamic-accessors"></a>Použití dynamických přístupových objektů

Dynamické přistupující objekty umožňují přístup ke zdroji dat, pokud nemáte žádné znalosti schématu databáze (podkladová struktura). Knihovna šablony technologie OLE DB poskytuje několik tříd, můžete to udělat.

[DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) příklad ukazuje způsob použití třídy dynamického přístupového objektu získat informace o sloupci a dynamicky vytvořit přistupující objekty.

## <a name="using-cdynamicaccessor"></a>Pomocí CDynamicAccessor

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) umožňuje přístup ke zdroji dat, pokud nemáte žádné znalosti schématu databáze (podkladová struktura databáze). `CDynamicAccessor` metody získat informace o sloupci například názvy sloupců, počet a typ data. Tato informace o sloupci použijete k vytvoření dynamicky přistupujícího objektu v době běhu. Informace o sloupci je uložen do vyrovnávací paměti, který je vytvořen a spravován společností tuto třídu. Získání dat z vyrovnávací paměti pomocí [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) metoda.

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

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

## <a name="using-cdynamicstringaccessor"></a>Pomocí CDynamicStringAccessor

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) funguje jako [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), s výjimkou jedním způsobem důležité. Při `CDynamicAccessor` požadavku na data v nativním formátu hlášené poskytovatelem, `CDynamicStringAccessor` požadavky, že zprostředkovatel načíst všechna data z úložiště dat jako řetězce data. To je zvlášť vhodné pro jednoduché úlohy, které nevyžadují výpočet hodnot v úložišti dat, například zobrazení nebo tisk úložiště dat obsah.

Použití `CDynamicStringAccessor` metody získat informace o sloupci. Tato informace o sloupci použijete k vytvoření dynamicky přistupujícího objektu v době běhu. Informace o sloupci je uložen do vyrovnávací paměti, vytvořit a spravovat touto třídou. Získání dat z vyrovnávací paměti pomocí [CDynamicStringAccessor::GetString](../../data/oledb/cdynamicstringaccessor-getstring.md) nebo jej uložte do vyrovnávací paměti pomocí [CDynamicStringAccessor::SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).

## <a name="example"></a>Příklad

### <a name="code"></a>Kód

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

## <a name="using-cdynamicparameteraccessor"></a>Pomocí CDynamicParameterAccessor

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) je podobná [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)kromě toho, že `CDynamicParameterAccessor` získává informace o parametrech, chcete-li nastavit, že zavoláte [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) rozhraní. Zprostředkovatel musí podporovat `ICommandWithParameters` pro příjemce k použití této třídy.

Informace o parametru je uložen do vyrovnávací paměti, vytvořit a spravovat touto třídou. Parametr data získáte z vyrovnávací paměti pomocí [CDynamicParameterAccessor::GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) a [CDynamicParameterAccessor::GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Příklad, který ukazuje, jak používat tuto třídu pro spuštění systému SQL Server uložené procedury a získat hodnoty parametrů výstup, naleznete v části [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) ukázkový kód v [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) úložišti na Githubu.

## <a name="see-also"></a>Viz také

[Použití přístupových objektů](../../data/oledb/using-accessors.md)  
[CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)  
[CDynamicStringAccessor – třída](../../data/oledb/cdynamicstringaccessor-class.md)  
[CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)  
[DynamicConsumer Sample](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)  
