---
title: Zpracování výjimek
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.exceptions
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
ms.openlocfilehash: 8b40afbfcc453a4908b434dc53b7b86959673453
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55851679"
---
# <a name="exception-processing"></a>Zpracování výjimek

Když je program spuštěn, může dojít, počet nestandardní podmínky a chyb s názvem "výjimek". Ty mohou zahrnovat vyčerpání paměti, chyb přidělení prostředků a nepodařilo se najít soubory.

Knihovny Microsoft Foundation Class používá schématu zpracování výjimek, které je Modelováno podle přesně jeden navrhovaná výboru standardy ANSI jazyka C++. Obslužná rutina výjimky musíte nastavit před voláním funkce, které mohou nastat abnormální situace. Pokud funkci setká nestandardní podmínky, vyvolá výjimku a řízení je předáno obslužná rutina výjimky.

Obslužné rutiny výjimek nastaví několik makra, které jsou součástí knihovny Microsoft Foundation Class. Počet dalších globálních funkcí, které pomáhají vyvolat výjimky specializované a ukončit programy, v případě potřeby. Tato makra a globální funkce spadají do následujících kategorií:

- Makra výjimek, které strukturovat vaše obslužná rutina výjimky.

- Exception-throwing funkce), které generují výjimky určitých typů.

- Ukončení funkce, které způsobí ukončení programu.

Příklady a další podrobnosti najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Makra výjimek

|||
|-|-|
|[ZKUSTE](#try)|Určuje blok kódu pro zpracování výjimek.|
|[CATCH](#catch)|Určuje blok kódu pro zachycování výjimky z předchozího **zkuste** bloku.|
|[CATCH_ALL](#catch_all)|Určuje blok kódu pro zachycení všech výjimek z předchozího **zkuste** bloku.|
|[AND_CATCH](#and_catch)|Určuje blok kódu pro zachytávání výjimek další typy z předchozího **zkuste** bloku.|
|[AND_CATCH_ALL](#and_catch_all)|Určuje blok kódu pro zachycení všech ostatních typů další výjimka vyvolána v předchozích **zkuste** bloku.|
|[END_CATCH](#end_catch)|Ukončí poslední **CATCH** nebo **AND_CATCH** bloku kódu.|
|[END_CATCH_ALL](#end_catch_all)|Ukončí poslední **CATCH_ALL** bloku kódu.|
|[VYVOLÁNÍ VÝJIMKY](#throw)|Vyvolá zadané výjimky.|
|[THROW_LAST](#throw_last)|Vyvolá aktuálně zpracování výjimek na další vnější obslužnou rutinu.|

### <a name="exception-throwing-functions"></a>Funkce vyvolávání výjimek

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Vyvolá výjimku archivu.|
|[AfxThrowFileException](#afxthrowfileexception)|Vyvolá výjimku souborů.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Vyvolá výjimku neplatný argument.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Vyvolá výjimku paměti.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Vyvolá výjimka není podporován.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Výjimku Windows prostředků nebyla nalezena.|
|[AfxThrowUserException](#afxthrowuserexception)|Vyvolá výjimku v rámci akce zahájená uživatelem programu.|

Knihovna MFC poskytuje dvě funkce vyvolávání výjimek speciálně pro výjimky OLE:

### <a name="ole-exception-functions"></a>OLE – výjimky funkce

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Vyvolá výjimku v rámci funkce automatizace OLE.|
|[AfxThrowOleException](#afxthrowoleexception)|Vyvolá výjimku OLE.|

Pro podporu výjimky databáze, databáze třídy poskytují dvě třídy výjimek, `CDBException` a `CDaoException`a globální funkce pro podporu typů výjimek:

### <a name="dao-exception-functions"></a>DAO – výjimky funkce

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Vyvolá výjimku [cdaoexception –](../../mfc/reference/cdaoexception-class.md) z vlastního kódu.|
|[AfxThrowDBException](#afxthrowdbexception)|Vyvolá výjimku [CDBException](../../mfc/reference/cdbexception-class.md) z vlastního kódu.|

Knihovna MFC poskytuje následující funkce ukončení:

### <a name="termination-functions"></a>Funkce ukončování

|||
|-|-|
|[AfxAbort](#afxabort)|Volá se, k ukončení aplikace při závažné chybě dochází.|

##  <a name="try"></a>  ZKUSTE

Nastaví **zkuste** bloku.

```
TRY
```

### <a name="remarks"></a>Poznámky

A **zkuste** bloku určuje blok kódu, který může vyvolat výjimky. Tyto výjimky jsou zpracovány v následujícím **CATCH** a **AND_CATCH** bloky. Rekurze je povolen: výjimky může být předán vnějším **zkuste** bloku, které ignoruje je nebo pomocí THROW_LAST – makro. End **zkuste** blok s END_CATCH nebo END_CATCH_ALL makra.

Další informace najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CATCH](#catch).

### <a name="requirements"></a>Požadavky

Záhlaví: afx.h

##  <a name="catch"></a>  CATCH

Definuje bloku kódu, který zachytí první typ výjimky vyvolané v předchozím **zkuste** bloku.

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Určuje typ výjimky pro testování. Seznam tříd výjimek standard najdete v tématu třídy [cexception –](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Určuje název objektu výjimky ukazatel, vytvořený makra. Název ukazatele můžete použít pro přístup k objektu výjimky v rámci **CATCH** bloku. Tato proměnná je deklarovaná za vás.

### <a name="remarks"></a>Poznámky

Kód zpracování výjimek můžete dotazování objekt výjimky, pokud je to vhodné, chcete-li získat další informace o konkrétní příčina výjimky. Vyvolání THROW_LAST – makro přesunout zpracování do dalšího snímku vnější výjimky. End **zkuste** blok s END_CATCH – makro.

Pokud *exception_class* je třída `CException`, pak všechny typy výjimka bude zachycena. Můžete použít [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) členskou funkci k určení byla vyvolána výjimka. Lepší způsob, jak zachytit několik druhy výjimek má používat sekvenční **AND_CATCH** příkazy, každý s odlišný typ výjimky.

Makro vytvoří ukazatel objektu výjimky. Chcete-li deklarovat sami nepotřebujete.

> [!NOTE]
>  **CATCH** bloku je definován jako obor C++ je oddělená složené závorky. Při deklarování proměnné v tomto oboru, jsou přístupné pouze v daném oboru. To platí i pro *exception_object_pointer_name*.

Další informace o výjimkách a CATCH – makro, najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>  CATCH_ALL

Definuje bloku kódu, který zachycuje všechny typy výjimek vyvolaných v předchozím **zkuste** bloku.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Určuje název objektu výjimky ukazatel, vytvořený makra. Název ukazatele můžete použít pro přístup k objektu výjimky v rámci `CATCH_ALL` bloku. Tato proměnná je deklarovaná za vás.

### <a name="remarks"></a>Poznámky

Kód zpracování výjimek můžete dotazování objekt výjimky, pokud je to vhodné, chcete-li získat další informace o konkrétní příčina výjimky. Vyvolat `THROW_LAST` – makro přesunout zpracování do dalšího snímku vnější výjimky. Pokud používáte **CATCH_ALL**, end **zkuste** blok s END_CATCH_ALL – makro.

> [!NOTE]
>  **CATCH_ALL** bloku je definován jako obor C++ je oddělená složené závorky. Při deklarování proměnné v tomto oboru, jsou přístupné pouze v daném oboru.

Další informace o výjimkách, najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="and_catch"></a>  AND_CATCH

Definuje blok kódu pro zachytávání typy další výjimka vyvolána v předchozích **zkuste** bloku.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_class*<br/>
Určuje typ výjimky pro testování. Seznam tříd výjimek standard najdete v tématu třídy [cexception –](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Název objekt výjimky ukazatel, který bude vytvořen pomocí makra. Název ukazatele můžete použít pro přístup k objektu výjimky v rámci **AND_CATCH** bloku. Tato proměnná je deklarovaná za vás.

### <a name="remarks"></a>Poznámky

Použijte makro CATCH pro zachycení jeden typ výjimky a pak AND_CATCH – makro zachytit jednotlivé následné typy. End **zkuste** blok s END_CATCH – makro.

Kód zpracování výjimek můžete dotazování objekt výjimky, pokud je to vhodné, chcete-li získat další informace o konkrétní příčina výjimky. THROW_LAST – makro v rámci volání **AND_CATCH** blokovat ke zpracování do dalšího snímku vnější výjimky. **AND_CATCH** označuje konec předchozí **CATCH** nebo **AND_CATCH** bloku.

> [!NOTE]
>  **AND_CATCH** bloku je definované jako obor C++ (která je oddělená složených závorek). Při deklarování proměnné v tomto oboru, mějte na paměti, že jsou přístupné pouze v daném oboru. To platí i pro *exception_object_pointer_name* proměnné.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CATCH](#catch).

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h
##  <a name="and_catch_all"></a>  AND_CATCH_ALL

Definuje blok kódu pro zachytávání typy další výjimka vyvolána v předchozích **zkuste** bloku.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer_name*<br/>
Název objekt výjimky ukazatel, který bude vytvořen pomocí makra. Název ukazatele můžete použít pro přístup k objektu výjimky v rámci **AND_CATCH_ALL** bloku. Tato proměnná je deklarovaná za vás.

### <a name="remarks"></a>Poznámky

Použití **CATCH** – makro zachytit jeden typ výjimky a pak AND_CATCH_ALL – makro zachytit všechny ostatní následující typy. Pokud používáte AND_CATCH_ALL, end **zkuste** blok s END_CATCH_ALL – makro.

Kód zpracování výjimek můžete dotazování objekt výjimky, pokud je to vhodné, chcete-li získat další informace o konkrétní příčina výjimky. THROW_LAST – makro v rámci volání **AND_CATCH_ALL** blokovat ke zpracování do dalšího snímku vnější výjimky. **AND_CATCH_ALL** označuje konec předchozí **CATCH** nebo **AND_CATCH_ALL** bloku.

> [!NOTE]
>  **AND_CATCH_ALL** bloku je definované jako obor C++ (která je oddělená složených závorek). Při deklarování proměnné v tomto oboru, mějte na paměti, že jsou přístupné pouze v daném oboru.

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="end_catch"></a>  END_CATCH

Označuje konec posledního **CATCH** nebo **AND_CATCH** bloku.

```
END_CATCH
```

### <a name="remarks"></a>Poznámky

Další informace o END_CATCH – makro, najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="end_catch_all"></a>  END_CATCH_ALL

Označuje konec posledního <strong>CATCH_ALL88 nebo ** AND_CATCH_ALL</strong> bloku.

```
END_CATCH_ALL
```

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="throw"></a>  THROW (MFC)

Vyvolá zadané výjimky.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parametry

*exception_object_pointer*<br/>
Odkazuje na objekt výjimky odvozený z `CException`.

### <a name="remarks"></a>Poznámky

**VYVOLAT** přerušení provádění, předávání přidružený ovládací prvek programu **CATCH** blokovat ve svém programu. Pokud jste ještě nezadali **CATCH** blokovat, pak řízení je předáno knihovny Microsoft Foundation Class modul, který zobrazí chybovou zprávu a ukončí.

Další informace najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="throw_last"></a>  THROW_LAST

Vyvolá výjimku zpět na další vnější **CATCH** bloku.

```
THROW_LAST()
```

### <a name="remarks"></a>Poznámky

Toto makro můžete místně vytvořený výjimku. Pokud se pokusíte vytvořit výjimku, která jste právě zachycena, bude obvykle dostanou mimo rozsah a odstranit. S **THROW_LAST**, výjimka je předána správně na novou **CATCH** obslužné rutiny.

Další informace najdete v článku [výjimky](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="afxthrowarchiveexception"></a>  Afxthrowarchiveexception –

Vyvolá výjimku archivu.

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parametry

*Příčina*<br/>
Určuje celé číslo označující důvod výjimky. Seznam možných hodnot najdete v tématu [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Odkazuje na řetězec obsahující název `CArchive` objekt, který způsobil výjimku (Pokud je k dispozici).

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="afxthrowfileexception"></a>  Afxthrowfileexception –

Vyvolá výjimku souborů.

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*Příčina*<br/>
Určuje celé číslo označující důvod výjimky. Seznam možných hodnot najdete v tématu [CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Obsahuje číslo chyby operačního systému (Pokud je k dispozici), který uvádí důvod výjimky. V příručce k operačního systému pro seznam kódů chyb.

*lpszFileName*<br/>
Odkazuje na řetězec obsahující název souboru, který způsobil výjimku (Pokud je k dispozici).

### <a name="remarks"></a>Poznámky

Je odpovědností zjistit příčinu založené na kód chyby operačního systému.

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

## <a name="afxthrowinvalidargexception"></a>  AfxThrowInvalidArgException

Vyvolá výjimku neplatný argument.

### <a name="syntax"></a>Syntaxe

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Poznámky

Tato funkce je volána, když se používají neplatné argumenty.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="afxthrowmemoryexception"></a>  Afxthrowmemoryexception –

Vyvolá výjimku paměti.

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Poznámky

Voláním této funkce, pokud volání základní systémové paměti alokátory (například **malloc** a [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) funkce Windows) nezdaří. Není potřeba ji volat **nové** protože **nové** vyvolá výjimka paměti automaticky pokud selhání přidělení paměti.

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="afxthrownotsupportedexception"></a>  AfxThrowNotSupportedException

Vyvolá výjimku, která je výsledkem požadavku nepodporované funkce.

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="afxthrowresourceexception"></a>  AfxThrowResourceException

Vyvolá výjimku prostředků.

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Poznámky

Nelze načíst prostředek Windows je obvykle voláním této funkce.

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="afxthrowuserexception"></a>  AfxThrowUserException

Vyvolá výjimku pro ukončení operace koncového uživatele.

```
void AfxThrowUserException();
```

### <a name="remarks"></a>Poznámky

Tato funkce je obvykle volána ihned po `AfxMessageBox` ohlásilo chybu pro uživatele.

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="afxthrowoledispatchexception"></a>  Afxthrowoledispatchexception –

Pomocí této funkce můžete vyvolat výjimku v rámci funkce automatizace OLE.

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
Kód chyby specifický pro aplikaci.

*lpszDescription*<br/>
Slovní popis chyby.

*nDescriptionID*<br/>
ID prostředku pro popis slovní chyby.

*nHelpID*<br/>
Kontextové nápovědy pro vaše aplikace nápovědy (. Soubor HLP).

### <a name="remarks"></a>Poznámky

Informace uvedené na této funkce lze zobrazit řízení aplikací (Microsoft Visual Basic nebo jiné aplikace klienta automatizace OLE).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="afxthrowoleexception"></a>  Afxthrowoleexception –

Vytvoří objekt typu `COleException` a vyvolá výjimku.

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parametry

*sc*<br/>
Stavový kód OLE, který označuje důvod výjimky.

*hr*<br/>
Zpracovat výsledek kódu, který označuje důvod výjimky.

### <a name="remarks"></a>Poznámky

Verze, která přijímá HRESULT jako argument převede na odpovídající SCODE tento kód výsledku. Další informace o HRESULT a SCODE najdete v tématu [struktura kódy chyb COM](/windows/desktop/com/structure-of-com-error-codes) v sadě Windows SDK.

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdao.h

##  <a name="afxthrowdaoexception"></a>  AfxThrowDaoException

Voláním této funkce vyvolá výjimku typu [cdaoexception –](../../mfc/reference/cdaoexception-class.md) z vlastního kódu.

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parametry

*nAfxDaoError*<br/>
Celočíselnou hodnotu představující DAO rozšířené kód chyby, které může být jedna z hodnot uveden v části [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror).

*scode*<br/>
OLE – kód chyby z rozhraní DAO, typu SCODE. Informace najdete v tématu [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Poznámky

Rozhraní volá také `AfxThrowDaoException`. Ve volání můžete předat jeden z parametrů nebo obojí. Například pokud chcete vyvolat jeden z chyby podle **CDaoException::nAfxDaoError** vám nevadí, ale *scode* parametr předat platný kód v *nAfxDaoError* parametr a přijměte výchozí hodnotu pro *scode*.

Informace o výjimkách týkající se tříd DAO knihovny MFC naleznete v tématu třídy `CDaoException` v této knihy a článek [výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afxdb.h

##  <a name="afxthrowdbexception"></a>  AfxThrowDBException

Voláním této funkce vyvolá výjimku typu `CDBException` z vlastního kódu.

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parametry

*nRetCode*<br/>
Hodnotu typu RETCODE definuje typ chyby, která způsobila vyvolání výjimky.

*pdb*<br/>
Ukazatel `CDatabase` objekt, který reprezentuje připojení zdroje dat, ke kterému je přidružené výjimky.

*hstmt*<br/>
Obslužná rutina HSTMT rozhraní ODBC, který určuje popisovač příkazu, ke kterému je přidružené výjimky.

### <a name="remarks"></a>Poznámky

Rámec volá `AfxThrowDBException` při dostane rozhraní ODBC RETCODE během volání funkce rozhraní ODBC API a interpretuje RETCODE jako výjimečné podmínce, spíše než chybu expectable. Operace přístupu k datům může například selhat z důvodu chyby čtení disku.

Informace o hodnotách RETCODE definované rozhraní ODBC naleznete v kapitole 8 "Načítání stavu a informací o chybě," v sadě Windows SDK. Informace o rozšíření MFC na tyto kódy najdete v tématu třídy [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

##  <a name="afxabort"></a>  Afxabort –

Výchozí funkce ukončení dodávané knihovnou MFC.

```
void  AfxAbort();
```

### <a name="remarks"></a>Poznámky

`AfxAbort` je volán interně MFC členské funkce při závažné chybě, jako je například vydá nezachycenou výjimku, která nelze zpracovat. Můžete volat `AfxAbort` ve výjimečných případech, kdy dojde katastrofální chyba, ze kterého nelze obnovit.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CATCH](#catch).

### <a name="requirements"></a>Požadavky

  **Hlavička** afx.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
[CException – třída](cexception-class.md)<br/>
[CInvalidArgException – třída](cinvalidargexception-class.md)
