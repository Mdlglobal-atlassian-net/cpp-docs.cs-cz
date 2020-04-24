---
title: CFile – třída
ms.date: 06/12/2018
f1_keywords:
- CFile
- AFX/CFile
- AFX/CFile::CFile
- AFX/CFile::Abort
- AFX/CFile::Close
- AFX/CFile::Duplicate
- AFX/CFile::Flush
- AFX/CFile::GetFileName
- AFX/CFile::GetFilePath
- AFX/CFile::GetFileTitle
- AFX/CFile::GetLength
- AFX/CFile::GetPosition
- AFX/CFile::GetStatus
- AFX/CFile::LockRange
- AFX/CFile::Open
- AFX/CFile::Read
- AFX/CFile::Remove
- AFX/CFile::Rename
- AFX/CFile::Seek
- AFX/CFile::SeekToBegin
- AFX/CFile::SeekToEnd
- AFX/CFile::SetFilePath
- AFX/CFile::SetLength
- AFX/CFile::SetStatus
- AFX/CFile::UnlockRange
- AFX/CFile::Write
- AFX/CFile::hFileNull
- AFX/CFile::m_hFile
- AFX/CFile::m_pTM
helpviewer_keywords:
- CFile [MFC], CFile
- CFile [MFC], Abort
- CFile [MFC], Close
- CFile [MFC], Duplicate
- CFile [MFC], Flush
- CFile [MFC], GetFileName
- CFile [MFC], GetFilePath
- CFile [MFC], GetFileTitle
- CFile [MFC], GetLength
- CFile [MFC], GetPosition
- CFile [MFC], GetStatus
- CFile [MFC], LockRange
- CFile [MFC], Open
- CFile [MFC], Read
- CFile [MFC], Remove
- CFile [MFC], Rename
- CFile [MFC], Seek
- CFile [MFC], SeekToBegin
- CFile [MFC], SeekToEnd
- CFile [MFC], SetFilePath
- CFile [MFC], SetLength
- CFile [MFC], SetStatus
- CFile [MFC], UnlockRange
- CFile [MFC], Write
- CFile [MFC], hFileNull
- CFile [MFC], m_hFile
- CFile [MFC], m_pTM
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
ms.openlocfilehash: 53afaf7732811e25729944eb71130a88e4f17a87
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754997"
---
# <a name="cfile-class"></a>CFile – třída

Základní třída pro třídy souborů třídy Třídy Microsoft Foundation.

## <a name="syntax"></a>Syntaxe

```
class CFile : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFile::CFile](#cfile)|Vytvoří `CFile` objekt z cesty nebo popisovače souboru.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFile::Přerušit](#abort)|Zavře soubor, který ignoruje všechna upozornění a chyby.|
|[CFile::Zavřít](#close)|Zavře soubor a odstraní objekt.|
|[CFile::Duplicate](#duplicate)|Vytvoří duplicitní objekt na základě tohoto souboru.|
|[CFile::Vyprázdnění](#flush)|Vyprázdní všechna data, která ještě nebyla zapsána.|
|[CFile::GetFileName](#getfilename)|Načte název vybraného souboru.|
|[CFile::GetFilePath](#getfilepath)|Načte úplnou cestu k souboru vybraného souboru.|
|[CFile::GetFileTitle](#getfiletitle)|Načte název vybraného souboru.|
|[CFile::GetLength](#getlength)|Načte délku souboru.|
|[CFile::GetPosition](#getposition)|Načte ukazatel aktuálního souboru.|
|[CFile::GetStatus](#getstatus)|Načte stav otevřeného souboru nebo ve statické verzi načte stav zadaného souboru (statická virtuální funkce).|
|[CFile::LockRange](#lockrange)|Uzamkne rozsah bajtů v souboru.|
|[CFile::Otevřít](#open)|Bezpečně otevře soubor s možností testování chyb.|
|[CFile::Číst](#read)|Čte (bez vyrovnávací paměti) data ze souboru na aktuální pozici souboru.|
|[CFile::Odebrat](#remove)|Odstraní zadaný soubor (statická funkce).|
|[CFile::Přejmenovat](#rename)|Přejmenuje zadaný soubor (statická funkce).|
|[CFile::Hledat](#seek)|Umístí aktuální ukazatel souboru.|
|[cFile::SeekToBegin](#seektobegin)|Umístí ukazatel aktuálního souboru na začátek souboru.|
|[cFile::SeekToend](#seektoend)|Umístí ukazatel aktuálního souboru na konec souboru.|
|[CFile::SetFilePath](#setfilepath)|Nastaví úplnou cestu k souboru vybraného souboru.|
|[CFile::SetLength](#setlength)|Změní délku souboru.|
|[CFile::SetStatus](#setstatus)|Nastaví stav zadaného souboru (statická, virtuální funkce).|
|[CFile::UnlockRange](#unlockrange)|Odemkne rozsah bajtů v souboru.|
|[CFile::Zápis](#write)|Zapíše (bez vyrovnávací paměti) data v souboru na aktuální pozici souboru.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CFile::POPISOVAČ operátora](#operator_handle)|Úchyt `CFile` k objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CFile::hSouborNull](#hfilenull)|Určuje, zda `CFile` má objekt platný popisovač.|
|[CFile::m_hFile](#m_hfile)|Obvykle obsahuje popisovač souborů operačního systému.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Název|Popis|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Ukazatel `CAtlTransactionManager` na objekt.|

## <a name="remarks"></a>Poznámky

Poskytuje přímo nebufferované, binární disk vstupní a výstupní služby, a nepřímo podporuje textové soubory a paměťové soubory prostřednictvím svých odvozených tříd. `CFile`pracuje ve spojení `CArchive` s třídou pro podporu serializace objektů třídy Microsoft Foundation.

Hierarchický vztah mezi touto třídou a jejími odvozenými třídami umožňuje programu `CFile` pracovat na všech objektech souborů prostřednictvím polymorfního rozhraní. Paměťový soubor se například chová jako soubor na disku.

Použití `CFile` a jeho odvozené třídy pro vstupně-va disku pro obecné účely. Pro `ofstream` formátovaný `iostream` text odeslaný do souboru na disku použijte nebo jiné třídy společnosti Microsoft.

Za normálních okolností je `CFile` soubor disku otevřen automaticky na konstrukci a uzavřen na zničení. Statické členské funkce umožňují vyslýchat stav souboru bez otevření souboru.

Další informace o `CFile`použití naleznete v článcích [Soubory v knihovně MFC](../../mfc/files-in-mfc.md) a [Zpracování souborů](../../c-runtime-library/file-handling.md) v *odkazu knihovny run-time*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

## <a name="cfileabort"></a><a name="abort"></a>CFile::Přerušit

Zavře soubor přidružený k tomuto objektu a znepřístupní soubor pro čtení nebo zápis.

```
virtual void Abort();
```

### <a name="remarks"></a>Poznámky

Pokud jste soubor nezavřeli před zničením objektu, destruktor jej zavře za vás.

Při zpracování výjimek `CFile::Abort` se `CFile::Close` liší od dvěma důležitými způsoby. Nejprve `Abort` funkce nebude vyvolat výjimku na selhání, protože chyby `Abort`jsou ignorovány . Za `Abort` druhé nebude **ASSERT,** pokud soubor nebyl otevřen nebo byl uzavřen dříve.

Pokud jste **new** použili `CFile` nový přidělit objekt na haldě, pak je nutné odstranit po zavření souboru. `Abort``m_hFile` nastaví `CFile::hFileNull`na .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

## <a name="cfilecfile"></a><a name="cfile"></a>CFile::CFile

Vytvoří a inicializuje `CFile` objekt.

```
CFile();
CFile(CAtlTransactionManager* pTM);
CFile(HANDLE hFile);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags,
CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>Parametry

*hSoubor*<br/>
Popisovač souboru připojit `CFile` k objektu.

*název souboru lpsz*<br/>
Relativní nebo úplná cesta k `CFile` souboru připojit k objektu.

*nOpenFlags*<br/>
Bitová kombinace (OR) možností přístupu k souboru pro zadaný soubor. Možné možnosti naleznete v části Poznámky.

*Ptm*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

V následujících pěti tabulkách jsou uvedeny možné možnosti parametru *nOpenFlags.*

Zvolte pouze jednu z následujících možností režimu přístupu k souborům. Výchozí režim přístupu `CFile::modeRead`k souborům je , který je jen pro čtení.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::modeRead`|Požadavky pouze pro čtení.|
|`CFile::modeWrite`|Požaduje pouze přístup pro zápis.|
|`CFile::modeReadWrite`|Požadavky na přístup pro čtení a zápis.|

Zvolte jednu z následujících možností režimu znaků.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::typeBinary`|Nastaví binární režim (používá se pouze v odvozených třídách).|
|`CFile::typeText`|Nastaví textový režim se speciálním zpracováním pro dvojice posuvu zpětného řádku vozíku (používá se pouze v odvozených třídách).|
|`CFile::typeUnicode`|Nastaví režim Unicode (používá se pouze v odvozených třídách). Text je zapsán do souboru ve formátu Unicode, když je aplikace postavena v konfiguraci Unicode. Do souboru není zapsán žádný kusovník.|

Zvolte pouze jednu z následujících možností režimu sdílení souborů. Výchozí režim sdílení `CFile::shareExclusive`souborů je , který je výhradní.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::shareDenyNone`|Žádná omezení sdílení.|
|`CFile::shareDenyRead`|Odepře přístup pro čtení všem ostatním.|
|`CFile::shareDenyWrite`|Odepře přístup pro zápis všem ostatním.|
|`CFile::shareExclusive`|Odepře přístup pro čtení a zápis všem ostatním.|

Zvolte první nebo obě následující možnosti režimu vytváření souborů. Výchozí režim vytváření `CFile::modeNoTruncate`je , který je otevřený existující.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::modeCreate`|Vytvoří nový soubor, pokud neexistuje žádný soubor. Pokud soubor již existuje, je přepsán a zpočátku nastaven na nulovou délku.|
|`CFile::modeNoTruncate`|Vytvoří nový soubor, pokud neexistuje žádný soubor; v opačném případě, pokud soubor již existuje, `CFile` je připojen k objektu.|

Zvolte následující možnosti ukládání souborů do mezipaměti, jak je popsáno. Ve výchozím nastavení systém používá schéma ukládání do mezipaměti pro obecné účely, které není k dispozici jako možnost.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::osNoBuffer`|Systém nepoužívá pro soubor mezipaměť. Tato možnost zruší následující 2 možnosti.|
|`CFile::osRandomAccess`|Mezipaměť souborů je optimalizována pro náhodný přístup. Nepoužívejte tuto možnost ani možnost sekvenčního skenování.|
|`CFile::osSequentialScan`|Mezipaměť souborů je optimalizována pro sekvenční přístup. Nepoužívejte tuto možnost i možnost přístupu s náhodným přístupem.|
|`CFile::osWriteThrough`|Operace zápisu jsou prováděny bez prodlení.|

Zvolte následující možnost zabezpečení, abyste zabránili zdědění popisovače souboru. Ve výchozím nastavení mohou všechny nové podřízené procesy používat popisovač souboru.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::modeNoInherit`|Zabrání všem podřízeným procesům v použití popisovače souboru.|

Výchozí konstruktor inicializuje členy, ale nepřipojí `CFile` k objektu soubor. Po použití tohoto konstruktoru použijte metodu [CFile::Open](#open) k `CFile` otevření souboru a jeho připojení k objektu.

Konstruktor s jedním parametrem inicializuje členy a `CFile` připojí k objektu existující soubor.

Konstruktor se dvěma parametry inicializuje členy a pokusí se otevřít zadaný soubor. Pokud tento konstruktor úspěšně otevře zadaný soubor, soubor `CFile` je připojen k objektu; jinak tento konstruktor vyvolá ukazatel `CInvalidArgException` na objekt. Další informace o zpracování výjimek naleznete v [tématu Výjimky](../../mfc/exception-handling-in-mfc.md).

Pokud `CFile` objekt úspěšně otevře zadaný soubor, automaticky jej `CFile` zavře, jakmile bude objekt zničen. v opačném případě je nutné explicitně zavřít soubor poté, co již není připojen k objektu. `CFile`

### <a name="example"></a>Příklad

Následující kód ukazuje, jak `CFile`používat .

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

## <a name="cfileclose"></a><a name="close"></a>CFile::Zavřít

Zavře soubor přidružený k tomuto objektu a znepřístupní soubor pro čtení nebo zápis.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Pokud jste soubor nezavřeli před zničením objektu, destruktor jej zavře za vás.

Pokud jste **new** použili `CFile` nový přidělit objekt na haldě, pak je nutné odstranit po zavření souboru. `Close``m_hFile` nastaví `CFile::hFileNull`na .

### <a name="example"></a>Příklad

Viz příklad pro [CFile::CFile](#cfile).

## <a name="cfileduplicate"></a><a name="duplicate"></a>CFile::Duplicate

Vytvoří duplicitní `CFile` objekt pro daný soubor.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na duplicitní `CFile` objekt.

### <a name="remarks"></a>Poznámky

Tato funkce je ekvivalentní funkci `_dup`c run-time .

## <a name="cfileflush"></a><a name="flush"></a>CFile::Vyprázdnění

Vynutí všechna zbývající data ve vyrovnávací paměti souboru, která mají být zapsána do souboru.

```
virtual void Flush();
```

### <a name="remarks"></a>Poznámky

Použití `Flush` nezaručuje vyprázdnění `CArchive` vyrovnávacích pamětí. Pokud používáte archiv, zavolejte [nejprve CArchive::Flush.](../../mfc/reference/carchive-class.md#flush)

### <a name="example"></a>Příklad

Podívejte se na příklad [pro CFile::SetFilePath](#setfilepath).

## <a name="cfilegetfilename"></a><a name="getfilename"></a>CFile::GetFileName

Volání této členské funkce načíst název zadaného souboru.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název souboru.

### <a name="remarks"></a>Poznámky

Například při volání `GetFileName` generovat zprávu pro uživatele o `c:\windows\write\myfile.wri`souboru , `myfile.wri`název souboru, , je vrácena.

Chcete-li vrátit celou cestu k souboru, včetně názvu, zavolejte [GetFilePath](#getfilepath). Chcete-li vrátit název `myfile`souboru ( ), volejte [GetFileTitle](#getfiletitle).

### <a name="example"></a>Příklad

Tento fragment kódu otevře SYSTEM. INI v adresáři windows. Pokud je nalezen, v příkladu se vytiskne název a cesta a název, jak je znázorněno v části Výstup:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

## <a name="cfilegetfilepath"></a><a name="getfilepath"></a>CFile::GetFilePath

Volání této členské funkce načíst úplnou cestu k zadanému souboru.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Návratová hodnota

Úplná cesta k zadanému souboru.

### <a name="remarks"></a>Poznámky

Například při volání `GetFilePath` generovat zprávu pro uživatele o `c:\windows\write\myfile.wri`souboru , `c:\windows\write\myfile.wri`cesta k souboru , je vrácena.

Chcete-li vrátit pouze název`myfile.wri`souboru ( ), volejte [GetFileName](#getfilename). Chcete-li vrátit název`myfile`souboru ( ), volejte [GetFileTitle](#getfiletitle).

### <a name="example"></a>Příklad

Viz příklad pro [GetFileName](#getfilename).

## <a name="cfilegetfiletitle"></a><a name="getfiletitle"></a>CFile::GetFileTitle

Volánítéto členské funkce načíst název souboru (zobrazovaný název) pro soubor.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

Název podkladového souboru.

### <a name="remarks"></a>Poznámky

Tato metoda volá [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) načíst název souboru. Pokud je metoda úspěšná, vrátí řetězec, který by systém použil k zobrazení názvu souboru uživateli. V opačném případě metoda volá [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) k načtení názvu souboru (včetně přípony souboru) podkladového souboru. To znamená, že přípona souboru není vždy zahrnuta v řetězci vráceného názvu souboru. Další informace naleznete v [tématech GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew) a [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) v sadě Windows SDK.

Chcete-li vrátit celou cestu k souboru, včetně názvu, zavolejte [GetFilePath](#getfilepath). Chcete-li vrátit pouze název souboru, zavolejte [GetFileName](#getfilename).

### <a name="example"></a>Příklad

Viz příklad pro [GetFileName](#getfilename).

## <a name="cfilegetlength"></a><a name="getlength"></a>CFile::GetLength

Získá aktuální logickou délku souboru v bajtů.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

## <a name="cfilegetposition"></a><a name="getposition"></a>CFile::GetPosition

Získá aktuální hodnotu ukazatele souboru, který lze použít `Seek`v pozdějších voláních .

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

## <a name="cfilegetstatus"></a><a name="getstatus"></a>CFile::GetStatus

Tato metoda načte informace o `CFile` stavu související s danou instancí objektu nebo s danou cestou k souboru.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*rStav*<br/>
Odkaz na uživatelem `CFileStatus` zadanou strukturu, která obdrží informace o stavu. Struktura `CFileStatus` má následující pole:

- `CTime m_ctime`Datum a čas vytvoření souboru.

- `CTime m_mtime`Datum a čas poslední změny souboru.

- `CTime m_atime`Datum a čas, kdy byl soubor naposledy zpřístupněn pro čtení.

- `ULONGLONG m_size`Logická velikost souboru v bajtů, jak je uvedeno příkazem DIR.

- `BYTE m_attribute`Bajt atributu souboru.

- `char m_szFullName[_MAX_PATH]`Absolutní název souboru v znakové sadě systému Windows.

*název souboru lpsz*<br/>
Řetězec v znakové sadě systému Windows, který je cestou k požadovanému souboru. Cesta může být relativní nebo absolutní nebo může obsahovat název síťové cesty.

*Ptm*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud jsou informace o stavu zadaného souboru úspěšně získány; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Nestatická verze `GetStatus` načte informace o stavu otevřeného `CFile` souboru přidruženého k danému objektu.  Statická verze `GetStatus` získá stav souboru z dané cesty k souboru bez skutečného otevření souboru. Tato verze je užitečná pro testování existence a přístupových práv souboru.

Člen `m_attribute` `CFileStatus` struktury odkazuje na sadu atributů souboru. Třída `CFile` poskytuje typ výčtu **atributů,** takže atributy souboru lze zadat symbolicky:

```
enum Attribute {
    normal =    0x00,
    readOnly =  0x01,
    hidden =    0x02,
    system =    0x04,
    volume =    0x08,
    directory = 0x10,
    archive =   0x20
    };
```

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#10](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]

## <a name="cfilehfilenull"></a><a name="hfilenull"></a>CFile::hSouborNull

Určuje přítomnost platného popisovače souboru `CFile` pro objekt.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Poznámky

Tato konstanta se používá `CFile` k určení, pokud má objekt platný popisovač souboru.

Následující příklad ukazuje tuto operaci:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

## <a name="cfilelockrange"></a><a name="lockrange"></a>CFile::LockRange

Uzamkne rozsah bajtů v otevřeném souboru a vyvolá výjimku, pokud je soubor již uzamčen.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Posun bajtu začátku rozsahu bajtů pro uzamčení.

*dwCount*<br/>
Počet bajtů v rozsahu k uzamčení.

### <a name="remarks"></a>Poznámky

Zamykání bajtů v souboru zabraňuje přístupu k těmto bajtům jinými procesy. Můžete zamknout více než jednu oblast souboru, ale nejsou povoleny žádné překrývající se oblasti.

Když odemknete `UnlockRange` oblast pomocí členské funkce, rozsah bajtů musí přesně odpovídat oblasti, která byla dříve uzamčena. Funkce `LockRange` neslučuje sousední oblasti. Pokud jsou dvě zamknuté oblasti sousedící, je nutné odemknout každou oblast zvlášť.

> [!NOTE]
> Tato funkce není k `CMemFile`dispozici pro -derived třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilem_hfile"></a><a name="m_hfile"></a>CFile::m_hFile

Obsahuje popisovač souboru operačního systému pro otevřený soubor.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Poznámky

`m_hFile`je veřejná proměnná typu UINT. Obsahuje `CFile::hFileNull`, indikátor prázdného souboru nezávislý na operačním systému, pokud popisovač nebyl přiřazen.

`m_hFile` Použití není doporučeno, protože význam člena závisí na odvozené třídy. `m_hFile`je veřejným členem pro usnadnění při podpoře nepolymorfní použití třídy.

## <a name="cfilem_ptm"></a><a name="m_ptm"></a>CFile::m_pTM

Ukazatel na `CAtlTransactionManager` objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

## <a name="cfileopen"></a><a name="open"></a>CFile::Otevřít

Přetíženo. `Open`je určen pro použití `CFile` s výchozím konstruktorem.

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
Řetězec, který obsahuje cestu k požadovanému souboru. Cesta může být relativní, absolutní nebo název sítě (UNC).

*nOpenFlags*<br/>
UINT, který definuje režim sdílení a přístupu souboru. Určuje akci, která má být vyřízení při otevírání souboru. Možnosti můžete kombinovat pomocí operátoru Bitwise-OR ( **&#124;** ). Je vyžadováno jedno přístupové oprávnění a jedna možnost sdílení. `modeCreate` režimy `modeNoInherit` a jsou volitelné. Seznam možností režimu naleznete v konstruktoru [CFile.](#cfile)

*chyba*<br/>
Ukazatel na existující objekt výjimky souboru, který obdrží stav neúspěšné operace.

*Ptm*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla otevřená zpráva úspěšná; jinak 0. Parametr *pError* má smysl pouze v případě, že je vrácena hodnota 0.

### <a name="remarks"></a>Poznámky

Tyto `Open` dvě funkce jsou "bezpečné" metody pro otevření souboru, kde selhání je normální, očekávaný stav.

Zatímco `CFile` konstruktor vyvolá výjimku v chybovém stavu, `Open` vrátí hodnotu FALSE pro chybové stavy. `Open`stále inicializovat [CFileException](../../mfc/reference/cfileexception-class.md) objekt popsat chybu, nicméně. Pokud nezadáte parametr *pError* nebo předáte hodnotu `CFileException`NULL `Open` pro chybu *pError*, vrátí funkce NEPRAVDA a nevyvolá . Pokud předáte ukazatel existujícímu `CFileException` `Open` a dojde k chybě, funkce jej vyplní informacemi popisujícími tuto chybu. `Open`nevyvolá výjimku v obou případech.

Následující tabulka popisuje možné výsledky `Open`souboru .

|`pError`|Došlo k chybě.|Návratová hodnota|CFileException obsah|
|--------------|------------------------|------------------|----------------------------|
|NULL|Ne|TRUE|neuvedeno|
|ptr až`CFileException`|Ne|TRUE|Nezměněn|
|NULL|Ano|FALSE|neuvedeno|
|ptr až`CFileException`|Ano|FALSE|inicializována pro popis chyby|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

## <a name="cfileoperator-handle"></a><a name="operator_handle"></a>CFile::POPISOVAČ operátora

Pomocí tohoto operátoru předejte `CFile` popisovač objektu funkcím, jako jsou `HANDLE` [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) a [GetFileTime,](/windows/win32/api/fileapi/nf-fileapi-getfiletime) které očekávají .

```
operator HANDLE() const;
```

## <a name="cfileread"></a><a name="read"></a>CFile::Číst

Přečte data do vyrovnávací paměti `CFile` ze souboru přidruženého k objektu.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na uživatelem zadanou vyrovnávací paměť, která má přijímat data přečtená ze souboru.

*nCount*<br/>
Maximální počet bajtů, které mají být přečteny ze souboru. U souborů v textovém režimu se dvojice datového kanálu řádku vozíku počítají jako jednotlivé znaky.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů přenesených do vyrovnávací paměti. Pro `CFile` všechny třídy může být vrácená hodnota menší než *nCount,* pokud bylo dosaženo konce souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Další příklad naleznete v tématu [CFile::Open](#open).

## <a name="cfileremove"></a><a name="remove"></a>CFile::Odebrat

Tato statická funkce odstraní soubor určený cestou.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*název souboru lpsz*<br/>
Řetězec, který je cesta k požadovanému souboru. Cesta může být relativní nebo absolutní a může obsahovat název sítě.

*Ptm*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

`Remove`neodebere adresář.

Členská `Remove` funkce vyvolá výjimku, pokud je připojený soubor otevřený nebo pokud soubor nelze odebrat. Tato funkce je ekvivalentní příkazu DEL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

## <a name="cfilerename"></a><a name="rename"></a>CFile::Přejmenovat

Tato statická funkce přejmenuje zadaný soubor.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszOldName*<br/>
Stará cesta.

*lpszNewName*<br/>
Nová cesta.

*Ptm*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

Adresáře nelze přejmenovat. Tato funkce je ekvivalentní příkazu REN.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

## <a name="cfileseek"></a><a name="seek"></a>CFile::Hledat

Přemístí ukazatel souboru do otevřeného souboru.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lVypnuto*<br/>
Počet bajtů pro přesunutí ukazatele souboru. Kladné hodnoty posunou ukazatel souboru na konec souboru; záporné hodnoty posunou ukazatel souboru směrem k začátku souboru.

*nFrom*<br/>
Pozice, o které se můžete snažit. Možné hodnoty naleznete v části Poznámky.

### <a name="return-value"></a>Návratová hodnota

Pozice ukazatele souboru, pokud byla metoda úspěšná; jinak vrácená hodnota není definována a `CFileException` je vyvolán ukazatel na výjimku.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny možné hodnoty parametru *nFrom.*

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::begin`|Hledat od začátku souboru.|
|`CFile::current`|Hledat z aktuálního umístění ukazatele souboru.|
|`CFile::end`|Hledat od konce souboru.|

Při otevření souboru je ukazatel souboru umístěn na 0, začátek souboru.

Ukazatel souboru můžete nastavit na pozici za koncem souboru. Pokud tak učiníte, velikost souboru se nezvětší, dokud do něj nezapíšete.

Obslužná rutina výjimky pro tuto metodu musí odstranit objekt výjimky po zpracování výjimky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

## <a name="cfileseektobegin"></a><a name="seektobegin"></a>cFile::SeekToBegin

Nastaví hodnotu ukazatele souboru na začátek souboru.

```cpp
void SeekToBegin();
```

### <a name="remarks"></a>Poznámky

`SeekToBegin()`je ekvivalentní `Seek( 0L, CFile::begin )`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfileseektoend"></a><a name="seektoend"></a>cFile::SeekToend

Nastaví hodnotu ukazatele souboru na logický konec souboru.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>Návratová hodnota

Délka souboru v bajtů.

### <a name="remarks"></a>Poznámky

`SeekToEnd()`je ekvivalentní `CFile::Seek( 0L, CFile::end )`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

## <a name="cfilesetfilepath"></a><a name="setfilepath"></a>CFile::SetFilePath

Volánítéto funkce určit cestu k souboru. Například pokud cesta k souboru není k dispozici při vytvoření [cfile](../../mfc/reference/cfile-class.md) objektu, volání `SetFilePath` poskytnout.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Ukazatel na řetězec určující novou cestu.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> `SetFilePath`neotevře soubor ani soubor nevytvoří; jednoduše přidruží objekt k `CFile` názvu cesty, který pak lze použít.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

## <a name="cfilesetlength"></a><a name="setlength"></a>CFile::SetLength

Voláním této funkce změňte délku souboru.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen*<br/>
Požadovaná délka souboru v bajtech. Tato hodnota může být větší nebo menší než aktuální délka souboru. Soubor bude podle potřeby rozšířen nebo zkrácen.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Pomocí `CMemFile`aplikace může tato `CMemoryException` funkce vyvolat objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

## <a name="cfilesetstatus"></a><a name="setstatus"></a>CFile::SetStatus

Nastaví stav souboru přidruženého k tomuto umístění souboru.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*název souboru lpsz*<br/>
Řetězec, který je cesta k požadovanému souboru. Cesta může být relativní nebo absolutní a může obsahovat název sítě.

*Stav*<br/>
Vyrovnávací paměť obsahující nové informace o stavu. Volání `GetStatus` členské funkce předvyplnit `CFileStatus` strukturu s aktuální hodnoty, pak provést změny podle potřeby. Pokud je hodnota 0, odpovídající položka stavu není aktualizována. Popis `CFileStatus` struktury naleznete v členské funkci [GetStatus.](#getstatus)

*Ptm*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

Chcete-li nastavit čas, upravte `m_mtime` pole *stavu*.

Při volání `SetStatus` do pokusu o změnu pouze atributy souboru `m_mtime` a člen struktury stavu souboru je nenulová, atributy mohou být také ovlivněny (změna časového razítka může mít vedlejší účinky na atributy). Pokud chcete pouze změnit atributy souboru, nejprve nastavte `m_mtime` člena struktury stavu souboru na `SetStatus`nulu a pak proveďte volání .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

## <a name="cfileunlockrange"></a><a name="unlockrange"></a>CFile::UnlockRange

Odemkne rozsah bajtů v otevřeném souboru.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Posun bajtu začátku rozsahu bajtů odemknout.

*dwCount*<br/>
Počet bajtů v rozsahu odemknout.

### <a name="remarks"></a>Poznámky

Podrobnosti naleznete v popisu členské funkce [LockRange.](#lockrange)

> [!NOTE]
> Tato funkce není k `CMemFile`dispozici pro -derived třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

## <a name="cfilewrite"></a><a name="write"></a>CFile::Zápis

Zapíše data z vyrovnávací paměti `CFile` do souboru přidruženého k objektu.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na uživatelem zadanou vyrovnávací paměť, která obsahuje data, která mají být zapsána do souboru.

*nCount*<br/>
Počet bajtů, které mají být přeneseny z vyrovnávací paměti. U souborů v textovém režimu se dvojice datového kanálu řádku vozíku počítají jako jednotlivé znaky.

### <a name="remarks"></a>Poznámky

`Write`vyvolá výjimku v reakci na několik podmínek, včetně podmínky úplné ho disku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Viz také příklady pro [CFile::CFile](#cfile) a [CFile::Open](#open).

## <a name="see-also"></a>Viz také

[Vzorek mfc DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile – třída](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile – třída](../../mfc/reference/cmemfile-class.md)
