---
title: CArchive – třída
ms.date: 11/04/2016
f1_keywords:
- CArchive
- AFX/CArchive
- AFX/CArchive::CArchive
- AFX/CArchive::Abort
- AFX/CArchive::Close
- AFX/CArchive::Flush
- AFX/CArchive::GetFile
- AFX/CArchive::GetObjectSchema
- AFX/CArchive::IsBufferEmpty
- AFX/CArchive::IsLoading
- AFX/CArchive::IsStoring
- AFX/CArchive::MapObject
- AFX/CArchive::Read
- AFX/CArchive::ReadClass
- AFX/CArchive::ReadObject
- AFX/CArchive::ReadString
- AFX/CArchive::SerializeClass
- AFX/CArchive::SetLoadParams
- AFX/CArchive::SetObjectSchema
- AFX/CArchive::SetStoreParams
- AFX/CArchive::Write
- AFX/CArchive::WriteClass
- AFX/CArchive::WriteObject
- AFX/CArchive::WriteString
- AFX/CArchive::m_pDocument
helpviewer_keywords:
- CArchive [MFC], CArchive
- CArchive [MFC], Abort
- CArchive [MFC], Close
- CArchive [MFC], Flush
- CArchive [MFC], GetFile
- CArchive [MFC], GetObjectSchema
- CArchive [MFC], IsBufferEmpty
- CArchive [MFC], IsLoading
- CArchive [MFC], IsStoring
- CArchive [MFC], MapObject
- CArchive [MFC], Read
- CArchive [MFC], ReadClass
- CArchive [MFC], ReadObject
- CArchive [MFC], ReadString
- CArchive [MFC], SerializeClass
- CArchive [MFC], SetLoadParams
- CArchive [MFC], SetObjectSchema
- CArchive [MFC], SetStoreParams
- CArchive [MFC], Write
- CArchive [MFC], WriteClass
- CArchive [MFC], WriteObject
- CArchive [MFC], WriteString
- CArchive [MFC], m_pDocument
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
ms.openlocfilehash: 8f169964c6a313f37b5ea50a5105af29af7b59b1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266325"
---
# <a name="carchive-class"></a>CArchive – třída

Umožňuje uložit složitou síť objektů v trvalém binárním formátu (obvykle úložiště na disku), který bude zachován po odstranění těchto objektů.

## <a name="syntax"></a>Syntaxe

```
class CArchive
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CArchive::CArchive](#carchive)|Vytvoří `CArchive` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CArchive::Abort](#abort)|Archiv se zavře bez vyvolání výjimky.|
|[CArchive::Close](#close)|Vyprázdní nepsaná dat a odpojí od `CFile`.|
|[CArchive::Flush](#flush)|Vyprázdní nepsaná dat z vyrovnávací paměti archivu.|
|[CArchive::GetFile](#getfile)|Získá `CFile` ukazatel objektu u tohoto archivu.|
|[CArchive::GetObjectSchema](#getobjectschema)|Volá se z `Serialize` funkce k určení verze objektu, který je deserializován.|
|[CArchive::IsBufferEmpty](#isbufferempty)|Určuje, zda vyrovnávací paměť vyprázdnění během Windows Sockets přijímat procesu.|
|[CArchive::IsLoading](#isloading)|Určuje, zda se načítá archivu.|
|[CArchive::IsStoring](#isstoring)|Určuje, zda je ukládání archivu.|
|[CArchive::MapObject](#mapobject)|Umístí objektů v objektu map, který není serializován do souboru, ale které jsou k dispozici pro podobjekty tak, aby odkazovaly.|
|[CArchive::Read](#read)|Přečte nezpracovaná bajtů.|
|[CArchive::ReadClass](#readclass)|Čtení odkaz na třídu s dříve uložili `WriteClass`.|
|[CArchive::ReadObject](#readobject)|Volání objektu `Serialize` funkce pro načtení.|
|[CArchive::ReadString](#readstring)|Načte jeden řádek textu.|
|[CArchive::SerializeClass](#serializeclass)|Čtení nebo zápis odkazu na třídu `CArchive` objekt v závislosti na směru `CArchive`.|
|[CArchive::SetLoadParams](#setloadparams)|Nastaví velikost, ke kterému poli zatížení roste. Musí být volána před načtením libovolného objektu, nebo před `MapObject` nebo `ReadObject` je volána.|
|[CArchive::SetObjectSchema](#setobjectschema)|Nastaví objekt schématu uloženou v objektu archivu.|
|[CArchive::SetStoreParams](#setstoreparams)|Nastaví velikost tabulky hash a velikost bloku na mapě používá k identifikaci počet jedinečných objektů: během procesu serializace.|
|[CArchive::Write](#write)|Zapíše nezpracovaná bajtů.|
|[CArchive::WriteClass](#writeclass)|Zapíše odkaz na `CRuntimeClass` k `CArchive`.|
|[CArchive::WriteObject](#writeobject)|Volání objektu `Serialize` funkce pro ukládání.|
|[CArchive::WriteString](#writestring)|Zapíše jeden řádek textu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CArchive::operator &lt;&lt;](#operator_lt_lt)|Ukládá objekty a primitivní typy do archivu.|
|[CArchive::operator &gt;&gt;](#operator_gt_gt)|Načte objekty a primitivní typy z archivu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CArchive::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Poznámky

`CArchive` nemá základní třídu.

Objekty můžete později načíst z trvalého úložiště rekonstrukce v paměti. Tento proces vytváření trvalých dat se nazývá "serializace."

Si můžete představit archivu objektu jako druh binárního datového proudu. Archiv jako vstupní/výstupní datový proud, je přidružený k souboru a umožňuje ve vyrovnávací paměti zápis a čtení dat do a z úložiště. Vstupní/výstupní datový proud zpracovává sekvence znaků ASCII, ale archiv zpracovává data binární objekt ve formátu efektivní, nonredundant.

Je nutné vytvořit [cfile –](../../mfc/reference/cfile-class.md) objektu před vytvořením `CArchive` objektu. Kromě toho musíte zajistit, že stav načtení/uložení archivu je kompatibilní s režim otevření souboru. Platí omezení na jeden aktivní archiv na soubor.

Při sestavování `CArchive` objektu, abyste ho připojili k objektu třídy `CFile` (nebo z odvozené třídy), který představuje otevřený soubor. Můžete také určit, zda archivu se použije pro načítání nebo ukládání. A `CArchive` objekt může zpracovat pouze primitivní typy, ale také objekty [CObject](../../mfc/reference/cobject-class.md)-odvozené třídy pro serializaci. Serializovatelné třídy má obvykle `Serialize` členská funkce a obvykle používá [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) makra, jak je popsáno v části třídy `CObject`.

Přetížená extrakce ( **>>**) a vložení ( **<<**) operátory jsou vhodné archivu programovací rozhraní, které podporují i primitivní typy a `CObject` -odvozené třídy.

`CArchive` také pro podporu programování pomocí třídy soketů knihovny MFC Windows [csocket –](../../mfc/reference/csocket-class.md) a [csocketfile –](../../mfc/reference/csocketfile-class.md). [IsBufferEmpty](#isbufferempty) členská funkce podporuje určité použití.

Další informace o `CArchive`, najdete v článcích [serializace](../../mfc/serialization-in-mfc.md) a [rozhraní Windows Sockets: Použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CArchive`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="abort"></a>  CArchive::Abort

Voláním této funkce archivu okno zavřít bez vyvolání výjimky.

```
void Abort ();
```

### <a name="remarks"></a>Poznámky

`CArchive` – Destruktor se běžně volání `Close`, které se vyprázdní všechna data, která nebyla uložena do přidruženého `CFile` objektu. To může způsobit výjimky.

Při zachytávání těchto výjimek, je vhodné použít `Abort`tak, aby destructing `CArchive` objekt nezpůsobí další výjimky. Při zpracování výjimek, `CArchive::Abort` nebude vyvolání výjimky na chyby, protože se na rozdíl od [CArchive::Close](#close), `Abort` ignoruje chyby.

Pokud jste použili **nové** přidělení `CArchive` objektů na haldě, pak je nutné odstranit až po zavření souboru.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive::WriteClass](#writeclass).

##  <a name="carchive"></a>  CArchive::CArchive

Vytvoří `CArchive` objektu a určuje, zda bude možné použít pro načítání nebo ukládání objektů.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Ukazatel `CFile` objekt, který je ultimate zdroji nebo cíli trvalá data.

*nMode*<br/>
Příznak, který určuje, zda se objekty načtené z nebo uložit do archivu. *NMode* parametr musí mít jednu z následujících hodnot:

- `CArchive::load` Načte data z archivu. Vyžaduje pouze `CFile` oprávnění ke čtení.

- `CArchive::store` Ukládá data do archivu. Vyžaduje `CFile` oprávnění k zápisu.

- `CArchive::bNoFlushOnDelete` Brání automaticky volání archivu `Flush` když je volán destruktor archivu. Pokud nastavíte tento příznak, zodpovídáte za explicitně voláním `Close` předtím, než je volán destruktor. Pokud ho nevidíte, bude vaše data poškozena.

*nBufSize*<br/>
Celé číslo, které určuje velikost vnitřní vyrovnávací paměti souboru, v bajtech. Všimněte si, že je výchozí velikost vyrovnávací paměti 4 096 bajtů. Pokud pravidelně archivovat velkých objektů, pomůže zvýšit výkon, pokud používáte větší velikost vyrovnávací paměti, které je násobkem velikosti vyrovnávací paměti souboru.

*lpBuf*<br/>
Volitelné ukazatele do uživatelem zadané vyrovnávací paměti o velikosti *nBufSize*. Pokud tento parametr nezadáte, archivu přidělí vyrovnávací paměť z lokální haldy a uvolní jej při zničení objektu. Archiv neuvolní uživatelem zadané vyrovnávací paměti.

### <a name="remarks"></a>Poznámky

Tato specifikace nelze změnit po vytvoření archivu.

Nesmíte používat `CFile` operace mění stav souboru, dokud neukončíte archivu. Tato operace bude poškození integrity archivu. Pozice ukazatele souboru může přístup kdykoli během serializace získáním objektu soubor archivu z [GetFile](#getfile) členské funkce a následným použitím [CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition) – funkce . Měli byste zavolat [CArchive::Flush](#flush) před získávání polohy ukazatele souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>  CArchive::Close

Vyprázdní žádná data zbývajících ve vyrovnávací paměti, archivu se zavře a odpojení ze souboru archivu.

```
void Close();
```

### <a name="remarks"></a>Poznámky

Nejsou povoleny žádné další operace v archivu. Po zavření archiv, můžete vytvořit jiný archivu pro stejný soubor nebo můžete zavřít soubor.

Členská funkce `Close` zajistí, že všechna data se přenáší z archivu do souboru a jeho znepřístupní archivu. K dokončení přenosu ze souboru na paměťové médium, musíte nejprve použít [CFile::Close](../../mfc/reference/cfile-class.md#close) a pak zničilo `CFile` objektu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive::WriteString](#writestring).

##  <a name="flush"></a>  CArchive::Flush

Vynutí žádná data zbývajících ve vyrovnávací paměti archiv k zápisu do souboru.

```
void Flush();
```

### <a name="remarks"></a>Poznámky

Členská funkce `Flush` zajistí, že všechna data se přenáší z archivu do souboru. Je nutné volat [CFile::Close](../../mfc/reference/cfile-class.md#close) dokončit přenos ze souboru k paměťovému médiu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>  CArchive::GetFile

Získá `CFile` ukazatel objektu u tohoto archivu.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní ukazatel `CFile` objektu používá.

### <a name="remarks"></a>Poznámky

Archiv před použitím musí vyprázdnění `GetFile`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>  CArchive::GetObjectSchema

Voláním této funkce z `Serialize` funkce k určení verze objektu, který je aktuálně deserializován.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Návratová hodnota

Během deserializace, verze objektu, který je čten.

### <a name="remarks"></a>Poznámky

Volání této funkce je platná pouze při `CArchive` načítání objektu ( [CArchive::IsLoading](#isloading) vrátí nenulovou hodnotu). Měla by být v prvním volání `Serialize` funkce a volané jen jednou. Návratová hodnota (UINT) -1 označuje, že číslo verze neznámý.

A `CObject`-odvozené třídy mohou používat kombinaci VERSIONABLE_SCHEMA (bitovým operátorem pomocí **nebo**) s verzí schématu (v IMPLEMENT_SERIAL – makro) k vytvoření "verzování objektu," to znamená, že objekt jehož `Serialize` Členská funkce může číst více verzí. Výchozí funkce framework (bez VERSIONABLE_SCHEMA) je vyvolání výjimky, když se neshoduje verze.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

##  <a name="isbufferempty"></a>  CArchive::IsBufferEmpty

Voláním této členské funkce k určení, zda objekt archivu vnitřní vyrovnávací paměť je prázdná.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud vyrovnávací paměť archivu je prázdná. jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je zadaný pro podporu programování pomocí třídy soketů knihovny MFC Windows `CSocketFile`. Není potřeba ho použít pro archiv přidružené `CFile` objektu.

Důvod pro použití `IsBufferEmpty` s archiv přidružené `CSocketFile` objektu je, že archivu vyrovnávací paměti může obsahovat více než jeden záznam nebo zprávy. Po přijetí zpráv, byste měli použít `IsBufferEmpty` pro řízení smyčky, který se bude přijímat data, dokud vyrovnávací paměť je prázdná. Další informace najdete v tématu [Receive](../../mfc/reference/casyncsocket-class.md#receive) členské funkce třídy `CAsyncSocket`, který ukazuje způsob použití `IsBufferEmpty`.

Další informace najdete v tématu [rozhraní Windows Sockets: Použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isloading"></a>  CArchive::IsLoading

Určuje, zda archivu načítá data.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud archiv se aktuálně používá pro načítání; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `Serialize` funkce archivované tříd.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

##  <a name="isstoring"></a>  CArchive::IsStoring

Určuje, zda archivu je ukládat data.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud archiv se aktuálně používá pro ukládání; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `Serialize` funkce archivované tříd.

Pokud `IsStoring` stav archivu je nenulovou hodnotu, pak jeho `IsLoading` stav je 0 a naopak.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

##  <a name="mapobject"></a>  CArchive::MapObject

Voláním této členské funkce umisťuje objekty na mapě, které nejsou ve skutečnosti serializován do souboru, ale které jsou k dispozici pro podobjekty tak, aby odkazovaly.

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Konstantní ukazatel na objekt uložené.

### <a name="remarks"></a>Poznámky

Například nemusí serializovat dokumentu, ale by serializovat položky, které jsou součástí dokumentu. Voláním `MapObject`, umožňují tyto položky nebo podobjektů, tak, aby odkazovaly dokument. Navíc může serializovat serializovaná podpoložek jejich *m_pDocument* zpětný ukazatel.

Můžete volat `MapObject` při ukládání do a načtení z `CArchive` objektu. `MapObject` Přidá zadaný objekt do interních datových struktur udržuje `CArchive` objektu během serializace a deserializace, ale na rozdíl od [se operace ReadObject](#readobject) a [operace WriteObject](#writeobject), nevolá serializace objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>  CArchive::m_pDocument

Nastavit na hodnotu NULL ve výchozím nastavení tento ukazatel `CDocument` lze nastavit k ničemu uživatele `CArchive` instance potřebuje.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Poznámky

Běžné použití ukazatele this je k předání dalších informací o procesu serializace pro všechny objekty serializována. To se provádí inicializace ukazatele s dokumentem ( `CDocument`-odvozené třídy), který probíhá serializace, tak, že objekty v rámci dokumentu můžete přístup k dokumentu v případě potřeby. This – ukazatel také používá `COleClientItem` objekty během serializace.

Nastaví framework *m_pDocument* v dokumentu se serializovat, když uživatel vydá soubor otevřít nebo uložit příkazu. Pokud serializujete propojování a vkládání (OLE) kontejneru dokumentu jiných důvodů než otevřít nebo uložit, je nutné explicitně nastavit *m_pDocument*. Například je třeba provést při serializaci dokumentu kontejneru do schránky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>  CArchive::operator &lt;&lt;

Uloží zadaný objekt nebo primitivní typ archivu.

```
friend CArchive& operator<<(
    CArchive& ar,
    const CObject* pOb);

throw(
    CArchiveException*,
    CFileException*);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator<<(
    const ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator<<(BYTE by);
CArchive& operator<<(WORD w);
CArchive& operator<<(LONG l);
CArchive& operator<<(DWORD dw);
CArchive& operator<<(float f);
CArchive& operator<<(double d);
CArchive& operator<<(int i);
CArchive& operator<<(short w);
CArchive& operator<<(char ch);
CArchive& operator<<(wchar_t ch);
CArchive& operator<<(unsigned u);
CArchive& operator<<(bool b);
CArchive& operator<<(ULONGLONG dwdw);
CArchive& operator<<(LONGLONG dwdw);
```

### <a name="return-value"></a>Návratová hodnota

A `CArchive` odkaz, který umožňuje více operátorů insertion na jednom řádku.

### <a name="remarks"></a>Poznámky

Poslední dvě verze výše jsou speciálně pro ukládání 64bitová celá čísla.

Pokud jste použili IMPLEMENT_SERIAL – makro v implementaci třídy, je přetížený operátor vkládání pro `CObject` zavolá chráněné `WriteObject`. Tato funkce volá `Serialize` funkce třídy.

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md) operátor vkládání (<<) podporuje diagnostiku vypsání a ukládání do archivu.

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CArchive` operátor vkládání << s **int** a **dlouhé** typy.

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Příklad

V tomto příkladu 2 ukazuje použití `CArchive` operátor vkládání << s `CStringT` typu.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>  CArchive::operator &gt;&gt;

Načte zadaný objekt nebo primitivní typ z archivu.

```
friend CArchive& operator>>(
    CArchive& ar,
    CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

friend CArchive& operator>>(
    CArchive& ar,
    const CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator>>(
    ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator>>(BYTE& by);
CArchive& operator>>(WORD& w);
CArchive& operator>>(int& i);
CArchive& operator>>(LONG& l);
CArchive& operator>>(DWORD& dw);
CArchive& operator>>(float& f);
CArchive& operator>>(double& d);
CArchive& operator>>(short& w);
CArchive& operator>>(char& ch);
CArchive& operator>>(wchar_t& ch);
CArchive& operator>>(unsigned& u);
CArchive& operator>>(bool& b);
CArchive& operator>>(ULONGLONG& dwdw);
CArchive& operator>>(LONGLONG& dwdw);
```

### <a name="return-value"></a>Návratová hodnota

A `CArchive` odkaz, který umožňuje více operátorů extrakce na jednom řádku.

### <a name="remarks"></a>Poznámky

Poslední dvě verze výše jsou speciálně pro načítání 64bitová celá čísla.

Pokud jste použili IMPLEMENT_SERIAL – makro v implementaci třídy, pak přetížení operátorů extrakce pro `CObject` volat rozhraní `ReadObject` – funkce (s nenulovou run-time třída ukazatele). Tato funkce volá `Serialize` funkce třídy.

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md) extrakce – operátor (>>) podporuje načítání z archivu.

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CArchive` extrakce operátor >> s **int** typu.

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CArchive` vkládání a extrakci operátory <\< a >> s `CStringT` typu.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

##  <a name="read"></a>  CArchive::Read

Přečte zadaný počet bajtů z archivu.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel do vyrovnávací paměti, uživatelem zadané, která se zobrazí data načtená z archivu.

*nMax*<br/>
Celé číslo bez znaménka určující počet bajtů ke čtení z archivu.

### <a name="return-value"></a>Návratová hodnota

Celé číslo bez znaménka obsahující počet skutečně přečtených bajtů. Pokud vrácená hodnota je menší než požadovaný, bylo dosaženo konce souboru. Ve stavu ukončení souboru není vyvolána žádná výjimka.

### <a name="remarks"></a>Poznámky

Archiv neinterpretuje bajtů.

Můžete použít `Read` členské funkce v rámci vaší `Serialize` funkce pro běžný struktury, které jsou obsaženy v objekty pro čtení.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

##  <a name="readclass"></a>  CArchive::ReadClass

Voláním této členské funkce získat odkaz na třídu s dříve uložené [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parametry

*pClassRefRequested*<br/>
Ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura, která odpovídá odkazech na třídy rozhraní požadované. Může mít hodnotu NULL.

*pSchema*<br/>
Ukazatel na schéma run-time třída dříve uložena.

*pObTag*<br/>
Číslo, které odkazuje na jedinečné značka objektu. Interně jej využívá provádění [se operace ReadObject](#readobject). Vystavené pro rozšířené programování. *pObTag* obvykle by měl mít hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury.

### <a name="remarks"></a>Poznámky

Pokud *pClassRefRequested* nemá hodnotu NULL, `ReadClass` ověří, jestli je kompatibilní s vaší třídy modulu runtime třídy archivované informace. Pokud není kompatibilní, `ReadClass` vyvolá výjimku [carchiveexception –](../../mfc/reference/carchiveexception-class.md).

Musíte použít modul runtime třídu [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v opačném případě `ReadClass` vyvolá výjimku [cnotsupportedexception –](../../mfc/reference/cnotsupportedexception-class.md).

Pokud *pSchema* má hodnotu NULL, schématem uložené třídy může být načten voláním [CArchive::GetObjectSchema](#getobjectschema); v opačném případě <strong>\*</strong>  *pSchema* bude obsahovat schéma run-time třída, která byla dřív uložená.

Můžete použít [SerializeClass](#serializeclass) místo `ReadClass`, která zpracovává čtení i zápis odkazech na třídy rozhraní.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive::WriteClass](#writeclass).

##  <a name="readobject"></a>  CArchive::ReadObject

Přečte data objektu z archivu a vytvoří objekt příslušného typu.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Konstantní ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura, která odpovídá objektu očekáváte, že ke čtení.

### <a name="return-value"></a>Návratová hodnota

A [CObject](../../mfc/reference/cobject-class.md) ukazatel, který musí být bezpečné přetypovat na správné odvozené třídy pomocí [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána `CArchive` extrakce ( **>>**) operátor přetížen pro [CObject](../../mfc/reference/cobject-class.md) ukazatele. `ReadObject`, volá `Serialize` funkce archivované třídy.

Pokud zadáte nenulovou hodnotu *pClass* parametr, který byl získán [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) – makro, pak funkce ověří run-time třída archivovaného objektu. Předpokladem je, že jste použili IMPLEMENT_SERIAL – makro v implementaci třídy.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive::WriteObject](#writeobject).

##  <a name="readstring"></a>  CArchive::ReadString

Voláním této členské funkce ke čtení textových dat do vyrovnávací paměti ze souboru spojené s `CArchive` objektu.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) poté, co je pro čtení ze souboru přidružená k objektu CArchive, která bude obsahovat výsledný řetězec.

*lpsz*<br/>
Určuje ukazatel do vyrovnávací paměti, zadané uživatele, který bude příjemcem řetězec zakončený hodnotou null text.

*nMax*<br/>
Určuje maximální počet znaků pro čtení. By měl být menší než velikost *lpsz* vyrovnávací paměti.

### <a name="return-value"></a>Návratová hodnota

Ve verzi, která vrací hodnotu TRUE v případě úspěchu; BOOL FALSE v opačném případě.

Ve verzi, která se vrátí `LPTSTR`, ukazatel do vyrovnávací paměti obsahující textových dat; Hodnota NULL, pokud bylo dosaženo souboru.

### <a name="remarks"></a>Poznámky

Ve verzi členská funkce se *Nmaximum* parametr, vyrovnávací paměti, když bude vyřizovat k omezení *Nmaximum* – 1 znaků. Čtení zastavena pár návratový znak odřádkování návrat na začátek řádku. Koncové znaky nového řádku jsou vždy odebrat. V obou případech je připojen znak null ('\0').

[CArchive::Read](#read) je k dispozici také pro režim textové zadání, ale neukončí na pár návratový znak odřádkování návrat na začátek řádku.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive::WriteString](#writestring).

##  <a name="serializeclass"></a>  CArchive::SerializeClass

Voláním této členské funkce, pokud chcete uložit a načíst informace o verzi základní třídy.

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Ukazatel na objekt třídy za běhu pro základní třídu.

### <a name="remarks"></a>Poznámky

`SerializeClass` čtení nebo zápis odkaz na třídu `CArchive` objekt, v závislosti na směru `CArchive`. Použití `SerializeClass` místo [ReadClass](#readclass) a [WriteClass](#writeclass) jako pohodlný způsob, jak serializovat objekty základní třídy. `SerializeClass` vyžaduje méně kódu a méně parametrů.

Stejně jako `ReadClass`, `SerializeClass` ověří, jestli je kompatibilní s vaší třídy modulu runtime třídy archivované informace. Pokud není kompatibilní, `SerializeClass` vyvolá výjimku [carchiveexception –](../../mfc/reference/carchiveexception-class.md).

Musíte použít modul runtime třídu [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v opačném případě `SerializeClass` vyvolá výjimku [cnotsupportedexception –](../../mfc/reference/cnotsupportedexception-class.md).

Použití [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) – makro k načtení hodnoty pro *pRuntimeClass* parametru. Základní třída musí mít použita [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) – makro.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>  CArchive::SetLoadParams

Volání `SetLoadParams` kdy se chystá čtení velký počet `CObject`-odvozené objekty z archivu.

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parametry

*nGrowBy*<br/>
Minimální počet slotů element přidělit, pokud je nutné zvýšit velikost.

### <a name="remarks"></a>Poznámky

`CArchive` používá pole zatížení při řešení odkazů na objekty uložené v archivu. `SetLoadParams` Umožňuje nastavit velikost, ke kterému poli zatížení roste.

Nesmějí volat `SetLoadParams` po načtení všech objektů, nebo po [MapObject](#mapobject) nebo [se operace ReadObject](#readobject) je volána.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="setobjectschema"></a>  CArchive::SetObjectSchema

Voláním této členské funkce pro nastavení schématu objektu uložená v archivní objekt *nSchema*.

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parametry

*nSchema*<br/>
Určuje schéma objektu.

### <a name="remarks"></a>Poznámky

Další volání [GetObjectSchema](#getobjectschema) vrátí hodnotu uloženou v *nSchema*.

Použití `SetObjectSchema` pokročilé správy verzí, například pokud chcete vynutit konkrétní verzi pro čtení v `Serialize` funkce odvozené třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>  CArchive::SetStoreParams

Použití `SetStoreParams` při ukládání velkého počtu `CObject`-odvozené objekty v archivu.

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parametry

*nHashSize*<br/>
Mapuje velikost zatřiďovací tabulky pro ukazatel rozhraní. By měl být Prvočíslo.

*nBlockSize*<br/>
Určuje členitosti přidělení paměti pro rozšíření parametry. Musí být mocninou čísla 2 pro zajištění nejlepšího výkonu.

### <a name="remarks"></a>Poznámky

`SetStoreParams` Umožňuje nastavit velikost tabulky hash a velikost bloku na mapě používá k identifikaci počet jedinečných objektů: během procesu serializace.

Nesmějí volat `SetStoreParams` jsou uložené všechny objekty, nebo po [MapObject](#mapobject) nebo [operace WriteObject](#writeobject) je volána.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="write"></a>  CArchive::Write

Zapíše zadaný počet bajtů do archivu.

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel do vyrovnávací paměti zadaných uživatelem, který obsahuje data, která mají být zapsána do archivu.

*nMax*<br/>
Celé číslo určující počet bajtů, které mají být zapsána do archivu.

### <a name="remarks"></a>Poznámky

Archiv neformátuje bajtů.

Můžete použít `Write` členské funkce v rámci vaší `Serialize` funkce k zapsání běžných struktury, které jsou obsaženy v objekty.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>  CArchive::WriteClass

Použití `WriteClass` ukládat informace o verzi a třídy základní třídy během serializace odvozené třídy.

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura, která odpovídá odkazech na třídy rozhraní požadované.

### <a name="remarks"></a>Poznámky

`WriteClass` zapíše odkaz na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pro základní třídu `CArchive`. Použití [CArchive::ReadClass](#readclass) k načtení odkazu.

`WriteClass` ověří, zda informace o archivovaném třídě je kompatibilní s vaší třídy modulu runtime. Pokud není kompatibilní, `WriteClass` vyvolá výjimku [carchiveexception –](../../mfc/reference/carchiveexception-class.md).

Musíte použít modul runtime třídu [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v opačném případě `WriteClass` vyvolá výjimku [cnotsupportedexception –](../../mfc/reference/cnotsupportedexception-class.md).

Můžete použít [SerializeClass](#serializeclass) místo `WriteClass`, která zpracovává čtení i zápis odkazech na třídy rozhraní.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>  CArchive::WriteObject

Uloží zadaný `CObject` do archivu.

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Konstantní ukazatel na objekt uložené.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána `CArchive` vložení ( **<<**) operátor přetížen pro `CObject`. `WriteObject`, volá `Serialize` funkce archivované třídy.

IMPLEMENT_SERIAL – makro musíte použít k povolení archivace. `WriteObject` Název třídy ASCII zapíše do archivu. Třída s tímto názvem se ověří později během procesu načtení. Speciální schéma kódování zabráníte zdvojení název třídy pro více objektů třídy. Toto schéma také zabrání redundantnímu úložišti s objekty, které se cílí více než jeden ukazatel.

Přesné objekt encoding – metoda (včetně názvu třídy ASCII) je podrobnost implementace a může změnit v budoucích verzích knihovny.

> [!NOTE]
>  Dokončení vytváření, odstraňování a aktualizuje všechny objekty, než začnete jejich archivace. Archiv se poškozený, jsou-li zkombinovány archivaci pomocí úpravy objektu.

### <a name="example"></a>Příklad

Definice třídy `CAge`, podívejte se na příklad pro [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>  CArchive::WriteString

Tato členská funkce slouží k zápisu dat z vyrovnávací paměti souboru spojené s `CArchive` objektu.

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Určuje ukazatel do vyrovnávací paměti, který obsahuje řetězec zakončený hodnotou null text.

### <a name="remarks"></a>Poznámky

Ukončující znak null ('\0') není zapsána do souboru. ani je nový řádek automaticky zapisovat.

`WriteString` vyvolá výjimku v reakci na několika podmínek, včetně stavu zaplnění disku.

`Write` je také k dispozici, ale místo se ukončuje na znak null, zapíše požadovaný počet bajtů do souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[CSocket – třída](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
