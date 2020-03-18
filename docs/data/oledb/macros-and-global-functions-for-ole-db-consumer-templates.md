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
ms.openlocfilehash: 83d38dda61d973b2d176ee7164011d665ee04655
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446848"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Makra a globální funkce pro šablony příjemců OLE DB

Šablony příjemce OLE DB zahrnují následující makra a globální funkce:

## <a name="global-functions"></a>Globální funkce

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Pokud se vrátí chyba, vypíše OLE DB informace o záznamu chyby do zařízení s výpisem paměti.|

## <a name="accessor-map-macros"></a>Makra mapy přistupujícího objektu

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Označuje začátek vstupu přistupujícího objektu.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Označuje začátek položek mapy přistupujícího objektu.|
|[END_ACCESSOR](#end_accessor)|Označuje konec položky přístupového objektu.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Označuje konec položek mapy přistupujícího objektu.|

## <a name="column-map-macros"></a>Makra map sloupců

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Označí začátek položek mapování sloupce v třídě záznamu uživatele.|
|[BLOB_ENTRY](#blob_entry)|Slouží k vytvoření vazby binárního rozsáhlého objektu (BLOB).|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Oznamuje délku sloupce dat objektu BLOB.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Oznamuje délku a stav sloupce dat objektu BLOB.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Oznamuje stav sloupce dat objektu BLOB.|
|[BLOB_NAME](#blob_name)|Slouží k vytvoření vazby binárního rozsáhlého objektu podle názvu sloupce.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Oznamuje délku sloupce dat objektu BLOB.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Oznamuje délku a stav sloupce dat objektu BLOB.|
|[BLOB_NAME_STATUS](#blob_name_status)|Oznamuje stav sloupce dat objektu BLOB.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Představuje položku záložky na sadě řádků. Položka záložky je zvláštní druh položky sloupce.|
|[COLUMN_ENTRY](#column_entry)|Představuje vazbu na konkrétní sloupec v databázi.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje parametry *Type*, *Length*, *Precision*, *Scale*a *status* .|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje proměnnou *Length* .|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje parametry *stavu* a *délky* .|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje parametry *Precision* a *Scale* .|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje proměnnou *Length* , parametry *Precision* a *Scale* .|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje proměnné *stavu* a *délky* , parametry *přesnosti* a *škálování* .|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje parametry *status* , *Precision* a *Scale* .|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje *stavovou* proměnnou.|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Představuje vazbu na konkrétní sloupec v databázi. Podporuje parametr *typu* .|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje parametry *typu* a *velikosti* .|
|[COLUMN_NAME](#column_name)|Představuje vazbu na konkrétní sloupec v databázi podle názvu.|
|[COLUMN_NAME_EX](#column_name_ex)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datového typu, velikosti, přesnosti, měřítka, délky sloupců a stavu sloupce.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci délky sloupce.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci délky a stavu sloupce.|
|[COLUMN_NAME_PS](#column_name_ps)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci přesnosti a škálování.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci přesnosti, škálování a délky sloupců.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci přesnosti, škálování, délky sloupců a stavu sloupce.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci stavu přesnosti, škálování a sloupce.|
|[COLUMN_NAME_STATUS](#column_name_status)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci stavu sloupce.|
|[COLUMN_NAME_TYPE](#column_name_type)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datového typu.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datového typu, přesnosti a škálování.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datového typu a velikosti.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Představuje vazbu na konkrétní sloupec v databázi podle názvu. Podporuje specifikace datového typu a stavu sloupce.|
|[END_COLUMN_MAP](#end_column_map)|Označí konec položek mapování sloupce.|

## <a name="command-macros"></a>Makra příkazů

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|Určuje příkaz, který se použije k vytvoření sady řádků při použití třídy [CCommand](../../data/oledb/ccommand-class.md) . Přijímá jenom typy řetězců, které odpovídají zadanému typu aplikace (ANSI nebo Unicode). Místo DEFINE_COMMAND doporučujeme použít [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) .|
|[DEFINE_COMMAND_EX](#define_command_ex)|Určuje příkaz, který se použije k vytvoření sady řádků při použití třídy [CCommand](../../data/oledb/ccommand-class.md) . Podporuje aplikace ANSI a Unicode.|

## <a name="parameter-map-macros"></a>Makra mapování parametrů

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Označuje začátek položek mapování parametrů v třídě záznamu uživatele.|
|[END_PARAM_MAP](#end_param_map)|Označuje konec položek mapování parametrů.|
|[SET_PARAM_TYPE](#set_param_type)|Určuje COLUMN_ENTRY makra, která následují SET_PARAM_TYPE makro jako vstup, výstup nebo vstup/výstup.|

### <a name="atltraceerrorrecords"></a>AtlTraceErrorRecords

Pokud se vrátí chyba, vypíše OLE DB informace o záznamu chyby do zařízení s výpisem paměti.

#### <a name="syntax"></a>Syntaxe

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Parametry

*hErr*<br/>
pro Hodnota HRESULT vrácená OLE DB členskou funkcí šablony spotřebitele.

#### <a name="remarks"></a>Poznámky

Pokud *hErr* není S_OK, `AtlTraceErrorRecords` vypíše OLE DB informace o záznamu chyby do zařízení s výpisem paměti (karta **ladění** v okně výstup nebo soubor). Informace o záznamu chyb, které se získávají od poskytovatele, obsahují číslo řádku, zdroj, popis, soubor s informacemi, kontext a identifikátor GUID pro každou položku záznamu chyby. `AtlTraceErrorRecords` vypíše tyto informace pouze v sestavení ladění. V sestavení vydaných verzí je to prázdný zástupný kód, který je optimalizován. Další informace naleznete v tématu [Třída CDBErrorInfo](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a>BEGIN_ACCESSOR

Označuje začátek vstupu přistupujícího objektu.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Parametry

*počet*<br/>
pro Číslo nulového posunu pro přistupující objekt v této mapě přístupového objektu.

*bAuto*<br/>
pro Určuje, zda se jedná o objekt pro přístup k automatickému přístupu nebo k ručnímu přístupu. Pokud je nastaveno na **true**, přistupující objekt je auto; Pokud je **hodnota false**, přistupující objekt je ruční. Objekt pro automatické přihlašování znamená, že se data načítají při operacích přesunu.

#### <a name="remarks"></a>Poznámky

V případě více přístupových objektů pro sadu řádků je nutné zadat BEGIN_ACCESSOR_MAP a použít makro BEGIN_ACCESSOR pro každý přistupující objekt. Makro BEGIN_ACCESSOR je dokončeno pomocí makra END_ACCESSOR. Makro BEGIN_ACCESSOR_MAP je dokončeno pomocí makra END_ACCESSOR_MAP.

#### <a name="example"></a>Příklad

Viz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_accessor_map"></a>BEGIN_ACCESSOR_MAP

Označuje začátek položek mapy přistupujícího objektu.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název třídy záznamu uživatele.

*počet*<br/>
pro Počet přístupových objektů v mapě tohoto přístupového objektu.

#### <a name="remarks"></a>Poznámky

V případě více přístupových objektů pro sadu řádků je nutné zadat BEGIN_ACCESSOR_MAP na začátku a použít makro BEGIN_ACCESSOR pro jednotlivé přistupující objekty. Makro BEGIN_ACCESSOR je dokončeno pomocí makra END_ACCESSOR. Mapa přístupového objektu je dokončena pomocí makra END_ACCESSOR_MAP.

Pokud máte v záznamu uživatele pouze jeden přistupující objekt, použijte [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)makra.

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

### <a name="end_accessor"></a>END_ACCESSOR

Označuje konec položky přístupového objektu.

#### <a name="syntax"></a>Syntaxe

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Poznámky

Pro více přístupových objektů pro sadu řádků je nutné zadat BEGIN_ACCESSOR_MAP a použít makro BEGIN_ACCESSOR pro každý přistupující objekt. Makro BEGIN_ACCESSOR je dokončeno pomocí makra END_ACCESSOR. Makro BEGIN_ACCESSOR_MAP je dokončeno pomocí makra END_ACCESSOR_MAP.

#### <a name="example"></a>Příklad

Viz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="end_accessor_map"></a>END_ACCESSOR_MAP

Označuje konec položek mapy přistupujícího objektu.

#### <a name="syntax"></a>Syntaxe

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Poznámky

Pro více přístupových objektů pro sadu řádků je nutné zadat BEGIN_ACCESSOR_MAP a použít makro BEGIN_ACCESSOR pro každý přistupující objekt. Makro BEGIN_ACCESSOR je dokončeno pomocí makra END_ACCESSOR. Makro BEGIN_ACCESSOR_MAP je dokončeno pomocí makra END_ACCESSOR_MAP.

#### <a name="example"></a>Příklad

Viz [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_column_map"></a>BEGIN_COLUMN_MAP

Označí začátek položky mapování sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název třídy záznamu uživatele odvozený od `CAccessor`.

#### <a name="remarks"></a>Poznámky

Toto makro se používá v případě jednoho přístupového objektu sady řádků. Pokud máte více přístupových objektů pro sadu řádků, použijte [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

Makro BEGIN_COLUMN_MAP je dokončeno pomocí makra END_COLUMN_MAP. Toto makro se používá v případě, že v záznamu uživatele je vyžadován pouze jeden přistupující objekt.

Sloupce odpovídají polím v sadě řádků, kterou chcete vytvořit.

#### <a name="example"></a>Příklad

Tady je ukázkový sloupec a mapa parametrů:

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a>BLOB_ENTRY

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vytvoření vazby binárního rozsáhlého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))).

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
pro Číslo sloupce

*IDENTIFIKÁTOR*<br/>
pro Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, použitý k načtení objektu BLOB.

*Flag*<br/>
pro Příznaky v režimu úložiště definované modelem strukturovaného úložiště OLE (například `STGM_READ`).

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="example"></a>Příklad

Přečtěte si, [Jak můžu načíst objekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a>BLOB_ENTRY_LENGTH

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vytvoření vazby binárního rozsáhlého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako u [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro také získá délku v bajtech sloupce objektu BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
pro Číslo sloupce

*IDENTIFIKÁTOR*<br/>
pro Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, použitý k načtení objektu BLOB.

*Flag*<br/>
pro Příznaky v režimu úložiště definované modelem strukturovaného úložiště OLE (například `STGM_READ`).

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
[out] \(Skutečné) délka v bajtech sloupci objektů BLOB.

#### <a name="example"></a>Příklad

Přečtěte si, [Jak můžu načíst objekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a>BLOB_ENTRY_LENGTH_STATUS

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vytvoření vazby binárního rozsáhlého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako u [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro také získá délku a stav sloupce objektu BLOB.

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
pro Číslo sloupce

*IDENTIFIKÁTOR*<br/>
pro Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, použitý k načtení objektu BLOB.

*Flag*<br/>
pro Příznaky v režimu úložiště definované modelem strukturovaného úložiště OLE (například `STGM_READ`).

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
[out] \(Skutečné) délka v bajtech sloupci objektů BLOB.

*stav*<br/>
mimo Stav sloupce dat objektu BLOB.

#### <a name="example"></a>Příklad

Přečtěte si, [Jak můžu načíst objekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a>BLOB_ENTRY_STATUS

Používá se s BEGIN_COLUMN_MAP nebo BEGIN_ACCESSOR_MAP k vytvoření vazby binárního rozsáhlého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako u [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro také získá stav sloupce objektu BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
pro Číslo sloupce

*IDENTIFIKÁTOR*<br/>
pro Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, použitý k načtení objektu BLOB.

*Flag*<br/>
pro Příznaky v režimu úložiště definované modelem strukturovaného úložiště OLE (například `STGM_READ`).

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*stav*<br/>
mimo Stav pole objektu BLOB.

#### <a name="example"></a>Příklad

Přečtěte si, [Jak můžu načíst objekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a>BLOB_NAME

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vytvoření vazby binárního rozsáhlého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako u [BLOB_ENTRY](../../data/oledb/blob-entry.md), s tím rozdílem, že toto makro místo čísla sloupce vybere název sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*IDENTIFIKÁTOR*<br/>
pro Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, použitý k načtení objektu BLOB.

*Flag*<br/>
pro Příznaky v režimu úložiště definované modelem strukturovaného úložiště OLE (například `STGM_READ`).

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="example"></a>Příklad

Přečtěte si, [Jak můžu načíst objekt BLOB?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a>BLOB_NAME_LENGTH

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vytvoření vazby binárního rozsáhlého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako u [BLOB_NAME](../../data/oledb/blob-name.md), s tím rozdílem, že toto makro také získá délku v bajtech sloupce dat objektu BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*IDENTIFIKÁTOR*<br/>
pro Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, použitý k načtení objektu BLOB.

*Flag*<br/>
pro Příznaky v režimu úložiště definované modelem strukturovaného úložiště OLE (například `STGM_READ`).

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
[out] \(Skutečné) délka v bajtech sloupci objektů BLOB.

### <a name="blob_name_length_status"></a>BLOB_NAME_LENGTH_STATUS

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vytvoření vazby binárního rozsáhlého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako u [BLOB_NAME](../../data/oledb/blob-name.md), s tím rozdílem, že toto makro také získá délku a stav sloupce dat objektu BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*IDENTIFIKÁTOR*<br/>
pro Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, použitý k načtení objektu BLOB.

*Flag*<br/>
pro Příznaky v režimu úložiště definované modelem strukturovaného úložiště OLE (například `STGM_READ`).

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
[out] \(Skutečné) délka v bajtech sloupci objektů BLOB.

*stav*<br/>
mimo Stav pole objektu BLOB.

### <a name="blob_name_status"></a>BLOB_NAME_STATUS

Používá se s BEGIN_COLUMN_MAP a END_COLUMN_MAP k vytvoření vazby binárního rozsáhlého objektu ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))). Podobně jako u [BLOB_NAME](../../data/oledb/blob-name.md), s tím rozdílem, že toto makro také získá stav sloupce dat objektu BLOB.

#### <a name="syntax"></a>Syntaxe

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*IDENTIFIKÁTOR*<br/>
pro Identifikátor GUID rozhraní, například `IDD_ISequentialStream`, použitý k načtení objektu BLOB.

*Flag*<br/>
pro Příznaky v režimu úložiště definované modelem strukturovaného úložiště OLE (například `STGM_READ`).

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*stav*<br/>
mimo Stav pole objektu BLOB.

### <a name="bookmark_entry"></a>BOOKMARK_ENTRY

Váže sloupec Bookmark.

#### <a name="syntax"></a>Syntaxe

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Parametry

*variabilní*<br/>
pro Proměnná, která má být svázána se sloupcem záložky.

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

Další informace najdete v tématu [použití záložek](using-bookmarks.md) a [třídy CBookmark](../../data/oledb/cbookmark-class.md).

### <a name="column_entry"></a>COLUMN_ENTRY

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo sloupce

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Makro COLUMN_ENTRY se používá v následujících umístěních:

- Mezi makry [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Mezi makry [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Mezi makry [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

#### <a name="example"></a>Příklad

Podívejte se na příklady v tématech makra [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="column_entry_ex"></a>COLUMN_ENTRY_EX

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo sloupce

*wType*<br/>
pro Datový typ.

*nLength*<br/>
pro Velikost dat v bajtech

*nPrecision*<br/>
pro Maximální přesnost, která se má použít při získávání dat a *wType* , je `DBTYPE_NUMERIC`. V opačném případě se tento parametr ignoruje.

*nScale*<br/>
pro Měřítko, které se má použít při získávání dat a *wType* , `DBTYPE_NUMERIC` nebo `DBTYPE_DECIMAL`.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
pro Proměnná, která se má svázat s délkou sloupce

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Makro COLUMN_ENTRY_EX se používá v následujících umístěních:

- Mezi makry [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Mezi makry [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Mezi makry [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

#### <a name="example"></a>Příklad

Viz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="column_entry_length"></a>COLUMN_ENTRY_LENGTH

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo sloupce od 1. Záložka odpovídá nule sloupce.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
pro Proměnná, která se má svázat s délkou sloupce

#### <a name="remarks"></a>Poznámky

Toto makro podporuje proměnnou *Length* . Používá se v následujících umístěních:

- Mezi makry [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Mezi makry [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Mezi makry [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_length_status"></a>COLUMN_ENTRY_LENGTH_STATUS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo sloupce

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
pro Proměnná, která se má svázat s délkou sloupce

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Toto makro použijte, když chcete podporovat proměnné Length a status. Používá se v následujících umístěních:

- Mezi makry [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Mezi makry [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Mezi makry [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_ps"></a>COLUMN_ENTRY_PS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo sloupce

*nPrecision*<br/>
pro Maximální přesnost sloupce, který chcete vytvořit.

*nScale*<br/>
pro Měřítko sloupce, který chcete vytvořit.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Umožňuje zadat přesnost a měřítko sloupce, který chcete vytvořit. Používá se v následujících umístěních:

- Mezi makry [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Mezi makry [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Mezi makry [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_ps_length"></a>COLUMN_ENTRY_PS_LENGTH

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo sloupce od 1. Záložka odpovídá nule sloupce.

*nPrecision*<br/>
pro Maximální přesnost sloupce, který chcete vytvořit.

*nScale*<br/>
pro Měřítko sloupce, který chcete vytvořit.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
pro Proměnná, která se má svázat s délkou sloupce

#### <a name="remarks"></a>Poznámky

Umožňuje zadat přesnost a měřítko sloupce, který chcete vytvořit. Toto makro podporuje proměnnou *Length* . Používá se v následujících umístěních:

- Mezi makry [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Mezi makry [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Mezi makry [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_ps_length_status"></a>COLUMN_ENTRY_PS_LENGTH_STATUS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo sloupce

*nPrecision*<br/>
pro Maximální přesnost sloupce, který chcete vytvořit.

*nScale*<br/>
pro Měřítko sloupce, který chcete vytvořit.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
pro Proměnná, která se má svázat s délkou sloupce

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Umožňuje zadat přesnost a měřítko sloupce, který chcete vytvořit. Toto makro použijte, když chcete podporovat proměnné Length a status. Používá se v následujících umístěních:

- Mezi makry [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Mezi makry [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Mezi makry [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_ps_status"></a>COLUMN_ENTRY_PS_STATUS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo sloupce

*nPrecision*<br/>
pro Maximální přesnost sloupce, který chcete vytvořit.

*nScale*<br/>
pro Měřítko sloupce, který chcete vytvořit.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Umožňuje zadat přesnost a měřítko sloupce, který chcete vytvořit. Toto makro podporuje proměnnou *stavu* . Používá se v následujících umístěních:

- Mezi makry [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Mezi makry [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Mezi makry [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_status"></a>COLUMN_ENTRY_STATUS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v databázi.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Parametry

Viz [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *referenci programátora OLE DB*.

*nOrdinal*<br/>
pro Číslo sloupce

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Toto makro podporuje proměnnou *stavu* . Používá se v následujících umístěních:

- Mezi makry [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Mezi makry [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Mezi makry [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_entry_type"></a>COLUMN_ENTRY_TYPE

Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje parametr *typu* .

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
pro Číslo sloupce

*wType*<br/>
pro Datový typ položky sloupce

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Toto makro je specializovaná varianta [COLUMN_ENTRY](../../data/oledb/column-entry.md) makra, která poskytuje prostředky pro určení datového typu.

### <a name="column_entry_type_size"></a>COLUMN_ENTRY_TYPE_SIZE

Představuje vazbu ke konkrétnímu sloupci v databázi. Podporuje parametry *typu* a *velikosti* .

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*nOrdinal*<br/>
pro Číslo sloupce

*wType*<br/>
pro Datový typ položky sloupce

*nLength*<br/>
pro Velikost položky sloupce v bajtech

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Toto makro je specializovaná varianta [COLUMN_ENTRY](../../data/oledb/column-entry.md) makra, která poskytuje způsob určení velikosti a typu dat.

### <a name="column_name"></a>COLUMN_NAME

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [COLUMN_ENTRY](../../data/oledb/column-entry.md), s tím rozdílem, že toto makro místo čísla sloupce převezme název sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Makra COLUMN_NAME_ * se používají na stejných místech jako [COLUMN_ENTRY](../../data/oledb/column-entry.md):

- Mezi makry [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) a [END_COLUMN_MAP](../../data/oledb/end-column-map.md) .

- Mezi makry [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) a [END_ACCESSOR](../../data/oledb/end-accessor.md) .

- Mezi makry [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) a [END_PARAM_MAP](../../data/oledb/end-param-map.md) .

### <a name="column_name_ex"></a>COLUMN_NAME_EX

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá datový typ, velikost, přesnost, měřítko, délku sloupce a stav sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*wType*<br/>
pro Datový typ.

*nLength*<br/>
pro Velikost dat v bajtech

*nPrecision*<br/>
pro Maximální přesnost, která se má použít při získávání dat a *wType* , je `DBTYPE_NUMERIC`. V opačném případě se tento parametr ignoruje.

*nScale*<br/>
pro Měřítko, které se má použít při získávání dat a *wType* , `DBTYPE_NUMERIC` nebo `DBTYPE_DECIMAL`.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
pro Proměnná, která se má svázat s délkou sloupce

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_length"></a>COLUMN_NAME_LENGTH

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s výjimkou toho, že toto makro také používá délku sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
pro Proměnná, která se má svázat s délkou sloupce

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_length_status"></a>COLUMN_NAME_LENGTH_STATUS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s výjimkou toho, že toto makro zároveň používá délku sloupce a stav sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
pro Proměnná, která se má svázat s délkou sloupce

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_ps"></a>COLUMN_NAME_PS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s tím rozdílem, že toto makro má také přesnost a škálování.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*nPrecision*<br/>
pro Maximální přesnost sloupce, který chcete vytvořit.

*nScale*<br/>
pro Měřítko sloupce, který chcete vytvořit.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_ps_length"></a>COLUMN_NAME_PS_LENGTH

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také používá přesnost, měřítko a délku sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*nPrecision*<br/>
pro Maximální přesnost sloupce, který chcete vytvořit.

*nScale*<br/>
pro Měřítko sloupce, který chcete vytvořit.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
pro Proměnná, která se má svázat s délkou sloupce

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_ps_length_status"></a>COLUMN_NAME_PS_LENGTH_STATUS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s tím rozdílem, že toto makro má také přesnost, měřítko, délku sloupce a stav sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*nPrecision*<br/>
pro Maximální přesnost sloupce, který chcete vytvořit.

*nScale*<br/>
pro Měřítko sloupce, který chcete vytvořit.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*časový*<br/>
pro Proměnná, která se má svázat s délkou sloupce

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_ps_status"></a>COLUMN_NAME_PS_STATUS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s tím rozdílem, že toto makro má také stav s přesností, škálováním a sloupci.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*nPrecision*<br/>
pro Maximální přesnost sloupce, který chcete vytvořit.

*nScale*<br/>
pro Měřítko sloupce, který chcete vytvořit.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_status"></a>COLUMN_NAME_STATUS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá stav sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_type"></a>COLUMN_NAME_TYPE

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá datový typ.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*wType*<br/>
pro Datový typ.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_type_ps"></a>COLUMN_NAME_TYPE_PS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá datový typ, přesnost a škálování.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*wType*<br/>
pro Datový typ.

*nPrecision*<br/>
pro Maximální přesnost, která se má použít při získávání dat a *wType* , je `DBTYPE_NUMERIC`. V opačném případě se tento parametr ignoruje.

*nScale*<br/>
pro Měřítko, které se má použít při získávání dat a *wType* , `DBTYPE_NUMERIC` nebo `DBTYPE_DECIMAL`.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_type_size"></a>COLUMN_NAME_TYPE_SIZE

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá data typu a velikost.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*wType*<br/>
pro Datový typ.

*nLength*<br/>
pro Velikost dat v bajtech

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="column_name_type_status"></a>COLUMN_NAME_TYPE_STATUS

Představuje vazbu na sadu řádků ke konkrétnímu sloupci v sadě řádků. Podobně jako u [column_name](../../data/oledb/column-name.md), s tím rozdílem, že toto makro také přebírá datový typ a stav sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Parametry

*pszName*<br/>
pro Ukazatel na název sloupce. Název musí být řetězec Unicode. To můžete provést tak, že před název vložíte "L", například: `L"MyColumn"`.

*wType*<br/>
pro Datový typ.

*stav*<br/>
pro Proměnná, která má být vázána na stav sloupce.

*údajů*<br/>
pro Odpovídající datový člen v záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Informace o tom, kde se používají makra COLUMN_NAME_ *, najdete v tématu [column_name](../../data/oledb/column-name.md) .

### <a name="end_column_map"></a>END_COLUMN_MAP

Označí konec položek mapování sloupce.

#### <a name="syntax"></a>Syntaxe

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Poznámky

Používá se s jediným přístupovým objektem pro sadu řádků. Makro BEGIN_COLUMN_MAP je dokončeno pomocí makra END_COLUMN_MAP.

#### <a name="example"></a>Příklad

Viz [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

### <a name="define_command"></a>DEFINE_COMMAND

Určuje příkaz, který se použije k vytvoření sady řádků při použití třídy [CCommand](../../data/oledb/ccommand-class.md) . Přijímá jenom typy řetězců, které odpovídají zadanému typu aplikace (ANSI nebo Unicode).

> [!NOTE]
>  Místo DEFINE_COMMAND doporučujeme použít [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) .

#### <a name="syntax"></a>Syntaxe

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název třídy záznamu uživatele (Command).

*szCommand*<br/>
pro Řetězec příkazu, který se použije k vytvoření sady řádků při použití [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Poznámky

Řetězec příkazu, který zadáte, bude použit jako výchozí, pokud neurčíte text příkazu v metodě [CCommand:: Open](../../data/oledb/ccommand-open.md) .

Toto makro přijímá řetězce ANSI, pokud sestavíte aplikaci jako ANSI nebo řetězce Unicode, pokud sestavíte aplikaci jako Unicode. Doporučuje se použít [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) místo DEFINE_COMMAND, protože bývalé řetězce podporující kódování Unicode bez ohledu na typ aplikace ANSI nebo Unicode.

#### <a name="example"></a>Příklad

Viz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="define_command_ex"></a>DEFINE_COMMAND_EX

Určuje příkaz, který se použije k vytvoření sady řádků při použití třídy [CCommand](../../data/oledb/ccommand-class.md) . Podporuje aplikace Unicode a ANSI.

#### <a name="syntax"></a>Syntaxe

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název třídy záznamu uživatele (Command).

*wszCommand*<br/>
pro Řetězec příkazu, který se použije k vytvoření sady řádků při použití [CCommand](../../data/oledb/ccommand-class.md).

#### <a name="remarks"></a>Poznámky

Řetězec příkazu, který zadáte, bude použit jako výchozí, pokud neurčíte text příkazu v metodě [CCommand:: Open](../../data/oledb/ccommand-open.md) .

Toto makro přijímá řetězce v kódování Unicode bez ohledu na typ aplikace. Toto makro je preferováno přes [DEFINE_COMMAND](../../data/oledb/define-command.md) , protože podporuje kódování Unicode a také aplikace ANSI.

#### <a name="example"></a>Příklad

Viz [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="begin_param_map"></a>BEGIN_PARAM_MAP

Označuje začátek položek mapování parametrů.

#### <a name="syntax"></a>Syntaxe

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Parametry

*znak*<br/>
pro Název třídy záznamu uživatele.

#### <a name="remarks"></a>Poznámky

Parametry jsou používány [příkazy](/previous-versions/windows/desktop/ms724608(v=vs.85)).

#### <a name="example"></a>Příklad

Podívejte se na příklad makra [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) .

### <a name="end_param_map"></a>END_PARAM_MAP

Označuje konec položek mapování parametrů.

#### <a name="syntax"></a>Syntaxe

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Příklad

Podívejte se na příklad makra [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) .

### <a name="set_param_type"></a>SET_PARAM_TYPE

Určuje COLUMN_ENTRY makra, která následují SET_PARAM_TYPE vstupu, výstupu nebo vstupu a výstupu makra.

#### <a name="syntax"></a>Syntaxe

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Parametry

*type*<br/>
pro Typ, který se má nastavit pro parametr

#### <a name="remarks"></a>Poznámky

Zprostředkovatelé podporují pouze vstupní a výstupní typy parametrů, které jsou podporovány podkladovým zdrojem dat. Typ je kombinací jedné nebo více `DBPARAMIO` hodnot (viz [struktury DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) v *Referenční příručce OLE DB programátora*):

- `DBPARAMIO_NOTPARAM` přistupující objekt nemá žádné parametry. Obvykle nastavíte `eParamIO` na tuto hodnotu v přístupových modulech řádků, abyste uživateli připomenout, že parametry jsou ignorovány.

- `DBPARAMIO_INPUT` vstupní parametr.

- `DBPARAMIO_OUTPUT` výstupní parametr.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` parametr je vstupní i výstupní parametr.

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

**Záhlaví:** atldbcli. h

## <a name="see-also"></a>Viz také

[Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[Šablony OLE DB příjemců](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenční dokumentace k šablonám příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
