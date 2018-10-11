---
title: db_param – (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.db_param
dev_langs:
- C++
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 153e1bba37b10da64b394c48ee1cf8c059ae86e9
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083019"
---
# <a name="dbparam"></a>db_param

Přidruží zadaný členskou proměnnou vstupní nebo výstupní parametr a odděluje citaci proměnné.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Parametry

*Pořadí*<br/>
Číslo sloupce (DBCOLUMNINFO pořadí), který je odpovídající pole v dané sadě řádků, ke kterému chcete svázat data.

*paramtype*<br/>
(Volitelné) Typ, který má nastavit pro parametr. Podporují pouze vstupně-výstupní typy parametrů, které podporují podkladovému zdroji dat. Typ je kombinace jedné nebo více hodnot DBPARAMIOENUM:

- DBPARAMIO_INPUT vstupního parametru.

- DBPARAMIO_OUTPUT výstupní parametr.

- DBPARAMIO_NOTPARAM přistupující objekt nemá žádné parametry. Nastavení `eParamIO` na tuto hodnotu v řádku přistupující objekty upozorňuje uživatele, že parametry budou ignorovány.

*Hodnota DbType*<br/>
(Volitelné) OLE DB [indikátor typu](/previous-versions/windows/desktop/ms711251) pro vstupní sloupec.

*Přesnost*<br/>
(Volitelné) Přesnost, který má být použit pro vstupní sloupec. Podrobnosti najdete v tématu Popis `bPrecision` elementu [DBBINDING struktura](/previous-versions/windows/desktop/ms716845)

*Škálování*<br/>
(Volitelné) Škálování, která má být použit pro vstupní sloupec. Podrobnosti najdete v tématu Popis `bScale` elementu [DBBINDING struktura](/previous-versions/windows/desktop/ms716845)

*Stav*<br/>
(Volitelné) Členské proměnné používané pro udržení stavu daného sloupce. Stav označuje, zda je hodnota sloupce datovou hodnotu nebo jinou hodnotu, jako je NULL. Možné hodnoty najdete v části [stav](/previous-versions/windows/desktop/ms722617) v *OLE DB referenční informace pro programátory*.

*Délka*<br/>
(Volitelné) Členské proměnné používané pro udržení velikost sloupce v bajtech.

## <a name="remarks"></a>Poznámky

**db_param –** definuje parametry, můžete použít v příkazech; proto použít je s `db_command`. Například můžete použít **db_param –** pro svázání parametrů v dotazů SQL nebo úložné procedury. Parametry v uložené proceduře jsou rozlišeny pomocí otazník (?). proto byste měli vytvořit vazbu datové členy v pořadí parametrů.

**db_param –** vymezuje členská data, která se může účastnit OLE DB `ICommandWithParameters`– na základě vazby. Nastaví typ parametru (vstupní nebo výstupní), typ OLE DB, přesnost, měřítko, stav a délka zadaného parametru. Tento atribut vloží makra příjemce technologie OLE DB BEGIN_PARAM_MAP... END_PARAM_MAP. Každý člen můžete označit **db_param –** atribut budou zaměstnávat jednu položku na mapě ve formě COLUMN_ENTRY.

**db_param –** se používá ve spojení s oběma [db_table](db-table.md) nebo [db_command](db-command.md) atributy.

Když příjemce atribut poskytovatel použije tento atribut na třídu, kompilátor bude přejmenujte třídu na \_ *YourClassName*přístupový objekt, kde *YourClassName* je název, který jste zadali třídy a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_ *YourClassName*přistupujícího objektu.  V zobrazení tříd zobrazí se obě třídy.

## <a name="example"></a>Příklad

Následující příklad vytvoří třídu příkazu na základě SalesbyYear uložené procedury v databázi Northwind. Přidruží první parametr v uložené proceduře se `m_RETURN_VALUE` proměnnou a definuje jako výstupní parametr. Přidruží poslední dva parametry (vstupu) s `m_Beginning_Date` a `m_Ending_Date`.

V následujícím příkladu `nOutput` proměnné s výstupní parametr.

```cpp
// db_param.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_source(L"my_connection_string"),
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")  
]
struct CSalesbyYear {
   DBSTATUS m_dwShippedDateStatus;
   DBSTATUS m_dwOrderIDStatus;
   DBSTATUS m_dwSubtotalStatus;
   DBSTATUS m_dwYearStatus;

   DBLENGTH m_dwShippedDateLength;
   DBLENGTH m_dwOrderIDLength;
   DBLENGTH m_dwSubtotalLength;
   DBLENGTH m_dwYearLength;

   // Bind columns
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];

   // Bind parameters
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;
};
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **struktura**, člen, metoda, místní|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy příjemce technologie OLE DB](ole-db-consumer-attributes.md)  
