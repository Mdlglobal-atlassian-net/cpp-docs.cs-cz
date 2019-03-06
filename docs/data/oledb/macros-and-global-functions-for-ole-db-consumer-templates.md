---
title: Makra a globální funkce pro šablony příjemců OLE DB
ms.date: 02/11/2019
f1_keywords:
- vc.templates.ole
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
ms.openlocfilehash: d4ed6b86d99cdfc272b5df10ede6af6bd05ed366
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426287"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Makra a globální funkce pro šablony příjemců OLE DB

Šablony příjemce technologie OLE DB zahrnují následující makra a globální funkce:

## <a name="global-functions"></a>Globální funkce

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Vypíše informace o záznamu chyby technologie OLE DB pro zařízení s výpisem paměti, pokud je vrácena chyba.|

## <a name="accessor-map-macros"></a>Makra Map přístupového objektu

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Označuje začátek položky přistupujícího objektu.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Označuje začátek položky přístupového objektu map.|
|[END_ACCESSOR](#end_accessor)|Označuje konec položky přistupujícího objektu.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Označuje konec položky přístupového objektu map.|

## <a name="column-map-macros"></a>Makra Map sloupec

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Označuje začátek položky mapování sloupce ve třídě uživatelského záznamu.|
|[BLOB_ENTRY](#blob_entry)|Umožňuje vytvořit vazbu binárních velkých objektů (BLOB).|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Sestavy délka sloupce dat objektů BLOB.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Sestavy, délku a stav sloupce dat objektů BLOB.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Hlásí stav sloupce dat objektů BLOB.|
|[BLOB_NAME](#blob_name)|Použít na binární rozsáhlý objekt navazují názvem sloupce.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Sestavy délka sloupce dat objektů BLOB.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Sestavy, délku a stav sloupce dat objektů BLOB.|
|[BLOB_NAME_STATUS](#blob_name_status)|Hlásí stav sloupce dat objektů BLOB.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Představuje položku záložku na sadě řádků. Položka Záložka je zvláštní druh položky sloupce.|
|[COLUMN_ENTRY](#column_entry)|Představuje vazbu na konkrétní sloupec v databázi.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *typ*, *délka*, *přesnost*, *škálování*, a *stav* parametry.|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *délka* proměnné.|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *stav* a *délka* parametry.|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *přesnost* a *škálování* parametry.|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *délka* proměnnou, *přesnost* a *škálování* parametry.|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *stav* a *délka* proměnné, *přesnost* a *škálování* parametry.|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *stav* proměnnou, *přesnost* a *škálování* parametry.|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *stav* proměnné.|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *typ* parametru.|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *typ* a *velikost* parametry.|
|[COLUMN_NAME](#column_name)|Představuje vazbu v databázi v určitém sloupci podle názvu.|
|[COLUMN_NAME_EX](#column_name_ex)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace datový typ, velikost, přesnost, měřítko, délka sloupce a sloupce stavu.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace délka sloupce.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace délka sloupce a stav.|
|[COLUMN_NAME_PS](#column_name_ps)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace přesnosti a měřítku.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace délky přesnost, měřítko a sloupce.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace přesnosti, škálování, délka sloupce a sloupce stavu.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace přesnost, měřítko a sloupec Stav.|
|[COLUMN_NAME_STATUS](#column_name_status)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikaci sloupce stavu.|
|[COLUMN_NAME_TYPE](#column_name_type)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace datového typu.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace datového typu, přesnost a měřítko.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace datového typu a velikosti.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Představuje vazbu v databázi v určitém sloupci podle názvu. Podporuje specifikace datového typu ve sloupci stav.|
|[END_COLUMN_MAP](#end_column_map)|Označuje konec položky mapování sloupce.|

## <a name="command-macros"></a>Makra příkazů

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|Určuje příkaz, který se použije k vytvoření sady řádků při použití [CCommand](../../data/oledb/ccommand-class.md) třídy. Přijímá pouze typy řetězce odpovídající určený typ aplikace (ANSI nebo Unicode). Doporučuje se, že používáte [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) místo DEFINE_COMMAND.|
|[DEFINE_COMMAND_EX](#define_command_ex)|Určuje příkaz, který se použije k vytvoření sady řádků při použití [CCommand](../../data/oledb/ccommand-class.md) třídy. Podporuje aplikace ANSI a Unicode.|

## <a name="parameter-map-macros"></a>Makra Map parametr

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Označuje začátek položek mapování parametrů ve třídě záznamů uživatele.|
|[END_PARAM_MAP](#end_param_map)|Označuje konec položek mapování parametrů.|
|[SET_PARAM_TYPE](#set_param_type)|Určuje COLUMN_ENTRY makra, které následují SET_PARAM_TYPE – makro jako vstup, výstup nebo vstupně výstupní.|

### <a name="atltraceerrorrecords"></a> AtlTraceErrorRecords

Vypíše informace o záznamu chyby technologie OLE DB pro zařízení s výpisem paměti, pokud je vrácena chyba.

#### <a name="syntax"></a>Syntaxe

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Parametry

*hErr*<br/>
[in] HRESULT vrácené funkcí člen šablona příjemce technologie OLE DB.

#### <a name="remarks"></a>Poznámky

Pokud *hErr* není S_OK, `AtlTraceErrorRecords` Vypíše informace o záznamu chyby technologie OLE DB pro zařízení s výpisem paměti ( **ladění** karty v okně výstupu nebo souboru). Informace o záznamu chyby, který získáte od zprostředkovatele, obsahuje číslo řádku, zdroj, popis, soubor nápovědy, kontextu a identifikátor GUID pro každou položku záznamu chyby. `AtlTraceErrorRecords` Vypíše tyto informace pouze v sestaveních ladění. V sestaveních pro vydání je prázdný zástupnou proceduru, která je optimalizovaná navýšení kapacity. Další informace najdete v tématu [cdberrorinfo – třída](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a> BEGIN_ACCESSOR

Označuje začátek položky přistupujícího objektu.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Parametry

*počet*<br/>
[in] Číslo nula posun pro přistupující objekt v této mapě přistupující objekt.

*bAuto*<br/>
[in] Určuje, jestli je tento přistupující objekt přístupový objekt automatické nebo ruční přistupující objekt. Pokud **true**, přistupující objekt je automaticky; pokud **false**, přistupujícím objektu je ruční. Automaticky přistupujícího objektu znamená, že se data načítají za vás na operací přesunutí.

#### <a name="remarks"></a>Poznámky

V případě více přístupových objektů pro sadu řádků budete muset zadat BEGIN_ACCESSOR_MAP a používat BEGIN_ACCESSOR – makro pro každé jednotlivé přistupujícího objektu. BEGIN_ACCESSOR – makro je dokončena s END_ACCESSOR – makro. BEGIN_ACCESSOR_MAP – makro je dokončena s END_ACCESSOR_MAP – makro.

#### <a name="example"></a>Příklad

Zobrazit [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_accessor_map"></a> BEGIN_ACCESSOR_MAP

Označuje začátek položky přístupového objektu map.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
[in] Název třídy uživatelského záznamu.

*počet*<br/>
[in] Počet přístupových objektů v této mapě přistupujícího objektu.

#### <a name="remarks"></a>Poznámky

V případě více přístupových objektů pro sadu řádků budete muset zadat BEGIN_ACCESSOR_MAP na začátku a použít BEGIN_ACCESSOR – makro pro každé jednotlivé přistupujícího objektu. BEGIN_ACCESSOR – makro je dokončena s END_ACCESSOR – makro. Přístupový objekt map je dokončena s END_ACCESSOR_MAP – makro.

Pokud máte pouze jeden přistupující objekt v záznamu uživatele, použijte makro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

#### <a name="example"></a>Příklad

```cpp
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
```

### <a name="end_accessor"></a> END_ACCESSOR

Označuje konec položky přistupujícího objektu.

#### <a name="syntax"></a>Syntaxe

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Poznámky

Pro více přístupových objektů pro sadu řádků budete muset zadat BEGIN_ACCESSOR_MAP a používat BEGIN_ACCESSOR – makro pro každé jednotlivé přistupujícího objektu. BEGIN_ACCESSOR – makro je dokončena s END_ACCESSOR – makro. BEGIN_ACCESSOR_MAP – makro je dokončena s END_ACCESSOR_MAP – makro.

#### <a name="example"></a>Příklad

Zobrazit [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="end_accessor_map"></a> END_ACCESSOR_MAP

Označuje konec položky přístupového objektu map.

#### <a name="syntax"></a>Syntaxe

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Poznámky

Pro více přístupových objektů pro sadu řádků budete muset zadat BEGIN_ACCESSOR_MAP a používat BEGIN_ACCESSOR – makro pro každé jednotlivé přistupujícího objektu. BEGIN_ACCESSOR – makro je dokončena s END_ACCESSOR – makro. BEGIN_ACCESSOR_MAP – makro je dokončena s END_ACCESSOR_MAP – makro.

#### <a name="example"></a>Příklad

Zobrazit [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_column_map"></a> BEGIN_COLUMN_MAP

Označuje začátek toho položku mapování sloupců.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
[in] Název třídy záznamů uživatele odvozen od `CAccessor`.

#### <a name="remarks"></a>Poznámky

Toto makro se používá v případě jeden přistupující objekt pro sadu řádků. Pokud máte více přístupových objektů pro sadu řádků, použijte [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

BEGIN_COLUMN_MAP – makro je dokončena s END_COLUMN_MAP – makro. Toto makro se používá, když je pouze jeden přistupující objekt v záznamu uživatele.

Sloupce odpovídají polím v dané sadě řádků, které chcete vytvořit vazbu.

#### <a name="example"></a>Příklad

Tady je ukázka sloupce a parametr mapy:

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a> BLOB_ENTRY

BEGIN_COLUMN_MAP a END_COLUMN_MAP používá k vytvoření vazby binární rozsáhlý objekt ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))).

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Číslo sloupce.

*IID*<br/>
[in] Identifikátor GUID, například rozhraní `IDD_ISequentialStream`, která slouží k načtení objektu BLOB.

*příznaky*<br/>
[in] Režim úložiště označí příznakem, jak jsou definovány v modelu strukturovaného úložiště OLE (například `STGM_READ`).

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="example"></a>Příklad

Zobrazit [Jak můžu k načtení objektu BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a> BLOB_ENTRY_LENGTH

BEGIN_COLUMN_MAP a END_COLUMN_MAP používá k vytvoření vazby binární rozsáhlý objekt ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro také získá délku v bajtech sloupce objektů BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Číslo sloupce.

*IID*<br/>
[in] Identifikátor GUID, například rozhraní `IDD_ISequentialStream`, která slouží k načtení objektu BLOB.

*příznaky*<br/>
[in] Režim úložiště označí příznakem, jak jsou definovány v modelu strukturovaného úložiště OLE (například `STGM_READ`).

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[out] \(Skutečné) délka v bajtech sloupci objektů BLOB.

#### <a name="example"></a>Příklad

Zobrazit [Jak můžu k načtení objektu BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a> BLOB_ENTRY_LENGTH_STATUS

BEGIN_COLUMN_MAP a END_COLUMN_MAP používá k vytvoření vazby binární rozsáhlý objekt ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro se také o získání délky a stavu ve sloupci objektu BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY_LENGTH_STATUS(
    nOrdinal,
    IID,
    flags,
    data,
    length,
    status )
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Číslo sloupce.

*IID*<br/>
[in] Identifikátor GUID, například rozhraní `IDD_ISequentialStream`, která slouží k načtení objektu BLOB.

*příznaky*<br/>
[in] Režim úložiště označí příznakem, jak jsou definovány v modelu strukturovaného úložiště OLE (například `STGM_READ`).

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[out] \(Skutečné) délka v bajtech sloupci objektů BLOB.

*status*<br/>
[out] Stav sloupce dat objektů BLOB.

#### <a name="example"></a>Příklad

Zobrazit [Jak můžu k načtení objektu BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a> BLOB_ENTRY_STATUS

Použít k vytvoření vazby binární rozsáhlý objekt s BEGIN_COLUMN_MAP nebo BEGIN_ACCESSOR_MAP ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro také umožňuje získat stav sloupci objektů BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Číslo sloupce.

*IID*<br/>
[in] Identifikátor GUID, například rozhraní `IDD_ISequentialStream`, která slouží k načtení objektu BLOB.

*příznaky*<br/>
[in] Režim úložiště označí příznakem, jak jsou definovány v modelu strukturovaného úložiště OLE (například `STGM_READ`).

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*status*<br/>
[out] Stav pole objektů BLOB.

#### <a name="example"></a>Příklad

Zobrazit [Jak můžu k načtení objektu BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a> BLOB_NAME

BEGIN_COLUMN_MAP a END_COLUMN_MAP používá k vytvoření vazby binární rozsáhlý objekt ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro přijímá název sloupce namísto číslo sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*IID*<br/>
[in] Identifikátor GUID, například rozhraní `IDD_ISequentialStream`, která slouží k načtení objektu BLOB.

*příznaky*<br/>
[in] Režim úložiště označí příznakem, jak jsou definovány v modelu strukturovaného úložiště OLE (například `STGM_READ`).

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="example"></a>Příklad

Zobrazit [Jak můžu k načtení objektu BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a> BLOB_NAME_LENGTH

BEGIN_COLUMN_MAP a END_COLUMN_MAP používá k vytvoření vazby binární rozsáhlý objekt ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_NAME](../../data/oledb/blob-name.md), s tím rozdílem, že toto makro také získá délku v bajtech sloupce dat objektů BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*IID*<br/>
[in] Identifikátor GUID, například rozhraní `IDD_ISequentialStream`, která slouží k načtení objektu BLOB.

*příznaky*<br/>
[in] Režim úložiště označí příznakem, jak jsou definovány v modelu strukturovaného úložiště OLE (například `STGM_READ`).

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[out] \(Skutečné) délka v bajtech sloupci objektů BLOB.

### <a name="blob_name_length_status"></a> BLOB_NAME_LENGTH_STATUS

BEGIN_COLUMN_MAP a END_COLUMN_MAP používá k vytvoření vazby binární rozsáhlý objekt ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_NAME](../../data/oledb/blob-name.md), s tím rozdílem, že toto makro se také o získání délky a stavu sloupce dat objektů BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*IID*<br/>
[in] Identifikátor GUID, například rozhraní `IDD_ISequentialStream`, která slouží k načtení objektu BLOB.

*příznaky*<br/>
[in] Režim úložiště označí příznakem, jak jsou definovány v modelu strukturovaného úložiště OLE (například `STGM_READ`).

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[out] \(Skutečné) délka v bajtech sloupci objektů BLOB.

*status*<br/>
[out] Stav pole objektů BLOB.

### <a name="blob_name_status"></a> BLOB_NAME_STATUS

BEGIN_COLUMN_MAP a END_COLUMN_MAP používá k vytvoření vazby binární rozsáhlý objekt ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_NAME](../../data/oledb/blob-name.md), s tím rozdílem, že toto makro také umožňuje získat stav sloupce dat objektů BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*IID*<br/>
[in] Identifikátor GUID, například rozhraní `IDD_ISequentialStream`, která slouží k načtení objektu BLOB.

*příznaky*<br/>
[in] Režim úložiště označí příznakem, jak jsou definovány v modelu strukturovaného úložiště OLE (například `STGM_READ`).

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*status*<br/>
[out] Stav pole objektů BLOB.

### <a name="bookmark_entry"></a> BOOKMARK_ENTRY

Vytvoří vazbu sloupec záložky.

#### <a name="syntax"></a>Syntaxe

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Parametry

*Proměnná*<br/>
[in] Proměnná bylo vázané na sloupce záložky.

#### <a name="example"></a>Příklad

```cpp
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```

Další informace najdete v tématu [pomocí záložky](using-bookmarks.md) a [CBookmark – třída](../../data/oledb/cbookmark-class.md).

### <a name="column_entry"></a> COLUMN_ENTRY

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Parametry

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenční informace pro OLE DB programátory*.

*nOrdinal*<br/>
[in] Číslo sloupce.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

COLUMN_ENTRY – makro se používá v následujících umístěních:

- Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

#### <a name="example"></a>Příklad

Podívejte se na příklady v tématech – makro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="column_entry_ex"></a> COLUMN_ENTRY_EX

Představuje vazbu na sadě řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenční informace pro OLE DB programátory*.

*nOrdinal*<br/>
[in] Číslo sloupce.

*wType*<br/>
[in] Datový typ.

*nLength*<br/>
[in] Velikost dat v bajtech.

*nPrecision*<br/>
[in] Maximální přesnost pro použití při získávání dat a *wType* je `DBTYPE_NUMERIC`. V opačném případě tento parametr je ignorován.

*nScale*<br/>
[in] Chcete použít při získávání dat a *wType* je `DBTYPE_NUMERIC` nebo `DBTYPE_DECIMAL`.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[in] Proměnná vázat délka sloupce.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

#### <a name="remarks"></a>Poznámky

COLUMN_ENTRY_EX – makro se používá v následujících umístěních:

- Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

#### <a name="example"></a>Příklad

Zobrazit [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="column_entry_length"></a> COLUMN_ENTRY_LENGTH

Představuje vazbu na sadě řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Parametry

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenční informace pro OLE DB programátory*.

*nOrdinal*<br/>
[in] Číslo sloupce s některou. Záložka odpovídá sloupci nula.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[in] Proměnná vázat délka sloupce.

#### <a name="remarks"></a>Poznámky

Podporuje toto makro *délka* proměnné. Používá se v následujících umístěních:

- Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_length_status"></a> COLUMN_ENTRY_LENGTH_STATUS

Představuje vazbu na sadě řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenční informace pro OLE DB programátory*.

*nOrdinal*<br/>
[in] Číslo sloupce.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[in] Proměnná vázat délka sloupce.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

#### <a name="remarks"></a>Poznámky

Použijte toto makro, pokud chcete zajistit podporu proměnné délky a stavu. Používá se v následujících umístěních:

- Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps"></a> COLUMN_ENTRY_PS

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenční informace pro OLE DB programátory*.

*nOrdinal*<br/>
[in] Číslo sloupce.

*nPrecision*<br/>
[in] Maximální přesnost sloupce, který chcete vytvořit vazbu.

*nScale*<br/>
[in] Škálování na sloupec, který chcete vytvořit vazbu.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Umožňuje určit hodnot precision a scale sloupce, který chcete vytvořit vazbu. Používá se v následujících umístěních:

- Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps_length"></a> COLUMN_ENTRY_PS_LENGTH

Představuje vazbu na sadě řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Parametry

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenční informace pro OLE DB programátory*.

*nOrdinal*<br/>
[in] Číslo sloupce s některou. Záložka odpovídá sloupci nula.

*nPrecision*<br/>
[in] Maximální přesnost sloupce, který chcete vytvořit vazbu.

*nScale*<br/>
[in] Škálování na sloupec, který chcete vytvořit vazbu.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[in] Proměnná vázat délka sloupce.

#### <a name="remarks"></a>Poznámky

Umožňuje určit hodnot precision a scale sloupce, který chcete vytvořit vazbu. Podporuje toto makro *délka* proměnné. Používá se v následujících umístěních:

- Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps_length_status"></a> COLUMN_ENTRY_PS_LENGTH_STATUS

Představuje vazbu na sadě řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenční informace pro OLE DB programátory*.

*nOrdinal*<br/>
[in] Číslo sloupce.

*nPrecision*<br/>
[in] Maximální přesnost sloupce, který chcete vytvořit vazbu.

*nScale*<br/>
[in] Škálování na sloupec, který chcete vytvořit vazbu.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[in] Proměnná vázat délka sloupce.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

#### <a name="remarks"></a>Poznámky

Umožňuje určit hodnot precision a scale sloupce, který chcete vytvořit vazbu. Použijte toto makro, pokud chcete zajistit podporu proměnné délky a stavu. Používá se v následujících umístěních:

- Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps_status"></a> COLUMN_ENTRY_PS_STATUS

Představuje vazbu na sadě řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Parametry

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenční informace pro OLE DB programátory*.

*nOrdinal*<br/>
[in] Číslo sloupce.

*nPrecision*<br/>
[in] Maximální přesnost sloupce, který chcete vytvořit vazbu.

*nScale*<br/>
[in] Škálování na sloupec, který chcete vytvořit vazbu.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

#### <a name="remarks"></a>Poznámky

Umožňuje určit hodnot precision a scale sloupce, který chcete vytvořit vazbu. Podporuje toto makro *stav* proměnné. Používá se v následujících umístěních:

- Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_status"></a> COLUMN_ENTRY_STATUS

Představuje vazbu na sadě řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Parametry

Zobrazit [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenční informace pro OLE DB programátory*.

*nOrdinal*<br/>
[in] Číslo sloupce.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

#### <a name="remarks"></a>Poznámky

Podporuje toto makro *stav* proměnné. Používá se v následujících umístěních:

- Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_type"></a> COLUMN_ENTRY_TYPE

Představuje vazbu na konkrétní sloupec v databázi. Podporuje *typ* parametru.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Číslo sloupce.

*wType*<br/>
[in] Datový typ vstupní sloupec.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Toto makro je specializované varianta [COLUMN_ENTRY](../../data/oledb/column-entry.md) makro, které poskytuje způsob určení datového typu.

### <a name="column_entry_type_size"></a> COLUMN_ENTRY_TYPE_SIZE

Představuje vazbu na konkrétní sloupec v databázi. Podporuje *typ* a *velikost* parametry.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
[in] Číslo sloupce.

*wType*<br/>
[in] Datový typ vstupní sloupec.

*nLength*<br/>
[in] Velikost vstupní sloupec v bajtech.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Toto makro je specializované varianta [COLUMN_ENTRY](../../data/oledb/column-entry.md) makro, které poskytuje prostředky pro určení velikosti a typu.

### <a name="column_name"></a> COLUMN_NAME

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_ENTRY](../../data/oledb/column-entry.md), s tím rozdílem, že toto makro přijímá název sloupce namísto číslo sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Makra COLUMN_NAME_ * se používají ve stejných míst jako [COLUMN_ENTRY](../../data/oledb/column-entry.md):

- Mezi [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) makra.

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_name_ex"></a> COLUMN_NAME_EX

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také datový typ, velikost, přesnosti, škálování, délka sloupce a sloupce stavu.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*wType*<br/>
[in] Datový typ.

*nLength*<br/>
[in] Velikost dat v bajtech.

*nPrecision*<br/>
[in] Maximální přesnost pro použití při získávání dat a *wType* je `DBTYPE_NUMERIC`. V opačném případě tento parametr je ignorován.

*nScale*<br/>
[in] Chcete použít při získávání dat a *wType* je `DBTYPE_NUMERIC` nebo `DBTYPE_DECIMAL`.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[in] Proměnná vázat délka sloupce.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_length"></a> COLUMN_NAME_LENGTH

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také délka sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[in] Proměnná vázat délka sloupce.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_length_status"></a> COLUMN_NAME_LENGTH_STATUS

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také délka sloupce a sloupce stavu.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[in] Proměnná vázat délka sloupce.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_ps"></a> COLUMN_NAME_PS

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také hodnot precision a scale.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*nPrecision*<br/>
[in] Maximální přesnost sloupce, který chcete vytvořit vazbu.

*nScale*<br/>
[in] Škálování na sloupec, který chcete vytvořit vazbu.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_ps_length"></a> COLUMN_NAME_PS_LENGTH

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také délka přesnost, měřítko a sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*nPrecision*<br/>
[in] Maximální přesnost sloupce, který chcete vytvořit vazbu.

*nScale*<br/>
[in] Škálování na sloupec, který chcete vytvořit vazbu.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[in] Proměnná vázat délka sloupce.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_ps_length_status"></a> COLUMN_NAME_PS_LENGTH_STATUS

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také přesnost, měřítko, délka sloupce a sloupce stavu.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*nPrecision*<br/>
[in] Maximální přesnost sloupce, který chcete vytvořit vazbu.

*nScale*<br/>
[in] Škálování na sloupec, který chcete vytvořit vazbu.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[in] Proměnná vázat délka sloupce.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_ps_status"></a> COLUMN_NAME_PS_STATUS

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také přesnost, měřítko a sloupec Stav.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*nPrecision*<br/>
[in] Maximální přesnost sloupce, který chcete vytvořit vazbu.

*nScale*<br/>
[in] Škálování na sloupec, který chcete vytvořit vazbu.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_status"></a> COLUMN_NAME_STATUS

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také sloupec Stav.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_type"></a> COLUMN_NAME_TYPE

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také datového typu.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*wType*<br/>
[in] Datový typ.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_type_ps"></a> COLUMN_NAME_TYPE_PS

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také datový typ, přesnost a měřítko.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*wType*<br/>
[in] Datový typ.

*nPrecision*<br/>
[in] Maximální přesnost pro použití při získávání dat a *wType* je `DBTYPE_NUMERIC`. V opačném případě tento parametr je ignorován.

*nScale*<br/>
[in] Chcete použít při získávání dat a *wType* je `DBTYPE_NUMERIC` nebo `DBTYPE_DECIMAL`.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_type_size"></a> COLUMN_NAME_TYPE_SIZE

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také datový typ a velikost.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*wType*<br/>
[in] Datový typ.

*nLength*<br/>
[in] Velikost dat v bajtech.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="column_name_type_status"></a> COLUMN_NAME_TYPE_STATUS

Představuje vazbu na sadě řádků na konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro přijímá také datový typ ve sloupci stav.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[in] Ukazatel na název sloupce. Název musí být řetězec s kódováním Unicode. Můžete to udělat tak, že vložíte "L" před název, například: `L"MyColumn"`.

*wType*<br/>
[in] Datový typ.

*status*<br/>
[in] Proměnná bylo vázané na sloupce stavu.

*data*<br/>
[in] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Zobrazit [COLUMN_NAME](../../data/oledb/column-name.md) informace o tom, kde se používají makra COLUMN_NAME_ *.

### <a name="end_column_map"></a> END_COLUMN_MAP

Označuje konec položky mapování sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Poznámky

Používá se s jeden přistupující objekt pro sadu řádků. BEGIN_COLUMN_MAP – makro je dokončena s END_COLUMN_MAP – makro.

#### <a name="example"></a>Příklad

See [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

### <a name="define_command"></a> DEFINE_COMMAND

Určuje příkaz, který se použije k vytvoření sady řádků při použití [CCommand](../../data/oledb/ccommand-class.md) třídy. Přijímá pouze typy řetězce odpovídající určený typ aplikace (ANSI nebo Unicode).

> [!NOTE]
>  Doporučuje se, že používáte [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) místo DEFINE_COMMAND.

#### <a name="syntax"></a>Syntaxe

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
[in] Název třídy uživatelů záznamu (příkaz).

*szCommand*<br/>
[in] Řetězec příkazu, který se použije k vytvoření sady řádků při použití [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Poznámky

Řetězec příkazu, který zadáte se použije jako výchozí, pokud nezadáte text příkazu v [CCommand::Open](../../data/oledb/ccommand-open.md) metody.

Toto makro přijímá řetězce ANSI, pokud vytváříte aplikaci jako ANSI nebo Unicode řetězce, pokud vytváříte aplikaci jako kódování Unicode. Doporučuje se, že používáte [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) místo DEFINE_COMMAND, protože bývalé řetězců v kódu Unicode, bez ohledu na typ aplikace ANSI nebo Unicode.

#### <a name="example"></a>Příklad

Zobrazit [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="define_command_ex"></a> DEFINE_COMMAND_EX

Určuje příkaz, který se použije k vytvoření sady řádků při použití [CCommand](../../data/oledb/ccommand-class.md) třídy. Podporuje kódování Unicode a ANSI aplikace.

#### <a name="syntax"></a>Syntaxe

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
[in] Název třídy uživatelů záznamu (příkaz).

*wszCommand*<br/>
[in] Řetězec příkazu, který se použije k vytvoření sady řádků při použití [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Poznámky

Řetězec příkazu, který zadáte se použije jako výchozí, pokud nezadáte text příkazu v [CCommand::Open](../../data/oledb/ccommand-open.md) metody.

Toto makro přijímá řetězců v kódu Unicode, bez ohledu na typ aplikace. Toto makro je upřednostňované nad [DEFINE_COMMAND](../../data/oledb/define-command.md) protože podporuje kódování Unicode a také aplikací ANSI.

#### <a name="example"></a>Příklad

Zobrazit [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="begin_param_map"></a> BEGIN_PARAM_MAP

Označuje začátek položek mapování parametrů.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Parametry

*x*<br/>
[in] Název třídy uživatelského záznamu.

#### <a name="remarks"></a>Poznámky

Parametry jsou používány [příkazy](/previous-versions/windows/desktop/ms724608(v=vs.85)).

#### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) – makro.

### <a name="end_param_map"></a> END_PARAM_MAP

Označuje konec položek mapování parametrů.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Příklad

Podívejte se na příklad pro [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) – makro.

### <a name="set_param_type"></a> SET_PARAM_TYPE

Určuje COLUMN_ENTRY makra, které SET_PARAM_TYPE – makro vstupní, výstupní nebo vstupně výstupní.

#### <a name="syntax"></a>Syntaxe

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Parametry

*type*<br/>
[in] Typ, který má nastavit pro parametr.

#### <a name="remarks"></a>Poznámky

Podporují pouze vstupní a výstupní typy parametrů podkladový zdroj dat nepodporuje. Typ je kombinace jedné nebo více `DBPARAMIO` hodnoty (viz [DBBINDING struktury](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *OLE DB referenční informace pro programátory*):

- `DBPARAMIO_NOTPARAM` Přistupující objekt nemá žádné parametry. Obvykle nastavena `eParamIO` na tuto hodnotu v řádku přístupové objekty pro upozornit uživatele, že parametry budou ignorovány.

- `DBPARAMIO_INPUT` Vstupní parametr.

- `DBPARAMIO_OUTPUT` Výstupní parametr.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` Parametr je vstupní a výstupní parametr.

#### <a name="example"></a>Příklad

```cpp
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** také atldbcli.h

## <a name="see-also"></a>Viz také:

[Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB – šablony příjemce](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)