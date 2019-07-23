---
title: CStdioFile – třída
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
ms.openlocfilehash: 068e59fdc19821487bc78141d10743363221518e
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375846"
---
# <a name="cstdiofile-class"></a>CStdioFile – třída

Představuje soubor běhového streamu jazyka C, který je otevřen funkcí run-time [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

## <a name="syntax"></a>Syntaxe

```
class CStdioFile : public CFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|`CStdioFile` Vytvoří objekt z cesty nebo ukazatele na soubor.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CStdioFile::Open](#open)|Přetíženo. Otevřít je navrženo pro použití s výchozím `CStdioFile` konstruktorem (Overrides [CFile –:: Open](../../mfc/reference/cfile-class.md#open)).|
|[CStdioFile::ReadString](#readstring)|Přečte jeden řádek textu.|
|[CStdioFile:: Seek](#seek)|Umístí ukazatel na aktuální soubor.|
|[CStdioFile::WriteString](#writestring)|Zapíše jeden řádek textu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Obsahuje ukazatel na otevřený soubor.|

## <a name="remarks"></a>Poznámky

Soubory streamu se ukládají do vyrovnávací paměti a dají se otevřít v textovém režimu (ve výchozím nastavení) nebo v binárním režimu.

Režim textu poskytuje speciální zpracování pro páry kanálů návratového řádku. Když do objektu textového režimu `CStdioFile` napíšete znak řádku (nový řádek) (0x0A), do souboru se pošle pár bajtů (0x0D, 0x0A). Při čtení je dvojice bajtů (0x0D, 0x0A) přeložena na jeden bajt 0x0A.

Funkce [CFile –](../../mfc/reference/cfile-class.md) jsou [duplicitní](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)a [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nejsou podporovány pro `CStdioFile`.

Pokud voláte tyto funkce na `CStdioFile`, získáte [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Další `CStdioFile`informace o použití naleznete v článcích [soubory v knihovně MFC](../../mfc/files-in-mfc.md) a [zpracování souborů](../../c-runtime-library/file-handling.md) v *Referenční příručce ke knihovně run-time*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFile –](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="cstdiofile"></a>CStdioFile::CStdioFile

Vytvoří a inicializuje `CStdioFile` objekt.

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
Určuje ukazatel na soubor vrácený voláním běhové funkce jazyka C [fopen](../../c-runtime-library/reference/fopen-wfopen.md).

*lpszFileName*<br/>
Určuje řetězec, který je cestou k požadovanému souboru. Cesta může být relativní nebo absolutní.

*nOpenFlags*<br/>
Určuje možnosti pro vytvoření souboru, sdílení souborů a režimy přístupu k souborům. Pomocí bitového operátoru OR ( **|** ) lze zadat více možností.

Jedna možnost režimu přístupu k souboru je povinná; jiné režimy jsou volitelné. Seznam možností režimu a dalších příznaků naleznete v tématu [CFile –:: CFile –](../../mfc/reference/cfile-class.md#cfile) . V knihovně MFC verze 3,0 a novější jsou příznaky sdílení povoleny.

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor nepřipojuje soubor k `CStdioFile` objektu. Při použití tohoto konstruktoru je nutné použít `CStdioFile::Open` metodu k otevření souboru a jeho připojení `CStdioFile` k objektu.

Konstruktor s jedním parametrem připojí k `CStdioFile` objektu otevřený datový proud souboru. Povolené hodnoty ukazatelů zahrnují předdefinované vstupně-výstupní vstupy ukazatelů *stdin*, *stdout*nebo *stderr*.

Konstruktor dvou parametrů vytvoří `CStdioFile` objekt a otevře odpovídající soubor s danou cestou.

Pokud předáte hodnotu NULL pro buď *pOpenStream* nebo *lpszFileName*, `CInvalidArgException*`konstruktor vyvolá.

Pokud soubor nelze otevřít nebo vytvořit, vyvolá `CFileException*`konstruktor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>  CStdioFile::m_pStream

Datový člen je ukazatel na otevřený soubor, který byl vrácen funkcí `fopen`run-time jazyka C. `m_pStream`

```
FILE* m_pStream;
```

### <a name="remarks"></a>Poznámky

Má hodnotu NULL, pokud soubor nebyl nikdy otevřen nebo byl zavřen.

##  <a name="open"></a>CStdioFile:: Open

Přetíženo. Otevřít je navrženo pro použití s výchozím `CStdioFile` konstruktorem.

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
Řetězec, který představuje cestu k požadovanému souboru. Cesta může být relativní nebo absolutní.

*nOpenFlags*<br/>
Režim sdílení a přístupu. Určuje akci, která se má provést při otevírání souboru. Možnosti lze kombinovat pomocí operátoru bitového operátoru OR&#124;(). Vyžaduje se jedno oprávnění k přístupu a jedna možnost sdílení. režimy modeCreate a modeNoInherit jsou volitelné.

*pError*<br/>
Ukazatel na existující objekt s výjimkou souboru, který obdrží stav operace, která selhala.

*pTM*<br/>
Ukazatel na `CAtlTransactionManager` objekt.

### <a name="return-value"></a>Návratová hodnota

TRUE v případě úspěchu; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

##  <a name="readstring"></a>CStdioFile::ReadString

Přečte textová data do vyrovnávací paměti, až do limitu *nmaximum*-1 znaků, ze souboru přidruženého `CStdioFile` k objektu.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Určuje ukazatel na vyrovnávací paměť zadanou uživatelem, která bude přijímat textový řetězec zakončený hodnotou null.

*Nmaximum*<br/>
Určuje maximální počet znaků, které mají být čteny, a nepočítá ukončující znak null.

*rString*<br/>
Odkaz na `CString` objekt, který bude obsahovat řetězec, když funkce vrátí.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyrovnávací paměť obsahující textová data. Hodnota NULL, pokud bylo dosaženo konce souboru bez čtení dat; nebo pokud logická hodnota, FALSE, pokud bylo dosaženo konce souboru, bez čtení jakýchkoli dat.

### <a name="remarks"></a>Poznámky

Čtení je zastaveno prvním znakem nového řádku. Pokud v takovém případě bylo přečteno méně než *nmaximum*znaků, bude ve vyrovnávací paměti uložen znak nového řádku. Znak null (' \ 0 ') je připojen v obou případech.

[CFile –:: Read](../../mfc/reference/cfile-class.md#read) je také k dispozici pro vstup v textovém režimu, ale nekončí dvojicí kanálu návratového řádku.

> [!NOTE]
>  Verze této funkce `'\n'` odebere, pokud je k dispozici; verze LPTStr není. `CString`

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>CStdioFile:: Seek

Přemístí ukazatel v dříve otevřeném souboru.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOff*<br/>
Počet bajtů, na které se má ukazatel přesunout

*Nze*<br/>
Režim pohybu ukazatele Musí být jedna z následujících hodnot:

- `CFile::begin`: Přesuňte ukazatel na soubor *lOff* bajty vpřed od začátku souboru.

- `CFile::current`: Přesuňte ukazatel na soubor *lOff* bajtů z aktuální pozice v souboru.

- `CFile::end`: Přesuňte ukazatel na soubor *lOff* bajtů z konce souboru. Všimněte si, že *lOff* musí být negativní, aby bylo možné hledat v existujícím souboru. kladné hodnoty budou hledat za koncem souboru.

### <a name="return-value"></a>Návratová hodnota

Pokud je požadovaná pozice platná, `Seek` vrátí nový posun bajtů od začátku souboru. V opačném případě není návratová hodnota definována a `CFileException` je vyvolána výjimka objektu.

### <a name="remarks"></a>Poznámky

`Seek` Funkce umožňuje náhodný přístup k obsahu souboru přesunutím ukazatele na určenou hodnotu, absolutní nebo relativně. Během hledání nejsou ve skutečnosti čtena žádná data. Pokud je požadovaná pozice větší než velikost souboru, bude délka souboru rozšířena na tuto pozici a nebude vyvolána žádná výjimka.

Když se soubor otevře, ukazatel na soubor se umístí na posun 0, začátek souboru.

Tato implementace `Seek` je založena na funkci `fseek`knihovny run-time (CRT). Existuje několik omezení používání `Seek` na datových proudech otevřených v textovém režimu. Další informace najdete v tématu [fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, jak použít `Seek` k přesunutí ukazatele 1000 bajtů od začátku `cfile` souboru. Všimněte si `Seek` , že nečtou data, takže musíte následně zavolat [CStdioFile:: ReadString](#readstring) pro čtení dat.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>CStdioFile::WriteString

Zapisuje data z vyrovnávací paměti do souboru přidruženého `CStdioFile` k objektu.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Určuje ukazatel na vyrovnávací paměť, která obsahuje řetězec zakončený hodnotou null.

### <a name="remarks"></a>Poznámky

Ukončující znak null ( `\0`) není zapsán do souboru. Tato metoda zapisuje znaky nového řádku v *lpsz* do souboru jako dvojici kanálů pro návrat na začátek řádku.

Pokud chcete zapisovat data, která nejsou zakončená hodnotou null, do souboru, použijte `CStdioFile::Write` nebo [CFile –:: Write](../../mfc/reference/cfile-class.md#write).

Tato metoda vyvolá výjimku `CInvalidArgException*` , pokud pro parametr *lpsz* zadáte hodnotu null.

Tato metoda vyvolá výjimku `CFileException*` v reakci na chyby systému souborů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Viz také:

[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[CFile –::D uplikovat](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile –:: LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile –:: UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException – třída](../../mfc/reference/cnotsupportedexception-class.md)
