---
title: Třída CArchiv
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
ms.openlocfilehash: ef8b6ec9060e8c15dd45f8203dadd2a2aca9e168
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753122"
---
# <a name="carchive-class"></a>Třída CArchiv

Umožňuje uložit složitou síť objektů v trvalé binární podobě (obvykle diskové úložiště), která přetrvává i po odstranění těchto objektů.

## <a name="syntax"></a>Syntaxe

```
class CArchive
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CArchiv::CArchiv](#carchive)|Vytvoří `CArchive` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CArchiv::Přerušit](#abort)|Zavře archiv bez vyvolání výjimky.|
|[CArchiv::Zavřít](#close)|Vyprázdní nepsaná data `CFile`a odpojí se od .|
|[CArchiv::Vyprázdnění](#flush)|Vyprázdní nepsaná data z vyrovnávací paměti archivu.|
|[CArchive::GetFile](#getfile)|Získá `CFile` ukazatel objektu pro tento archiv.|
|[CArchive::GetObjectSchema](#getobjectschema)|Volána `Serialize` z funkce k určení verze objektu, který je právě dekonstruován.|
|[CArchive::IsBufferEmpty](#isbufferempty)|Určuje, zda byla vyrovnávací paměť vyprázdněna během procesu příjmu zásuvek systému Windows Sockets.|
|[CArchiv::Načítání](#isloading)|Určuje, zda se archiv načítá.|
|[CArchiv::IsStoring](#isstoring)|Určuje, zda je archiv ukládání.|
|[CArchive::MapObject](#mapobject)|Umístí objekty do mapy, které nejsou serializovány do souboru, ale které jsou k dispozici pro podobjekty odkazovat.|
|[CArchiv::Číst](#read)|Čte nezpracované bajty.|
|[CArchive::ReadClass](#readclass)|Přečte odkaz na `WriteClass`třídu dříve uloženou s .|
|[CArchive::ReadObject](#readobject)|Volá `Serialize` funkci objektu pro načtení.|
|[CArchive::Řetězec čtení](#readstring)|Přečte jeden řádek textu.|
|[CArchive::SerializeClass](#serializeclass)|Přečte nebo zapíše `CArchive` odkaz třídy na `CArchive`objekt v závislosti na směru .|
|[CArchive::SetLoadParams](#setloadparams)|Nastaví velikost, na kterou roste pole zatížení. Musí být volána před načtením libovolného objektu nebo před `MapObject` nebo `ReadObject` je volána.|
|[CArchive::SetObjectSchema](#setobjectschema)|Nastaví schéma objektu uložené v objektu archivu.|
|[CArchive::SetStoreParams](#setstoreparams)|Nastaví velikost tabulky hash a velikost bloku mapy použité k identifikaci jedinečných objektů během procesu serializace.|
|[CArchiv::Zápis](#write)|Zapíše nezpracované bajty.|
|[CArchive::WriteClass](#writeclass)|Zapíše odkaz `CRuntimeClass` na `CArchive`.|
|[CArchive::WriteObject](#writeobject)|Volá `Serialize` funkci objektu pro ukládání.|
|[CArchive::Řetězec zápisu](#writestring)|Zapíše jeden řádek textu.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CArchiv::operátor&lt;&lt;](#operator_lt_lt)|Ukládá objekty a primitivní typy do archivu.|
|[CArchiv::operátor&gt;&gt;](#operator_gt_gt)|Načte objekty a primitivní typy z archivu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CArchiv::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>Poznámky

`CArchive`nemá základní třídu.

Později můžete načíst objekty z trvalého úložiště a znovu je vykonstovat v paměti. Tento proces vytváření trvalých dat se nazývá "serializace".

Objekt archivu si můžete usuzovat jako druh binárního datového proudu. Stejně jako vstupní a výstupní datový proud je archiv přidružen k souboru a umožňuje ukládání a čtení dat do a z úložiště ve vyrovnávací paměti. Vstupní a výstupní datový proud zpracovává sekvence znaků ASCII, ale archiv zpracovává binární objektová data v efektivním, neredundantním formátu.

Před vytvořením objektu `CArchive` je nutné vytvořit objekt [CFile.](../../mfc/reference/cfile-class.md) Kromě toho je nutné zajistit, aby byl stav načtení/ukládání archivu kompatibilní s otevřeným režimem souboru. Jste omezeni na jednu aktivní archivaci na soubor.

Při vytváření `CArchive` objektu jej připojíte k `CFile` objektu třídy (nebo odvozené třídy), který představuje otevřený soubor. Můžete také určit, zda bude archiv použit pro načítání nebo ukládání. Objekt `CArchive` může zpracovávat nejen primitivní typy, ale také objekty tříd odvozených z [CObject](../../mfc/reference/cobject-class.md)určených pro serializaci. Serializovatelná třída má obvykle `Serialize` členskou funkci a obvykle používá [makra DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a `CObject` [IMPLEMENT_SERIAL,](../../mfc/reference/run-time-object-model-services.md#implement_serial) jak je popsáno v části třída .

Přetížené extrakce **>>**( ) a **<<** vkládání ( ) operátory jsou pohodlné `CObject`archivprogramační rozhraní, které podporují primitivní typy a odvozené třídy.

`CArchive`Podporuje také programování s třídami [CSockets](../../mfc/reference/csocket-class.md) systému MFC Windows Sockets a [CSocketFile](../../mfc/reference/csocketfile-class.md). Členská funkce [IsBufferEmpty](#isbufferempty) toto použití podporuje.

Další informace `CArchive`naleznete v článcích [Serializace](../../mfc/serialization-in-mfc.md) a [Zásuvky systému Windows: Použití soketů s archivací](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CArchive`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="carchiveabort"></a><a name="abort"></a>CArchiv::Přerušit

Volání této funkce zavřete archiv bez vyvolání výjimky.

```cpp
void Abort ();
```

### <a name="remarks"></a>Poznámky

`CArchive` Destruktor obvykle `Close`zavolá , který vyprázdní všechna data, která nebyla uložena do přidruženého `CFile` objektu. To může způsobit výjimky.

Při zachycení těchto výjimek je vhodné `Abort`použít , aby destrukce objektu `CArchive` nezpůsobila další výjimky. Při zpracování výjimek `CArchive::Abort` nevyvolá výjimku při selháních, protože na rozdíl od [CArchive::Close](#close)ignoruje `Abort` chyby.

Pokud jste **new** použili `CArchive` nový přidělit objekt na haldě, pak je nutné odstranit po zavření souboru.

### <a name="example"></a>Příklad

  Viz příklad pro [CArchive::WriteClass](#writeclass).

## <a name="carchivecarchive"></a><a name="carchive"></a>CArchiv::CArchiv

Vytvoří `CArchive` objekt a určí, zda bude použit pro načítání nebo ukládání objektů.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>Parametry

*pSoubor*<br/>
Ukazatel na `CFile` objekt, který je konečným zdrojem nebo cílem trvalých dat.

*nRežim*<br/>
Příznak, který určuje, zda budou objekty načteny z archivu nebo do ní uloženy. Parametr *nMode* musí mít jednu z následujících hodnot:

- `CArchive::load`Načte data z archivu. Vyžaduje `CFile` pouze oprávnění ke čtení.

- `CArchive::store`Uloží data do archivu. Vyžaduje `CFile` oprávnění k zápisu.

- `CArchive::bNoFlushOnDelete`Zabrání archivu v `Flush` automatickém volání při volání destruktoru archivu. Pokud nastavíte tento příznak, jste `Close` zodpovědní za explicitní volání před destruktor je volána. Pokud tak neučiníte, budou data poškozena.

*nBufVelikost*<br/>
Celé číslo, které určuje velikost vnitřní vyrovnávací paměti souboru v bajtů. Všimněte si, že výchozí velikost vyrovnávací paměti je 4 096 bajtů. Pokud běžně archivujete velké objekty, zvýšíte výkon, pokud použijete větší velikost vyrovnávací paměti, která je násobkem velikosti vyrovnávací paměti souboru.

*lpBuf*<br/>
Volitelný ukazatel na uživatelem dodanou vyrovnávací paměť velikosti *nBufSize*. Pokud tento parametr nezadáte, archiv přidělí vyrovnávací paměť z místní haldy a uvolní ji při zničení objektu. Archiv neuvolní vyrovnávací paměť dodanou uživatelem.

### <a name="remarks"></a>Poznámky

Tuto specifikaci nelze po vytvoření archivu změnit.

Operace nesmíte `CFile` měnit stav souboru, dokud archiv nezavřete. Každá taková operace poškodí integritu archivu. K pozici ukazatele souboru můžete kdykoli během serializace přistupovat získáním objektu souboru archivu z členské funkce [GetFile](#getfile) a potom pomocí funkce [CFile::GetPosition.](../../mfc/reference/cfile-class.md#getposition) Měli byste zavolat [CArchive::Flush](#flush) před získáním pozice ukazatele souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

## <a name="carchiveclose"></a><a name="close"></a>CArchiv::Zavřít

Vyprázdní všechna data zbývající do vyrovnávací paměti, zavře archiv a odpojí archiv od souboru.

```cpp
void Close();
```

### <a name="remarks"></a>Poznámky

Žádné další operace v archivu nejsou povoleny. Po zavření archivu můžete vytvořit další archiv pro stejný soubor nebo soubor zavřít.

Členská `Close` funkce zajišťuje, že všechna data jsou přenesena z archivu do souboru a znepřístupňuje archiv. Chcete-li dokončit přenos ze souboru na paměťové médium, musíte nejprve použít [CFile::Close](../../mfc/reference/cfile-class.md#close) a potom `CFile` zničit objekt.

### <a name="example"></a>Příklad

  Viz příklad pro [CArchive::WriteString](#writestring).

## <a name="carchiveflush"></a><a name="flush"></a>CArchiv::Vyprázdnění

Vynutí všechna zbývající data ve vyrovnávací paměti archivu, která mají být zapsána do souboru.

```cpp
void Flush();
```

### <a name="remarks"></a>Poznámky

Členská `Flush` funkce zajišťuje přenos všech dat z archivu do souboru. Chcete-li dokončit přenos ze souboru na paměťové médium, musíte zavolat [CFile::Close.](../../mfc/reference/cfile-class.md#close)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

## <a name="carchivegetfile"></a><a name="getfile"></a>CArchive::GetFile

Získá `CFile` ukazatel objektu pro tento archiv.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>Návratová hodnota

Konstantní ukazatel na `CFile` objekt, který se používá.

### <a name="remarks"></a>Poznámky

Před použitím `GetFile`je nutné archiv vyprázdnit .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

## <a name="carchivegetobjectschema"></a><a name="getobjectschema"></a>CArchive::GetObjectSchema

Volání této funkce `Serialize` z funkce k určení verze objektu, který je právě rekonstruován.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>Návratová hodnota

Během deserializace verze objektu čtení.

### <a name="remarks"></a>Poznámky

Volání této funkce je `CArchive` platné pouze při načítání objektu ( [CArchive::IsLoading](#isloading) vrátí nenulovou hodnotu). Mělo by se jedná `Serialize` o první volání ve funkci a voláno pouze jednou. Vrácená hodnota ( UINT)-1 označuje, že číslo verze není známo.

A `CObject`-derived class may use VERSIONABLE_SCHEMA combined (using bitwise **OR)** with the schema version itself (in the `Serialize` IMPLEMENT_SERIAL macro) to create a "versionable object", to znamená, že objekt, jehož členská funkce může číst více verzí. Výchozí funkce rozhraní (bez VERSIONABLE_SCHEMA) je vyvolat výjimku, pokud je verze neodpovídající.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

## <a name="carchiveisbufferempty"></a><a name="isbufferempty"></a>CArchive::IsBufferEmpty

Volání této členské funkce k určení, zda je vnitřní vyrovnávací paměť objektu archivu prázdná.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je vyrovnávací paměť archivu prázdná; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce je poskytována pro podporu programování `CSocketFile`pomocí třídy MFC Windows Sockets . Není nutné jej použít pro archiv přidružený `CFile` k objektu.

Důvodem použití `IsBufferEmpty` s archivem `CSocketFile` přidruženým k objektu je, že vyrovnávací paměť archivu může obsahovat více než jednu zprávu nebo záznam. Po obdržení jedné zprávy `IsBufferEmpty` byste měli použít k řízení smyčky, která pokračuje v příjmu dat, dokud není vyrovnávací paměť prázdná. Další informace naleznete [Receive](../../mfc/reference/casyncsocket-class.md#receive) v tématu `CAsyncSocket`Receive členské funkce `IsBufferEmpty`třídy , která ukazuje, jak používat .

Další informace naleznete [v tématu Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="carchiveisloading"></a><a name="isloading"></a>CArchiv::Načítání

Určuje, zda archiv načítá data.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je archiv právě používán pro načtení; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce `Serialize` je volána funkcemi archivovaných tříd.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

## <a name="carchiveisstoring"></a><a name="isstoring"></a>CArchiv::IsStoring

Určuje, zda archiv ukládá data.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je archiv právě používán pro ukládání; jinak 0.

### <a name="remarks"></a>Poznámky

Tato členská funkce `Serialize` je volána funkcemi archivovaných tříd.

Pokud `IsStoring` je stav archivu nenulový, pak je jeho `IsLoading` stav 0 a naopak.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

## <a name="carchivemapobject"></a><a name="mapobject"></a>CArchive::MapObject

Volání této členské funkce umístit objekty v mapě, které nejsou skutečně serializovány do souboru, ale které jsou k dispozici pro podobjekty odkazovat.

```cpp
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*Pob*<br/>
Konstantní ukazatel na objekt, který je uložen.

### <a name="remarks"></a>Poznámky

Dokument například neserializujete, ale serializujete položky, které jsou součástí dokumentu. Voláním `MapObject`můžete povolit tyto položky nebo podobjekty odkazovat na dokument. Serializované podpoložky mohou také serializovat svůj *m_pDocument* zpět.

Můžete volat `MapObject` při ukládání a načtení z objektu. `CArchive` `MapObject`přidá zadaný objekt do vnitřních datových struktur udržovaných `CArchive` objektem během serializace a deserializace, ale na rozdíl od Objektů [ReadObject](#readobject) a [WriteObject](#writeobject)nevolá serializovat objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

## <a name="carchivem_pdocument"></a><a name="m_pdocument"></a>CArchiv::m_pDocument

Nastavte hodnotu NULL ve výchozím `CDocument` nastavení, tento ukazatel na `CArchive` lze nastavit na cokoli, co uživatel instance chce.

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>Poznámky

Běžné použití tohoto ukazatele je sdělit další informace o procesu serializace na všechny objekty, které jsou serializovány. Toho je dosaženo inicializací `CDocument`ukazatele s dokumentem (odvozená třída), který je serializován, takovým způsobem, že objekty v dokumentu mohou v případě potřeby přistupovat k dokumentu. Tento ukazatel je `COleClientItem` také používán objekty během serializace.

Rozhraní framework nastaví *m_pDocument* na dokument serializovaný, když uživatel vydá příkaz Otevřít soubor nebo Uložit. Pokud serializujete dokument kontejneru OLE (Object Linking and Embedding) z jiných důvodů, než je otevření nebo uložení souboru, musíte explicitně nastavit *m_pDocument*. Například byste to provést při serializaci dokumentu kontejneru do schránky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

## <a name="carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>CArchiv::operátor&lt;&lt;

Uloží uvedený objekt nebo primitivní typ do archivu.

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

Odkaz, `CArchive` který umožňuje více operátorů vložení na jednom řádku.

### <a name="remarks"></a>Poznámky

Poslední dvě výše uvedené verze jsou speciálně pro ukládání 64bitových celočísel.

Pokud jste použili IMPLEMENT_SERIAL makro v implementaci třídy, pak `CObject` operátor `WriteObject`vložení přetížené pro volání chráněné . Tato funkce zase volá `Serialize` funkci třídy.

Operátor vložení [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (<<) podporuje diagnostický dumping a ukládání do archivu.

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CArchive` operátoru vložení << s **int** a **long** typy.

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>Příklad

Tento příklad 2 ukazuje použití `CArchive` operátoru vložení << `CStringT` s typem.

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

## <a name="carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>CArchiv::operátor&gt;&gt;

Načte uvedený objekt nebo primitivní typ z archivu.

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

Odkaz, `CArchive` který umožňuje více operátorů extrakce na jednom řádku.

### <a name="remarks"></a>Poznámky

Poslední dvě výše uvedené verze jsou speciálně pro načítání 64bitových celá čísla.

Pokud jste použili IMPLEMENT_SERIAL makro v implementaci třídy, `CObject` pak `ReadObject` operátory extrakce přetížené pro volání chráněné funkce (s ukazatelem třídy run-time). Tato funkce zase volá `Serialize` funkci třídy.

Operátor extrakce [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) (>>) podporuje načítání z archivu.

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CArchive` operátoru extrakce >> s typem **int.**

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>Příklad

Tento příklad ukazuje použití `CArchive` vkládání a extrakce \< operátory <`CStringT` a >> s typem.

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

## <a name="carchiveread"></a><a name="read"></a>CArchiv::Číst

Přečte zadaný počet bajtů z archivu.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na uživatelem zadanou vyrovnávací paměť, která má přijímat data přečtená z archivu.

*nMax*<br/>
Nepodepsané celé číslo určující počet bajtů, které mají být přečteny z archivu.

### <a name="return-value"></a>Návratová hodnota

Nepodepsané celé číslo obsahující počet skutečně přečtených bajtů. Pokud je vrácená hodnota menší než požadované číslo, bylo dosaženo konce souboru. Na podmínku konce souboru není vyvolána žádná výjimka.

### <a name="remarks"></a>Poznámky

Archiv neinterpretuje bajty.

Členní `Read` funkci v rámci `Serialize` funkce můžete použít pro čtení běžných struktur, které jsou obsaženy v objektech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

## <a name="carchivereadclass"></a><a name="readclass"></a>CArchive::ReadClass

Volání této členské funkce číst odkaz na třídu dříve uloženou s [WriteClass](#writeclass).

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>Parametry

*pClassRefRequested*<br/>
Ukazatel na strukturu [CRuntimeClass,](../../mfc/reference/cruntimeclass-structure.md) která odpovídá požadovanému odkazu na třídu. Může být NULL.

*pSchema*<br/>
Ukazatel na schéma třídy run-time dříve uložené.

*pObTag*<br/>
Číslo, které odkazuje na jedinečnou značku objektu. Interně používá implementace [ReadObject](#readobject). Vystaveno pouze pro pokročilé programování; *pObTag* by normálně měla být NULL.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [cRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury.

### <a name="remarks"></a>Poznámky

Pokud *pClassRefRequested* není `ReadClass` NULL, ověří, zda jsou archivované informace o třídě kompatibilní s vaší třídou runtime. Pokud není kompatibilní, `ReadClass` vyvolá [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Vaše třída runtime musí používat [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v `ReadClass` opačném případě vyvolá [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pokud *pSchema* je NULL, schéma uložené třídy lze načíst voláním [CArchive::GetObjectSchema](#getobjectschema); <strong>\*</strong>jinak *pSchema* bude obsahovat schéma run-time třídy, která byla dříve uložena.

Můžete použít [SerializeClass](#serializeclass) `ReadClass`místo , který zpracovává čtení i zápis odkazu na třídu.

### <a name="example"></a>Příklad

  Viz příklad pro [CArchive::WriteClass](#writeclass).

## <a name="carchivereadobject"></a><a name="readobject"></a>CArchive::ReadObject

Přečte data objektu z archivu a vytvoří objekt příslušného typu.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>Parametry

*pClass*<br/>
Konstantní ukazatel na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktury, která odpovídá objektu, který očekáváte číst.

### <a name="return-value"></a>Návratová hodnota

A [CObject](../../mfc/reference/cobject-class.md) ukazatel, který musí být bezpečně přetypována na správnou odvozenou třídu pomocí [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof).

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle `CArchive` volána operátorem extrakce ( **>>**) přetíženým pro ukazatel [CObject.](../../mfc/reference/cobject-class.md) `ReadObject`, podle pořadí, `Serialize` volá funkci archivované třídy.

Pokud zadáte parametr *pClass* nenulový, který získá [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) makro, pak funkce ověří třídu run-time archivovaného objektu. To předpokládá, že jste použili makro IMPLEMENT_SERIAL při implementaci třídy.

### <a name="example"></a>Příklad

  Viz příklad pro [CArchive::WriteObject](#writeobject).

## <a name="carchivereadstring"></a><a name="readstring"></a>CArchive::Řetězec čtení

Volání této členské funkce pro čtení textových dat `CArchive` do vyrovnávací paměti ze souboru přidruženého k objektu.

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>Parametry

*rString*<br/>
Odkaz na [CString,](../../atl-mfc-shared/reference/cstringt-class.md) který bude obsahovat výsledný řetězec po čtení ze souboru přidruženého k objektu CArchive.

*lpsz*<br/>
Určuje ukazatel myši na vyrovnávací paměť dodanou uživatelem, která obdrží textový řetězec ukončený nulou.

*nMax*<br/>
Určuje maximální počet znaků ke čtení. By měla být menší než velikost vyrovnávací paměti *lpsz.*

### <a name="return-value"></a>Návratová hodnota

Ve verzi, která vrací BOOL, TRUE v případě úspěchu; FALSE jinak.

Ve verzi, která `LPTSTR`vrací , ukazatel na vyrovnávací paměť obsahující textová data; NULL, pokud bylo dosaženo konce souboru.

### <a name="remarks"></a>Poznámky

Ve verzi členské funkce s parametrem *nMax* bude vyrovnávací paměť držet až limit *nMax* - 1 znaků. Čtení je zastaveno dvojicí posuvu návratu vozíku. Koncové znaky nového řádku jsou vždy odebrány. V obou případech je připojen znak null (\0).

[CArchive::Read](#read) je také k dispozici pro vstup v textovém režimu, ale nekončí na dvojici přísunu řádku vozíku.

### <a name="example"></a>Příklad

  Viz příklad pro [CArchive::WriteString](#writestring).

## <a name="carchiveserializeclass"></a><a name="serializeclass"></a>CArchive::SerializeClass

Volání této členské funkce, pokud chcete uložit a načíst informace o verzi základní třídy.

```cpp
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Ukazatel na objekt třídy run-time pro základní třídu.

### <a name="remarks"></a>Poznámky

`SerializeClass`přečte nebo zapíše odkaz `CArchive` na třídu na objekt, v závislosti na směru `CArchive`. Místo `SerializeClass` [ReadClass](#readclass) a [WriteClass](#writeclass) jako pohodlný způsob serializace objektů základní třídy; `SerializeClass` vyžaduje méně kódu a méně parametrů.

Stejně jako `ReadClass`ověří, `SerializeClass` zda jsou archivované informace o třídě kompatibilní s vaší třídou runtime. Pokud není kompatibilní, `SerializeClass` vyvolá [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Vaše třída runtime musí používat [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v `SerializeClass` opačném případě vyvolá [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Pomocí [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) makra načtěte hodnotu parametru *pRuntimeClass.* Základní třída musí používat [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) makro.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

## <a name="carchivesetloadparams"></a><a name="setloadparams"></a>CArchive::SetLoadParams

Volání, `SetLoadParams` když budete číst velký `CObject`počet odvozených objektů z archivu.

```cpp
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>Parametry

*nGrowBy*<br/>
Minimální počet slotů element udělit, pokud je nutné zvýšení velikosti.

### <a name="remarks"></a>Poznámky

`CArchive`používá načítací pole k překladu odkazů na objekty uložené v archivu. `SetLoadParams`umožňuje nastavit velikost, na kterou se zvětšuje pole zatížení.

Nesmíte volat `SetLoadParams` po načtení žádného objektu nebo po volání [MapObject](#mapobject) nebo [ReadObject.](#readobject)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivesetobjectschema"></a><a name="setobjectschema"></a>CArchive::SetObjectSchema

Volánítéto členské funkce nastavte schéma objektu uložené v objektu archivu na *nSchema*.

```cpp
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>Parametry

*nSchema*<br/>
Určuje schéma objektu.

### <a name="remarks"></a>Poznámky

Další volání [GetObjectSchema](#getobjectschema) vrátí hodnotu uloženou v *nSchema*.

Používá `SetObjectSchema` se pro pokročilou správu verzí; například pokud chcete vynutit konkrétní verzi číst `Serialize` ve funkci odvozené třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

## <a name="carchivesetstoreparams"></a><a name="setstoreparams"></a>CArchive::SetStoreParams

Používá `SetStoreParams` se při ukládání velkého `CObject`počtu odvozených objektů do archivu.

```cpp
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>Parametry

*nHashVelikost*<br/>
Velikost tabulky hash pro mapy ukazatele rozhraní. Mělo by to být prvočíslo.

*nBlockSize*<br/>
Určuje rozlišovací schopnost přidělení paměti pro rozšíření parametrů. By měl být výkon 2 pro nejlepší výkon.

### <a name="remarks"></a>Poznámky

`SetStoreParams`umožňuje nastavit velikost tabulky hash a velikost bloku mapy použité k identifikaci jedinečných objektů během procesu serializace.

Nesmíte volat `SetStoreParams` po uložení objektů nebo po [volání MapObject](#mapobject) nebo [WriteObject.](#writeobject)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivewrite"></a><a name="write"></a>CArchiv::Zápis

Zapíše do archivu zadaný počet bajtů.

```cpp
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na uživatelem zadanou vyrovnávací paměť, která obsahuje data, která mají být zapsána do archivu.

*nMax*<br/>
Celé číslo, které určuje počet bajtů, které mají být zapsány do archivu.

### <a name="remarks"></a>Poznámky

Archiv neformátuje bajty.

Členská `Write` funkce v rámci `Serialize` funkce můžete psát běžné struktury, které jsou obsaženy v objektech.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

## <a name="carchivewriteclass"></a><a name="writeclass"></a>CArchive::WriteClass

Slouží `WriteClass` k uložení informací o verzi a třídě základní třídy během serializace odvozené třídy.

```cpp
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>Parametry

*pClassRef*<br/>
Ukazatel na strukturu [CRuntimeClass,](../../mfc/reference/cruntimeclass-structure.md) která odpovídá požadovanému odkazu na třídu.

### <a name="remarks"></a>Poznámky

`WriteClass`zapíše odkaz na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pro základní `CArchive`třídu na . Použijte [CArchive::ReadClass](#readclass) k načtení odkazu.

`WriteClass`ověří, zda jsou archivované informace o třídě kompatibilní s vaší třídou runtime. Pokud není kompatibilní, `WriteClass` vyvolá [CArchiveException](../../mfc/reference/carchiveexception-class.md).

Vaše třída runtime musí používat [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); v `WriteClass` opačném případě vyvolá [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Můžete použít [SerializeClass](#serializeclass) `WriteClass`místo , který zpracovává čtení i zápis odkazu na třídu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

## <a name="carchivewriteobject"></a><a name="writeobject"></a>CArchive::WriteObject

Zadaný `CObject` soubor ukládá do archivu.

```cpp
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>Parametry

*Pob*<br/>
Konstantní ukazatel na objekt, který je uložen.

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle `CArchive` volána **<<** operátorem insertion ( ) přetíženým pro `CObject`. `WriteObject`, podle pořadí, `Serialize` volá funkci archivované třídy.

K povolení archivace je nutné použít IMPLEMENT_SERIAL makro. `WriteObject`zapíše název třídy ASCII do archivu. Tento název třídy je ověřen později během procesu načítání. Speciální schéma kódování zabraňuje zbytečnému duplikaci názvu třídy pro více objektů třídy. Toto schéma také zabraňuje redundantní ukládání objektů, které jsou cíle více než jeden ukazatel.

Metoda přesného kódování objektů (včetně přítomnosti názvu třídy ASCII) je podrobností implementace a může se změnit v budoucích verzích knihovny.

> [!NOTE]
> Než začnete vytvářet, spouštět a aktualizovat všechny objekty, dokončete jejich vytváření, odstranění a aktualizaci. Archiv bude poškozen, pokud smícháte archivaci s úpravou objektu.

### <a name="example"></a>Příklad

Definice třídy `CAge`naleznete v příkladu [pro CObList::CObList](../../mfc/reference/coblist-class.md#coblist).

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

## <a name="carchivewritestring"></a><a name="writestring"></a>CArchive::Řetězec zápisu

Tato členská funkce slouží k zápisu dat `CArchive` z vyrovnávací paměti do souboru přidruženého k objektu.

```cpp
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Určuje ukazatel na vyrovnávací paměť obsahující textový řetězec s nulovým ukončem.

### <a name="remarks"></a>Poznámky

Ukončující znak null (\0') není zapsán do souboru; ani se automaticky nepíše nový řádek.

`WriteString`vyvolá výjimku v reakci na několik podmínek, včetně podmínky úplné ho disku.

`Write`je také k dispozici, ale místo ukončení na znak null, zapíše požadovaný počet bajtů do souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[CSocket – třída](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
