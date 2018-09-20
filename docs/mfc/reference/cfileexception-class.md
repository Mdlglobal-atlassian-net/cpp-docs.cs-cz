---
title: Cfileexception – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d6230e488bdcca6f21e6c867c86c86f18a05bbe
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441457"
---
# <a name="cfileexception-class"></a>Cfileexception – třída

Představuje podmínku výjimky vztahující se k souboru.

## <a name="syntax"></a>Syntaxe

```
class CFileException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|Vytvoří `CFileException` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|Vrátí způsobit, že kód odpovídající počet chyb za běhu.|
|[CFileException::GetErrorMessage](#geterrormessage)|Načte zpráva popisující výjimku.|
|[CFileException::OsErrorToException](#oserrortoexception)|Vrátí kód příčina odpovídající kód chyby operačního systému.|
|[CFileException::ThrowErrno](#throwerrno)|Vyvolá výjimku souborů podle čísla chyby modulu runtime.|
|[CFileException::ThrowOsError](#throwoserror)|Vyvolá výjimku souborů založené na číslo chyby operačního systému.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CFileException::m_cause](#m_cause)|Obsahuje přenositelný kód odpovídá příčina výjimky.|
|[CFileException::m_lOsError](#m_loserror)|Obsahuje číslo související chyby operačního systému.|
|[CFileException::m_strFileName](#m_strfilename)|Obsahuje název souboru pro tuto výjimku.|

## <a name="remarks"></a>Poznámky

`CFileException` Třída zahrnuje veřejné datové členy, které obsahují kód přenosný příčina a číslo chyby operačního systému – konkrétní. Třída také poskytuje statické členské funkce pro generování souboru výjimek a vrácení kódů příčiny chyby operačního systému a C chybám za běhu.

`CFileException` objekty jsou vytvořena a vyvolána `CFile` členské funkce a v členské funkce odvozené třídy. Můžete přístup k těmto objektům v rámci oboru **CATCH** výrazu. Pro přenositelnost můžete použijte pouze kód příčina získáte z důvodu výjimky. Další informace o výjimkách, najdete v článku [zpracování výjimek (MFC)](../../mfc/exception-handling-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="cfileexception"></a>  CFileException::CFileException

Vytvoří `CFileException` objekt, který uchovává příčina kód a kód operačního systému v objektu.

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>Parametry

*Příčina*<br/>
Proměnná výčtového typu, který označuje důvod výjimky. Zobrazit [CFileException::m_cause](#m_cause) seznam možných hodnot.

*lOsError*<br/>
Z důvodu provozních konkrétní systém pro výjimku, pokud je k dispozici. *LOsError* parametr obsahuje více informace než *způsobit* nepodporuje.

*lpszArchiveName*<br/>
Odkazuje na řetězec obsahující název `CFile` objekt, který způsobil výjimku.

### <a name="remarks"></a>Poznámky

Nepoužívejte tento konstruktor přímo, ale místo toho volat funkci globální [afxthrowfileexception –](exception-processing.md#afxthrowfileexception).

> [!NOTE]
>  Proměnná *lOsError* platí jenom pro `CFile` a `CStdioFile` objekty. `CMemFile` Třídy nezpracovává tomto kódu chyby.

##  <a name="errnotoexception"></a>  CFileException::ErrnoToException

Převede hodnotu na chyby dané knihovny run-time `CFileException` chybovou hodnotu ve výčtu.

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>Parametry

*nErrno*<br/>
Celé číslo chybový kód definovaný v souboru zahrnutí za běhu ERRNO. H.

### <a name="return-value"></a>Návratová hodnota

Výčtová hodnota, která odpovídá chybovou hodnotu daného knihovny run-time.

### <a name="remarks"></a>Poznámky

Zobrazit [CFileException::m_cause](#m_cause) seznam možných hodnot výčtu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

##  <a name="geterrormessage"></a>  CFileException::GetErrorMessage

Načte text, který popisuje výjimku.

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>Parametry

*lpszError*<br/>
[out v] Ukazatel do vyrovnávací paměti, která obdrží chybovou zprávu.

*nMaxError*<br/>
[in] Maximální počet znaků, které může obsahovat zadané vyrovnávací paměti. To zahrnuje ukončující znak null.

*pnHelpContext*<br/>
[out v] Ukazatel na celé číslo bez znaménka, která přijímá ID kontextové nápovědy Pokud `NULL`, je vrácena žádná ID.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud metoda byla úspěšná. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud zadané vyrovnávací paměti je příliš malá, je zkrátí chybovou zprávu.

### <a name="example"></a>Příklad

Následující příklad používá `CFileException::GetErrorMessage`.

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

##  <a name="m_cause"></a>  CFileException::m_cause

Obsahuje hodnoty, které jsou definované `CFileException` výčtového typu.

```
int m_cause;
```

### <a name="remarks"></a>Poznámky

Tento datový člen je veřejná proměnná typu **int**. Čítačů a jejich význam jsou následující:

- `CFileException::none` 0: nedošlo k žádné chybě.

- `CFileException::genericException` 1: došlo k nespecifikované chybě.

- `CFileException::fileNotFound` 2: soubor nebyl nalezen.

- `CFileException::badPath` 3: všechny nebo část cesty je neplatný.

- `CFileException::tooManyOpenFiles` 4: byl překročen povolený počet otevřených souborů.

- `CFileException::accessDenied` 5: soubor není přístupný.

- `CFileException::invalidFile` 6: došlo k pokusu o použití neplatný popisovač souboru.

- `CFileException::removeCurrentDir` 7: aktuální pracovní adresář nejde odebrat.

- `CFileException::directoryFull` 8: neexistují žádné záznamy adresářů.

- `CFileException::badSeek` 9: došlo k chybě při pokusu o nastavení ukazatele souboru.

- `CFileException::hardIO` 10: došlo k chybě hardwaru.

- `CFileException::sharingViolation` 11: SDÍLENÁ SLOŽKA. Soubor EXE nebyla načtena, nebo byla sdílená oblast uzamčena.

- `CFileException::lockViolation` 12: došlo pokusu o uzamčení oblasti, která již byla uzamčena.

- `CFileException::diskFull` 14: disk je plný.

- `CFileException::endOfFile` 15: bylo dosaženo konce souboru.

    > [!NOTE]
    >  Tyto `CFileException` příčina enumerátory se liší od `CArchiveException` způsobit enumerátory.

    > [!NOTE]
    > `CArchiveException::generic` je zastaralý. Místo nich se používá `genericException`. Pokud **obecný** se použijí v aplikaci a vytvořené s parametrem/CLR, výslednou syntaxi chyby nejsou snadno dekódovat.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

##  <a name="m_loserror"></a>  CFileException::m_lOsError

Obsahuje kód chyby operačního systému: pro tuto výjimku.

```
LONG m_lOsError;
```

### <a name="remarks"></a>Poznámky

V příručce k operačního systému technical seznam kódů chyb. Tento datový člen je veřejná proměnná typu LONG.

##  <a name="m_strfilename"></a>  CFileException::m_strFileName

Obsahuje název souboru pro tuto podmínku.

```
CString m_strFileName;
```

##  <a name="oserrortoexception"></a>  CFileException::OsErrorToException

Vrátí enumerátor, který odpovídá daný *lOsError* hodnotu. Pokud neznámý kód chyby, vrátí funkce `CFileException::generic`.

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>Parametry

*lOsError*<br/>
Kód chyby operačního systému – konkrétní.

### <a name="return-value"></a>Návratová hodnota

Výčtová hodnota, která odpovídá hodnotě dané chybě operačního systému.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

##  <a name="throwerrno"></a>  CFileException::ThrowErrno

Vytvoří `CFileException` odpovídající objekt daného *nErrno* hodnotu a potom vyvolá výjimku.

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*nErrno*<br/>
Celé číslo chybový kód definovaný v souboru zahrnutí za běhu ERRNO. H.

*lpszFileName*<br/>
Ukazatel na řetězec obsahující název souboru, který výjimku způsobila, pokud je k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

##  <a name="throwoserror"></a>  CFileException::ThrowOsError

Vyvolá výjimku `CFileException` odpovídající danou *lOsError* hodnotu. Pokud neznámý kód chyby, pak funkce vyvolá výjimku kódovat jako `CFileException::generic`.

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parametry

*lOsError*<br/>
Kód chyby operačního systému – konkrétní.

*lpszFileName*<br/>
Ukazatel na řetězec obsahující název souboru, který výjimku způsobila, pokud je k dispozici.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>Viz také

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Zpracování výjimek](../../mfc/reference/exception-processing.md)



