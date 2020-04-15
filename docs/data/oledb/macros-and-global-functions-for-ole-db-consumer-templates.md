---
title: Makra a globální funkce pro šablony příjemců OLE DB
ms.date: 02/11/2019
f1_keywords:
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
ms.openlocfilehash: 8b898990672f590f6047eef6fdfd1ed7eecb3f92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369816"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Makra a globální funkce pro šablony příjemců OLE DB

Šablony spotřebitelů TECHNOLOGIE OLE DB obsahují následující makra a globální funkce:

## <a name="global-functions"></a>Globální funkce

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Pokud je vrácena chyba, vypíše do zařízení s výpisem stavu paměti informace o chybovém záznamu technologie OLE DB.|

## <a name="accessor-map-macros"></a>Makra mapy přístupu

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Označuje začátek přistupující položky.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Označuje začátek položek mapy přistupujícího nebo přístupu.|
|[END_ACCESSOR](#end_accessor)|Označuje konec přistupující položky.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Označuje konec položek mapy přistupujícího nebo přístupu.|

## <a name="column-map-macros"></a>Makra mapování sloupců

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Označuje začátek položek mapy sloupců ve třídě záznamu uživatele.|
|[BLOB_ENTRY](#blob_entry)|Slouží k vázání binárního velkého objektu (BLOB).|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Hlásí délku datového sloupce BLOB.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Hlásí délku a stav datového sloupce BLOB.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Hlásí stav datového sloupce BLOB.|
|[BLOB_NAME](#blob_name)|Slouží k vytvoření svázání binárního velkého objektu podle názvu sloupce.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Hlásí délku datového sloupce BLOB.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Hlásí délku a stav datového sloupce BLOB.|
|[BLOB_NAME_STATUS](#blob_name_status)|Hlásí stav datového sloupce BLOB.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Představuje položku záložky v sadě řádků. Položka záložky je zvláštní druh položky sloupce.|
|[COLUMN_ENTRY](#column_entry)|Představuje vazbu na konkrétní sloupec v databázi.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *parametry typu*, *délky*, *přesnosti*, *měřítka*a *stavu.*|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje proměnnou *length.*|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje parametry *stavu* a *délky.*|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *parametry přesnosti* a *měřítka.*|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje parametry proměnné *délky,* *přesnosti* a *měřítka.*|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *proměnné stavu* a *délky,* *přesnost* a *parametry měřítka.*|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *parametry stavové* proměnné, *přesnosti* a *měřítka.*|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *proměnnou stavu.*|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje parametr *typu.*|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje *parametry typu* a *velikosti.*|
|[COLUMN_NAME](#column_name)|Představuje vazbu na konkrétní sloupec v databázi podle názvu.|
|[COLUMN_NAME_EX](#column_name_ex)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datového typu, velikosti, přesnosti, měřítka, délky sloupce a stavu sloupce.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci délky sloupu.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci délky a stavu sloupce.|
|[COLUMN_NAME_PS](#column_name_ps)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci přesnosti a měřítka.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci přesnosti, měřítka a délky sloupce.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci přesnosti, měřítka, délky sloupce a stavu sloupce.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci přesnosti, měřítka a stavu sloupce.|
|[COLUMN_NAME_STATUS](#column_name_status)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci stavu sloupce.|
|[COLUMN_NAME_TYPE](#column_name_type)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datového typu.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datového typu, přesnosti a měřítka.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datového typu a velikosti.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datového typu a stavu sloupce.|
|[END_COLUMN_MAP](#end_column_map)|Označuje konec položek mapy sloupců.|

## <a name="command-macros"></a>Příkaz ová l.

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|Určuje příkaz, který bude použit k vytvoření sady řádků při použití třídy [CCommand.](../../data/oledb/ccommand-class.md) Přijímá pouze typy řetězců odpovídající zadanému typu aplikace (ANSI nebo Unicode). Doporučujeme používat [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) místo DEFINE_COMMAND.|
|[DEFINE_COMMAND_EX](#define_command_ex)|Určuje příkaz, který bude použit k vytvoření sady řádků při použití třídy [CCommand.](../../data/oledb/ccommand-class.md) Podporuje aplikace ANSI a Unicode.|

## <a name="parameter-map-macros"></a>Makra mapování parametrů

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Označí začátek položek mapy parametrů ve třídě záznamu uživatele.|
|[END_PARAM_MAP](#end_param_map)|Označuje konec položek mapy parametrů.|
|[SET_PARAM_TYPE](#set_param_type)|Určuje COLUMN_ENTRY makra, která následují za SET_PARAM_TYPE makra jako vstup, výstup nebo vstup/výstup.|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a>AtlTraceErrorRecords

Pokud je vrácena chyba, vypíše do zařízení s výpisem stavu paměti informace o chybovém záznamu technologie OLE DB.

#### <a name="syntax"></a>Syntaxe

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Parametry

*Herr*<br/>
[v] HRESULT vrácené členskou funkcí šablony příjemce TECHNOLOGIE OLE DB.

#### <a name="remarks"></a>Poznámky

Pokud *hErr* není `AtlTraceErrorRecords` S_OK, vypíše informace o záznamu chyby TECHNOLOGIE OLE DB do zařízení s výpisem stavu paměti (karta **Ladění** okna Výstup nebo souboru). Informace o záznamu chyby, které jsou získány od zprostředkovatele, zahrnují číslo řádku, zdroj, popis, soubor nápovědy, kontext a identifikátor GUID pro každou položku záznamu chyby. `AtlTraceErrorRecords`vypíše tyto informace pouze v sestavení ladění. Ve verzi sestavení je prázdný zástupný kód, který je optimalizován. Další informace naleznete v tématu [CDBErrorInfo Class](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a><a name="begin_accessor"></a>BEGIN_ACCESSOR

Označuje začátek přistupující položky.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Parametry

*num*<br/>
[v] Číslo nulového odsazení pro přistupujícího oru v této mapě přistupujícího chodu.

*bAuto*<br/>
[v] Určuje, zda je tento přistupující objekt automatickým přistupujícím objektem nebo ruční mstiteč. Pokud **true**, přistupující ho je auto; pokud **false**, přistupující odkaz je ruční. Automatický přistupující objekt znamená, že data jsou načtena pro vás při operacích přesunutí.

#### <a name="remarks"></a>Poznámky

V případě více přistupujících osob v sadě řádků je třeba zadat BEGIN_ACCESSOR_MAP a použít BEGIN_ACCESSOR makro pro každý jednotlivý přistupující ho. Makro BEGIN_ACCESSOR je doplněno END_ACCESSOR makra. Makro BEGIN_ACCESSOR_MAP je doplněno END_ACCESSOR_MAP makra.

#### <a name="example"></a>Příklad

Viz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a>BEGIN_ACCESSOR_MAP

Označuje začátek položek mapy přistupujícího nebo přístupu.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název třídy záznamu uživatele.

*num*<br/>
[v] Počet přístupových částí v této mapě přistupujícího přístupu.

#### <a name="remarks"></a>Poznámky

V případě více přistupujících osob v sadě řádků je třeba zadat BEGIN_ACCESSOR_MAP na začátku a použít BEGIN_ACCESSOR makro pro každý jednotlivý přistupující ho. Makro BEGIN_ACCESSOR je doplněno END_ACCESSOR makra. Mapa přistupujícího oru je doplněna END_ACCESSOR_MAP makro.

Pokud máte v uživatelském záznamu pouze jeden přistupující odkaz, použijte [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)maker .

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

### <a name="end_accessor"></a><a name="end_accessor"></a>END_ACCESSOR

Označuje konec přistupující položky.

#### <a name="syntax"></a>Syntaxe

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Poznámky

Pro více přistupujících osob v sadě řádků je třeba zadat BEGIN_ACCESSOR_MAP a použít BEGIN_ACCESSOR makro pro každý jednotlivý přistupující ho. Makro BEGIN_ACCESSOR je doplněno END_ACCESSOR makra. Makro BEGIN_ACCESSOR_MAP je doplněno END_ACCESSOR_MAP makra.

#### <a name="example"></a>Příklad

Viz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a>END_ACCESSOR_MAP

Označuje konec položek mapy přistupujícího nebo přístupu.

#### <a name="syntax"></a>Syntaxe

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Poznámky

Pro více přistupujících osob v sadě řádků je třeba zadat BEGIN_ACCESSOR_MAP a použít BEGIN_ACCESSOR makro pro každý jednotlivý přistupující ho. Makro BEGIN_ACCESSOR je doplněno END_ACCESSOR makra. Makro BEGIN_ACCESSOR_MAP je doplněno END_ACCESSOR_MAP makra.

#### <a name="example"></a>Příklad

Viz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_column_map"></a><a name="begin_column_map"></a>BEGIN_COLUMN_MAP

Označuje začátek položky mapy sloupců.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název třídy záznamu uživatele odvozené z `CAccessor`.

#### <a name="remarks"></a>Poznámky

Toto makro se používá v případě jednoho přistupujícího serveru na sadě řádků. Pokud máte více přistupujících pořádků na sadu řádků, použijte [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

Makro BEGIN_COLUMN_MAP je doplněno END_COLUMN_MAP makra. Toto makro se používá v případě, že je v záznamu uživatele vyžadován pouze jeden přistupující odkaz.

Sloupce odpovídají polím v sadě řádků, které chcete svázat.

#### <a name="example"></a>Příklad

Zde je ukázkový sloupec a mapa parametrů:

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a>BLOB_ENTRY

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vázání binárního velkého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))).

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinální*<br/>
[v] Číslo sloupce.

*Iid*<br/>
[v] Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, slouží k načtení objektu BLOB.

*příznaky*<br/>
[v] Příznaky režimu úložiště definované modelem strukturovaného úložiště `STGM_READ`OLE (například).

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="example"></a>Příklad

Podívejte [se, jak lze získat objekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a>BLOB_ENTRY_LENGTH

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vázání binárního velkého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro také získá délku v bajtů sloupce BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Parametry

*nOrdinální*<br/>
[v] Číslo sloupce.

*Iid*<br/>
[v] Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, slouží k načtení objektu BLOB.

*příznaky*<br/>
[v] Příznaky režimu úložiště definované modelem strukturovaného úložiště `STGM_READ`OLE (například).

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[out] (Skutečná) délka v bajtech sloupce BLOB.

#### <a name="example"></a>Příklad

Podívejte [se, jak lze získat objekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a>BLOB_ENTRY_LENGTH_STATUS

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vázání binárního velkého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro také získá délku a stav sloupce BLOB.

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

*nOrdinální*<br/>
[v] Číslo sloupce.

*Iid*<br/>
[v] Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, slouží k načtení objektu BLOB.

*příznaky*<br/>
[v] Příznaky režimu úložiště definované modelem strukturovaného úložiště `STGM_READ`OLE (například).

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[out] (Skutečná) délka v bajtech sloupce BLOB.

*Stav*<br/>
[out] Stav datového sloupce BLOB.

#### <a name="example"></a>Příklad

Podívejte [se, jak lze získat objekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a>BLOB_ENTRY_STATUS

Používá se s BEGIN_COLUMN_MAP nebo BEGIN_ACCESSOR_MAP k vázání binárního velkého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro také získá stav sloupce BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Parametry

*nOrdinální*<br/>
[v] Číslo sloupce.

*Iid*<br/>
[v] Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, slouží k načtení objektu BLOB.

*příznaky*<br/>
[v] Příznaky režimu úložiště definované modelem strukturovaného úložiště `STGM_READ`OLE (například).

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Stav*<br/>
[out] Stav pole BLOB.

#### <a name="example"></a>Příklad

Podívejte [se, jak lze získat objekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a><a name="blob_name"></a>BLOB_NAME

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vázání binárního velkého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro má název sloupce namísto čísla sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Iid*<br/>
[v] Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, slouží k načtení objektu BLOB.

*příznaky*<br/>
[v] Příznaky režimu úložiště definované modelem strukturovaného úložiště `STGM_READ`OLE (například).

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="example"></a>Příklad

Podívejte [se, jak lze získat objekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a><a name="blob_name_length"></a>BLOB_NAME_LENGTH

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vázání binárního velkého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_NAME](../../data/oledb/blob-name.md), s tím rozdílem, že toto makro také získá délku v bajtů datového sloupce BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Iid*<br/>
[v] Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, slouží k načtení objektu BLOB.

*příznaky*<br/>
[v] Příznaky režimu úložiště definované modelem strukturovaného úložiště `STGM_READ`OLE (například).

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[out] (Skutečná) délka v bajtech sloupce BLOB.

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a>BLOB_NAME_LENGTH_STATUS

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vázání binárního velkého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_NAME](../../data/oledb/blob-name.md), s tím rozdílem, že toto makro také získá délku a stav sloupce dat BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Iid*<br/>
[v] Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, slouží k načtení objektu BLOB.

*příznaky*<br/>
[v] Příznaky režimu úložiště definované modelem strukturovaného úložiště `STGM_READ`OLE (například).

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[out] (Skutečná) délka v bajtech sloupce BLOB.

*Stav*<br/>
[out] Stav pole BLOB.

### <a name="blob_name_status"></a><a name="blob_name_status"></a>BLOB_NAME_STATUS

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vázání binárního velkého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako [BLOB_NAME](../../data/oledb/blob-name.md), s tím rozdílem, že toto makro také získá stav sloupce dat BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Iid*<br/>
[v] Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, slouží k načtení objektu BLOB.

*příznaky*<br/>
[v] Příznaky režimu úložiště definované modelem strukturovaného úložiště `STGM_READ`OLE (například).

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Stav*<br/>
[out] Stav pole BLOB.

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a>BOOKMARK_ENTRY

Sváže sloupec záložky.

#### <a name="syntax"></a>Syntaxe

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Parametry

*Proměnné*<br/>
[v] Proměnná, která má být vázána na sloupec záložky.

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

Další informace naleznete [v tématu Použití záložek](using-bookmarks.md) a [třídy CBookmark](../../data/oledb/cbookmark-class.md).

### <a name="column_entry"></a><a name="column_entry"></a>COLUMN_ENTRY

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *odkazu programátora OLE DB*.

*nOrdinální*<br/>
[v] Číslo sloupce.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Makro COLUMN_ENTRY se používá na následujících místech:

- Mezi [makry BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

#### <a name="example"></a>Příklad

Podívejte se na příklady v tématech maker, [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a>COLUMN_ENTRY_EX

Představuje vazbu na sadu řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *odkazu programátora OLE DB*.

*nOrdinální*<br/>
[v] Číslo sloupce.

*Wtype*<br/>
[v] Datový typ.

*nDélka*<br/>
[v] Velikost dat v bajtů.

*nPřesnost*<br/>
[v] Maximální přesnost pro použití při získávání `DBTYPE_NUMERIC`dat a *wType* je . V opačném případě je tento parametr ignorován.

*nMěřítko*<br/>
[v] Měřítko, které se má použít `DBTYPE_NUMERIC` při `DBTYPE_DECIMAL`získávání dat a *wType* je nebo .

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[v] Proměnná, která má být vázána na délku sloupce.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Makro COLUMN_ENTRY_EX se používá na následujících místech:

- Mezi [makry BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

#### <a name="example"></a>Příklad

Viz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="column_entry_length"></a><a name="column_entry_length"></a>COLUMN_ENTRY_LENGTH

Představuje vazbu na sadu řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *odkazu programátora OLE DB*.

*nOrdinální*<br/>
[v] Číslo sloupce, počínaje jedním. Záložka odpovídá sloupci nula.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[v] Proměnná, která má být vázána na délku sloupce.

#### <a name="remarks"></a>Poznámky

Toto makro podporuje proměnnou *length.* Používá se na následujících místech:

- Mezi [makry BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a>COLUMN_ENTRY_LENGTH_STATUS

Představuje vazbu na sadu řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *odkazu programátora OLE DB*.

*nOrdinální*<br/>
[v] Číslo sloupce.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[v] Proměnná, která má být vázána na délku sloupce.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Toto makro použijte, pokud chcete podporovat proměnné délky a stavu. Používá se na následujících místech:

- Mezi [makry BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a>COLUMN_ENTRY_PS

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *odkazu programátora OLE DB*.

*nOrdinální*<br/>
[v] Číslo sloupce.

*nPřesnost*<br/>
[v] Maximální přesnost sloupce, který chcete vázat.

*nMěřítko*<br/>
[v] Měřítko sloupce, který chcete svázat.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Umožňuje určit přesnost a měřítko sloupce, který chcete svázat. Používá se na následujících místech:

- Mezi [makry BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a>COLUMN_ENTRY_PS_LENGTH

Představuje vazbu na sadu řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *odkazu programátora OLE DB*.

*nOrdinální*<br/>
[v] Číslo sloupce, počínaje jedním. Záložka odpovídá sloupci nula.

*nPřesnost*<br/>
[v] Maximální přesnost sloupce, který chcete vázat.

*nMěřítko*<br/>
[v] Měřítko sloupce, který chcete svázat.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[v] Proměnná, která má být vázána na délku sloupce.

#### <a name="remarks"></a>Poznámky

Umožňuje určit přesnost a měřítko sloupce, který chcete svázat. Toto makro podporuje proměnnou *length.* Používá se na následujících místech:

- Mezi [makry BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a>COLUMN_ENTRY_PS_LENGTH_STATUS

Představuje vazbu na sadu řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *odkazu programátora OLE DB*.

*nOrdinální*<br/>
[v] Číslo sloupce.

*nPřesnost*<br/>
[v] Maximální přesnost sloupce, který chcete vázat.

*nMěřítko*<br/>
[v] Měřítko sloupce, který chcete svázat.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[v] Proměnná, která má být vázána na délku sloupce.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Umožňuje určit přesnost a měřítko sloupce, který chcete svázat. Toto makro použijte, pokud chcete podporovat proměnné délky a stavu. Používá se na následujících místech:

- Mezi [makry BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a>COLUMN_ENTRY_PS_STATUS

Představuje vazbu na sadu řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *odkazu programátora OLE DB*.

*nOrdinální*<br/>
[v] Číslo sloupce.

*nPřesnost*<br/>
[v] Maximální přesnost sloupce, který chcete vázat.

*nMěřítko*<br/>
[v] Měřítko sloupce, který chcete svázat.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Umožňuje určit přesnost a měřítko sloupce, který chcete svázat. Toto makro podporuje *proměnnou stavu.* Používá se na následujících místech:

- Mezi [makry BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_status"></a><a name="column_entry_status"></a>COLUMN_ENTRY_STATUS

Představuje vazbu na sadu řádků na konkrétní sloupec v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *odkazu programátora OLE DB*.

*nOrdinální*<br/>
[v] Číslo sloupce.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Toto makro podporuje *proměnnou stavu.* Používá se na následujících místech:

- Mezi [makry BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_entry_type"></a><a name="column_entry_type"></a>COLUMN_ENTRY_TYPE

Představuje vazbu na konkrétní sloupec v databázi. Podporuje parametr *typu.*

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinální*<br/>
[v] Číslo sloupce.

*Wtype*<br/>
[v] Datový typ položky sloupce.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Toto makro je specializovanou variantou [COLUMN_ENTRY](../../data/oledb/column-entry.md) makra, která poskytuje prostředky pro určení datového typu.

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a>COLUMN_ENTRY_TYPE_SIZE

Představuje vazbu na konkrétní sloupec v databázi. Podporuje *parametry typu* a *velikosti.*

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinální*<br/>
[v] Číslo sloupce.

*Wtype*<br/>
[v] Datový typ položky sloupce.

*nDélka*<br/>
[v] Velikost položky sloupce v bajtech.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Toto makro je specializovanou variantou [COLUMN_ENTRY](../../data/oledb/column-entry.md) makra, která poskytuje prostředky pro určení velikosti a typu dat.

### <a name="column_name"></a><a name="column_name"></a>Column_name

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_ENTRY](../../data/oledb/column-entry.md), s tím rozdílem, že toto makro má název sloupce namísto čísla sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Makra COLUMN_NAME_* se používají na stejných místech jako [COLUMN_ENTRY](../../data/oledb/column-entry.md):

- Mezi [makry BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP.](../../data/oledb/end-column-map.md)

- Mezi [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) makra.

- Mezi [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) makra.

### <a name="column_name_ex"></a><a name="column_name_ex"></a>COLUMN_NAME_EX

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá datový typ, velikost, přesnost, měřítko, délku sloupce a stav sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Wtype*<br/>
[v] Datový typ.

*nDélka*<br/>
[v] Velikost dat v bajtů.

*nPřesnost*<br/>
[v] Maximální přesnost pro použití při získávání `DBTYPE_NUMERIC`dat a *wType* je . V opačném případě je tento parametr ignorován.

*nMěřítko*<br/>
[v] Měřítko, které se má použít `DBTYPE_NUMERIC` při `DBTYPE_DECIMAL`získávání dat a *wType* je nebo .

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[v] Proměnná, která má být vázána na délku sloupce.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_length"></a><a name="column_name_length"></a>COLUMN_NAME_LENGTH

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také trvá délku sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[v] Proměnná, která má být vázána na délku sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a>COLUMN_NAME_LENGTH_STATUS

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro má také délku sloupce a stav sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[v] Proměnná, která má být vázána na délku sloupce.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_ps"></a><a name="column_name_ps"></a>COLUMN_NAME_PS

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také bere přesnost a měřítko.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*nPřesnost*<br/>
[v] Maximální přesnost sloupce, který chcete vázat.

*nMěřítko*<br/>
[v] Měřítko sloupce, který chcete svázat.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a>COLUMN_NAME_PS_LENGTH

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také trvá přesnost, měřítko a délku sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*nPřesnost*<br/>
[v] Maximální přesnost sloupce, který chcete vázat.

*nMěřítko*<br/>
[v] Měřítko sloupce, který chcete svázat.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[v] Proměnná, která má být vázána na délku sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a>COLUMN_NAME_PS_LENGTH_STATUS

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá přesnost, měřítko, délku sloupce a stav sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*nPřesnost*<br/>
[v] Maximální přesnost sloupce, který chcete vázat.

*nMěřítko*<br/>
[v] Měřítko sloupce, který chcete svázat.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Délka*<br/>
[v] Proměnná, která má být vázána na délku sloupce.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a>COLUMN_NAME_PS_STATUS

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá přesnost, měřítko a stav sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*nPřesnost*<br/>
[v] Maximální přesnost sloupce, který chcete vázat.

*nMěřítko*<br/>
[v] Měřítko sloupce, který chcete svázat.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_status"></a><a name="column_name_status"></a>COLUMN_NAME_STATUS

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro má také stav sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_type"></a><a name="column_name_type"></a>COLUMN_NAME_TYPE

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá datový typ.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Wtype*<br/>
[v] Datový typ.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a>COLUMN_NAME_TYPE_PS

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá datový typ, přesnost a měřítko.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Wtype*<br/>
[v] Datový typ.

*nPřesnost*<br/>
[v] Maximální přesnost pro použití při získávání `DBTYPE_NUMERIC`dat a *wType* je . V opačném případě je tento parametr ignorován.

*nMěřítko*<br/>
[v] Měřítko, které se má použít `DBTYPE_NUMERIC` při `DBTYPE_DECIMAL`získávání dat a *wType* je nebo .

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a>COLUMN_NAME_TYPE_SIZE

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá datový typ a velikost.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Wtype*<br/>
[v] Datový typ.

*nDélka*<br/>
[v] Velikost dat v bajtů.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a>COLUMN_NAME_TYPE_STATUS

Představuje vazbu na sadu řádků na konkrétní sloupec v sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá stav datového typu a sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
[v] Ukazatel na název sloupce. Název musí být řetězec Unicode. Toho můžete dosáhnout umístěním písmene L před název, `L"MyColumn"`například: .

*Wtype*<br/>
[v] Datový typ.

*Stav*<br/>
[v] Proměnná, která má být vázána na stav sloupce.

*Dat*<br/>
[v] Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_*, naleznete v [COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="end_column_map"></a><a name="end_column_map"></a>END_COLUMN_MAP

Označuje konec položek mapy sloupců.

#### <a name="syntax"></a>Syntaxe

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Poznámky

Používá se s jedním přistupujícím členem na sadě řádků. Makro BEGIN_COLUMN_MAP je doplněno END_COLUMN_MAP makra.

#### <a name="example"></a>Příklad

Viz [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

### <a name="define_command"></a><a name="define_command"></a>DEFINE_COMMAND

Určuje příkaz, který bude použit k vytvoření sady řádků při použití třídy [CCommand.](../../data/oledb/ccommand-class.md) Přijímá pouze typy řetězců odpovídající zadanému typu aplikace (ANSI nebo Unicode).

> [!NOTE]
> Doporučujeme používat [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) místo DEFINE_COMMAND.

#### <a name="syntax"></a>Syntaxe

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název třídy uživatelského záznamu (příkazu).

*szCommand*<br/>
[v] Příkazový řetězec, který bude použit k vytvoření sady řádků při použití [příkazu CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Poznámky

Zadaný příkazový řetězec bude použit jako výchozí, pokud nezadáte text příkazu v metodě [CCommand::Open.](../../data/oledb/ccommand-open.md)

Toto makro přijímá řetězce ANSI, pokud vytvoříte aplikaci jako ANSI, nebo unicode řetězce, pokud vytvoříte aplikaci jako Unicode. Doporučujese používat [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) místo DEFINE_COMMAND, protože první přijímá řetězce Unicode, bez ohledu na typ aplikace ANSI nebo Unicode.

#### <a name="example"></a>Příklad

Viz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="define_command_ex"></a><a name="define_command_ex"></a>DEFINE_COMMAND_EX

Určuje příkaz, který bude použit k vytvoření sady řádků při použití třídy [CCommand.](../../data/oledb/ccommand-class.md) Podporuje aplikace Unicode a ANSI.

#### <a name="syntax"></a>Syntaxe

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název třídy uživatelského záznamu (příkazu).

*příkaz wsz*<br/>
[v] Příkazový řetězec, který bude použit k vytvoření sady řádků při použití [příkazu CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Poznámky

Zadaný příkazový řetězec bude použit jako výchozí, pokud nezadáte text příkazu v metodě [CCommand::Open.](../../data/oledb/ccommand-open.md)

Toto makro přijímá řetězce Unicode bez ohledu na typ aplikace. Toto makro je upřednostňováno před [DEFINE_COMMAND,](../../data/oledb/define-command.md) protože podporuje aplikace Unicode i ANSI.

#### <a name="example"></a>Příklad

Viz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="begin_param_map"></a><a name="begin_param_map"></a>BEGIN_PARAM_MAP

Označuje začátek položek mapy parametrů.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Parametry

*X*<br/>
[v] Název třídy záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Parametry jsou [používány příkazy](/previous-versions/windows/desktop/ms724608(v=vs.85)).

#### <a name="example"></a>Příklad

Podívejte se na příklad [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) makra.

### <a name="end_param_map"></a><a name="end_param_map"></a>END_PARAM_MAP

Označuje konec položek mapy parametrů.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Příklad

Podívejte se na příklad [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) makra.

### <a name="set_param_type"></a><a name="set_param_type"></a>SET_PARAM_TYPE

Určuje COLUMN_ENTRY makra, která následují za SET_PARAM_TYPE vstupu makra, výstupu nebo vstupu/výstupu.

#### <a name="syntax"></a>Syntaxe

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Parametry

*Typ*<br/>
[v] Typ, který chcete nastavit pro parametr.

#### <a name="remarks"></a>Poznámky

Zprostředkovatelé podporují pouze typy vstupních a výstupních parametrů, které jsou podporovány podkladovým zdrojem dat. Typ je kombinací jedné nebo `DBPARAMIO` více hodnot (viz [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)) in the *OLE DB Programmer's Reference*):

- `DBPARAMIO_NOTPARAM`Přistupující objekt nemá žádné parametry. Obvykle natuto `eParamIO` hodnotu v přístupových objektech řádku připomenout uživateli, že parametry jsou ignorovány.

- `DBPARAMIO_INPUT`Vstupní parametr.

- `DBPARAMIO_OUTPUT`Výstupní parametr.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT`Parametr je vstupní i výstupní parametr.

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

**Záhlaví:** atldbcli.h

## <a name="see-also"></a>Viz také

[Makra a globální funkce pro šablony spotřebitelů technologie OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[Šablony spotřebitelů OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Odkaz na šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
