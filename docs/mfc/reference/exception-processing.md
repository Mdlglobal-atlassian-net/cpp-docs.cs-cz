---
title: Zpracování výjimek
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: d33da7a9bc81f9733df840a87fbbbeca1e02cc04
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855279"
---
# <a name="exception-processing"></a>Zpracování výjimek

Když se program spustí, může dojít k několika neobvyklým podmínkám a chybám nazývaným "výjimky". To může zahrnovat nedostatek paměti, chyby přidělení prostředků a selhání při hledání souborů.

Knihovna Microsoft Foundation Class používá schéma zpracování výjimek, které je navrženo těsně po tom, co navrhl výbor standardů ANSI pro C++. Před voláním funkce, která může narazit na neobvyklou situaci, musí být nastavená obslužná rutina výjimky. Pokud funkce narazí na neobvyklou podmínku, vyvolá výjimku a ovládací prvek je předán obslužné rutině výjimky.

Několik maker, která jsou součástí knihovna Microsoft Foundation Class, nastaví obslužné rutiny výjimek. Řada dalších globálních funkcí může vyvolat specializované výjimky a v případě potřeby ukončit programy. Tato makra a globální funkce spadají do následujících kategorií:

- Makra výjimek, která strukturují obslužnou rutinu výjimky.

- Funkce vyvolávající výjimku, které generují výjimky určitých typů.

- Ukončení funkcí, což způsobí ukončení programu.

Příklady a další podrobnosti najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Makra výjimek

|||
|-|-|
|[Zkuste](#try)|Určuje blok kódu pro zpracování výjimek.|
|[CATCH](#catch)|Určuje blok kódu pro zachycení výjimky z předchozího **testovaného** bloku.|
|[CATCH_ALL](#catch_all)|Určuje blok kódu pro zachycení všech výjimek z předchozího **testovaného** bloku.|
|[AND_CATCH](#and_catch)|Určuje blok kódu pro zachycení dalších typů výjimek z předchozího **testovaného** bloku.|
|[AND_CATCH_ALL](#and_catch_all)|Určuje blok kódu pro zachycení všech dalších typů výjimek vyvolaných v předchozím bloku **Try** .|
|[END_CATCH](#end_catch)|Ukončí poslední blok **catch** nebo **AND_CATCHho** bloku kódu.|
|[END_CATCH_ALL](#end_catch_all)|Ukončí poslední blok kódu **CATCH_ALL** .|
|[VYVOLÁ](#throw)|Vyvolá určenou výjimku.|
|[THROW_LAST](#throw_last)|Vyvolá Aktuálně zpracovávanou výjimku z další vnější obslužné rutiny.|

### <a name="exception-throwing-functions"></a>Výjimky – vyvolání funkcí

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Vyvolá výjimku archivu.|
|[AfxThrowFileException](#afxthrowfileexception)|Vyvolá výjimku souboru.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Vyvolá výjimku neplatného argumentu.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Vyvolá výjimku paměti.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Vyvolá výjimku, která není podporována.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Vyvolá výjimku Windows prostředku-Nenalezeno.|
|[AfxThrowUserException](#afxthrowuserexception)|Vyvolá výjimku v akci programu iniciované uživatelem.|

Knihovna MFC poskytuje dvě funkce pro vyvolání výjimek specificky pro výjimky OLE:

### <a name="ole-exception-functions"></a>Funkce výjimek OLE

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Vyvolá výjimku v rámci funkce automatizace OLE.|
|[AfxThrowOleException](#afxthrowoleexception)|Vyvolá výjimku OLE.|

Pro podporu výjimek databáze poskytují třídy databáze dvě třídy výjimek, `CDBException` a `CDaoException`a globální funkce pro podporu typů výjimek:

### <a name="dao-exception-functions"></a>Funkce výjimky DAO

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Vyvolá [CDaoException](../../mfc/reference/cdaoexception-class.md) z vlastního kódu.|
|[AfxThrowDBException](#afxthrowdbexception)|Vyvolá [CDBException](../../mfc/reference/cdbexception-class.md) z vlastního kódu.|

Knihovna MFC poskytuje následující funkci ukončení:

### <a name="termination-functions"></a>Funkce ukončení

|||
|-|-|
|[AfxAbort](#afxabort)|Volá se, aby se ukončila aplikace, když dojde k závažné chybě.|

##  <a name="try"></a>Zkuste

Nastaví blok **Try** .

```
TRY
```

### <a name="remarks"></a>Poznámky

Blok **Try** identifikuje blok kódu, který může vyvolat výjimky. Tyto výjimky jsou zpracovávány v následujících blocích **catch** a **AND_CATCH** . Rekurze je povolena: výjimky mohou být předány do vnějšího bloku **Try** , a to buď jejich ignorováním, nebo pomocí makra THROW_LAST. Ukončete blok **Try** pomocí makra END_CATCH nebo END_CATCH_ALL.

Další informace najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [catch](#catch).

### <a name="requirements"></a>Požadavky

Záhlaví: AFX –. h

##  <a name="catch"></a>CATCH

Definuje blok kódu, který zachytává první typ výjimky vyvolaný v předchozím bloku **Try** .

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Určuje typ výjimky, která se má testovat. Seznam standardních tříd výjimek naleznete v tématu Třída [CException –](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Určuje název ukazatele objektu výjimky, který bude vytvořen makrem. Můžete použít název ukazatele pro přístup k objektu výjimky v rámci bloku **catch** . Tato proměnná je deklarována za vás.

### <a name="remarks"></a>Poznámky

Kód pro zpracování výjimek může dotazování objekt výjimky, pokud je to vhodné, pro získání dalších informací o konkrétní příčině výjimky. Vyvolat makro THROW_LAST pro posunutí zpracování na další vnější rámec výjimky. Ukončete blok **Try** pomocí END_CATCHho makra.

Pokud *exception_class* je `CException`třídy, budou zachyceny všechny typy výjimek. Můžete použít členskou funkci [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) k určení, která konkrétní výjimka byla vyvolána. Lepší způsob, jak zachytit několik druhů výjimek, je použití sekvenčních příkazů **AND_CATCH** , z nichž každý má jiný typ výjimky.

Ukazatel objektu výjimky je vytvořen pomocí makra. Nemusíte ho deklarovat sami.

> [!NOTE]
>  Blok **catch** je definován jako C++ obor vymezený složenými závorkami. Pokud deklarujete proměnné v tomto oboru, budou přístupné pouze v rámci tohoto oboru. To platí také pro *exception_object_pointer_name*.

Další informace o výjimkách a makru CATCH naleznete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>CATCH_ALL

Definuje blok kódu, který zachycuje všechny typy výjimek, které jsou vyvolány v předchozím bloku **Try** .

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Určuje název ukazatele objektu výjimky, který bude vytvořen makrem. Můžete použít název ukazatele pro přístup k objektu výjimky v rámci `CATCH_ALL` bloku. Tato proměnná je deklarována za vás.

### <a name="remarks"></a>Poznámky

Kód pro zpracování výjimek může dotazování objekt výjimky, pokud je to vhodné, pro získání dalších informací o konkrétní příčině výjimky. Vyvolat makro `THROW_LAST` pro posunutí zpracování na další vnější rámec výjimky. Pokud používáte **CATCH_ALL**, ukončete blok **TRY** pomocí makra END_CATCH_ALL.

> [!NOTE]
>  Blok **CATCH_ALL** je definován jako C++ obor vymezený složenými závorkami. Pokud deklarujete proměnné v tomto oboru, budou přístupné pouze v rámci tohoto oboru.

Další informace o výjimkách najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFile –:: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="and_catch"></a>AND_CATCH

Definuje blok kódu pro zachycení dalších typů výjimek vyvolaných v předchozím bloku **Try** .

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Určuje typ výjimky, která se má testovat. Seznam standardních tříd výjimek naleznete v tématu Třída [CException –](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Název ukazatele objektu výjimky, který bude vytvořen makrem. Můžete použít název ukazatele pro přístup k objektu výjimky v rámci **AND_CATCH** bloku. Tato proměnná je deklarována za vás.

### <a name="remarks"></a>Poznámky

Použijte makro CATCH k zachycení jednoho typu výjimky a potom makro AND_CATCH pro zachycení každého následného typu. Ukončete blok **Try** pomocí END_CATCHho makra.

Kód pro zpracování výjimek může dotazování objekt výjimky, pokud je to vhodné, pro získání dalších informací o konkrétní příčině výjimky. Zavolejte makro THROW_LAST v rámci bloku **AND_CATCH** , aby se zpracování posunulo na další vnější rámec výjimky. **AND_CATCH** označuje konec předchozího bloku **catch** nebo **AND_CATCH** .

> [!NOTE]
>  Blok **AND_CATCH** je definován jako C++ obor (vymezený složenými závorkami). Pokud deklarujete proměnné v tomto oboru, nezapomeňte, že jsou přístupné pouze v rámci tohoto oboru. To platí i pro *exception_object_pointer_name* proměnnou.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [catch](#catch).

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h
##  <a name="and_catch_all"></a>AND_CATCH_ALL

Definuje blok kódu pro zachycení dalších typů výjimek vyvolaných v předchozím bloku **Try** .

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Název ukazatele objektu výjimky, který bude vytvořen makrem. Můžete použít název ukazatele pro přístup k objektu výjimky v rámci **AND_CATCH_ALL** bloku. Tato proměnná je deklarována za vás.

### <a name="remarks"></a>Poznámky

Použijte makro **catch** k zachycení jednoho typu výjimky, potom makro AND_CATCH_ALL pro zachycení všech dalších dalších typů. Pokud používáte AND_CATCH_ALL, ukončete blok **Try** pomocí makra END_CATCH_ALL.

Kód pro zpracování výjimek může dotazování objekt výjimky, pokud je to vhodné, pro získání dalších informací o konkrétní příčině výjimky. Zavolejte makro THROW_LAST v rámci bloku **AND_CATCH_ALL** , aby se zpracování posunulo na další vnější rámec výjimky. **AND_CATCH_ALL** označuje konec předchozího bloku **catch** nebo **AND_CATCH_ALL** .

> [!NOTE]
>  Blok **AND_CATCH_ALL** je definován jako C++ obor (oddělený závorkami). Pokud deklarujete proměnné v tomto oboru, nezapomeňte, že jsou přístupné pouze v rámci tohoto oboru.

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="end_catch"></a>END_CATCH

Označuje konec posledního bloku **catch** nebo **AND_CATCH** .

```
END_CATCH
```

### <a name="remarks"></a>Poznámky

Další informace o makru END_CATCH naleznete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="end_catch_all"></a>END_CATCH_ALL

Označuje konec posledního **CATCH_ALL88** nebo bloku **AND_CATCH_ALL** .

```
END_CATCH_ALL
```

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="throw"></a>THROW (MFC)

Vyvolá určenou výjimku.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer*<br/>
Odkazuje na objekt výjimky odvozený z `CException`.

### <a name="remarks"></a>Poznámky

**Throw** vykonání přerušení programu a předání řízení přidruženému bloku **catch** v programu. Pokud jste blok **catch** neposkytli, pak je ovládací prvek předán modulu knihovna Microsoft Foundation Class, který vytiskne chybovou zprávu a ukončí se.

Další informace najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="throw_last"></a>THROW_LAST

Vyvolá výjimku zpět do dalšího vnějšího bloku **catch** .

```
THROW_LAST()
```

### <a name="remarks"></a>Poznámky

Toto makro umožňuje vyvolat místně vytvořenou výjimku. Pokud se pokusíte vyvolat výjimku, kterou jste právě zachytili, obvykle se přestanou mimo rozsah a odstraní se. Při **THROW_LAST**je výjimka předána do další obslužné rutiny **catch** správně.

Další informace najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFile –:: Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="afxthrowarchiveexception"></a>AfxThrowArchiveException

Vyvolá výjimku archivu.

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parametry

*způsobit*<br/>
Určuje celé číslo, které označuje důvod výjimky. Seznam možných hodnot naleznete v tématu [CArchiveException:: m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Odkazuje na řetězec obsahující název objektu `CArchive`, který způsobil výjimku (je-li k dispozici).

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="afxthrowfileexception"></a>AfxThrowFileException

Vyvolá výjimku souboru.

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*způsobit*<br/>
Určuje celé číslo, které označuje důvod výjimky. Seznam možných hodnot naleznete v tématu [CFileException:: m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Obsahuje číslo chyby operačního systému (Pokud je k dispozici), které uvádí důvod výjimky. Seznam chybových kódů najdete v příručce k operačnímu systému.

*lpszFileName*<br/>
Odkazuje na řetězec obsahující název souboru, který způsobil výjimku (je-li k dispozici).

### <a name="remarks"></a>Poznámky

Zodpovídáte za zjištění příčiny na základě kódu chyby operačního systému.

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

## <a name="afxthrowinvalidargexception"></a>AfxThrowInvalidArgException

Vyvolá výjimku neplatného argumentu.

### <a name="syntax"></a>Syntaxe

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Poznámky

Tato funkce se volá, když se použijí neplatné argumenty.

### <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="afxthrowmemoryexception"></a>AfxThrowMemoryException

Vyvolá výjimku paměti.

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Poznámky

Tuto funkci volejte, pokud selže volání systémových přidělování paměti (například \ GlobalAlloc **a funkce** systému [](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows). Nemusíte ji volat pro funkci **New** , protože **Nová** dojde k automatickému vyvolání výjimky paměti, pokud se přidělení paměti nezdaří.

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="afxthrownotsupportedexception"></a>AfxThrowNotSupportedException

Vyvolá výjimku, která je výsledkem požadavku na nepodporovanou funkci.

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="afxthrowresourceexception"></a>AfxThrowResourceException

Vyvolá výjimku prostředku.

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Poznámky

Tato funkce se obvykle volá, když nelze načíst prostředek systému Windows.

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="afxthrowuserexception"></a>AfxThrowUserException

Vyvolá výjimku pro zastavení operace koncového uživatele.

```
void AfxThrowUserException();
```

### <a name="remarks"></a>Poznámky

Tato funkce se obvykle volá hned po `AfxMessageBox` nahlásila uživateli chybu.

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException

Pomocí této funkce lze vyvolat výjimku v rámci funkce automatizace OLE.

```
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>Parametry

*wCode*<br/>
Kód chyby specifický pro vaši aplikaci.

*lpszDescription*<br/>
Slovní popis chyby

*nDescriptionID*<br/>
ID prostředku pro slovní popis chyby

*nHelpID*<br/>
Kontext nápovědu pro nápovědu vaší aplikace (. HLP) souboru.

### <a name="remarks"></a>Poznámky

Informace poskytované této funkci mohou být zobrazeny v rámci aplikace pro řízení (Microsoft Visual Basic nebo jiné klientské aplikace automatizace technologie OLE).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="afxthrowoleexception"></a>AfxThrowOleException

Vytvoří objekt typu `COleException` a vyvolá výjimku.

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*příkaz*<br/>
Stavový kód OLE, který určuje důvod výjimky.

*oddělení*<br/>
Zpracujte kód výsledku, který označuje důvod výjimky.

### <a name="remarks"></a>Poznámky

Verze, která používá HRESULT jako argument, převede tento kód výsledku do odpovídající Code. Další informace o HRESULT a Code naleznete v tématu [Struktura kódů chyb modelu COM](/windows/win32/com/structure-of-com-error-codes) v Windows SDK.

### <a name="requirements"></a>Požadavky

  **Header** afxdao. h

##  <a name="afxthrowdaoexception"></a>AfxThrowDaoException

Voláním této funkce vyvoláte výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md) z vlastního kódu.

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parametry

*nAfxDaoError*<br/>
Celočíselná hodnota představující Rozšířený kód chyby DAO, což může být jedna z hodnot uvedených v části [CDaoException:: m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*Code*<br/>
Kód chyby OLE z rozhraní DAO typu Code. Informace naleznete v tématu [CDaoException:: m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Poznámky

Rozhraní také volá `AfxThrowDaoException`. V volání můžete předat jeden z parametrů nebo obojí. Například pokud chcete vyvolat jednu z chyb definovaných v **CDaoException:: nAfxDaoError** , ale nezáleží na parametru *Code* , předejte v parametru *nAfxDaoError* platný kód a přijměte výchozí hodnotu pro *Code*.

Informace o výjimkách souvisejících s třídami knihovny MFC rozhraní DAO naleznete v tématu Class `CDaoException` v této knize a v článku [výjimky: výjimky databáze](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Požadavky

  **Header** AFXDB. h

##  <a name="afxthrowdbexception"></a>AfxThrowDBException

Voláním této funkce vyvoláte výjimku typu `CDBException` z vlastního kódu.

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
Hodnota typu RETCODE, která definuje typ chyby, která způsobila vyvolání výjimky.

*PDB*<br/>
Ukazatel na objekt `CDatabase`, který představuje připojení ke zdroji dat, ke kterému je výjimka přidružena.

*hstmt*<br/>
Popisovač ODBC HSTMT, který určuje popisovač příkazu, ke kterému je výjimka přidružena.

### <a name="remarks"></a>Poznámky

Rozhraní volá `AfxThrowDBException`, když obdrží rozhraní ODBC RETCODE ze volání funkce rozhraní ODBC API a interpretuje RETCODE jako výjimečnou podmínku spíše než očekávanou chybu. Například operace přístupu k datům může selhat kvůli chybě čtení disku.

Informace o hodnotách RETCODE definovaných pomocí rozhraní ODBC naleznete v části kapitola 8 "načítání informací o stavu a chybách" v Windows SDK. Informace o rozšířeních MFC pro tyto kódy naleznete v tématu Třída [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

##  <a name="afxabort"></a>AfxAbort

Výchozí funkce ukončení poskytovaná knihovnou MFC.

```
void  AfxAbort();
```

### <a name="remarks"></a>Poznámky

`AfxAbort` se interně nazývá členské funkce knihovny MFC, když dojde k závažné chybě, jako je nezachycená výjimka, kterou nelze zpracovat. Pokud se setkáte s závažnou chybou, ze které nelze provést obnovení, můžete volat `AfxAbort` ve vzácných případech.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [catch](#catch).

### <a name="requirements"></a>Požadavky

  **Header** AFX –. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CException – třída](cexception-class.md)<br/>
[CInvalidArgException – třída](cinvalidargexception-class.md)
