---
title: Třída CFileException
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
ms.openlocfilehash: 2d1025ca33d5641982ba52f1ac539db85df3bfd5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373895"
---
# <a name="cfileexception-class"></a>Třída CFileException

Představuje podmínku výjimky související se souborem.

## <a name="syntax"></a>Syntaxe

```
class CFileException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|Vytvoří `CFileException` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CFileException::Výjimka ErrnoToException](#errnotoexception)|Vrátí kód příčiny odpovídající číslu chyby za běhu.|
|[CFileException::GetErrorMessage](#geterrormessage)|Načte zprávu popisující výjimku.|
|[CFileException::OsErrorToException](#oserrortoexception)|Vrátí kód příčiny odpovídající kódu chyby operačního systému.|
|[CFileException::ThrowErrno](#throwerrno)|Vyvolá výjimku souboru na základě čísla chyby za běhu.|
|[CFileException::ThrowOsError](#throwoserror)|Vyvolá výjimku souboru na základě čísla chyby operačního systému.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CFileException::m_cause](#m_cause)|Obsahuje přenosný kód odpovídající příčině výjimky.|
|[CFileException::m_lOsError](#m_loserror)|Obsahuje související číslo chyby operačního systému.|
|[CFileException::m_strFileName](#m_strfilename)|Obsahuje název souboru pro tuto výjimku.|

## <a name="remarks"></a>Poznámky

Třída `CFileException` obsahuje veřejné datové členy, které obsahují kód přenosné příčiny a číslo chyby specifické pro operační systém. Třída také poskytuje statické členské funkce pro vyvolání výjimek souboru a pro vrácení kódů příčiny pro chyby operačního systému a chyby c run-time.

`CFileException`objekty jsou konstruovány a vyvolány v `CFile` členských funkcích a v členských funkcích odvozených tříd. K těmto objektům můžete přistupovat v rámci výrazu **CATCH.** Pro přenositelnost použijte pouze kód příčiny k získání důvodu výjimky. Další informace o výjimkách naleznete v článku [Zpracování výjimek (MFC).](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cfileexceptioncfileexception"></a><a name="cfileexception"></a>CFileException::CFileException

Vytvoří objekt, `CFileException` který ukládá kód příčiny a kód operačního systému v objektu.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*Způsobit*<br/>
Ve výčtu typ proměnné, která označuje důvod výjimky. Seznam možných hodnot naleznete v tématu [CFileException::m_cause.](#m_cause)

*Chyba iOs*<br/>
Operační systém specifický důvod pro výjimku, pokud je k dispozici. Parametr *iOsError* poskytuje více informací než *příčina.*

*lpszArchiveName*<br/>
Odkazuje na řetězec obsahující název `CFile` objektu, který způsobuje výjimku.

### <a name="remarks"></a>Poznámky

Nepoužívejte tento konstruktor přímo, ale spíše volat globální funkce [AfxThrowFileException](exception-processing.md#afxthrowfileexception).

> [!NOTE]
> Proměnná *chyba iOsError* `CFile` se `CStdioFile` vztahuje pouze na objekty a objekty. Třída `CMemFile` nezpracovává tento kód chyby.

## <a name="cfileexceptionerrnotoexception"></a><a name="errnotoexception"></a>CFileException::Výjimka ErrnoToException

Převede danou chybovou hodnotu knihovny za běhu na hodnotu `CFileException` chybové hodnoty s výčtem.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Parametry

*nErrno*<br/>
Celočíselný kód chyby definovaný v běhu zahrnout soubor ERRNO. H.

### <a name="return-value"></a>Návratová hodnota

Výčet hodnoty, která odpovídá dané hodnotě chyby knihovny za běhu.

### <a name="remarks"></a>Poznámky

Seznam možných výčtových hodnot naleznete v tématu [CFileException::m_cause.](#m_cause)

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

## <a name="cfileexceptiongeterrormessage"></a><a name="geterrormessage"></a>CFileException::GetErrorMessage

Načte text, který popisuje výjimku.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Parametry

*chyba lpsz*<br/>
[dovnitř, ven] Ukazatel na vyrovnávací paměť, která obdrží chybovou zprávu.

*nChyba*<br/>
[v] Maximální počet znaků, které může zadaná vyrovnávací paměť pojmout. To zahrnuje ukončující znak null.

*pnHelpContext*<br/>
[dovnitř, ven] Ukazatel na nepodepsané celé číslo, které obdrží ID kontextu nápovědy. Pokud `NULL`je vráceno žádné ID.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud byla metoda úspěšná; jinak FALSE.

### <a name="remarks"></a>Poznámky

Pokud je zadaná vyrovnávací paměť příliš malá, chybová zpráva je zkrácena.

### <a name="example"></a>Příklad

Následující příklad `CFileException::GetErrorMessage`používá .

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

## <a name="cfileexceptionm_cause"></a><a name="m_cause"></a>CFileException::m_cause

Obsahuje hodnoty definované `CFileException` ve výčtu typu.

```
int m_cause;
```

### <a name="remarks"></a>Poznámky

Tento datový člen je veřejná proměnná typu **int**. Čítači výčtu a jejich význam jsou následující:

- `CFileException::none`0: Nedošlo k žádné chybě.

- `CFileException::genericException`1: Došlo k nespecifikované chybě.

- `CFileException::fileNotFound`2: Soubor nelze nalézt.

- `CFileException::badPath`3: Celá cesta nebo její část je neplatná.

- `CFileException::tooManyOpenFiles`4: Povolený počet otevřených souborů byl překročen.

- `CFileException::accessDenied`5: Soubor nelze získat přístup.

- `CFileException::invalidFile`6: Došlo k pokusu o použití neplatného popisovače souboru.

- `CFileException::removeCurrentDir`7: Aktuální pracovní adresář nelze odebrat.

- `CFileException::directoryFull`8: Neexistují žádné další položky adresáře.

- `CFileException::badSeek`9: Při pokusu o nastavení ukazatele souboru došlo k chybě.

- `CFileException::hardIO`10: Došlo k chybě hardwaru.

- `CFileException::sharingViolation`11: PODÍL. EXE nebyl načten nebo byla uzamčena sdílená oblast.

- `CFileException::lockViolation`12: Došlo k pokusu o uzamčení oblasti, která již byla uzamčena.

- `CFileException::diskFull`14: Disk je plný.

- `CFileException::endOfFile`15: Bylo dosaženo konce souboru.

    > [!NOTE]
    >  Tyto `CFileException` příčiny výčtu se `CArchiveException` liší od čítače výčtu příčiny.

    > [!NOTE]
    > `CArchiveException::generic`je zastaralé. Místo toho použijte `genericException`. Pokud **obecný** se používá v aplikaci a je sestaven s /clr, výsledné chyby syntaxe není snadné rozluštit.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

## <a name="cfileexceptionm_loserror"></a><a name="m_loserror"></a>CFileException::m_lOsError

Obsahuje kód chyby operačního systému pro tuto výjimku.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Poznámky

Seznam kódů chyb naleznete v technické příručce operačního systému. Tento datový člen je veřejná proměnná typu LONG.

## <a name="cfileexceptionm_strfilename"></a><a name="m_strfilename"></a>CFileException::m_strFileName

Obsahuje název souboru pro tuto podmínku výjimky.

```
CString m_strFileName;
```

## <a name="cfileexceptionoserrortoexception"></a><a name="oserrortoexception"></a>CFileException::OsErrorToException

Vrátí čítač výčtu, který odpovídá dané hodnotě *iOsError.* Pokud není kód chyby znám, `CFileException::generic`vrátí funkce program .

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Parametry

*Chyba iOs*<br/>
Kód chyby specifický pro operační systém.

### <a name="return-value"></a>Návratová hodnota

Výčet hodnoty, která odpovídá dané hodnotě chyby operačního systému.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

## <a name="cfileexceptionthrowerrno"></a><a name="throwerrno"></a>CFileException::ThrowErrno

Vytvoří `CFileException` objekt odpovídající dané hodnotě *nErrno* a pak vyvolá výjimku.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*nErrno*<br/>
Celočíselný kód chyby definovaný v běhu zahrnout soubor ERRNO. H.

*název souboru lpsz*<br/>
Ukazatel na řetězec obsahující název souboru, který způsobil výjimku, pokud je k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

## <a name="cfileexceptionthrowoserror"></a><a name="throwoserror"></a>CFileException::ThrowOsError

Vyvolá `CFileException` odpovídající hodnotu *iOsError.* Pokud kód chyby není znám, pak funkce vyvolá `CFileException::generic`výjimku kódovkou jako .

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*Chyba iOs*<br/>
Kód chyby specifický pro operační systém.

*název souboru lpsz*<br/>
Ukazatel na řetězec obsahující název souboru, který způsobil výjimku, pokud je k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Viz také

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Zpracování výjimek](../../mfc/reference/exception-processing.md)
