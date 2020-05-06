---
title: db_command (atribut COM C++)
ms.date: 07/10/2018
f1_keywords:
- vc-attr.db_command
helpviewer_keywords:
- db_command attribute
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
ms.openlocfilehash: 87043315def59bcd7cff706710d988cc0ed37876
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825427"
---
# <a name="db_command"></a>db_command

Vytvoří příkaz OLE DB.

## <a name="syntax"></a>Syntaxe

```cpp
[ db_command(command, name, source_name, hresult, bindings, bulk_fetch)
]
```

### <a name="parameters"></a>Parametry

*systému*<br/>
Řetězec příkazu, který obsahuje text příkazu OLE DB. Jednoduchý příklad:

```cpp
[ db_command ( command = "Select * from Products" ) ]
```

Syntaxe *příkazu* je následující:

> blok parametrů vazby 1 \
> &nbsp;&nbsp;OLE DB příkaz \
> blok parametrů vazby 2 \
> &nbsp;&nbsp;pokračování příkazu OLE DB Command \
> blok parametrů vazby 3 \
> ...

*Blok parametrů vazby* je definován následujícím způsobem:

> **(\[ ** *BindType* **]** *szVar1* szVar1 \[, *szVar2* szVar2 \[, *nVar3* nVar3 \[,...]]] **)**

kde:

- **(** označuje začátek bloku datové vazby.

- **\[***BindType* **]** je jedním z následujících řetězců nerozlišujících velká a malá písmena:

  - ** \[db_column]** váže každou členskou proměnnou na sloupec v sadě řádků.

  - ** \[BindTo]** (stejné jako ** \[db_column]**).

  - ** \[v]** váže členské proměnné jako vstupní parametry.

  - ** \[out]** váže členské proměnné jako výstupní parametry.

  - v, out] ** \[** váže členské proměnné jako vstupní a výstupní parametry.

- *szVarX*, *nVarX* se přeloží na členskou proměnnou v rámci aktuálního oboru.

- **)** označuje konec bloku datové vazby.

Pokud řetězec příkazu obsahuje jeden nebo více specifikátorů, jako je \[například in] \[, out] nebo \[in/out], **db_command** sestavení mapování parametrů.

Pokud řetězec příkazu obsahuje jeden nebo více parametrů, například \[db_column] nebo \[BindTo], **db_command** vygeneruje sadu řádků a mapu přístupového objektu pro obsluhu těchto vázaných proměnných. Další informace najdete v tématu [db_accessor](db-accessor.md) .

> [!NOTE]
> \[*BindType*] syntaxe a parametr *Bindings* nejsou platné při použití **db_command** na úrovni třídy.

Tady jsou některé příklady bloků parametrů vazby. Následující příklad váže datové `m_au_fname` členy a `m_au_lname` s sloupci `au_fname` a `au_lname` v tabulce Autoři v databázi pubs:

```cpp
TCHAR m_au_fname[21];
TCHAR m_au_lname[41];
TCHAR m_state[3] = 'CA';

[db_command (command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \
   "FROM dbo.authors " \
   "WHERE state = ?([in]m_state)")
]
```

*Jméno*<br/>
Volitelné Název popisovače, který používáte pro práci se sadou řádků. Pokud zadáte *název*, **db_command** vygeneruje třídu se zadaným *názvem*, který lze použít k procházení sady řádků nebo k provedení více dotazů akce. Pokud *název*nezadáte, nebude možné vrátit uživatele více než jeden řádek výsledků.

*source_name*<br/>
Volitelné `CSession` Proměnná nebo instance třídy, u které je použit `db_source` atribut, na kterém se příkaz spustí. Viz [db_source](db-source.md).

**db_command** kontroluje, zda je proměnná použitá pro *source_name* platná, takže zadaná proměnná by měla být ve funkci nebo globálním oboru.

*HRESULT*<br/>
Volitelné Identifikuje proměnnou, která dostane hodnotu HRESULT tohoto databázového příkazu. Pokud proměnná neexistuje, bude automaticky vložena atributem.

*vazeb*<br/>
Volitelné Umožňuje oddělit parametry vazby z příkazu OLE DB.

Pokud zadáte hodnotu pro *vazby*, **db_command** bude analyzovat přidruženou hodnotu a nebude analyzovat \[parametr *BindType*]. Toto použití vám umožňuje použít syntaxi poskytovatele OLE DB. Chcete-li zakázat analýzu bez parametrů vazby, `Bindings=""`zadejte.

Pokud nezadáte hodnotu pro *vazby*, **db_command** bude analyzovat blok parametrů vazby, hledání "**(**", následované **\[** _BindType_**]** v závorkách, následované jednou nebo více dříve deklarovanými členskými proměnnými jazyka C++ následovanými znakem "**)**". Veškerý text mezi závorkami bude z výsledného příkazu odstraněn a tyto parametry budou použity k vytvoření vazeb sloupců a parametrů pro tento příkaz.

*bulk_fetch*<br/>
Volitelné Celočíselná hodnota, která určuje počet řádků, které se mají načíst.

Výchozí hodnota je 1, což určuje, že se načítají jednotlivé řádky (sada řádků bude typu [CRowset](../../data/oledb/crowset-class.md)).

Hodnota větší než 1 určuje hromadné načítání řádků. Hromadné načítání řádků odkazuje na schopnost hromadných sad řádků načíst více popisovačů řádků (sada řádků bude typu [CBulkRowset](../../data/oledb/cbulkrowset-class.md) a bude volat `SetRows` se zadaným počtem řádků).

Pokud je *bulk_fetch* menší než jedna, `SetRows` vrátí se nula.

## <a name="remarks"></a>Poznámky

**db_command** vytvoří objekt [CCommand](../../data/oledb/ccommand-class.md) , který je používán příjemcem OLE DB ke spuštění příkazu.

Můžete použít **db_command** s oborem třídy nebo funkce; Hlavním rozdílem je rozsah `CCommand` objektu. S rozsahem funkcí jsou data, jako jsou například vazby ukončena na funkci end. Jak třída, tak použití oboru funkcí zahrnují třídu `CCommand<>`šablony příjemce OLE DB, ale argumenty šablony se pro funkce a případy třídy liší. V případě funkce budou vazby provedeny do `Accessor` , který zahrnuje místní proměnné, zatímco použití třídy odvodí `CAccessor`odvozenou třídu jako argument. Při použití jako atributu class **db_command** pracuje ve spojení s **db_column**.

**db_command** lze použít ke spuštění příkazů, které nevracejí sadu výsledků dotazu.

Pokud poskytovatel atributu příjemce použije tento atribut pro třídu, kompilátor \_přejmenuje třídu na přistupující objekt *YourClassName*, kde *YourClassName* je název, který jste přiřadili třídě, a kompilátor vytvoří také třídu s názvem *YourClassName*, která je odvozena z \_přístupového objektu *YourClassName*.  V Zobrazení tříd se zobrazí obě třídy.

## <a name="example"></a>Příklad

Tato ukázka definuje příkaz, který vybere první a poslední název z tabulky, kde sloupec State odpovídá "CA". **db_command** vytvoří a přečte sadu řádků, na které můžete volat funkce generované průvodcem, jako jsou [OpenAll a CloseAll](../../data/oledb/consumer-wizard-generated-methods.md), a `CRowset` také členské funkce, jako je například [MoveNext](../../data/oledb/crowset-movenext.md).

Všimněte si, že tento kód vyžaduje, abyste zadali vlastní připojovací řetězec, který se připojuje k databázi pubs. Informace o tom, jak to udělat ve vývojovém prostředí, najdete v tématech [Postup: připojení k databázi a procházení existujících objektů](/sql/ssdt/how-to-connect-to-a-database-and-browse-existing-objects) a [Přidání nových připojení](/visualstudio/data-tools/add-new-connections).

```cpp
// db_command.h
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

#pragma once

[  db_source(L"your connection string"), db_command(L" \
      SELECT au_lname, au_fname \
      FROM dbo.authors \
      WHERE state = 'CA'")  ]

struct CAuthors {
   // In order to fix several issues with some providers, the code below may bind
   // columns in a different order than reported by the provider

   DBSTATUS m_dwau_lnameStatus;
   DBSTATUS m_dwau_fnameStatus;
   DBLENGTH m_dwau_lnameLength;
   DBLENGTH m_dwau_fnameLength;

   [ db_column("au_lname", status="m_dwau_lnameStatus", length="m_dwau_lnameLength") ] TCHAR m_au_lname[41];
   [ db_column("au_fname", status="m_dwau_fnameStatus", length="m_dwau_fnameLength") ] TCHAR m_au_fname[21];

   [ db_param("7", paramtype="DBPARAMIO_INPUT") ] TCHAR m_state[3];

   void GetRowsetProperties(CDBPropSet* pPropSet) {
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   }
};
```

## <a name="example"></a>Příklad

```cpp
// db_command.cpp
// compile with: /c
#include "db_command.h"

int main(int argc, _TCHAR* argv[]) {
   HRESULT hr = CoInitialize(NULL);

   // Instantiate rowset
   CAuthors rs;

   // Open rowset and move to first row
   strcpy_s(rs.m_state, sizeof(rs.m_state), _T("CA"));
   hr = rs.OpenAll();
   hr = rs.MoveFirst();

   // Iterate through the rowset
   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET ) {
      // Print out the column information for each row
      printf("First Name: %s, Last Name: %s\n", rs.m_au_fname, rs.m_au_lname);
      hr = rs.MoveNext();
   }

   rs.CloseAll();
   CoUninitialize();
}
```

## <a name="example"></a>Příklad

Tato ukázka používá `db_source` třídu `CMySource`zdroje dat a `db_command` třídy `CCommand1` příkazů a. `CCommand2`

```cpp
// db_command_2.cpp
// compile with: /c
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>
// class usage for both db_source and db_command

[  db_source(L"your connection string"), db_command(L" \
      SELECT au_lname, au_fname \
      FROM dbo.authors \
      WHERE state = 'CA'")  ]
struct CMySource {
   HRESULT OpenDataSource() {
      return S_OK;
   }
};

[db_command(command = "SELECT * FROM Products")]
class CCommand1 {};

[db_command(command = "SELECT FNAME, LNAME FROM Customers")]
class CCommand2 {};

int main() {
   CMySource s;
   HRESULT hr = s.OpenDataSource();
   if (SUCCEEDED(hr)) {
      CCommand1 c1;
      hr = c1.Open(s);

      CCommand2 c2;
      hr = c2.Open(s);
   }

   s.CloseDataSource();
}
```

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**, člen, metoda, místní|
|**REPEATABLE**|No|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také

[Atributy příjemce technologie OLE DB](ole-db-consumer-attributes.md)<br/>
[Samostatné atributy](stand-alone-attributes.md)
