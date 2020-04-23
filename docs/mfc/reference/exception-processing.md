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
ms.openlocfilehash: bdf9dee88c29621bdc77c83d2633d93b4b9d10a7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751613"
---
# <a name="exception-processing"></a>Zpracování výjimek

Při spuštění programu může dojít k řadě neobvyklých podmínek a chyb nazývaných "výjimky". Mezi ně může patřit nedostatek paměti, chyby přidělení prostředků a selhání při hledání souborů.

Knihovna tříd Microsoft Foundation používá schéma zpracování výjimek, které je modelováno přesně podle schématu navrženého výborem pro standardy ANSI pro jazyk C++. Obslužná rutina výjimky musí být nastavena před voláním funkce, která může narazit na neobvyklou situaci. Pokud funkce narazí na abnormální podmínku, vyvolá výjimku a ovládací prvek je předán obslužné rutině výjimky.

Několik maker, která jsou součástí knihovny tříd Microsoft Foundation, nastaví obslužné rutiny výjimek. Řada dalších globálních funkcí pomáhá vyvolat specializované výjimky a v případě potřeby ukončit programy. Tato makra a globální funkce spadají do následujících kategorií:

- Makra výjimek, která strukturují obslužnou rutinu výjimky.

- Funkce vyvolání výjimky), které generují výjimky určitých typů.

- Ukončení funkce, které způsobují ukončení programu.

Příklady a další podrobnosti naleznete v článku [Výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Makra výjimek

|||
|-|-|
|[TRY](#try)|Označuje blok kódu pro zpracování výjimek.|
|[Chytit](#catch)|Označuje blok kódu pro zachycení výjimky z předchozího bloku **TRY.**|
|[CATCH_ALL](#catch_all)|Označuje blok kódu pro zachycení všech výjimek z předchozího bloku **TRY.**|
|[AND_CATCH](#and_catch)|Označuje blok kódu pro zachycení další chod typů výjimek z předchozího bloku **TRY.**|
|[AND_CATCH_ALL](#and_catch_all)|Označuje blok kódu pro zachycení všech dalších typů výjimek vyzdvižených v předchozím bloku **TRY.**|
|[END_CATCH](#end_catch)|Ukončí poslední blok kódu **CATCH** nebo **AND_CATCH.**|
|[END_CATCH_ALL](#end_catch_all)|Ukončí poslední **CATCH_ALL** bloku kódu.|
|[Hodit](#throw)|Vyvolá zadanou výjimku.|
|[THROW_LAST](#throw_last)|Vyvolá aktuálně zmanipulovní výjimku na další vnější obslužnou rutinu.|

### <a name="exception-throwing-functions"></a>Funkce vyvolání výjimek

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Vyvolá výjimku archivu.|
|[Výjimka AfxThrowFileException](#afxthrowfileexception)|Vyvolá výjimku souboru.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Vyvolá výjimku neplatný argument.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Vyvolá výjimku paměti.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Vyvolá nepodporovanou výjimku.|
|[Výjimka afxThrowResourceException](#afxthrowresourceexception)|Vyvolá výjimku, která nebyla nalezena.|
|[Výjimka afxThrowUserException](#afxthrowuserexception)|Vyvolá výjimku v akci programu iniciované uživatelem.|

Knihovna MFC poskytuje dvě funkce vyvolání výjimek speciálně pro výjimky OLE:

### <a name="ole-exception-functions"></a>Funkce výjimky OLE

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Vyvolá výjimku v rámci funkce automatizace OLE.|
|[AfxThrowOleException](#afxthrowoleexception)|Vyvolá výjimku OLE.|

Pro podporu výjimek databáze poskytují třídy `CDBException` databáze `CDaoException`dvě třídy výjimek a aplikace a globální funkce pro podporu typů výjimek:

### <a name="dao-exception-functions"></a>Funkce výjimky DAO

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Vyvolá [Výjimku CDaoException](../../mfc/reference/cdaoexception-class.md) z vlastního kódu.|
|[AfxThrowDBException](#afxthrowdbexception)|Vyvolá [CDBException](../../mfc/reference/cdbexception-class.md) z vlastního kódu.|

Knihovna MFC poskytuje následující funkci ukončení:

### <a name="termination-functions"></a>Funkce ukončení

|||
|-|-|
|[AfxAbort](#afxabort)|Volána k ukončení aplikace, když dojde k závažné chybě.|

## <a name="try"></a><a name="try"></a>Zkuste

Nastaví blok **TRY.**

```
TRY
```

### <a name="remarks"></a>Poznámky

Blok **TRY** identifikuje blok kódu, který může vyvolat výjimky. Tyto výjimky jsou zpracovány v **následujících** catch a **AND_CATCH** bloky. Rekurze je povolena: výjimky mohou být předány vnějšímu bloku **TRY,** a to buď jejich ignorováním, nebo použitím THROW_LAST makra. Ukončite blok **TRY** END_CATCH nebo END_CATCH_ALL makru.

Další informace naleznete v článku [Výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

Viz příklad pro [CATCH](#catch).

### <a name="requirements"></a>Požadavky

Záhlaví: afx.h

## <a name="catch"></a><a name="catch"></a>Chytit

Definuje blok kódu, který zachycuje první typ výjimky vyzývaný v předchozím bloku **TRY.**

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Určuje typ výjimky, pro který se má testovat. Seznam standardních tříd výjimek naleznete v části [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Určuje název ukazatele objektu výjimky, který bude vytvořen makra. Název ukazatele můžete použít pro přístup k objektu výjimky v rámci bloku **CATCH.** Tato proměnná je deklarována za vás.

### <a name="remarks"></a>Poznámky

Kód zpracování výjimky můžete dotazovat objekt výjimky, pokud je to vhodné, chcete-li získat další informace o konkrétní příčinu výjimky. Vyvoláte makro THROW_LAST a přesuňte zpracování na další vnější rámec výjimky. Ukončite blok **TRY** END_CATCH makra.

Pokud *exception_class* je `CException`třída , budou zachyceny všechny typy výjimek. Můžete použít [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) členskou funkci k určení, která konkrétní výjimka byla vyvolána. Lepší způsob, jak zachytit několik druhů výjimek, je použití sekvenčních **příkazů AND_CATCH,** každý s jiným typem výjimky.

Ukazatel objektu výjimky je vytvořen makra. Nemusíte to deklarovat sami.

> [!NOTE]
> Blok **CATCH** je definován jako obor Jazyka C++ vymezený závorkami. Pokud deklarujete proměnné v tomto oboru, jsou přístupné pouze v rámci tohoto oboru. To platí i pro *exception_object_pointer_name*.

Další informace o výjimkách a makro CATCH naleznete v článku [Výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

## <a name="catch_all"></a><a name="catch_all"></a>CATCH_ALL

Definuje blok kódu, který zachycuje všechny typy výjimek vyzdvižené v předchozím bloku **TRY.**

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Určuje název ukazatele objektu výjimky, který bude vytvořen makra. Název ukazatele můžete použít pro přístup k `CATCH_ALL` objektu výjimky v rámci bloku. Tato proměnná je deklarována za vás.

### <a name="remarks"></a>Poznámky

Kód zpracování výjimky můžete dotazovat objekt výjimky, pokud je to vhodné, chcete-li získat další informace o konkrétní příčinu výjimky. Vyvolat `THROW_LAST` makro přesunout zpracování na další vnější rámec výjimky. Pokud používáte **CATCH_ALL**, ukončite blok **TRY** END_CATCH_ALL makro.

> [!NOTE]
> Blok **CATCH_ALL** je definován jako obor Jazyka C++ vymezený závorkami. Pokud deklarujete proměnné v tomto oboru, jsou přístupné pouze v rámci tohoto oboru.

Další informace o výjimkách naleznete v článku [Výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

Viz příklad [cfile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="and_catch"></a><a name="and_catch"></a>AND_CATCH

Definuje blok kódu pro zachycení další typy výjimek vyvolána v předchozím **bloku TRY.**

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Určuje typ výjimky, pro který se má testovat. Seznam standardních tříd výjimek naleznete v části [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Název ukazatele objektu výjimky, který bude vytvořen makra. Název ukazatele můžete použít pro přístup k objektu výjimky v rámci **bloku AND_CATCH.** Tato proměnná je deklarována za vás.

### <a name="remarks"></a>Poznámky

Pomocí makra CATCH zachyťte jeden typ výjimky a pak AND_CATCH makro k zachycení každého následujícího typu. Ukončite blok **TRY** END_CATCH makra.

Kód zpracování výjimky můžete dotazovat objekt výjimky, pokud je to vhodné, chcete-li získat další informace o konkrétní příčinu výjimky. Volání makra THROW_LAST v bloku **AND_CATCH** přesunout zpracování na další vnější rámec výjimky. **AND_CATCH** označuje konec předchozího bloku **CATCH** nebo **AND_CATCH.**

> [!NOTE]
> Blok **AND_CATCH** je definován jako obor Jazyka C++ (vymezený složenými závorkami). Pokud deklarujete proměnné v tomto oboru, nezapomeňte, že jsou přístupné pouze v rámci tohoto oboru. To platí i pro *proměnnou exception_object_pointer_name.*

### <a name="example"></a>Příklad

Viz příklad pro [CATCH](#catch).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="and_catch_all"></a><a name="and_catch_all"></a>AND_CATCH_ALL

Definuje blok kódu pro zachycení další typy výjimek vyvolána v předchozím **bloku TRY.**

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Název ukazatele objektu výjimky, který bude vytvořen makra. Název ukazatele můžete použít pro přístup k objektu výjimky v rámci **bloku AND_CATCH_ALL.** Tato proměnná je deklarována za vás.

### <a name="remarks"></a>Poznámky

Pomocí makra **CATCH** zachyťte jeden typ výjimky, pak AND_CATCH_ALL makro zachytit všechny ostatní následující typy. Pokud používáte AND_CATCH_ALL, ukončite blok **TRY** END_CATCH_ALL makry.

Kód zpracování výjimky můžete dotazovat objekt výjimky, pokud je to vhodné, chcete-li získat další informace o konkrétní příčinu výjimky. Volání THROW_LAST makro v bloku **AND_CATCH_ALL** přesunout zpracování na další vnější rámec výjimky. **AND_CATCH_ALL** označuje konec předchozího bloku **CATCH** nebo **AND_CATCH_ALL.**

> [!NOTE]
> Blok **AND_CATCH_ALL** je definován jako obor Jazyka C++ (vymezený závorkami). Pokud deklarujete proměnné v tomto oboru, nezapomeňte, že jsou přístupné pouze v rámci tohoto oboru.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="end_catch"></a><a name="end_catch"></a>END_CATCH

Označuje konec **poslednícatch** nebo **AND_CATCH** bloku.

```
END_CATCH
```

### <a name="remarks"></a>Poznámky

Další informace o END_CATCH makru naleznete v článku [Výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="end_catch_all"></a><a name="end_catch_all"></a>END_CATCH_ALL

Označuje konec posledního **CATCH_ALL88** nebo **AND_CATCH_ALL** bloku.

```
END_CATCH_ALL
```

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="throw-mfc"></a><a name="throw"></a>THROW (MFC)

Vyvolá zadanou výjimku.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer*<br/>
Odkazuje na objekt výjimky `CException`odvozený z aplikace .

### <a name="remarks"></a>Poznámky

**THROW** přeruší spuštění programu a předá řízení přidruženému bloku **CATCH** v programu. Pokud jste nezadali blok **CATCH,** je ovládací prvek předán modulu Knihovny tříd microsoft foundation, který vytiskne chybovou zprávu a ukončí.

Další informace naleznete v článku [Výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="throw_last"></a><a name="throw_last"></a>THROW_LAST

Vyvolá výjimku zpět na další vnější **CATCH** bloku.

```
THROW_LAST()
```

### <a name="remarks"></a>Poznámky

Toto makro umožňuje vyvolat místně vytvořenou výjimku. Pokud se pokusíte vyvolat výjimku, kterou jste právě chytili, obvykle přejde mimo rozsah a bude odstraněna. S **THROW_LAST**je výjimka předána správně další obslužné rutině **CATCH.**

Další informace naleznete v článku [Výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

Viz příklad [cfile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a>AfxThrowArchiveException

Vyvolá výjimku archivu.

```cpp
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parametry

*Způsobit*<br/>
Určuje celé číslo, které označuje důvod výjimky. Seznam možných hodnot naleznete v tématu [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Odkazuje na řetězec obsahující název `CArchive` objektu, který způsobil výjimku (pokud je k dispozici).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="afxthrowfileexception"></a><a name="afxthrowfileexception"></a>Výjimka AfxThrowFileException

Vyvolá výjimku souboru.

```cpp
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*Způsobit*<br/>
Určuje celé číslo, které označuje důvod výjimky. Seznam možných hodnot naleznete v tématu [CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*Chyba iOs*<br/>
Obsahuje číslo chyby operačního systému (pokud je k dispozici), které uvádí důvod výjimky. Seznam kódů chyb najdete v příručce k operačnímu systému.

*název souboru lpsz*<br/>
Odkazuje na řetězec obsahující název souboru, který způsobil výjimku (pokud je k dispozici).

### <a name="remarks"></a>Poznámky

Jste zodpovědní za určení příčiny na základě kódu chyby operačního systému.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="afxthrowinvalidargexception"></a><a name="afxthrowinvalidargexception"></a>AfxThrowInvalidArgException

Vyvolá výjimku neplatný argument.

### <a name="syntax"></a>Syntaxe

```cpp
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána při použití neplatných argumentů.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a>AfxThrowMemoryException

Vyvolá výjimku paměti.

```cpp
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Poznámky

Volání této funkce, pokud volání základní alokátory systémové paměti (například **malloc** a [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows funkce) nezdaří. Není nutné volat pro **nové,** protože **new** vyvolá výjimku paměti automaticky, pokud se nezdaří přidělení paměti.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a>AfxThrowNotSupportedException

Vyvolá výjimku, která je výsledkem požadavku na nepodporovanou funkci.

```cpp
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a>Výjimka afxThrowResourceException

Vyvolá výjimku prostředku.

```cpp
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Poznámky

Tato funkce se obvykle nazývá, když nelze načíst prostředek systému Windows.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="afxthrowuserexception"></a><a name="afxthrowuserexception"></a>Výjimka afxThrowUserException

Vyvolá výjimku k zastavení operace koncového uživatele.

```cpp
void AfxThrowUserException();
```

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle `AfxMessageBox` volána ihned poté, co oznámila chybu uživateli.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException

Tato funkce slouží k vyvolání výjimky v rámci funkce automatizace OLE.

```cpp
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

*wKód*<br/>
Kód chyby specifický pro vaši aplikaci.

*lpszDescription*<br/>
Slovní popis chyby.

*nDescriptionID*<br/>
ID prostředku pro popis slovní chyby.

*nHelpID*<br/>
Kontext nápovědy pro nápovědu aplikace (. HLP).

### <a name="remarks"></a>Poznámky

Informace poskytnuté této funkci mohou být zobrazeny aplikací řízení (Microsoft Visual Basic nebo jinou klientskou aplikací automatizace OLE).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="afxthrowoleexception"></a><a name="afxthrowoleexception"></a>AfxThrowOleException

Vytvoří objekt typu `COleException` a vyvolá výjimku.

```cpp
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*Sc*<br/>
Stavový kód OLE, který označuje důvod výjimky.

*Hr*<br/>
Zpracovat kód výsledku, který označuje důvod výjimky.

### <a name="remarks"></a>Poznámky

Verze, která přebírá HRESULT jako argument převede tento kód výsledku do odpovídajícího SCODE. Další informace o hresult a scode naleznete [v tématu Struktura kódů chyb COM](/windows/win32/com/structure-of-com-error-codes) v sadě Windows SDK.

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdao.h

## <a name="afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a>AfxThrowDaoException

Volání této funkce vyvolat výjimku typu [CDaoException](../../mfc/reference/cdaoexception-class.md) z vlastního kódu.

```cpp
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parametry

*nAfxDaoChyba*<br/>
Celá hodnota představující rozšířený kód chyby DAO, což může být jedna z hodnot uvedených pod [cdaoexception::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*kód*<br/>
Kód chyby OLE z DAO typu SCODE. Další informace naleznete v tématu [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Poznámky

Rámec také `AfxThrowDaoException`volá . Ve volání můžete předat jeden z parametrů nebo obojí. Chcete-li například vyvolat jednu z chyb definovaných v **cdaoexception::nAfxDaoError,** ale nestaráte se o parametr *scode,* předejte platný kód v parametru *nAfxDaoError* a přijměte výchozí hodnotu pro *scode*.

Informace o výjimkách souvisejících s třídami Knihovny `CDaoException` MFC DAO naleznete v této knize a v článku [Výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afxdb.h

## <a name="afxthrowdbexception"></a><a name="afxthrowdbexception"></a>AfxThrowDBException

Volání této funkce vyvolat výjimku typu `CDBException` z vlastního kódu.

```cpp
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
Hodnota typu RETCODE, definování typu chyby, která způsobila výjimku vyvolat.

*Pdb*<br/>
Ukazatel na `CDatabase` objekt, který představuje připojení zdroje dat, ke kterému je přidružena výjimka.

*hstmt*<br/>
Popisovač HSTMT ODBC, který určuje popisovač příkazu, ke kterému je přidružena výjimka.

### <a name="remarks"></a>Poznámky

Rozhraní framework `AfxThrowDBException` volá, když obdrží RETCODE ODBC z volání funkce rozhraní API ROZHRANÍ ODBC a interpretuje RETCODE jako výjimečnou podmínku, nikoli očekávanou chybu. Operace přístupu k datům může například selhat z důvodu chyby čtení disku.

Informace o hodnotách RETCODE definovaných rozhraním ODBC naleznete v kapitole 8 V části Načítání informací o stavu a chybách v kani SDK systému Windows. Informace o rozšíření knihovny MFC k těmto kódům naleznete v tématu [cdbexception](../../mfc/reference/cdbexception-class.md)třídy .

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="afxabort"></a><a name="afxabort"></a>AfxAbort

Výchozí funkce ukončení dodaná knihovnou MFC.

```cpp
void  AfxAbort();
```

### <a name="remarks"></a>Poznámky

`AfxAbort`je volána interně funkcemi členů knihovny MFC, pokud dojde k závažné chybě, jako je například nezachycená výjimka, kterou nelze zpracovat. Můžete volat `AfxAbort` ve výjimečných případech, když narazíte na katastrofickou chybu, ze které nelze obnovit.

### <a name="example"></a>Příklad

Viz příklad pro [CATCH](#catch).

### <a name="requirements"></a>Požadavky

  **Záhlaví** afx.h

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)<br/>
[CException – třída](cexception-class.md)<br/>
[CInvalidArgException – třída](cinvalidargexception-class.md)
