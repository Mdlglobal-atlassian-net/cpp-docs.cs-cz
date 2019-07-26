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
ms.openlocfilehash: 3cf5c3b7a79e846928b5a7ee0af12a3324e141a3
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376357"
---
# <a name="carchive-class"></a>CArchive – třída

Umožňuje uložit složitou síť objektů do trvalého binárního formátu (obvykle úložiště na disku), která po odstranění těchto objektů přetrvává.

## <a name="syntax"></a>Syntaxe

```
class CArchive
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CArchive:: CArchive](#carchive)|`CArchive` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CArchive:: Abort](#abort)|Zavře archiv bez vyvolání výjimky.|
|[CArchive:: Close](#close)|Vyprázdní nezapsaná data a odpojí je `CFile`od.|
|[CArchive:: flush](#flush)|Vyprázdní nezapsaná data z archivní vyrovnávací paměti.|
|[CArchive:: GetFile](#getfile)|Získá ukazatel `CFile` objektu pro tento archiv.|
|[CArchive:: GetObjectSchema](#getobjectschema)|Volána z `Serialize` funkce k určení verze objektu, který je deserializován.|
|[CArchive::IsBufferEmpty](#isbufferempty)|Určuje, zda byla vyrovnávací paměť vyprázdněna během procesu přijímání rozhraní Windows Sockets.|
|[CArchive:: IsLoaded](#isloading)|Určuje, zda se archiv načítá.|
|[CArchive:: ukládá se](#isstoring)|Určuje, zda archiv ukládá.|
|[CArchive:: MapObject](#mapobject)|Umístí objekty do mapy, které nejsou serializovány do souboru, ale jsou k dispozici pro podobjekty, na které se má odkazovat.|
|[CArchive:: Read](#read)|Přečte nezpracované bajty.|
|[CArchive:: ReadClass](#readclass)|Přečte odkaz na třídu dříve uložený pomocí `WriteClass`.|
|[CArchive:: ReadObject](#readobject)|Volá `Serialize` funkci objektu pro načtení.|
|[CArchive:: ReadString](#readstring)|Přečte jeden řádek textu.|
|[CArchive:: SerializeClass](#serializeclass)|Přečte nebo zapíše odkaz na třídu `CArchive` do objektu v závislosti na směru. `CArchive`|
|[CArchive:: SetLoadParams](#setloadparams)|Nastaví velikost, na kterou se pole zatížení zvětšuje. Musí být volána před načtením objektu nebo před `MapObject` `ReadObject` jeho voláním.|
|[CArchive:: SetObjectSchema](#setobjectschema)|Nastaví schéma objektu uložené v archivním objektu.|
|[CArchive:: SetStoreParams](#setstoreparams)|Nastaví velikost zatřiďovací tabulky a velikost bloku mapy použitou k identifikaci jedinečných objektů během procesu serializace.|
|[CArchive:: Write](#write)|Zapisuje nezpracované bajty.|
|[CArchive:: WriteClass](#writeclass)|Zapíše odkaz `CRuntimeClass` `CArchive`na.|
|[CArchive:: WriteObject](#writeobject)|Zavolá `Serialize` funkci objektu pro uložení.|
|[CArchive:: WriteString](#writestring)|Zapíše jeden řádek textu.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CArchive:: operator&lt;&lt;](#operator_lt_lt)|Ukládá objekty a primitivní typy do archivu.|
|[CArchive:: operator&gt;&gt;](#operator_gt_gt)|Načte objekty a primitivní typy z archivu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CArchive::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Poznámky

`CArchive`nemá základní třídu.

Později můžete načíst objekty z trvalého úložiště, které je retvoří v paměti. Tento proces, který provádí data trvalě, se nazývá "serializace".

Archivní objekt si můžete představit jako typ binárního datového proudu. Podobně jako vstupní/výstupní datový proud je archiv přidružen k souboru a povoluje zápis do vyrovnávací paměti a čtení dat do a z úložiště. Vstupní a výstupní datový proud zpracovává sekvence znaků ASCII, ale archiv zpracovává binární data objektů v efektivním, neredundantním formátu.

Objekt [CFile –](../../mfc/reference/cfile-class.md) je nutné vytvořit předtím, než budete moci vytvořit `CArchive` objekt. Kromě toho je nutné zajistit, aby stav zatížení a uložení archivu byl kompatibilní s režimem otevírání souboru. Máte omezené na jednu aktivní archivaci na jeden soubor.

Při vytváření `CArchive` objektu ho připojíte k objektu třídy `CFile` (nebo odvozené třídě), která představuje otevřený soubor. Také určete, jestli se má archiv použít k načtení nebo uložení. Objekt může zpracovat nejen primitivní typy, ale také objekty tříd odvozených od CObject, které jsou navrženy pro serializaci. [](../../mfc/reference/cobject-class.md) `CArchive` Serializovatelný třída má `Serialize` obvykle členskou funkci a obvykle používá makra [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) , jak je popsáno v části Class `CObject`.

Přetížené operátory pro extrakci **>>** () a vložení **<<** () jsou praktické archivační rozhraní pro programování, které podporuje oba primitivní `CObject`typy i odvozené třídy.

`CArchive`podporuje také programování se třídami MFC Windows Sockets [CSocket –](../../mfc/reference/csocket-class.md) a [CSocketFile](../../mfc/reference/csocketfile-class.md). Členská funkce [IsBufferEmpty](#isbufferempty) podporuje toto využití.

Další informace o `CArchive`naleznete v článku serializace [](../../mfc/serialization-in-mfc.md) a [rozhraní Windows Sockets: Použití soketů s](../../mfc/windows-sockets-using-sockets-with-archives.md)archivy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CArchive`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="abort"></a>CArchive:: Abort

Voláním této funkce zavřete archiv bez vyvolání výjimky.

```
void Abort ();
```

### <a name="remarks"></a>Poznámky

Destruktor bude obvykle volat `Close`, čímž se zaprázdní všechna data, která nebyla uložena do přidruženého `CFile` objektu. `CArchive` To může způsobit výjimky.

Při zachycení těchto výjimek je vhodné použít `Abort`, aby destruktura `CArchive` objektu nezpůsobila další výjimky. Při zpracování výjimek `CArchive::Abort` nebude vyvolána výjimka při selhání, protože na rozdíl od [CArchive:: Close](#close), `Abort` ignoruje selhání.

Pokud jste použili **New** pro přidělení `CArchive` objektu na haldě, je nutné jej po zavření souboru odstranit.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive:: WriteClass](#writeclass).

##  <a name="carchive"></a>CArchive:: CArchive

`CArchive` Vytvoří objekt a určí, zda bude použit pro načítání nebo ukládání objektů.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Ukazatel na `CFile` objekt, který je konečným zdrojem nebo cílem trvalých dat.

*nMode*<br/>
Příznak, který určuje, zda budou objekty načteny nebo uloženy do archivu. Parametr *nMode* musí mít jednu z následujících hodnot:

- `CArchive::load`Načte data z archivu. Vyžaduje pouze `CFile` oprávnění ke čtení.

- `CArchive::store`Ukládá data do archivu. Vyžaduje `CFile` oprávnění k zápisu.

- `CArchive::bNoFlushOnDelete`Zabraňuje automatickému volání `Flush` archivu při volání destruktoru archivu. Pokud jste tento příznak nastavili, zodpovídáte za explicitní `Close` volání před voláním destruktoru. Pokud to neuděláte, vaše data budou poškozena.

*nBufSize*<br/>
Celé číslo, které určuje velikost vnitřní vyrovnávací paměti souborů (v bajtech). Všimněte si, že výchozí velikost vyrovnávací paměti je 4 096 bajtů. Pokud často archivujete velké objekty, zvýšíte výkon, pokud použijete větší vyrovnávací paměť, která je násobkem velikosti vyrovnávací paměti souborů.

*lpBuf*<br/>
Volitelný ukazatel na vyrovnávací paměť zadanou uživatelem velikosti *nBufSize*. Pokud tento parametr nezadáte, archiv přidělí vyrovnávací paměť z místní haldy a uvolní ji při zničení objektu. Archiv neuvolňuje vyrovnávací paměť poskytnutou uživatelem.

### <a name="remarks"></a>Poznámky

Po vytvoření archivu už tuto specifikaci nemůžete změnit.

Operace nemůžete `CFile` použít k změně stavu souboru, dokud jste archiv nezavřeli. Každá taková operace bude mít za škodu integritu archivu. K pozici ukazatele souboru můžete přistupovat kdykoli během serializace tím, že získáte objekt souboru archivu z členské funkce GetFile [](#getfile) a potom použijete funkci [CFile –:: GetPosition](../../mfc/reference/cfile-class.md#getposition) . Před získáním pozice ukazatele souboru byste měli zavolat metodu [CArchive:: flush](#flush) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>CArchive:: Close

Vyprázdní všechna zbývající data ve vyrovnávací paměti, zavře archiv a odpojí archiv ze souboru.

```
void Close();
```

### <a name="remarks"></a>Poznámky

V archivu nejsou povoleny žádné další operace. Po zavření archivu můžete vytvořit další archiv pro stejný soubor nebo můžete soubor zavřít.

Členská funkce `Close` zajistí, že všechna data budou přenesena z archivu do souboru a nebude tak k dispozici archiv. Chcete-li dokončit přenos ze souboru na médium úložiště, je nutné nejprve použít [CFile –:: Close](../../mfc/reference/cfile-class.md#close) a potom zničit `CFile` objekt.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive:: WriteString](#writestring).

##  <a name="flush"></a>CArchive:: flush

Vynutí zápis všech dat zbývajících ve vyrovnávací paměti archivu do souboru.

```
void Flush();
```

### <a name="remarks"></a>Poznámky

Členská funkce `Flush` zajišťuje, že všechna data budou přenesena z archivu do souboru. Chcete-li dokončit přenos ze souboru na médium úložiště, je nutné zavolat [CFile –:: Close](../../mfc/reference/cfile-class.md#close) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>CArchive:: GetFile

Získá ukazatel `CFile` objektu pro tento archiv.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní ukazatel na `CFile` objekt, který se používá.

### <a name="remarks"></a>Poznámky

Před použitím `GetFile`je nutné archiv vyprázdnit.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>CArchive:: GetObjectSchema

Voláním této funkce z `Serialize` funkce určete verzi objektu, který je právě deserializován.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Návratová hodnota

Během deserializace je načtená verze objektu.

### <a name="remarks"></a>Poznámky

Volání této funkce je platné pouze v případě `CArchive` , že je objekt načítán ( [CArchive:: Overloads](#isloading) vrátí nenulovou hodnotu). Mělo by se jednat o první volání `Serialize` funkce a volá se jenom jednou. Návratová hodnota (UINT) – 1 označuje, že číslo verze je neznámé.

Třída odvozená od třídy může používat VERSIONABLE_SCHEMA kombinovaných (pomocí bitových **nebo**) se samotnou verzí schématu (v makru IMPLEMENT_SERIAL) k vytvoření "objektu s možnostmi správy", který je `Serialize` objektem, jehož členská funkce může číst. `CObject` více verzí. Výchozí funkce architektury (bez VERSIONABLE_SCHEMA) je vyvolat výjimku, pokud se verze neshoduje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

##  <a name="isbufferempty"></a>CArchive:: IsBufferEmpty

Voláním této členské funkce určíte, zda je vnitřní vyrovnávací paměť objektu archivu prázdná.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je vyrovnávací paměť archivu prázdná; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato funkce je poskytována pro podporu programování pomocí třídy `CSocketFile`MFC rozhraní Windows Sockets. Nemusíte ho používat pro archiv přidružený `CFile` k objektu.

Důvodem použití `IsBufferEmpty` s archivem přidruženým `CSocketFile` k objektu je, že vyrovnávací paměť archivu může obsahovat více než jednu zprávu nebo záznam. Po přijetí jedné zprávy byste měli použít `IsBufferEmpty` k řízení smyčky, která bude nadále přijímat data, dokud není vyrovnávací paměť prázdná. Další informace naleznete v tématu funkce [Receive](../../mfc/reference/casyncsocket-class.md#receive) member třídy `CAsyncSocket`, která ukazuje, jak použít `IsBufferEmpty`.

Další informace najdete v tématu [Windows Sockets: Použití soketů s](../../mfc/windows-sockets-using-sockets-with-archives.md)archivy.

##  <a name="isloading"></a>CArchive:: IsLoaded

Určuje, zda archiv načítá data.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se archiv aktuálně používá pro načítání; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `Serialize` funkcemi archivovaných tříd.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

##  <a name="isstoring"></a>CArchive:: ukládá se

Určuje, zda archiv ukládá data.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se archiv aktuálně používá k ukládání; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána `Serialize` funkcemi archivovaných tříd.

Pokud je `IsLoading` stav archivu nenulová, je jeho stav 0 a naopak. `IsStoring`

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

##  <a name="mapobject"></a>CArchive:: MapObject

Zavolejte tuto členskou funkci pro umístění objektů do mapy, které nejsou ve skutečnosti serializovány do souboru, ale jsou k dispozici pro podobjekty k referenci.

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Konstantní ukazatel na objekt, který se ukládá.

### <a name="remarks"></a>Poznámky

Například nemůžete serializovat dokument, ale měli byste serializovat položky, které jsou součástí dokumentu. Voláním `MapObject`povolíte tyto položky nebo podobjektům odkaz na dokument. Serializované podpoložky také mohou serializovat svůj ukazatel *m_pDocument* zpátky.

Můžete zavolat `MapObject` při ukládání do a načítání `CArchive` z objektu. `MapObject`Přidá zadaný objekt do vnitřních datových struktur udržovaných `CArchive` objektem během serializace a deserializace, ale na rozdíl od [ReadObject](#readobject) a [WriteObject](#writeobject)nevolá serializaci objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>  CArchive::m_pDocument

Ve výchozím nastavení nastavte na hodnotu null. Tento ukazatel `CDocument` na může být nastaven na cokoli, co uživatel `CArchive` instance chce.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Poznámky

Běžným použitím tohoto ukazatele je předat dodatečné informace o procesu serializace všem serializovaným objektům. Toho je dosaženo inicializací ukazatele s dokumentem ( `CDocument`odvozenou třídou), která je serializována tak, že objekty v dokumentu budou mít v případě potřeby přístup k dokumentu. Tento ukazatel je používán `COleClientItem` také objekty během serializace.

Rozhraní nastaví *m_pDocument* na serializovaný dokument, když uživatel vydá příkaz k otevření nebo uložení souboru. Pokud jste serializováni dokument kontejneru Linking and Embeddinging (OLE) pro jiné důvody než soubor otevřít nebo uložit, musíte explicitně nastavit *m_pDocument*. To můžete provést například při serializaci dokumentu kontejneru do schránky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>CArchive:: operator&lt;&lt;

Ukládá do archivu zadaný objekt nebo primitivní typ.

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

`CArchive` Odkaz, který umožňuje více operátorů vkládání na jednom řádku.

### <a name="remarks"></a>Poznámky

Poslední dvě verze jsou určené konkrétně pro ukládání 64 celých čísel.

Pokud jste v implementaci třídy použili makro IMPLEMENT_SERIAL, operátor vložení je přetížen pro `CObject` volání Protected. `WriteObject` Tato funkce zase volá `Serialize` funkci třídy.

Operátor [](../../atl-mfc-shared/reference/cstringt-class.md) vložení CStringT (< <) podporuje diagnostický dumping a ukládání do archivu.

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CArchive` operátoru vložení < < s typy **int** a **Long** .

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Příklad

Tento příklad 2 ukazuje použití `CArchive` operátoru vložení < < `CStringT` s typem.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>CArchive:: operator&gt;&gt;

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

`CArchive` Odkaz, který umožňuje více operátorů extrakce na jednom řádku.

### <a name="remarks"></a>Poznámky

Poslední dvě verze jsou určené konkrétně pro načítání 64 celých čísel.

Pokud jste použili makro IMPLEMENT_SERIAL v implementaci vaší třídy, pak rozhraní extrakce přetížené pro `CObject` volání chráněné `ReadObject` funkce (s nenulovým ukazatelem třídy run-time). Tato funkce zase volá `Serialize` funkci třídy.

Operátor [](../../atl-mfc-shared/reference/cstringt-class.md) extrakce CStringT (> >) podporuje načítání z archivu.

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CArchive` operátoru extrakce > > s typem **int** .

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CArchive` operátorů vložení a extrakce <\< `CStringT` a > > s typem.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

##  <a name="read"></a>CArchive:: Read

Přečte zadaný počet bajtů z archivu.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na vyrovnávací paměť zadanou uživatelem, která přijímá data načtená z archivu.

*Nmaximum*<br/>
Unsigned integer určující počet bajtů, které mají být načteny z archivu.

### <a name="return-value"></a>Návratová hodnota

Unsigned integer obsahující počet bajtů, které jsou ve skutečnosti čteny. Pokud je vrácená hodnota menší než požadované číslo, bylo dosaženo konce souboru. V podmínce konec souboru není vyvolána žádná výjimka.

### <a name="remarks"></a>Poznámky

Archiv neinterpretuje bajty.

Můžete použít `Read` členskou funkci v rámci své `Serialize` funkce pro čtení běžných struktur, které jsou obsaženy ve vašich objektech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

##  <a name="readclass"></a>CArchive:: ReadClass

Volejte tuto členskou funkci pro čtení odkazu na třídu dříve uloženou pomocí [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parametry

*pClassRefRequested*<br/>
Ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , která odpovídá požadovanému odkazu na třídu. Může mít hodnotu NULL.

*pSchema*<br/>
Ukazatel na schéma běhové třídy, která byla dříve uložena.

*pObTag*<br/>
Číslo, které odkazuje na jedinečnou značku objektu. Používá se interně implementací [ReadObject](#readobject). Vystaveno pouze pro pokročilé programování; *pObTag* by normálně měla mít hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) .

### <a name="remarks"></a>Poznámky

Pokud *pClassRefRequested* není null, `ReadClass` ověří, že informace o archivovaných třídách jsou kompatibilní s vaší třídou prostředí Runtime. Pokud není kompatibilní, `ReadClass` vyvolá výjimku [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Třída runtime musí používat [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v opačném případě vyvolá výjimku [CNotSupportedException.](../../mfc/reference/cnotsupportedexception-class.md) `ReadClass`

Pokud má *pSchema* hodnotu null, schéma uložené třídy lze načíst voláním [CArchive:: GetObjectSchema](#getobjectschema); v opačném případě pSchema bude obsahovat schéma běhové třídy, která byla dříve uložena.  <strong>\*</strong>

Můžete použít [SerializeClass](#serializeclass) namísto `ReadClass`, který zpracovává čtení i zápis odkazu na třídu.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive:: WriteClass](#writeclass).

##  <a name="readobject"></a>CArchive:: ReadObject

Přečte data objektu z archivu a vytvoří objekt příslušného typu.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Konstantní ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , která odpovídá objektu, který očekáváte ke čtení.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [CObject](../../mfc/reference/cobject-class.md) , který musí být bezpečně převeden na správnou odvozenou třídu pomocí [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána `CArchive` operátorem extrakce ( **>>** ) přetíženým pro ukazatel [CObject](../../mfc/reference/cobject-class.md) . `ReadObject`pak volá `Serialize` funkci archivní třídy.

Pokud zadáte nenulový parametr *pClass* , který je získán pomocí makra [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) , funkce ověří třídu run-time archivovaného objektu. To předpokládá, že jste v implementaci třídy použili makro IMPLEMENT_SERIAL.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive:: WriteObject](#writeobject).

##  <a name="readstring"></a>CArchive:: ReadString

Zavolejte tuto členskou funkci pro čtení textových dat do vyrovnávací paměti ze souboru přidruženého k `CArchive` objektu.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který bude obsahovat výsledný řetězec poté, co je načten ze souboru přidruženého k objektu CArchive.

*lpsz*<br/>
Určuje ukazatel na vyrovnávací paměť zadanou uživatelem, která bude přijímat textový řetězec zakončený hodnotou null.

*Nmaximum*<br/>
Určuje maximální počet znaků, které mají být čteny. Hodnota by měla být menší než velikost vyrovnávací paměti *lpsz* .

### <a name="return-value"></a>Návratová hodnota

Ve verzi, která vrací BOOL, TRUE v případě úspěchu; V opačném případě NEPRAVDA.

Ve verzi, která vrací `LPTSTR`, ukazatel na vyrovnávací paměť obsahující textová data; Hodnota NULL, pokud bylo dosaženo konce souboru.

### <a name="remarks"></a>Poznámky

Ve verzi členské funkce s parametrem *nmaximum* bude vyrovnávací paměť obsahovat limit *nmaximum* -1 znaků. Čtení je zastaveno dvojicí kanálu návratového řádku. Koncové znaky nového řádku jsou vždy odebrány. Znak null (' \ 0 ') je připojen v obou případech.

[CArchive:: Read](#read) je také k dispozici pro vstup v textovém režimu, ale nekončí dvojicí kanálu návratového řádku.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive:: WriteString](#writestring).

##  <a name="serializeclass"></a>CArchive:: SerializeClass

Tuto členskou funkci volejte, pokud chcete uložit a načíst informace o verzi základní třídy.

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Ukazatel na objekt běhové třídy pro základní třídu.

### <a name="remarks"></a>Poznámky

`SerializeClass`přečte nebo zapíše odkaz na třídu do `CArchive` objektu v závislosti na směru. `CArchive` Používejte `SerializeClass` místo [ReadClass](#readclass) a [WriteClass](#writeclass) jako pohodlný způsob, jak serializovat objekty základní třídy; `SerializeClass` vyžaduje méně kódu a méně parametrů.

`ReadClass` Napříkladověřuje,žeinformaceoarchivovanýchtřídáchjsoukompatibilnísvaší`SerializeClass` třídou modulu runtime. Pokud není kompatibilní, `SerializeClass` vyvolá výjimku [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Třída runtime musí používat [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v opačném případě vyvolá výjimku [CNotSupportedException.](../../mfc/reference/cnotsupportedexception-class.md) `SerializeClass`

Použijte makro [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) k načtení hodnoty pro parametr *pRuntimeClass* . Základní třída musí používat makro [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>CArchive:: SetLoadParams

Zavolejte `SetLoadParams` , když budete číst velký `CObject`počet objektů odvozených z archivu.

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parametry

*nGrowBy*<br/>
Minimální počet slotů pro prvky, které mají být přiděleny, je-li nutné zvětšit velikost.

### <a name="remarks"></a>Poznámky

`CArchive`používá pole Load k překladu odkazů na objekty uložené v archivu. `SetLoadParams`umožňuje nastavit velikost, na kterou se pole zatížení zvětšuje.

Po načtení libovolného objektu `SetLoadParams` nebo po volání [MapObject](#mapobject) nebo [ReadObject](#readobject) se nemusíte volat.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="setobjectschema"></a>CArchive:: SetObjectSchema

Zavolejte tuto členskou funkci pro nastavení schématu objektu uloženého v objektu archivu na *nSchema*.

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parametry

*nSchema*<br/>
Určuje schéma objektu.

### <a name="remarks"></a>Poznámky

Při dalším volání [GetObjectSchema](#getobjectschema) se vrátí hodnota uložená v *nSchema*.

Použijte `SetObjectSchema` pro pokročilou správu verzí, například pokud chcete vynutit, aby byla konkrétní verze čtena `Serialize` ve funkci odvozené třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>CArchive:: SetStoreParams

Použijte `SetStoreParams` při ukládání velkého `CObject`počtu objektů odvozených v archivu.

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parametry

*nHashSize*<br/>
Velikost zatřiďovací tabulky pro mapy ukazatelů rozhraní Mělo by být hlavní číslo.

*nBlockSize*<br/>
Určuje členitost přidělení paměti pro rozšíření parametrů. Pro nejlepší výkon by měl být mocnina 2.

### <a name="remarks"></a>Poznámky

`SetStoreParams`umožňuje nastavit velikost zatřiďovací tabulky a velikost bloku mapy, která se používá k identifikaci jedinečných objektů během procesu serializace.

Po uložení žádného `SetStoreParams` objektu nebo po volání [MapObject](#mapobject) nebo [WriteObject](#writeobject) se nemusíte volat.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="write"></a>CArchive:: Write

Zapíše do archivu zadaný počet bajtů.

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na vyrovnávací paměť zadanou uživatelem, která obsahuje data, která mají být zapsána do archivu.

*Nmaximum*<br/>
Celé číslo, které určuje počet bajtů, které mají být zapsány do archivu.

### <a name="remarks"></a>Poznámky

Archiv neformátuje bajty.

Můžete použít `Write` členskou funkci v rámci vaší `Serialize` funkce k zápisu běžných struktur, které jsou obsaženy ve vašich objektech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>CArchive:: WriteClass

Slouží `WriteClass` k uložení informací o verzi a třídě základní třídy během serializace odvozené třídy.

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , která odpovídá požadovanému odkazu na třídu.

### <a name="remarks"></a>Poznámky

`WriteClass`Zapíše odkaz na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pro základní třídu na `CArchive`. K načtení odkazu použijte [CArchive:: ReadClass](#readclass) .

`WriteClass`ověřuje, že informace o archivovaných třídách jsou kompatibilní s vaší třídou prostředí Runtime. Pokud není kompatibilní, `WriteClass` vyvolá výjimku [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Třída runtime musí používat [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v opačném případě vyvolá výjimku [CNotSupportedException.](../../mfc/reference/cnotsupportedexception-class.md) `WriteClass`

Můžete použít [SerializeClass](#serializeclass) namísto `WriteClass`, který zpracovává čtení i zápis odkazu na třídu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>CArchive:: WriteObject

Ukládá zadaný `CObject` do archivu.

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Konstantní ukazatel na objekt, který se ukládá.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána `CArchive` operátorem vložení ( **<<** ) přetíženým pro. `CObject` `WriteObject`pak volá `Serialize` funkci archivní třídy.

K povolení archivace je nutné použít makro IMPLEMENT_SERIAL. `WriteObject`zapíše název třídy ASCII do archivu. Tento název třídy se ověří později během procesu načítání. Speciální schéma kódování zabraňuje zbytečnému duplikaci názvu třídy pro více objektů třídy. Toto schéma také zabraňuje redundantnímu úložišti objektů, které jsou cíleny na více než jeden ukazatel.

Přesná metoda kódování objektu (včetně přítomnosti názvu třídy ASCII) je detailní detail implementace a může se změnit v budoucích verzích knihovny.

> [!NOTE]
>  Než začnete archivovat své objekty, dokončete vytváření, odstraňování a aktualizace všech svých objektů. Archiv bude poškozený, pokud budete kombinovat archivaci se změnou objektu.

### <a name="example"></a>Příklad

Definici třídy `CAge`naleznete v příkladu pro [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>CArchive:: WriteString

Tuto členskou funkci použijte k zápisu dat z vyrovnávací paměti do souboru přidruženého `CArchive` k objektu.

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Určuje ukazatel na vyrovnávací paměť obsahující textový řetězec zakončený hodnotou null.

### <a name="remarks"></a>Poznámky

Ukončující znak null (' \ 0 ') není zapsán do souboru; automaticky se zapisuje i nový řádek.

`WriteString`vyvolá výjimku v reakci na několik podmínek, včetně podmínky úplného disku.

`Write`je také k dispozici, ale místo ukončení na znaku null zapisuje požadovaný počet bajtů do souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[CSocket – třída](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
