---
title: "CArchive – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9cc94e78656c53156b8696b927780f46e939861a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="carchive-class"></a>CArchive – třída
Umožňuje uložit nejsložitějších sítí objektů v trvalé binárního formátu (obvykle úložiště disku), která je uchována po odstranění těchto objektů.  
  
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
|[CArchive::Abort](#abort)|Zavře archivu bez způsobení výjimky.|  
|[CArchive::Close](#close)|Počet vyprázdnění unwritten data a odpojí od `CFile`.|  
|[CArchive::Flush](#flush)|Vyprázdnění unwritten data z archivu vyrovnávací paměti.|  
|[CArchive::GetFile](#getfile)|Získá `CFile` ukazatele na objekt pro archivu.|  
|[CArchive::GetObjectSchema](#getobjectschema)|Volání z `Serialize` funkce určení verze objektu, který je deserializován.|  
|[CArchive::IsBufferEmpty](#isbufferempty)|Určuje, zda vyrovnávací paměť vyprázdnění během Windows Sockets přijímat procesu.|  
|[CArchive::IsLoading](#isloading)|Určuje, zda je načítání archivu.|  
|[CArchive::IsStoring](#isstoring)|Určuje, zda je ukládání do archivu.|  
|[CArchive::MapObject](#mapobject)|Umístí mapu, která nejsou serializované k souboru, ale které jsou k dispozici pro podobjektů, pro které chcete-li objekty.|  
|[CArchive::Read](#read)|Přečte nezpracovaná bajtů.|  
|[CArchive::ReadClass](#readclass)|Čtení odkazu na třídu dříve uložené s `WriteClass`.|  
|[CArchive::ReadObject](#readobject)|Volání objektu `Serialize` funkce pro načtení.|  
|[CArchive::ReadString](#readstring)|Přečte jeden řádek textu.|  
|[CArchive::SerializeClass](#serializeclass)|Čtení nebo zápisu odkazu na `CArchive` objekt v závislosti na směru `CArchive`.|  
|[CArchive::SetLoadParams](#setloadparams)|Nastaví velikost, do které zvětšování pole zatížení. Musí být voláno před načtením libovolného objektu nebo před `MapObject` nebo `ReadObject` je volána.|  
|[CArchive::SetObjectSchema](#setobjectschema)|Nastaví objekt schématu uložené v objektu archivu.|  
|[CArchive::SetStoreParams](#setstoreparams)|Nastaví velikost tabulky hash a velikost bloku mapy použije k identifikaci objektů jedinečný během serializace.|  
|[CArchive::Write](#write)|Zapíše nezpracovaná bajtů.|  
|[CArchive::WriteClass](#writeclass)|Zapíše odkaz na `CRuntimeClass` k `CArchive`.|  
|[CArchive::WriteObject](#writeobject)|Volání objektu `Serialize` funkce pro ukládání.|  
|[CArchive::WriteString](#writestring)|Zapíše na jednom řádku textu.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CArchive::operator&lt;&lt;](#operator_lt_lt)|Ukládá objekty a primitivní typy do archivu.|  
|[CArchive::operator&gt;&gt;](#operator_gt_gt)|Načte z archivu objekty a primitivní typy.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CArchive::m_pDocument](#m_pdocument)||  
  
## <a name="remarks"></a>Poznámky  
 `CArchive`nemá základní třídu.  
  
 Objekty můžete později načíst z trvalého úložiště, je rekonstrukce v paměti. Tento proces převedení dat trvalé se nazývá "serializace."  
  
 Si můžete představit jako druh binárního datového proudu objektu archivu. Jako vstupně výstupní datový proud archivu je přiřazen k souboru a umožňuje ve vyrovnávací paměti zápis a čtení dat do a z úložiště. Vstupní/výstupní proud zpracovává posloupnosti znaků ASCII, ale archiv zpracovává data binární objekt ve formátu efektivní, nonredundant.  
  
 Musíte vytvořit [cfile –](../../mfc/reference/cfile-class.md) objektu před vytvořením `CArchive` objektu. Kromě toho musíte zajistit, že stav zatížení nebo úložiště do archivu je kompatibilní s režim otevření souboru. Jste omezeni na jednu aktivní archivu na soubor.  
  
 Když vytvoříte `CArchive` objektu, připojte ji k aktualizaci objektu třídy `CFile` (nebo odvozené třídy), která představuje soubor otevřený. Můžete také určit, zda archivu se použije pro načítání nebo ukládání. A `CArchive` objekt může zpracovat pouze primitivní typy, ale také objekty [CObject](../../mfc/reference/cobject-class.md)-odvozených tříd pro serializaci. Serializovatelné třídy má obvykle `Serialize` – členská funkce a obvykle používá [declare_serial –](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [implement_serial –](../../mfc/reference/run-time-object-model-services.md#implement_serial) makra, jak je popsáno v části třídy `CObject`.  
  
 Přetížené extrakce (  **>>** ) a vkládání (  **<<** ) operátory jsou vhodné archivu programovací rozhraní, které podporují i primitivní typy a `CObject` -odvozených třídách.  
  
 `CArchive`také podporuje programování pomocí třídy MFC Windows Sockets [CSocket](../../mfc/reference/csocket-class.md) a [CSocketFile](../../mfc/reference/csocketfile-class.md). [IsBufferEmpty](#isbufferempty) – členská funkce podporuje toto využití.  
  
 Další informace o `CArchive`, najdete v článcích [serializace](../../mfc/serialization-in-mfc.md) a [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CArchive`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="abort"></a>CArchive::Abort  
 Volání této funkce zavřete archivu bez způsobení výjimky.  
  
```  
void Abort ();
```  
  
### <a name="remarks"></a>Poznámky  
 **CArchive** destruktor normálně zavolá **Zavřít**, který se vyprázdní žádná data, která dosud nebyla uložena s příslušnými `CFile` objektu. To může způsobit výjimky.  
  
 Při zachytávání tyto výjimky, je vhodné použít **Abort**tak, aby destructing `CArchive` objekt nezpůsobí další výjimky. Při zpracování výjimek, `CArchive::Abort` nebude vyvolat výjimku o selhání, protože se na rozdíl od [CArchive::Close](#close), **Abort** ignoruje selhání.  
  
 Pokud jste použili **nové** přidělit `CArchive` objektu v haldě, pak je nutné odstranit po zavření souboru.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CArchive::WriteClass](#writeclass).  
  
##  <a name="carchive"></a>CArchive::CArchive  
 Vytvoří `CArchive` objektu a určuje, zda bude použit pro načítání nebo ukládání objektů.  
  
```  
CArchive(
    CFile* pFile,  
    UINT nMode,  
    int nBufSize = 4096,  
    void* lpBuf = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pFile`  
 Ukazatel `CFile` objekt, který je ultimate zdroji nebo cíli trvalá data.  
  
 `nMode`  
 Příznak, který určuje, zda se objekty načtené ze nebo uložit do archivu. `nMode` Parametr musí mít jednu z následujících hodnot:  
  
- **CArchive::load** načte data z archivu. Vyžaduje pouze `CFile` oprávnění ke čtení.  
  
- **CArchive::store** uloží data do archivu. Vyžaduje `CFile` oprávnění k zápisu.  
  
- **CArchive::bNoFlushOnDelete** brání archivu automaticky volání `Flush` kdy se nazývá destruktor archivu. Pokud nastavíte tento příznak, jste odpovědni za explicitně volání **Zavřít** předtím, než se nazývá destruktoru. Pokud ho použít nechcete, bude vaše data poškozena.  
  
 `nBufSize`  
 Celé číslo, které určuje velikost vyrovnávací paměti interní souboru v bajtech. Všimněte si, že výchozí velikost vyrovnávací paměti je 4 096 bajtů. Pokud pravidelně archivujete rozsáhlé objekty, umožní zvýšení výkonu, pokud používáte větší velikost vyrovnávací paměti, které je násobkem velikost vyrovnávací paměti souboru.  
  
 `lpBuf`  
 Volitelným ukazatelem uživatelem zadané vyrovnávací paměti o velikosti `nBufSize`. Pokud tento parametr nezadáte, archivu přiděluje vyrovnávací paměť z lokální haldy a uvolní ji při objekt zničena. Archiv neuvolní uživatelem zadané vyrovnávací paměti.  
  
### <a name="remarks"></a>Poznámky  
 Toto nastavení nemohou změnit po vytvoření archivu.  
  
 Nesmíte používat `CFile` operations ke změně stavu souboru, zavřete archivu. Všechny tyto operace bude dojít k poškození integrity archivu. Může získat přístup k umístění ukazatele souboru kdykoli během serializace získáním objektu soubor do archivu z [GetFile](#getfile) – členská funkce a potom pomocí [CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition) – funkce . By měly volat [CArchive::Flush](#flush) před získání pozici ukazatele souboru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]  
  
##  <a name="close"></a>CArchive::Close  
 Vyprázdnění veškerá data ve vyrovnávací paměti, zavře archivu a odpojení ze souboru do archivu.  
  
```  
void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Nejsou povolené žádné další operace v archivu. Po ukončení archiv, můžete vytvořit další archivu u stejného souboru nebo můžete zavřít soubor.  
  
 Členská funkce **Zavřít** zajistí, že všechna data se přenáší z archivu do souboru, a umožňuje archivu není k dispozici. K dokončení přenosu ze souboru na úložné médium, musíte nejprve použít [CFile::Close](../../mfc/reference/cfile-class.md#close) a pak odstraňte `CFile` objektu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CArchive::WriteString](#writestring).  
  
##  <a name="flush"></a>CArchive::Flush  
 Vynutí veškerá data ve vyrovnávací paměti archivu má být zapsán do souboru.  
  
```  
void Flush();
```  
  
### <a name="remarks"></a>Poznámky  
 Členská funkce `Flush` zajistí, že všechna data se přenáší z archivu do souboru. Je třeba volat [CFile::Close](../../mfc/reference/cfile-class.md#close) k dokončení přenosu ze souboru na úložné médium.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]  
  
##  <a name="getfile"></a>CArchive::GetFile  
 Získá `CFile` ukazatele na objekt pro archivu.  
  
```  
CFile* GetFile() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Konstantní ukazatel `CFile` objekt používá.  
  
### <a name="remarks"></a>Poznámky  
 Musí vyprázdnění archivu před použitím `GetFile`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]  
  
##  <a name="getobjectschema"></a>CArchive::GetObjectSchema  
 Volání této funkce z `Serialize` funkce určení verze objektu, který je aktuálně deserializován.  
  
```  
UINT GetObjectSchema();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Během deserializace, verze objektu, který je čten.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce je platná pouze když `CArchive` objektu je právě načítán ( [CArchive::IsLoading](#isloading) vrátí nenulovou hodnotu). By mělo být prvním volání v `Serialize` funkce a zavolat pouze jednou. Vrácená hodnota ( **Celé_číslo**) -1 označuje, že číslo verze neznámý.  
  
 A `CObject`-odvozené třídy mohou používat **versionable_schema –** kombinaci (pomocí bitový `OR`) s verzí schématu sám sebe (v `IMPLEMENT_SERIAL` makro) k vytvoření "verzování objektu," tedy objekt jehož `Serialize` – členská funkce může číst několik verzí. Výchozí funkce framework (bez **versionable_schema –**), je vyvolána výjimka, pokud je neodpovídající verze.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]  
  
##  <a name="isbufferempty"></a>CArchive::IsBufferEmpty  
 Volání této funkce člen k určení, zda objekt archivu vnitřní vyrovnávací paměť je prázdná.  
  
```  
BOOL IsBufferEmpty() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud do archivu vyrovnávací paměť je prázdná. jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce poskytuje pro podporu programování pomocí třídy MFC Windows Sockets `CSocketFile`. Není potřeba ho použít pro archiv přidružené `CFile` objektu.  
  
 Důvod použití `IsBufferEmpty` s archiv přidružené `CSocketFile` objekt je, že vyrovnávací paměti do archivu může obsahovat více zpráv nebo záznam. Po přijetí jednu zprávu, měli byste použít `IsBufferEmpty` k řízení smyčku, který se bude s příjmem dat, dokud vyrovnávací paměť je prázdná. Další informace najdete v tématu [Receive](../../mfc/reference/casyncsocket-class.md#receive) funkce člena třídy `CAsyncSocket`, který ukazuje způsob použití `IsBufferEmpty`.  
  
 Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="isloading"></a>CArchive::IsLoading  
 Určuje, zda archivu načítá data.  
  
```  
BOOL IsLoading() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud archivu je právě používán pro načítání; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je volána `Serialize` funkce archivovaný tříd.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]  
  
##  <a name="isstoring"></a>CArchive::IsStoring  
 Určuje, zda archivu ukládá data.  
  
```  
BOOL IsStoring() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud archivu se aktuálně používá pro ukládání; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tento člen funkce je volána `Serialize` funkce archivovaný tříd.  
  
 Pokud `IsStoring` stav archivu je nenulové hodnoty, potom jeho `IsLoading` stav je 0 a naopak.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]  
  
##  <a name="mapobject"></a>CArchive::MapObject  
 Volání této funkce člen umístit objekty mapu, která nejsou serializované skutečně k souboru, ale které jsou pro podobjektů, pro které chcete-li k dispozici.  
  
```  
void MapObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>Parametry  
 `pOb`  
 Konstantní ukazatel na objekt uložené.  
  
### <a name="remarks"></a>Poznámky  
 Například nemusí serializovat dokumentu, ale by serializovat položky, které jsou součástí dokumentu. Při volání `MapObject`, můžete povolit tyto položky nebo podobjektů, chcete-li dokumentu. Navíc může serializovat serializovaných podřízených položek jejich `m_pDocument` zpětný ukazatel.  
  
 Můžete volat `MapObject` při ukládání do a z načíst `CArchive` objektu. `MapObject`Přidá zadaný objekt do interních datových strukturách udržované `CArchive` objektu během serializace a deserializace, ale na rozdíl od [se operace ReadObject](#readobject) a [operace WriteObject](#writeobject) **,** nevolá serializaci objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]  
  
 [!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]  
  
 [!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]  
  
 [!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]  
  
##  <a name="m_pdocument"></a>CArchive::m_pDocument  
 Nastavte na **NULL** ve výchozím nastavení tento ukazatel na **CDocument** může být nastaven na nic uživatel `CArchive` instance chce.  
  
```  
CDocument* m_pDocument;  
```  
  
### <a name="remarks"></a>Poznámky  
 Běžné použití tento ukazatel je nesou Další informace o procesu serializace pro všechny objekty serializována. Toho se dosáhne inicializace ukazatel pomocí dokumentu ( **CDocument**-odvozené třídy), je serializována, tak, že objekty v tomto dokumentu získat k dokumentu přístup v případě potřeby. Tento ukazatel je také používány `COleClientItem` objekty během serializace.  
  
 Nastaví framework `m_pDocument` v dokumentu se serializovat, když uživatel problémy soubor otevřít nebo uložit příkaz. Pokud jste serializovat kontejneru dokument propojování a vkládání (OLE) z důvodů než soubor otevřít nebo uložit, je nutné explicitně nastavit `m_pDocument`. Například by to uděláte při serializaci dokumentu kontejneru do schránky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]  
  
##  <a name="operator_lt_lt"></a>CArchive::operator&lt;&lt;  
 Ukládá uvedené objekt nebo primitivní typ do archivu.  
  
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
 A `CArchive` odkaz, který umožňuje více operátorů insertion na jeden řádek.  
  
### <a name="remarks"></a>Poznámky  
 Poslední dvě verze výše jsou speciálně určené pro ukládání 64bitových celých čísel.  
  
 Pokud jste použili `IMPLEMENT_SERIAL` makro v implementaci třídy a pak operátor vložení přetížený pro `CObject` volá chráněného **operace WriteObject**. Tato funkce se pak zavolá `Serialize` funkce třídy.  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) operátor vložení (<<) podporuje diagnostiku vypsání a ukládání do archivu.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje použití `CArchive` operátor vložení << s `int` a `long` typy.  
  
 [!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]  
  
### <a name="example"></a>Příklad  
 Příklad 2 ukazuje použití `CArchive` operátor vložení << s `CStringT` typu.  
  
 [!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]  
  
##  <a name="operator_gt_gt"></a>CArchive::operator&gt;&gt;  
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
 A `CArchive` odkaz, který umožňuje více operátorů extrakce na jeden řádek.  
  
### <a name="remarks"></a>Poznámky  
 Poslední dvě verze výše jsou speciálně určené pro načítání 64bitových celých čísel.  
  
 Pokud jste použili `IMPLEMENT_SERIAL` makro v implementaci třídy a pak operátorů extrakce přetížený pro `CObject` volání chráněného **se operace ReadObject** – funkce (s nenulovou run-time třída ukazatel). Tato funkce se pak zavolá `Serialize` funkce třídy.  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md) extrakce – operátor (>>) podporuje načítání z archivu.  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje použití `CArchive` extrakce operátor >> s `int` typu.  
  
 [!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]  
  
### <a name="example"></a>Příklad  
 Tento příklad ukazuje použití `CArchive` vložení a extrakce operátory <\< a >> s `CStringT` typu.  
  
 [!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]  
  
##  <a name="read"></a>CArchive::Read  
 Přečte zadaný počet bajtů z archivu.  
  
```  
UINT Read(void* lpBuf, UINT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Ukazatel na uživatelem zadané vyrovnávací paměť, která se zobrazí data načtená z archivu.  
  
 `nMax`  
 Celé číslo bez znaménka určující počet Bajty čtení z archivu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nepodepsanou celočíselnou hodnotu obsahující číslo ve skutečnosti přečtených bajtů. Pokud návratová hodnota je menší než požadovaný, bylo dosaženo konce souboru. Nedojde k výjimce na podmínky end souboru.  
  
### <a name="remarks"></a>Poznámky  
 Archiv neinterpretuje bajtů.  
  
 Můžete použít **čtení** – členská funkce v rámci vaší `Serialize` funkce pro čtení obyčejnou struktury, které jsou součástí vašich objektů.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]  
  
##  <a name="readclass"></a>CArchive::ReadClass  
 Volání této funkce člen načíst odkaz na třídu dříve uložené s [WriteClass](#writeclass).  
  
```  
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,  
    UINT* pSchema = NULL,  
    DWORD* pObTag = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pClassRefRequested`  
 Ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura, která odpovídá referenci třídy požadovaný. Může být **NULL**.  
  
 `pSchema`  
 Ukazatel na schéma run-time třída dříve uložené.  
  
 `pObTag`  
 Číslo, které odkazuje na objektu jedinečné značky. Používaná interně k provádění [se operace ReadObject](#readobject). Vystavený pro pokročilé programování pouze; `pObTag` za normálních okolností by měla být **NULL**.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura.  
  
### <a name="remarks"></a>Poznámky  
 Pokud `pClassRefRequested` není **NULL**, `ReadClass` ověřuje, že informace o archivovaném třídě je kompatibilní s vaší třídy modulu runtime. Pokud není kompatibilní, `ReadClass` vyvolá výjimku [CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Musí používat vlastní třídy runtime [declare_serial –](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [implement_serial –](../../mfc/reference/run-time-object-model-services.md#implement_serial), jinak hodnota `ReadClass` vyvolá výjimku [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Pokud `pSchema` je **NULL**, může načíst schéma uložené třídy volání [CArchive::GetObjectSchema](#getobjectschema), jinak hodnota  **\***  `pSchema`bude obsahovat schéma run-time třída, která byla dříve uložená.  
  
 Můžete použít [SerializeClass](#serializeclass) místo `ReadClass`, která zpracovává čtení i zápis odkazu na třídu.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CArchive::WriteClass](#writeclass).  
  
##  <a name="readobject"></a>CArchive::ReadObject  
 Přečte objekt data z archivu a vytvoří objekt příslušného typu.  
  
```  
CObject* ReadObject(const CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>Parametry  
 `pClass`  
 Konstantní ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura, která odpovídá objektu očekávají čtení.  
  
### <a name="return-value"></a>Návratová hodnota  
 A [CObject](../../mfc/reference/cobject-class.md) ukazatele, který je možné bezpečně přetypovat na správnou odvozené třídy pomocí [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof).  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána normálně `CArchive` extrakce (  **>>** ) operátor přetížený pro [CObject](../../mfc/reference/cobject-class.md) ukazatel. **Se operace ReadObject**, pak zavolá `Serialize` funkce archivovaný třídy.  
  
 Pokud zadáte nenulové hodnoty `pClass` parametr, který byl získán [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) makro, pak funkce ověřuje run-time třída archivovaný objektu. Toto předpokládá, že jste použili `IMPLEMENT_SERIAL` makro k implementaci třídy.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CArchive::WriteObject](#writeobject).  
  
##  <a name="readstring"></a>CArchive::ReadString  
 Volání této funkce člen číst data textu do vyrovnávací paměti ze souboru přidružené `CArchive` objektu.  
  
```  
BOOL ReadString(CString& rString); 
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `rString`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) po je pro čtení ze souboru přidružená k objektu CArchive, která bude obsahovat výsledný řetězec.  
  
 `lpsz`  
 Určuje ukazatel uživatelem zadané vyrovnávací paměť, která bude přijímat ukončené hodnotou null textový řetězec.  
  
 `nMax`  
 Určuje maximální počet znaků ke čtení. By měl mít hodnotu menší než velikost *lpsz* vyrovnávací paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ve verzi, která vrací **BOOL**, **TRUE** v případě úspěšného; **FALSE** jinak.  
  
 Ve verzi, která vrací `LPTSTR`, ukazatel do vyrovnávací paměti obsahující textová data; **NULL** Pokud bylo dosaženo end souboru.  
  
### <a name="remarks"></a>Poznámky  
 V této verzi členská funkce s `nMax` parametr vyrovnávací paměti bude obsahovat do maximální počet `nMax` – 1 znaků. Čtení je zastavena pár znaků CR vrátit-konce řádku. Koncové znaky nového řádku jsou vždy odebrat. V obou případech se připojí znak hodnoty null ('\0').  
  
 [CArchive::Read](#read) je k dispozici také pro režim textové vstupu, ale nezavře na pár znaků CR vrátit-konce řádku.  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro [CArchive::WriteString](#writestring).  
  
##  <a name="serializeclass"></a>CArchive::SerializeClass  
 Volání této funkce člen, pokud chcete uložit a načíst informace o verzi základní třídy.  
  
```  
void SerializeClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>Parametry  
 `pClassRef`  
 Ukazatel na objekt run-time třída pro základní třídy.  
  
### <a name="remarks"></a>Poznámky  
 `SerializeClass`čtení nebo zápisu odkazu na třídu k `CArchive` objekt, v závislosti na směru `CArchive`. Použití `SerializeClass` místě [ReadClass](#readclass) a [WriteClass](#writeclass) jako pohodlný způsob, jak serializovat objekty základní třídy; `SerializeClass` vyžaduje méně kódu a méně parametry.  
  
 Jako `ReadClass`, `SerializeClass` ověřuje, že informace o archivovaném třídě je kompatibilní s vaší třídy modulu runtime. Pokud není kompatibilní, `SerializeClass` vyvolá výjimku [CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Musí používat vlastní třídy runtime [declare_serial –](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [implement_serial –](../../mfc/reference/run-time-object-model-services.md#implement_serial), jinak hodnota `SerializeClass` vyvolá výjimku [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Použití [RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) makro k načtení hodnoty pro `pRuntimeClass` parametr. Základní třída musí mít používá [implement_serial –](../../mfc/reference/run-time-object-model-services.md#implement_serial) makro.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]  
  
##  <a name="setloadparams"></a>CArchive::SetLoadParams  
 Volání `SetLoadParams` když chcete číst velký počet `CObject`-odvozené objekty z archivu.  
  
```  
void SetLoadParams(UINT nGrowBy = 1024);
```  
  
### <a name="parameters"></a>Parametry  
 `nGrowBy`  
 Minimální počet element sloty přidělit, pokud je nutné zvýšit velikost.  
  
### <a name="remarks"></a>Poznámky  
 `CArchive`používá zatížení pole odkazy na objekty uložené v archivu. `SetLoadParams`Umožňuje nastavit velikost, do které zvětšování pole zatížení.  
  
 Nelze volat `SetLoadParams` po načtení všech objektů, nebo po [MapObject](#mapobject) nebo [se operace ReadObject](#readobject) je volána.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="setobjectschema"></a>CArchive::SetObjectSchema  
 Volání této funkce člena pro nastavení uložená v objektu archivu do schématu objektu `nSchema`.  
  
```  
void SetObjectSchema(UINT nSchema);
```  
  
### <a name="parameters"></a>Parametry  
 `nSchema`  
 Určuje schéma objektu.  
  
### <a name="remarks"></a>Poznámky  
 Další volání [GetObjectSchema](#getobjectschema) vrátí s hodnotou uloženou v `nSchema`.  
  
 Použití `SetObjectSchema` pro pokročilé správy verzí; například pokud chcete vynutit na konkrétní verzi čtení v `Serialize` funkce odvozené třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]  
  
##  <a name="setstoreparams"></a>CArchive::SetStoreParams  
 Použití `SetStoreParams` při ukládání velkého počtu `CObject`-odvozené objekty v rámci archivu.  
  
```  
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```  
  
### <a name="parameters"></a>Parametry  
 *nHashSize*  
 Mapuje velikost tabulku hash pro ukazatel rozhraní. Musí být číslo prime.  
  
 `nBlockSize`  
 Určuje členitost přidělení paměti pro rozšíření parametry. Musí být násobkem 2 pro nejlepší výkon.  
  
### <a name="remarks"></a>Poznámky  
 `SetStoreParams`Umožňuje nastavit velikost tabulky hash a velikost bloku mapy použije k identifikaci objektů jedinečný během serializace.  
  
 Nelze volat `SetStoreParams` se ukládají všechny objekty, nebo po [MapObject](#mapobject) nebo [operace WriteObject](#writeobject) je volána.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="write"></a>CArchive::Write  
 Zapíše zadaný počet bajtů do archivu.  
  
```  
void Write(const void* lpBuf, INT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Ukazatel do vyrovnávací paměti zadanou uživatelem, který obsahuje data, která mají být zapsána do archivu.  
  
 `nMax`  
 Celé číslo, které určuje počet bajtů, které mají být zapsána do archivu.  
  
### <a name="remarks"></a>Poznámky  
 Do archivu není formátu bajtů.  
  
 Můžete použít **zápisu** – členská funkce v rámci vaší `Serialize` funkce zápis běžném provozu struktur, které jsou součástí vašich objektů.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]  
  
##  <a name="writeclass"></a>CArchive::WriteClass  
 Použití `WriteClass` ukládat informace o verzi a třídy základní třídy během serializace odvozené třídy.  
  
```  
void WriteClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>Parametry  
 `pClassRef`  
 Ukazatel [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) struktura, která odpovídá referenci třídy požadovaný.  
  
### <a name="remarks"></a>Poznámky  
 `WriteClass`zapíše odkaz na [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) pro základní třídu pro `CArchive`. Použití [CArchive::ReadClass](#readclass) k načtení odkazu.  
  
 `WriteClass`ověřuje, že informace o archivovaném třídě je kompatibilní s vaší třídy modulu runtime. Pokud není kompatibilní, `WriteClass` vyvolá výjimku [CArchiveException](../../mfc/reference/carchiveexception-class.md).  
  
 Musí používat vlastní třídy runtime [declare_serial –](../../mfc/reference/run-time-object-model-services.md#declare_serial) a [implement_serial –](../../mfc/reference/run-time-object-model-services.md#implement_serial), jinak hodnota `WriteClass` vyvolá výjimku [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Můžete použít [SerializeClass](#serializeclass) místo `WriteClass`, která zpracovává čtení i zápis odkazu na třídu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]  
  
##  <a name="writeobject"></a>CArchive::WriteObject  
 Uloží zadaný `CObject` do archivu.  
  
```  
void WriteObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>Parametry  
 `pOb`  
 Konstantní ukazatel na objekt uložené.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána normálně `CArchive` vložení (  **<<** ) operátor přetížený pro `CObject`. **Operace WriteObject**, pak zavolá `Serialize` funkce archivovaný třídy.  
  
 Je nutné použít `IMPLEMENT_SERIAL` makro povolení archivace. **Operace WriteObject** zapíše název třídy ASCII do archivu. Tento název třídy je ověřen později v průběhu procesu načítání. Speciální schéma kódování zabráníte zdvojení název třídy pro více objektů třídy. Toto schéma rovněž zamezí redundantní úložiště objektů, které jsou cílem více než jeden ukazatele.  
  
 Přesný objekt encoding – metoda (včetně přítomnost název třídy ASCII) podrobností implementace a změnit v budoucích verzích knihovny.  
  
> [!NOTE]
>  Dokončete vytváření, odstraňování a aktualizaci všech objektů, než začnete archivovat je. Pokud kombinujete archivace s úpravy objektu vašem archivu poškozen.  
  
### <a name="example"></a>Příklad  
 Pro definici třídy `CAge`, podívejte se na příklad pro [CObList::CObList](../../mfc/reference/coblist-class.md#coblist).  
  
 [!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]  
  
##  <a name="writestring"></a>CArchive::WriteString  
 Tuto funkci člen použít k zápisu dat z vyrovnávací paměti do souboru přidružené `CArchive` objektu.  
  
```  
void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>Parametry  
 `lpsz`  
 Určuje ukazatel na vyrovnávací paměť obsahující ukončené hodnotou null textového řetězce.  
  
### <a name="remarks"></a>Poznámky  
 Ukončovací znak hodnoty null ('\0') není zapsán do souboru; ani se nový řádek automaticky zapisuje.  
  
 `WriteString`vyvolá výjimku v reakci na několika podmínek, včetně disku úplné podmínku.  
  
 **Zápis** je také k dispozici, ale místo se ukončuje na prázdný znak, zapíše požadovaný počet bajtů k souboru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Cfile – třída](../../mfc/reference/cfile-class.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [CSocket – třída](../../mfc/reference/csocket-class.md)   
 [CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
