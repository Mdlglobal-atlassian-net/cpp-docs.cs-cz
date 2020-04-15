---
title: CStdioFile – třída
ms.date: 08/29/2019
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
ms.openlocfilehash: 80ee65aa339a38b3d8434bc4c7cb977e263f037b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366019"
---
# <a name="cstdiofile-class"></a>CStdioFile – třída

Představuje soubor datového proudu C, který byl otevřen [fopen](../../c-runtime-library/reference/fopen-wfopen.md)funkcí run-time .

## <a name="syntax"></a>Syntaxe

```
class CStdioFile : public CFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|Vytvoří `CStdioFile` objekt z cesty nebo ukazatele souboru.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CStdioFile::Otevřít](#open)|Přetíženo. Open je určen pro `CStdioFile` použití s výchozím konstruktorem (Přepsání [CFile::Open).](../../mfc/reference/cfile-class.md#open)|
|[CStdioFile::Řetězec čtení](#readstring)|Přečte jeden řádek textu.|
|[CStdioFile::Hledat](#seek)|Umístí aktuální ukazatel souboru.|
|[CStdioFile::Zápis](#writestring)|Zapíše jeden řádek textu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|Obsahuje ukazatel na otevřený soubor.|

## <a name="remarks"></a>Poznámky

Soubory datového proudu jsou uloženy do vyrovnávací paměti a lze je otevřít v textovém režimu (výchozí) nebo v binárním režimu.

Režim textu poskytuje speciální zpracování pro dvojice posuvu zpětného řádku vozíku. Při zápisu znaku přívozního řádku (nový řádek) `CStdioFile` (0x0A) do objektu textového režimu je do souboru odeslán bajtový pár (0x0D, 0x0A). Při čtení je bajtový pár (0x0D, 0x0A) přeložen na jeden bajt 0x0A.

[Funkce CFile](../../mfc/reference/cfile-class.md) [Duplicate](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange)a [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nejsou podporovány pro `CStdioFile`.

Pokud voláte tyto `CStdioFile`funkce na , získáte [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Další informace o `CStdioFile`použití naleznete v článcích [Soubory v knihovně MFC](../../mfc/files-in-mfc.md) a [Zpracování souborů](../../c-runtime-library/file-handling.md) v *odkazu knihovny run-time*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cstdiofilecstdiofile"></a><a name="cstdiofile"></a>CStdioFile::CStdioFile

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
Určuje ukazatel souboru vrácený voláním funkce c [fopen](../../c-runtime-library/reference/fopen-wfopen.md)run-time.

*název souboru lpsz*<br/>
Určuje řetězec, který je cestou k požadovanému souboru. Cesta může být relativní nebo absolutní.

*nOpenFlags*<br/>
Určuje možnosti pro režimy vytváření souborů, sdílení souborů a přístupu k souborům. Můžete určit více možností pomocí bitového **|** operátoru OR ( ).

Je vyžadována jedna možnost režimu přístupu k souborům; ostatní režimy jsou volitelné. Seznam možností režimu a dalších příznaků naleznete v tématu [CFile::CFile.](../../mfc/reference/cfile-class.md#cfile) V knihovně MFC verze 3.0 a novější chod sdílené položky jsou povoleny.

*Ptm*<br/>
Ukazatel na catltransactionmanager objektu.

### <a name="remarks"></a>Poznámky

Výchozí konstruktor nepřipojí k objektu `CStdioFile` soubor. Při použití tohoto konstruktoru `CStdioFile::Open` je nutné použít metodu k `CStdioFile` otevření souboru a jeho připojení k objektu.

Jednoparametrový konstruktor připojí k objektu `CStdioFile` otevřený datový proud souboru. Povolené hodnoty ukazatele zahrnují předdefinované ukazatele vstupního/výstupního souboru *stdin*, *stdout*nebo *stderr*.

Dvouparametrový konstruktor vytvoří `CStdioFile` objekt a otevře odpovídající soubor s danou cestou.

Pokud předáte null pro *pOpenStream* nebo *lpszFileName* `CInvalidArgException*`, konstruktor vyvolá .

Pokud soubor nelze otevřít nebo vytvořit, konstruktor `CFileException*`vyvolá .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

## <a name="cstdiofilem_pstream"></a><a name="m_pstream"></a>CStdioFile::m_pStream

Datový `m_pStream` člen je ukazatel na otevřený soubor vrácený funkcí `fopen`run-time jazyka C .

```
FILE* m_pStream;
```

### <a name="remarks"></a>Poznámky

Je null, pokud soubor nebyl nikdy otevřen nebo byl uzavřen.

## <a name="cstdiofileopen"></a><a name="open"></a>CStdioFile::Otevřít

Přetíženo. Open je určen pro `CStdioFile` použití s výchozím konstruktorem.

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

*název souboru lpsz*<br/>
Řetězec, který je cesta k požadovanému souboru. Cesta může být relativní nebo absolutní.

*nOpenFlags*<br/>
Režim sdílení a přístupu. Určuje akci, která má být vyřízení při otevírání souboru. Možnosti můžete kombinovat pomocí operátoru bitové-OR (&#124;). Je vyžadováno jedno přístupové oprávnění a jedna možnost sdílení. režimCreate a modeNoInherit režimy jsou volitelné.

*chyba*<br/>
Ukazatel na existující objekt výjimky souboru, který obdrží stav neúspěšné operace.

*Ptm*<br/>
Ukazatel na `CAtlTransactionManager` objekt.

### <a name="return-value"></a>Návratová hodnota

PRAVDA v případě úspěchu; jinak FALSE.

### <a name="remarks"></a>Poznámky

## <a name="cstdiofilereadstring"></a><a name="readstring"></a>CStdioFile::Řetězec čtení

Načte textová data do vyrovnávací paměti až do limitu *nMax* `CStdioFile` -1 znaků ze souboru přidruženého k objektu.

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Určuje ukazatel myši na vyrovnávací paměť dodanou uživatelem, která obdrží textový řetězec ukončený nulou.

*nMax*<br/>
Určuje maximální počet znaků ke čtení, nepočítá ukončující znak null.

*rString*<br/>
Odkaz na `CString` objekt, který bude obsahovat řetězec, když se vrátí funkce.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyrovnávací paměť obsahující textová data. NULL, pokud bylo dosaženo konce souboru bez čtení dat; nebo pokud logické, FALSE, pokud bylo dosaženo konce souboru bez čtení dat.

### <a name="remarks"></a>Poznámky

Čtení je zastaveno prvním znakem nového řádku. Pokud v takovém případě byly přečteny méně než *nMax*-1 znaků, znak nového řádku je uložen ve vyrovnávací paměti. V obou případech je připojen znak null (\0).

[CFile::Read](../../mfc/reference/cfile-class.md#read) je také k dispozici pro vstup v textovém režimu, ale nekončí na dvojici přísunu řádku řádku vozíku.

> [!NOTE]
> Verze `CString` této funkce odebere `'\n'` if present; verze LPTSTR není.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

## <a name="cstdiofileseek"></a><a name="seek"></a>CStdioFile::Hledat

Přemístí ukazatel v dříve otevřeném souboru.

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lVypnuto*<br/>
Počet bajtů pro přesunutí ukazatele.

*nFrom*<br/>
Režim pohybu ukazatele. Toto musí být jedna z následujících hodnot:

- `CFile::begin`: Přesunutí ukazatele souboru *lOff* bajtů vpřed od začátku souboru.

- `CFile::current`: Přesuňte ukazatel souboru *lOff* bajtů z aktuální pozice v souboru.

- `CFile::end`: Přesuňte ukazatel souboru *lOff* bajtů z konce souboru. Všimněte si, že *lOff* musí být negativní hledat do existujícího souboru; kladné hodnoty budou usilovat o konec souboru.

### <a name="return-value"></a>Návratová hodnota

Pokud je požadovaná `Seek` pozice legální, vrátí nový posun bajtů od začátku souboru. V opačném případě je vrácená `CFileException` hodnota nedefinovaná a je vyvolán objekt.

### <a name="remarks"></a>Poznámky

Funkce `Seek` umožňuje náhodný přístup k obsahu souboru přesunutím ukazatele o zadanou částku, absolutně nebo relativně. Během hledání se ve skutečnosti nečtou žádná data. Pokud je požadovaná pozice větší než velikost souboru, délka souboru bude prodloužena na tuto pozici a nebude vyvolána žádná výjimka.

Při otevření souboru je ukazatel souboru umístěn na odsazení 0, začátek souboru.

Tato implementace `Seek` je založena na funkci `fseek`Knihovna run-time (CRT). Existuje několik omezení pro `Seek` použití na datových proudech otevřených v textovém režimu. Další informace naleznete v [tématu fseek, _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md).

### <a name="example"></a>Příklad

Následující příklad ukazuje, `Seek` jak přesunout ukazatel 1000 bajtů `cfile` od začátku souboru. Všimněte `Seek` si, že nečte data, takže je nutné následně volat [CStdioFile::ReadString](#readstring) pro čtení dat.

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

## <a name="cstdiofilewritestring"></a><a name="writestring"></a>CStdioFile::Zápis

Zapíše data z vyrovnávací paměti `CStdioFile` do souboru přidruženého k objektu.

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
Určuje ukazatel na vyrovnávací paměť, která obsahuje řetězec s ukončeným hodnotou null.

### <a name="remarks"></a>Poznámky

Ukončující znak `\0`null ( ) není zapsán do souboru. Tato metoda zapisuje znaky nového řádku v *lpsz* do souboru jako dvojice zpětného posuvu řádku vozíku.

Pokud chcete zapisovat data, která nejsou ukončena `CStdioFile::Write` nulou do souboru, použijte nebo [CFile::Write](../../mfc/reference/cfile-class.md#write).

Tato metoda vyvolá, `CInvalidArgException*` pokud zadáte NULL pro parametr *lpsz.*

Tato metoda vyvolá `CFileException*` v reakci na chyby systému souborů.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>Viz také

[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException – třída](../../mfc/reference/cnotsupportedexception-class.md)
