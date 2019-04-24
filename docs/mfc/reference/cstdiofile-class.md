---
title: CStdioFile Class
ms.date: 11/04/2016
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
ms.openlocfilehash: fd42934107591905a1bbc273ee9eec4b37e58ea7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323801"
---
# <a name="cstdiofile-class"></a>CStdioFile Class

Představuje běhový streamový soubor C jako otevřený pomocí běhové funkce [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

## <a name="syntax"></a>Syntaxe

```
class CStdioFile : public CFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|Vytvoří `CStdioFile` objekt z ukazatele na cestu nebo soubor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CStdioFile::Open](#open)|Přetíženo. Otevřít je určený pro použití s výchozím `CStdioFile` konstruktoru (přepíše [CFile::Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::ReadString](#readstring)|Načte jeden řádek textu.|
|[CStdioFile::Seek](#seek)|Umístí ukazatel na aktuální soubor.|
|[CStdioFile::WriteString](#writestring)|Zapíše jeden řádek textu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Obsahuje ukazatel na otevřený soubor.|

## <a name="remarks"></a>Poznámky

Stream souborů jsou ukládány do vyrovnávací paměti a lze je otevřít v textovém režimu (výchozí) nebo binárním režimu.

Režim textové obsahuje speciální zpracování pro páry znaků CR návratový znak odřádkování. Při psaní nový řádek znak (0x0A) do textového režimu `CStdioFile` objektu, pár bajtů (0x0D, 0x0A) posílá do souboru. Při čtení bajtů pár (0x0D, 0x0A) se přeloží na jeden bajt 0x0A.

[Cfile –](../../mfc/reference/cfile-class.md) funkce [duplicitní](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), a [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nejsou podporovány pro `CStdioFile`.

Při volání těchto funkcí na `CStdioFile`, zobrazí se [cnotsupportedexception –](../../mfc/reference/cnotsupportedexception-class.md).

Další informace o používání `CStdioFile`, najdete v článcích [soubory v prostředí MFC](../../mfc/files-in-mfc.md) a [zpracování souborů](../../c-runtime-library/file-handling.md) v *Run-Time Library Reference*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="cstdiofile"></a>  CStdioFile::CStdioFile

Vytvoří a inicializuje `CStdioFile` objektu.

```
CStdioFile();
CStdioFile(CAtlTransactionManager* pTM);
  CStdioFile(FILE* pOpenStream);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parametry

*pOpenStream*<br/>
Ukazatel na soubor vrácený voláním funkce modulu runtime jazyka C určuje [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

*lpszFileName*<br/>
Určuje řetězec, který určuje cestu k souboru požadovaného. Cesta může být relativní nebo absolutní.

*nOpenFlags*<br/>
Určuje možnosti pro vytvoření souboru, sdílení souborů a režimy přístupu k souboru. Můžete zadat více možností s využitím bitový operátor OR ( **|** ) – operátor.

Jedna možnost režim přístupu k souboru se vyžaduje; jiné režimy jsou volitelné. Zobrazit [CFile::CFile](../../mfc/reference/cfile-class.md#cfile) seznam možností režimu a další příznaky. V prostředí MFC verze 3.0 nebo novější jsou povoleny příznaky sdílené složky.

*pTM*<br/>
Ukazatel na objekt catltransactionmanager –.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor se nepřipojí k souboru `CStdioFile` objektu. Při používání tohoto konstruktoru, je nutné použít `CStdioFile::Open` metodu pro otevření souboru a připojte ji k `CStdioFile` objektu.

Konstruktor jedním parametrem připojí otevření souboru datového proudu `CStdioFile` objektu. Povolené hodnoty ukazatele obsahují předdefinované vstupní a výstupní soubor ukazatele *stdin*, *stdout*, nebo *stderr*.

Vytvoří dvě parametr konstruktoru `CStdioFile` objektu a otevře odpovídající soubor s danou cestou.

Pokud předáte hodnotu NULL pro buď *pOpenStream* nebo *lpszFileName*, vyvolá konstruktor `CInvalidArgException*`.

Pokud soubor nejde otevřít nebo vytvořit, vyvolá konstruktor `CFileException*`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>  CStdioFile::m_pStream

`m_pStream` Datový člen je ukazatel na otevřený soubor vrácená rozhraním funkci run-time C `fopen`.

```
FILE* m_pStream;
```

### <a name="remarks"></a>Poznámky

To má hodnotu NULL, pokud soubor dosud nebyla otevřena nebo bylo ukončeno.

##  <a name="open"></a>  CStdioFile::Open

Přetíženo. Otevřít je určený pro použití s výchozím `CStdioFile` konstruktoru.

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Řetězec, který určuje cestu k souboru požadovaného. Cesta může být relativní nebo absolutní.

*nOpenFlags*<br/>
Režim sdílení a přístup. Určuje akci, která má provést při otevírání souboru. Možnosti lze kombinovat pomocí bitového operátoru OR (&#124;) – operátor. Jsou vyžadovány; jeden přístupová oprávnění a možnost jedna sdílená složka režimy modeCreate a modeNoInherit jsou volitelné.

*pError*<br/>
Ukazatel na existující objekt výjimky souborů, který se zobrazí stav operace, která selhala.

*pTM*<br/>
Ukazatel `CAtlTransactionManager` objektu.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="readstring"></a>  CStdioFile::ReadString

Přečte text data do vyrovnávací paměti, až limitu *Nmaximum*-1 znaků ze souboru spojené s `CStdioFile` objektu.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Určuje ukazatel do vyrovnávací paměti, zadané uživatele, který bude příjemcem řetězec zakončený hodnotou null text.

*nMax*<br/>
Určuje maximální počet znaků pro čtení, výčtu nebudou započteny ukončující znak null.

*rString*<br/>
Odkaz na `CString` objekt, který bude obsahovat řetězec, pokud funkce vrátí.

### <a name="return-value"></a>Návratová hodnota

Ukazatel do vyrovnávací paměti obsahující textová data. Hodnota NULL, pokud bylo dosaženo souboru bez přečtení všech dat; nebo pokud logická hodnota, FALSE, pokud ukončení souboru bylo dosaženo bez přečtení žádná data.

### <a name="remarks"></a>Poznámky

Čtení zastavena podle prvního znaku nového řádku. Pokud v takovém případě méně než tento počet *Nmaximum*přečetl(a) znaky-1, znak nového řádku jsou uloženy ve vyrovnávací paměti. V obou případech je připojen znak null ('\0').

[CFile::Read](../../mfc/reference/cfile-class.md#read) je k dispozici také pro režim textové zadání, ale neukončí na pár návratový znak odřádkování návrat na začátek řádku.

> [!NOTE]
>  `CString` Odebere verze této funkce `'\n'` Pokud jsou k dispozici; LPTSTR verze nepracuje.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>  CStdioFile::Seek

Přemístí ukazatel v dříve otevřený soubor.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOff*<br/>
Počet bajtů k přesunutí ukazatele.

*nFrom*<br/>
Režim pohyb ukazatele. Musí být jedna z následujících hodnot:

- `CFile::begin`: Přesuňte ukazatel na soubor *lOff* vpřed bajtů od začátku souboru.

- `CFile::current`: Přesuňte ukazatel na soubor *lOff* bajtů z aktuální pozice v souboru.

- `CFile::end`: Přesuňte ukazatel na soubor *lOff* bajtů z konce souboru. Všimněte si, že *lOff* musí být záporné vystavit do existujících souborů; kladné hodnoty pozice za koncem souboru.

### <a name="return-value"></a>Návratová hodnota

Pokud je možné, požadovanou pozici `Seek` vrátí nové posun bajtu od začátku souboru. V opačném případě není definováno návratovou hodnotu a `CFileException` objektu je vyvolána výjimka.

### <a name="remarks"></a>Poznámky

`Seek` Funkce umožňuje náhodný přístup k obsahu souboru přesunutím ukazatele zadanou velikost, relativně nebo vůbec. Během hledání ve skutečnosti nenačtou žádná data. Pokud požadovaný pozice je větší než velikost souboru, délka souboru bude možné rozšířit na této pozici a bude vyvolána žádná výjimka.

Když je soubor otevřen, ukazatel na soubor je umístěn na posunu 0, na začátek souboru.

Tato implementace `Seek` je založená na funkci Run-Time Library (CRT) `fseek`. Existuje několik omezení využití `Seek` u streamů otevřít v textovém režimu. Další informace najdete v tématu [fseek _fseeki64 –](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `Seek` přesunout ukazatel 1000 bajtů od začátku `cfile` souboru. Všimněte si, že `Seek` nenačítá data, takže lze následně zavolat [CStdioFile::ReadString](#readstring) číst data.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>  CStdioFile::WriteString

Zapisuje data ze vyrovnávací paměť do souboru spojené s `CStdioFile` objektu.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Určuje ukazatel do vyrovnávací paměti, která obsahuje řetězec zakončený hodnotou null.

### <a name="remarks"></a>Poznámky

Ukončující znak null ( `\0`) není zapsána do souboru. Tato metoda zapisuje znaky nového řádku *lpsz* do souboru jako dvojice návratový nebo odřádkování návrat na začátek řádku.

Pokud chcete zapisovat data, která nejsou zakončené znakem null do souboru, použijte `CStdioFile::Write` nebo [CFile::Write](../../mfc/reference/cfile-class.md#write).

Tato metoda vyvolá `CInvalidArgException*` Pokud zadáte hodnotu NULL pro *lpsz* parametru.

Tato metoda vyvolá `CFileException*` v reakci na chyby.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Viz také:

[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException – třída](../../mfc/reference/cnotsupportedexception-class.md)
