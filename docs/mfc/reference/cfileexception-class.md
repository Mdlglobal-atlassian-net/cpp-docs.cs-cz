---
title: CFileException – třída
ms.date: 11/04/2016
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
ms.openlocfilehash: a3514c76d4136fe2bc0b096cc382e6f7f4dd3392
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418648"
---
# <a name="cfileexception-class"></a>CFileException – třída

Představuje podmínku výjimky vztahující se k souboru.

## <a name="syntax"></a>Syntaxe

```
class CFileException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|Vytvoří objekt `CFileException`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|Vrátí příčinu kódu odpovídající běhovému číslu chyby.|
|[CFileException:: GetErrorMessage](#geterrormessage)|Načte zprávu popisující výjimku.|
|[CFileException::OsErrorToException](#oserrortoexception)|Vrátí kód příčiny odpovídající kódu chyby operačního systému.|
|[CFileException::ThrowErrno](#throwerrno)|Vyvolá výjimku souboru na základě čísla běhové chyby.|
|[CFileException::ThrowOsError](#throwoserror)|Vyvolá výjimku souboru na základě čísla chyby operačního systému.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CFileException:: m_cause](#m_cause)|Obsahuje přenosný kód odpovídající výjimce výjimky.|
|[CFileException:: m_lOsError](#m_loserror)|Obsahuje související číslo chyby operačního systému.|
|[CFileException:: m_strFileName](#m_strfilename)|Obsahuje název souboru pro tuto výjimku.|

## <a name="remarks"></a>Poznámky

Třída `CFileException` zahrnuje veřejné datové členy, které obsahují přenosný kód příčiny a číslo chyby specifické pro operační systém. Třída také poskytuje statické členské funkce pro vyvolávání výjimek souborů a vrácení kódů příčin pro chyby operačního systému a běhové chyby jazyka C.

objekty `CFileException` jsou vytvářeny a vyvolány v `CFile` členských funkcích a v členských funkcích odvozených tříd. K těmto objektům máte přístup v rámci rozsahu výrazu **catch** . Pro přenositelnost použijte k získání důvodu výjimky pouze kód příčiny. Další informace o výjimkách naleznete v článku [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CException –](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="cfileexception"></a>CFileException::CFileException

Vytvoří objekt `CFileException`, který ukládá kód příčiny a kód operačního systému v objektu.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*způsobit*<br/>
Proměnná výčtového typu, která určuje důvod výjimky. Seznam možných hodnot naleznete v tématu [CFileException:: m_cause](#m_cause) .

*lOsError*<br/>
Důvod pro výjimku specifický pro operační systém, je-li k dispozici. Parametr *lOsError* poskytuje více informací, než *způsobuje* .

*lpszArchiveName*<br/>
Odkazuje na řetězec obsahující název objektu `CFile`, který způsobil výjimku.

### <a name="remarks"></a>Poznámky

Nepoužívejte tento konstruktor přímo, ale místo toho volejte globální funkci [AfxThrowFileException](exception-processing.md#afxthrowfileexception).

> [!NOTE]
>  Proměnná *lOsError* se vztahuje pouze na objekty `CFile` a `CStdioFile`. Třída `CMemFile` nezpracovává tento kód chyby.

##  <a name="errnotoexception"></a>CFileException::ErrnoToException

Převede zadanou hodnotu chyby běhové knihovny na `CFileException` výčtovou hodnotu chyby.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Parametry

*nErrno*<br/>
Celočíselný kód chyby, jak je definován v souboru include run-time ERRNO. Y.

### <a name="return-value"></a>Návratová hodnota

Hodnota výčtu, která odpovídá dané chybové hodnotě běhové knihovny.

### <a name="remarks"></a>Poznámky

Seznam možných hodnot výčtu naleznete v tématu [CFileException:: m_cause](#m_cause) .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

##  <a name="geterrormessage"></a>CFileException:: GetErrorMessage

Načte text, který popisuje výjimku.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszError*<br/>
[in, out] Ukazatel na vyrovnávací paměť, která obdrží chybovou zprávu.

*nMaxError*<br/>
pro Maximální počet znaků, které může zadaná vyrovnávací paměť uchovávat. To zahrnuje ukončující znak null.

*pnHelpContext*<br/>
[in, out] Ukazatel na unsigned integer, který obdrží ID kontextové aplikace Help. Pokud `NULL`, nevrátí se žádné ID.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud je zadaná vyrovnávací paměť příliš malá, chybová zpráva se zkrátí.

### <a name="example"></a>Příklad

Následující příklad používá `CFileException::GetErrorMessage`.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

##  <a name="m_cause"></a>CFileException:: m_cause

Obsahuje hodnoty definované výčtovým typem `CFileException`.

```
int m_cause;
```

### <a name="remarks"></a>Poznámky

Tento datový člen je veřejná proměnná typu **int**. Enumerátory a jejich významy jsou následující:

- `CFileException::none` 0: nedošlo k žádné chybě.

- `CFileException::genericException` 1: došlo k neurčené chybě.

- `CFileException::fileNotFound` 2: soubor se nepovedlo najít.

- `CFileException::badPath` 3: celá cesta nebo část cesty není platná.

- `CFileException::tooManyOpenFiles` 4: byl překročen povolený počet otevřených souborů.

- `CFileException::accessDenied` 5: soubor není k dispozici.

- `CFileException::invalidFile` 6: došlo k pokusu o použití neplatného popisovače souboru.

- `CFileException::removeCurrentDir` 7: aktuální pracovní adresář nelze odebrat.

- `CFileException::directoryFull` 8: nejsou k dispozici žádné další položky adresáře.

- `CFileException::badSeek` 9: při pokusu o nastavení ukazatele na soubor došlo k chybě.

- `CFileException::hardIO` 10: došlo k chybě hardwaru.

- `CFileException::sharingViolation` 11: sdílení. Soubor EXE nebyl načten nebo byla sdílená oblast uzamčena.

- `CFileException::lockViolation` 12: došlo k pokusu o uzamčení oblasti, která již byla uzamčena.

- `CFileException::diskFull` 14: disk je plný.

- `CFileException::endOfFile` 15: bylo dosaženo konce souboru.

    > [!NOTE]
    >  Tyto `CFileException` způsobují, že enumerátory jsou odlišné od `CArchiveException` způsobujících výčty.

    > [!NOTE]
    > `CArchiveException::generic` je zastaralá. Místo toho použijte `genericException`. Pokud je v aplikaci použito **Obecné** a sestavené s možností/CLR, nejsou výsledné chyby syntaxe snadno čitelné.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

##  <a name="m_loserror"></a>CFileException:: m_lOsError

Obsahuje kód chyby operačního systému pro tuto výjimku.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Poznámky

Seznam chybových kódů najdete v technické příručce k operačnímu systému. Tento datový člen je veřejná proměnná typu LONG.

##  <a name="m_strfilename"></a>CFileException:: m_strFileName

Obsahuje název souboru pro tuto podmínku výjimky.

```
CString m_strFileName;
```

##  <a name="oserrortoexception"></a>CFileException::OsErrorToException

Vrátí enumerátor, který odpovídá zadané hodnotě *lOsError* . Pokud kód chyby není znám, funkce vrátí `CFileException::generic`.

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Parametry

*lOsError*<br/>
Kód chyby specifický pro operační systém.

### <a name="return-value"></a>Návratová hodnota

Hodnota výčtu, která odpovídá zadané hodnotě chyby operačního systému.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

##  <a name="throwerrno"></a>CFileException::ThrowErrno

Vytvoří objekt `CFileException` odpovídající dané hodnotě *nErrno* a potom vyvolá výjimku.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*nErrno*<br/>
Celočíselný kód chyby, jak je definován v souboru include run-time ERRNO. Y.

*lpszFileName*<br/>
Ukazatel na řetězec obsahující název souboru, který způsobil výjimku, je-li k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

##  <a name="throwoserror"></a>CFileException::ThrowOsError

Vyvolá `CFileException` odpovídající dané hodnotě *lOsError* . Pokud kód chyby není znám, funkce vyvolá výjimku kódovanou jako `CFileException::generic`.

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*lOsError*<br/>
Kód chyby specifický pro operační systém.

*lpszFileName*<br/>
Ukazatel na řetězec obsahující název souboru, který způsobil výjimku, je-li k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Viz také

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Zpracování výjimek](../../mfc/reference/exception-processing.md)
