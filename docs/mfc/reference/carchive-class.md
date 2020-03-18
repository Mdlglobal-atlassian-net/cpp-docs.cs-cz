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
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418893"
---
# <a name="carchive-class"></a>CArchive – třída

Umožňuje uložit složitou síť objektů do trvalého binárního formátu (obvykle úložiště na disku), která po odstranění těchto objektů přetrvává.

## <a name="syntax"></a>Syntaxe

```
class CArchive
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CArchive:: CArchive](#carchive)|Vytvoří objekt `CArchive`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CArchive:: Abort](#abort)|Zavře archiv bez vyvolání výjimky.|
|[CArchive:: Close](#close)|Vyprázdní nezapsaná data a odpojí je od `CFile`.|
|[CArchive:: flush](#flush)|Vyprázdní nezapsaná data z archivní vyrovnávací paměti.|
|[CArchive:: GetFile](#getfile)|Získá ukazatel objektu `CFile` pro tento archiv.|
|[CArchive:: GetObjectSchema](#getobjectschema)|Volána z funkce `Serialize` k určení verze objektu, který je deserializován.|
|[CArchive:: IsBufferEmpty](#isbufferempty)|Určuje, zda byla vyrovnávací paměť vyprázdněna během procesu přijímání rozhraní Windows Sockets.|
|[CArchive:: IsLoaded](#isloading)|Určuje, zda se archiv načítá.|
|[CArchive:: ukládá se](#isstoring)|Určuje, zda archiv ukládá.|
|[CArchive:: MapObject](#mapobject)|Umístí objekty do mapy, které nejsou serializovány do souboru, ale jsou k dispozici pro podobjekty, na které se má odkazovat.|
|[CArchive:: Read](#read)|Přečte nezpracované bajty.|
|[CArchive:: ReadClass](#readclass)|Přečte odkaz na třídu dříve uložený pomocí `WriteClass`.|
|[CArchive:: ReadObject](#readobject)|Volá funkci `Serialize` objektu pro načtení.|
|[CArchive:: ReadString](#readstring)|Přečte jeden řádek textu.|
|[CArchive:: SerializeClass](#serializeclass)|Přečte nebo zapíše odkaz na třídu do objektu `CArchive` v závislosti na směru `CArchive`.|
|[CArchive:: SetLoadParams](#setloadparams)|Nastaví velikost, na kterou se pole zatížení zvětšuje. Musí být volána před načtením jakéhokoliv objektu nebo před zavoláním `MapObject` nebo `ReadObject`.|
|[CArchive:: SetObjectSchema](#setobjectschema)|Nastaví schéma objektu uložené v archivním objektu.|
|[CArchive:: SetStoreParams](#setstoreparams)|Nastaví velikost zatřiďovací tabulky a velikost bloku mapy použitou k identifikaci jedinečných objektů během procesu serializace.|
|[CArchive:: Write](#write)|Zapisuje nezpracované bajty.|
|[CArchive:: WriteClass](#writeclass)|Zapíše odkaz na `CRuntimeClass` do `CArchive`.|
|[CArchive:: WriteObject](#writeobject)|Volá funkci `Serialize` objektu pro ukládání.|
|[CArchive:: WriteString](#writestring)|Zapíše jeden řádek textu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CArchive:: operator &lt;&lt;](#operator_lt_lt)|Ukládá objekty a primitivní typy do archivu.|
|[CArchive:: operator &gt;&gt;](#operator_gt_gt)|Načte objekty a primitivní typy z archivu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CArchive:: m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Poznámky

`CArchive` nemá základní třídu.

Později můžete načíst objekty z trvalého úložiště, které je retvoří v paměti. Tento proces, který provádí data trvalě, se nazývá "serializace".

Archivní objekt si můžete představit jako typ binárního datového proudu. Podobně jako vstupní/výstupní datový proud je archiv přidružen k souboru a povoluje zápis do vyrovnávací paměti a čtení dat do a z úložiště. Vstupní a výstupní datový proud zpracovává sekvence znaků ASCII, ale archiv zpracovává binární data objektů v efektivním, neredundantním formátu.

Objekt [CFile –](../../mfc/reference/cfile-class.md) je nutné vytvořit předtím, než můžete vytvořit objekt `CArchive`. Kromě toho je nutné zajistit, aby stav zatížení a uložení archivu byl kompatibilní s režimem otevírání souboru. Máte omezené na jednu aktivní archivaci na jeden soubor.

Když vytvoříte objekt `CArchive`, připojíte ho k objektu třídy `CFile` (nebo odvozené třídě), která představuje otevřený soubor. Také určete, jestli se má archiv použít k načtení nebo uložení. Objekt `CArchive` může zpracovat nejen primitivní typy, ale také objekty tříd odvozených od [CObject](../../mfc/reference/cobject-class.md), které jsou navržené pro serializaci. Serializovatelný třída má obvykle `Serialize` členskou funkci a obvykle používá [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) makra, jak je popsáno v části Třída `CObject`.

Přetížené operátory pro extrakci ( **>>** ) a vložení ( **<<** ) jsou praktické archivační rozhraní pro programování, které podporuje oba primitivní typy i `CObject`odvozené třídy.

`CArchive` také podporuje programování s třídami MFC Windows Sockets [CSocket –](../../mfc/reference/csocket-class.md) a [CSocketFile](../../mfc/reference/csocketfile-class.md). Členská funkce [IsBufferEmpty](#isbufferempty) podporuje toto využití.

Další informace o `CArchive`najdete v článcích [serializace](../../mfc/serialization-in-mfc.md) a [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

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

Destruktor `CArchive` obvykle volá `Close`, čímž se vyprázdní všechna data, která nebyla uložena do přidruženého objektu `CFile`. To může způsobit výjimky.

Při zachycení těchto výjimek je vhodné použít `Abort`, takže destrukturování objektu `CArchive` nezpůsobí další výjimky. Při zpracování výjimek `CArchive::Abort` nevyvolá výjimku při selhání, protože na rozdíl od [CArchive:: Close](#close), `Abort` ignoruje selhání.

Pokud jste použili **New** pro přidělení objektu `CArchive` na haldě, je nutné jej po zavření souboru odstranit.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive:: WriteClass](#writeclass).

##  <a name="carchive"></a>CArchive:: CArchive

Vytvoří objekt `CArchive` a určí, zda bude použit pro načítání nebo ukládání objektů.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parametry

*pFile*<br/>
Ukazatel na objekt `CFile`, který je konečným zdrojem nebo cílem trvalých dat.

*nMode*<br/>
Příznak, který určuje, zda budou objekty načteny nebo uloženy do archivu. Parametr *nMode* musí mít jednu z následujících hodnot:

- `CArchive::load` načte data z archivu. Vyžaduje pouze `CFile` oprávnění ke čtení.

- `CArchive::store` ukládá data do archivu. Vyžaduje `CFile` oprávnění k zápisu.

- `CArchive::bNoFlushOnDelete` zabraňuje archivu v automatickém volání `Flush` při volání destruktoru archivu. Pokud jste tento příznak nastavili, zodpovídáte za explicitní volání `Close` před voláním destruktoru. Pokud to neuděláte, vaše data budou poškozena.

*nBufSize*<br/>
Celé číslo, které určuje velikost vnitřní vyrovnávací paměti souborů (v bajtech). Všimněte si, že výchozí velikost vyrovnávací paměti je 4 096 bajtů. Pokud často archivujete velké objekty, zvýšíte výkon, pokud použijete větší vyrovnávací paměť, která je násobkem velikosti vyrovnávací paměti souborů.

*lpBuf*<br/>
Volitelný ukazatel na vyrovnávací paměť zadanou uživatelem velikosti *nBufSize*. Pokud tento parametr nezadáte, archiv přidělí vyrovnávací paměť z místní haldy a uvolní ji při zničení objektu. Archiv neuvolňuje vyrovnávací paměť poskytnutou uživatelem.

### <a name="remarks"></a>Poznámky

Po vytvoření archivu už tuto specifikaci nemůžete změnit.

Nemůžete použít operace `CFile` pro změnu stavu souboru, dokud jste archiv nezavřeli. Každá taková operace bude mít za škodu integritu archivu. K pozici ukazatele souboru můžete přistupovat kdykoli během serializace tím, že získáte objekt souboru archivu z členské funkce [GetFile](#getfile) a potom použijete funkci [CFile –:: GetPosition](../../mfc/reference/cfile-class.md#getposition) . Před získáním pozice ukazatele souboru byste měli zavolat metodu [CArchive:: flush](#flush) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>CArchive:: Close

Vyprázdní všechna zbývající data ve vyrovnávací paměti, zavře archiv a odpojí archiv ze souboru.

```
void Close();
```

### <a name="remarks"></a>Poznámky

V archivu nejsou povoleny žádné další operace. Po zavření archivu můžete vytvořit další archiv pro stejný soubor nebo můžete soubor zavřít.

Členská funkce `Close` zajistí, že všechna data budou přenesena z archivu do souboru a nebude tak k dispozici archiv. Chcete-li dokončit přenos ze souboru na médium úložiště, je nutné nejprve použít [CFile –:: Close](../../mfc/reference/cfile-class.md#close) a poté zničit objekt `CFile`.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive:: WriteString](#writestring).

##  <a name="flush"></a>CArchive:: flush

Vynutí zápis všech dat zbývajících ve vyrovnávací paměti archivu do souboru.

```
void Flush();
```

### <a name="remarks"></a>Poznámky

Členská funkce `Flush` zajistí, že všechna data budou přenesena z archivu do souboru. Chcete-li dokončit přenos ze souboru na médium úložiště, je nutné zavolat [CFile –:: Close](../../mfc/reference/cfile-class.md#close) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>CArchive:: GetFile

Získá ukazatel objektu `CFile` pro tento archiv.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní ukazatel na objekt `CFile` používaný.

### <a name="remarks"></a>Poznámky

Předtím, než použijete `GetFile`, je nutné archiv vyprázdnit.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>CArchive:: GetObjectSchema

Voláním této funkce z funkce `Serialize` určíte verzi objektu, který je právě deserializován.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Návratová hodnota

Během deserializace je načtená verze objektu.

### <a name="remarks"></a>Poznámky

Volání této funkce je platné pouze v případě, že je načten objekt `CArchive` ( [CArchive:: Overloads](#isloading) vrátí nenulovou hodnotu). Mělo by se jednat o první volání funkce `Serialize` a volá se jenom jednou. Návratová hodnota (UINT) – 1 označuje, že číslo verze je neznámé.

Třída odvozená od `CObject`může používat VERSIONABLE_SCHEMA kombinované (pomocí bitového **nebo**) se samotnou verzí schématu (v makru IMPLEMENT_SERIAL) k vytvoření "objektu s možnostmi", který je objektem, jehož `Serialize` členská funkce může číst více verzí. Výchozí funkce architektury (bez VERSIONABLE_SCHEMA) je vyvolat výjimku, pokud se verze neshoduje.

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

Tato funkce je poskytována pro podporu programování pomocí `CSocketFile`třídy MFC Windows Sockets. Nemusíte ho používat pro archiv přidružený k objektu `CFile`.

Důvodem použití `IsBufferEmpty` s archivem přidruženým k objektu `CSocketFile` je, že vyrovnávací paměť archivu může obsahovat více než jednu zprávu nebo záznam. Po přijetí jedné zprávy byste měli použít `IsBufferEmpty` k řízení smyčky, která bude nadále přijímat data, dokud není vyrovnávací paměť prázdná. Další informace naleznete v tématu funkce [Receive](../../mfc/reference/casyncsocket-class.md#receive) member třídy `CAsyncSocket`, která ukazuje, jak používat `IsBufferEmpty`.

Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isloading"></a>CArchive:: IsLoaded

Určuje, zda archiv načítá data.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se archiv aktuálně používá pro načítání; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce je volána funkcemi `Serialize` archivovaných tříd.

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

Tato členská funkce je volána funkcemi `Serialize` archivovaných tříd.

Pokud je stav `IsStoring` archivu nenulová, je jeho stav `IsLoading` 0 a naopak.

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

Například nemůžete serializovat dokument, ale měli byste serializovat položky, které jsou součástí dokumentu. Voláním `MapObject`povolíte tyto položky nebo podobjektům odkaz na dokument. Serializované podpoložky také mohou serializovat svůj *m_pDocument* ukazatel na pozadí.

Můžete volat `MapObject` při ukládání do a načítání z objektu `CArchive`. `MapObject` přidá zadaný objekt do vnitřních datových struktur udržovaných při serializaci a deserializaci pomocí objektu `CArchive`, ale na rozdíl od [ReadObject](#readobject) a [WriteObject](#writeobject)nevolá serializaci objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>CArchive:: m_pDocument

Ve výchozím nastavení nastavte na hodnotu NULL. Tento ukazatel na `CDocument` lze nastavit na cokoli, co uživatel `CArchive` instance chce.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Poznámky

Běžným použitím tohoto ukazatele je předat dodatečné informace o procesu serializace všem serializovaným objektům. Toho lze dosáhnout inicializací ukazatele s dokumentem (`CDocument`odvozené třídy), který je serializován, takovým způsobem, aby objekty v dokumentu měly v případě potřeby přístup k dokumentu. Tento ukazatel je také používán `COleClientItem` objekty během serializace.

Rozhraní nastaví *m_pDocument* do serializovaného dokumentu, když uživatel vydá příkaz k otevření nebo uložení souboru. Pokud jste serializováni dokument kontejneru Linking and Embeddinging (OLE) pro jiné důvody než soubor otevřít nebo uložit, je nutné explicitně nastavit *m_pDocument*. To můžete provést například při serializaci dokumentu kontejneru do schránky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>CArchive:: operator &lt;&lt;

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

Odkaz na `CArchive`, který umožňuje více operátorů vkládání na jednom řádku.

### <a name="remarks"></a>Poznámky

Poslední dvě verze jsou určené konkrétně pro ukládání 64 celých čísel.

Pokud jste použili makro IMPLEMENT_SERIAL v implementaci třídy, pak operátor vložení přetížení pro `CObject` volá chráněný `WriteObject`. Tato funkce zase volá funkci `Serialize` třídy.

Operátor vložení [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (< <) podporuje diagnostický dumping a ukládání do archivu.

### <a name="example"></a>Příklad

Tento příklad ukazuje použití operátoru vkládání `CArchive` < < s typy **int** a **Long** .

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Příklad

Tento příklad 2 ukazuje použití operátoru vkládání `CArchive` < < s `CStringT` typem.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>CArchive:: operator &gt;&gt;

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

Odkaz na `CArchive`, který umožňuje více operátorů extrakce na jednom řádku.

### <a name="remarks"></a>Poznámky

Poslední dvě verze jsou určené konkrétně pro načítání 64 celých čísel.

Pokud jste použili makro IMPLEMENT_SERIAL v implementaci vaší třídy, pak jsou Přetěžování operátorů extrakce pro `CObject` volání funkce Protected `ReadObject` (s nenulovým ukazatelem třídy run-time). Tato funkce zase volá funkci `Serialize` třídy.

Operátor extrakce [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (> >) podporuje načítání z archivu.

### <a name="example"></a>Příklad

Tento příklad ukazuje použití operátoru extrakce `CArchive` > > s typem **int** .

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Příklad

Tento příklad ukazuje použití operátorů vkládání a extrakce `CArchive` <\< a > > s typem `CStringT`.

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

Můžete použít členskou funkci `Read` v rámci své `Serialize` funkce pro čtení běžných struktur, které jsou obsaženy ve vašich objektech.

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

Pokud *pClassRefRequested* není NULL, `ReadClass` ověří, že informace o archivovaných třídách jsou kompatibilní s vaší třídou prostředí Runtime. Pokud není kompatibilní, `ReadClass` vyvolá výjimku [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Třída runtime musí používat [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v opačném případě `ReadClass` vyvolá výjimku [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pokud má *pSchema* hodnotu null, schéma uložené třídy lze načíst voláním [CArchive:: GetObjectSchema](#getobjectschema); v opačném případě <strong>\*</strong> *pSchema* bude obsahovat schéma běhové třídy, která byla dříve uložena.

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

Tato funkce je obvykle volána pomocí operátoru `CArchive` extrakce ( **>>** ) přetíženého pro ukazatel [CObject](../../mfc/reference/cobject-class.md) . `ReadObject`pak zavolá funkci `Serialize` archivní třídy.

Pokud zadáte nenulový parametr *pClass* , který je získán pomocí makra [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) , funkce ověří třídu run-time archivovaného objektu. To předpokládá, že jste v implementaci třídy použili makro IMPLEMENT_SERIAL.

### <a name="example"></a>Příklad

  Podívejte se na příklad pro [CArchive:: WriteObject](#writeobject).

##  <a name="readstring"></a>CArchive:: ReadString

Volejte tuto členskou funkci pro čtení textových dat do vyrovnávací paměti ze souboru přidruženého k objektu `CArchive`.

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

`SerializeClass` čte nebo zapisuje odkaz na třídu do objektu `CArchive` v závislosti na směru `CArchive`. Použijte `SerializeClass` místo [ReadClass](#readclass) a [WriteClass](#writeclass) jako pohodlný způsob, jak serializovat objekty základní třídy; `SerializeClass` vyžaduje menší kód a méně parametrů.

Podobně jako `ReadClass``SerializeClass` ověřuje, že informace o archivovaných třídách jsou kompatibilní s vaší třídou prostředí Runtime. Pokud není kompatibilní, `SerializeClass` vyvolá výjimku [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Třída runtime musí používat [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v opačném případě `SerializeClass` vyvolá výjimku [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pomocí makra [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) načtěte hodnotu parametru *pRuntimeClass* . Základní třída musí používat makro [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>CArchive:: SetLoadParams

Pokud se chystáte číst velký počet objektů odvozených od `CObject`z archivu, zavolejte `SetLoadParams`.

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parametry

*nGrowBy*<br/>
Minimální počet slotů pro prvky, které mají být přiděleny, je-li nutné zvětšit velikost.

### <a name="remarks"></a>Poznámky

`CArchive` používá pole Load k překladu odkazů na objekty uložené v archivu. `SetLoadParams` umožňuje nastavit velikost, na kterou se pole zatížení zvětšuje.

Po načtení objektu nebo po volání [MapObject](#mapobject) nebo [ReadObject](#readobject) není nutné volat `SetLoadParams`.

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

Použít `SetObjectSchema` pro pokročilou správu verzí; Například pokud chcete vynutit, aby byla konkrétní verze čtena ve `Serialize` funkce odvozené třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>CArchive:: SetStoreParams

Při ukládání velkého počtu objektů odvozených `CObject`do archivu použijte `SetStoreParams`.

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parametry

*nHashSize*<br/>
Velikost zatřiďovací tabulky pro mapy ukazatelů rozhraní Mělo by být hlavní číslo.

*nBlockSize*<br/>
Určuje členitost přidělení paměti pro rozšíření parametrů. Pro nejlepší výkon by měl být mocnina 2.

### <a name="remarks"></a>Poznámky

`SetStoreParams` umožňuje nastavit velikost zatřiďovací tabulky a velikost bloku mapy použitou k identifikaci jedinečných objektů během procesu serializace.

Nemusíte volat `SetStoreParams` po uložení objektů nebo po volání metody [MapObject](#mapobject) nebo [WriteObject](#writeobject) .

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

V rámci funkce `Serialize` můžete použít členskou funkci `Write` k zápisu běžných struktur, které jsou obsaženy ve vašich objektech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>CArchive:: WriteClass

Použijte `WriteClass` k uložení informací o verzi a třídě základní třídy během serializace odvozené třídy.

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Ukazatel na strukturu [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) , která odpovídá požadovanému odkazu na třídu.

### <a name="remarks"></a>Poznámky

`WriteClass` zapíše odkaz na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pro základní třídu na `CArchive`. K načtení odkazu použijte [CArchive:: ReadClass](#readclass) .

`WriteClass` ověří, zda jsou informace o archivovaných třídách kompatibilní s vaší třídou prostředí Runtime. Pokud není kompatibilní, `WriteClass` vyvolá výjimku [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Třída runtime musí používat [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v opačném případě `WriteClass` vyvolá výjimku [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Můžete použít [SerializeClass](#serializeclass) namísto `WriteClass`, který zpracovává čtení i zápis odkazu na třídu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>CArchive:: WriteObject

Uloží zadanou `CObject` do archivu.

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*pOb*<br/>
Konstantní ukazatel na objekt, který se ukládá.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána operátorem vkládání `CArchive` ( **<<** ) přetíženým pro `CObject`. `WriteObject`pak zavolá funkci `Serialize` archivní třídy.

K povolení archivace je nutné použít makro IMPLEMENT_SERIAL. `WriteObject` zapíše název třídy ASCII do archivu. Tento název třídy se ověří později během procesu načítání. Speciální schéma kódování zabraňuje zbytečnému duplikaci názvu třídy pro více objektů třídy. Toto schéma také zabraňuje redundantnímu úložišti objektů, které jsou cíleny na více než jeden ukazatel.

Přesná metoda kódování objektu (včetně přítomnosti názvu třídy ASCII) je detailní detail implementace a může se změnit v budoucích verzích knihovny.

> [!NOTE]
>  Než začnete archivovat své objekty, dokončete vytváření, odstraňování a aktualizace všech svých objektů. Archiv bude poškozený, pokud budete kombinovat archivaci se změnou objektu.

### <a name="example"></a>Příklad

Definici `CAge`třídy naleznete v příkladu pro [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>CArchive:: WriteString

Tato členská funkce slouží k zápisu dat z vyrovnávací paměti do souboru přidruženého k objektu `CArchive`.

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Určuje ukazatel na vyrovnávací paměť obsahující textový řetězec zakončený hodnotou null.

### <a name="remarks"></a>Poznámky

Ukončující znak null (' \ 0 ') není zapsán do souboru; automaticky se zapisuje i nový řádek.

`WriteString` vyvolá výjimku v reakci na několik podmínek, včetně podmínky úplného disku.

`Write` je také k dispozici, ale místo ukončení na znaku null zapisuje požadovaný počet bajtů do souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[CSocket – třída](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
