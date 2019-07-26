---
title: CFile – – Třída
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
ms.openlocfilehash: a258773633f503dc0638d76509953b3410dafbd8
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375761"
---
# <a name="cfile-class"></a>CFile – – Třída

Základní třída pro třídy souborů Microsoft Foundation Class.

## <a name="syntax"></a>Syntaxe

```
class CFile : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CFile –:: CFile –](#cfile)|`CFile` Vytvoří objekt z cesty nebo popisovače souboru.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CFile –:: Abort](#abort)|Zavře soubor ignoruje všechna upozornění a chyby.|
|[CFile –:: Close](#close)|Zavře soubor a odstraní objekt.|
|[CFile –::D uplikovat](#duplicate)|Vytvoří duplicitní objekt na základě tohoto souboru.|
|[CFile –:: flush](#flush)|Vyprázdní všechna data, která se ještě budou zapisovat.|
|[CFile –:: getsoubor](#getfilename)|Načte název souboru vybraného souboru.|
|[CFile –:: GetFilePath](#getfilepath)|Načte úplnou cestu k souboru vybraného souboru.|
|[CFile –:: GetFileTitle](#getfiletitle)|Načte název vybraného souboru.|
|[CFile –:: GetLength](#getlength)|Načte délku souboru.|
|[CFile –:: GetPosition](#getposition)|Načte aktuální ukazatel na soubor.|
|[CFile –:: GetStatus](#getstatus)|Načte stav otevřeného souboru nebo ve statické verzi načte stav zadaného souboru (statická, virtuální funkce).|
|[CFile –:: LockRange](#lockrange)|Zamkne rozsah bajtů v souboru.|
|[CFile –:: Open](#open)|Bezpečně otevře soubor s možností testování chyb.|
|[CFile –:: Read](#read)|Načte (nebufferovaná) data ze souboru na aktuální pozici souboru.|
|[CFile –:: Remove](#remove)|Odstraní zadaný soubor (statická funkce).|
|[CFile –:: rename](#rename)|Přejmenuje zadaný soubor (statická funkce).|
|[CFile –:: Seek](#seek)|Umístí ukazatel na aktuální soubor.|
|[CFile::SeekToBegin](#seektobegin)|Umístí ukazatel na aktuální soubor na začátek souboru.|
|[CFile –:: SeekToEnd](#seektoend)|Umístí ukazatel na aktuální soubor na konec souboru.|
|[CFile –:: SetFilePath](#setfilepath)|Nastaví úplnou cestu k souboru pro vybraný soubor.|
|[CFile –:: SetLength](#setlength)|Změní délku souboru.|
|[CFile –:: SetStatus](#setstatus)|Nastaví stav zadaného souboru (statická, virtuální funkce).|
|[CFile –:: UnlockRange](#unlockrange)|Odemkne rozsah bajtů v souboru.|
|[CFile –:: Write](#write)|Zapisuje (nebufferovaná) data do souboru do aktuální pozice souboru.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[CFile –:: operator – popisovač](#operator_handle)|Popisovač `CFile` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CFile –:: hFileNull](#hfilenull)|Určuje, zda `CFile` má objekt platný popisovač.|
|[CFile::m_hFile](#m_hfile)|Obvykle obsahuje popisovač souborů operačního systému.|

### <a name="protected-data-members"></a>Chránění členové dat

|Name|Popis|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objekt.|

## <a name="remarks"></a>Poznámky

Přímo poskytuje neuložené vyrovnávací paměti, binární vstupně-výstupní služby disku a nepřímo podporuje textové soubory a paměťové soubory prostřednictvím jejich odvozených tříd. `CFile`pracuje ve spojení s `CArchive` třídou pro podporu serializace objektů Microsoft Foundation Class.

Hierarchický vztah mezi touto třídou a jeho odvozenou třídou umožňuje vašemu programu pracovat na všech objektech souborů prostřednictvím `CFile` polymorfního rozhraní. Soubor paměti se například chová jako soubor na disku.

Použijte `CFile` a jeho odvozené třídy pro účely vstupu/výstupu disku pro obecné účely. Použijte `ofstream` nebo jiné třídy `iostream` Microsoftu pro formátovaný text odeslaný do souboru na disku.

Obvykle se soubor na disku otevírá automaticky při `CFile` vytváření a zavírání při zničení. Statické členské funkce umožňují dotazování stav souboru bez otevření souboru.

Další `CFile`informace o použití naleznete v článcích [soubory v knihovně MFC](../../mfc/files-in-mfc.md) a [zpracování souborů](../../c-runtime-library/file-handling.md) v *Referenční příručce ke knihovně run-time*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFX –. h

##  <a name="abort"></a>CFile –:: Abort

Zavře soubor přidružený k tomuto objektu a nastaví soubor jako nedostupný pro čtení nebo zápis.

```
virtual void Abort();
```

### <a name="remarks"></a>Poznámky

Pokud jste soubor nezavřeli před zničením objektu, destruktor ho uzavře za vás.

Při zpracování výjimek `CFile::Abort` se liší od `CFile::Close` dvou důležitých způsobů. Nejprve funkce při selhání nevyvolá výjimku, protože chyby jsou `Abort`ignorovány. `Abort` Za `Abort` druhé nevyhodnotí **, jestli se** soubor neotevřel, nebo se dřív zavřel.

Pokud jste použili **New** pro přidělení `CFile` objektu na haldě, je nutné jej po zavření souboru odstranit. `Abort`nastaví `m_hFile` na `CFile::hFileNull`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>CFile –:: CFile –

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

*hFile*<br/>
Popisovač souboru, který se má připojit k `CFile` objektu.

*lpszFileName*<br/>
Relativní nebo úplná cesta k souboru, který se má připojit `CFile` k objektu

*nOpenFlags*<br/>
Bitová kombinace možností přístupu k souboru pro zadaný soubor. Možné možnosti najdete v části poznámky.

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

Následující pět tabulek uvádí možné možnosti pro parametr *nOpenFlags* .

Vyberte jenom jednu z následujících možností režimu přístupu k souborům. Výchozí režim přístupu k souborům je `CFile::modeRead`, který je jen pro čtení.

|Value|Popis|
|-----------|-----------------|
|`CFile::modeRead`|Vyžádá jenom přístup pro čtení.|
|`CFile::modeWrite`|Vyžádá jenom přístup pro zápis.|
|`CFile::modeReadWrite`|Vyžádá přístup pro čtení a zápis.|

Vyberte jednu z následujících možností režimu znaků.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::typeBinary`|Nastaví binární režim (používá se pouze v odvozených třídách).|
|`CFile::typeText`|Nastaví režim textu se speciálním zpracováním pro páry kanálů návratového řádku (používá se pouze v odvozených třídách).|
|`CFile::typeUnicode`|Nastaví režim kódování Unicode (používá se pouze v odvozených třídách). Text se zapisuje do souboru ve formátu Unicode, když je aplikace sestavená v konfiguraci Unicode. Do souboru se nezapisuje žádný kusovník.|

Vyberte jenom jednu z následujících možností režimu sdílení souborů. Výchozím režimem sdílení souborů je `CFile::shareExclusive`, který je exkluzivní.

|Value|Popis|
|-----------|-----------------|
|`CFile::shareDenyNone`|Žádná omezení sdílení.|
|`CFile::shareDenyRead`|Odepře přístup pro čtení všem ostatním.|
|`CFile::shareDenyWrite`|Zakazuje přístup pro zápis všem ostatním.|
|`CFile::shareExclusive`|Odepře přístup pro čtení a zápis všem ostatním.|

Vyberte první nebo obojí z následujících možností režimu vytváření souborů. Výchozí režim vytváření je `CFile::modeNoTruncate`, který je otevřený.

|Value|Popis|
|-----------|-----------------|
|`CFile::modeCreate`|Vytvoří nový soubor, pokud žádný soubor neexistuje. Pokud soubor již existuje, bude přepsán a zpočátku nastaven na nulovou délku.|
|`CFile::modeNoTruncate`|Vytvoří nový soubor, pokud žádný soubor neexistuje. v opačném případě, pokud soubor již existuje, je připojen k `CFile` objektu.|

Vyberte následující možnosti ukládání do mezipaměti, jak je popsáno níže. Ve výchozím nastavení systém používá schéma ukládání do mezipaměti pro obecné účely, které není dostupné jako možnost.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::osNoBuffer`|Systém pro tento soubor nepoužívá zprostředkující mezipaměť. Tato možnost zruší následující dvě možnosti.|
|`CFile::osRandomAccess`|Mezipaměť souborů je optimalizována pro náhodný přístup. Nepoužívejte tuto možnost a možnost sekvenčního prohledávání.|
|`CFile::osSequentialScan`|Mezipaměť souborů je optimalizována pro sekvenční přístup. Tuto možnost nepoužívejte a možnost náhodný přístup.|
|`CFile::osWriteThrough`|Operace zápisu se provádějí bez zpoždění.|

Chcete-li zabránit dědění popisovače souboru, vyberte následující možnost zabezpečení. Ve výchozím nastavení mohou všechny nové podřízené procesy použít popisovač souboru.

|Value|Popis|
|-----------|-----------------|
|`CFile::modeNoInherit`|Zabraňuje všem podřízeným procesům v použití popisovače souboru.|

Výchozí konstruktor inicializuje členy, ale nepřipojí soubor k `CFile` objektu. Po použití tohoto konstruktoru použijte metodu [CFile –:: Open](#open) k otevření souboru a k `CFile` objektu ho připojte.

Konstruktor s jedním parametrem inicializuje členy a připojí existující soubor k `CFile` objektu.

Konstruktor se dvěma parametry inicializuje členy a pokusí se otevřít zadaný soubor. Pokud tento konstruktor úspěšně otevře zadaný soubor, soubor je připojen k `CFile` objektu; v opačném případě tento konstruktor vyvolá ukazatel `CInvalidArgException` na objekt. Další informace o zpracování výjimek naleznete v tématu [výjimky](../../mfc/exception-handling-in-mfc.md).

Pokud objekt úspěšně otevře zadaný soubor, tento soubor se automaticky zavře, `CFile` když je objekt zničen. v opačném případě je nutné explicitně zavřít soubor poté, co již není připojen k `CFile` objektu. `CFile`

### <a name="example"></a>Příklad

Následující kód ukazuje, jak použít `CFile`.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>CFile –:: Close

Zavře soubor přidružený k tomuto objektu a nastaví soubor jako nedostupný pro čtení nebo zápis.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Pokud jste soubor nezavřeli před zničením objektu, destruktor ho uzavře za vás.

Pokud jste použili **New** pro přidělení `CFile` objektu na haldě, je nutné jej po zavření souboru odstranit. `Close`nastaví `m_hFile` na `CFile::hFileNull`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFile –:: CFile –](#cfile).

##  <a name="duplicate"></a>CFile –::D uplikovat

Vytvoří duplicitní `CFile` objekt pro daný soubor.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na duplicitní `CFile` objekt.

### <a name="remarks"></a>Poznámky

Tato funkce je ekvivalentní funkci `_dup`run-time jazyka C.

##  <a name="flush"></a>CFile –:: flush

Vynutí zápis všech dat zbývajících do vyrovnávací paměti souborů do souboru.

```
virtual void Flush();
```

### <a name="remarks"></a>Poznámky

Použití `Flush` nezaručuje vyprázdnění `CArchive` vyrovnávacích pamětí. Pokud používáte archiv, zavolejte nejprve [CArchive:: flush](../../mfc/reference/carchive-class.md#flush) .

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFile –:: SetFilePath](#setfilepath).

##  <a name="getfilename"></a>CFile –:: getsoubor

Zavolejte tuto členskou funkci, aby se načetl název zadaného souboru.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název souboru

### <a name="remarks"></a>Poznámky

Například při volání `GetFileName` pro vygenerování zprávy uživateli o souboru `c:\windows\write\myfile.wri`, je vrácen název souboru `myfile.wri`.

Chcete-li vrátit celou cestu k souboru, včetně názvu, volejte metodu [GetFilePath](#getfilepath). Chcete-li vrátit název souboru ( `myfile`), zavolejte [GetFileTitle](#getfiletitle).

### <a name="example"></a>Příklad

Tento fragment kódu otevře systém. Soubor INI v adresáři WINDOWS Pokud je tato funkce nalezena, bude v příkladu vytištěn název a cesta a název, jak je uvedeno v části výstup:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>CFile –:: GetFilePath

Zavolejte tuto členskou funkci, aby se načetla úplná cesta k zadanému souboru.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Návratová hodnota

Úplná cesta k zadanému souboru.

### <a name="remarks"></a>Poznámky

Například při volání `GetFilePath` , aby vygenerovala zprávu uživateli o souboru `c:\windows\write\myfile.wri` `c:\windows\write\myfile.wri`, je vrácena cesta k souboru.

Chcete-li vrátit pouze název souboru (`myfile.wri`), zavolejte metodu getsouboru. [](#getfilename) Chcete-li vrátit název souboru (`myfile`), zavolejte [GetFileTitle](#getfiletitle).

### <a name="example"></a>Příklad

Podívejte se na příklad [](#getfilename)pro getsouboru.

##  <a name="getfiletitle"></a>CFile –:: GetFileTitle

Chcete-li načíst název souboru (zobrazovaný název) pro daný soubor, zavolejte tuto členskou funkci.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

Název podkladového souboru.

### <a name="remarks"></a>Poznámky

Tato metoda volá [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea) , aby načetla název souboru. V případě úspěchu metoda vrátí řetězec, který by systém použil k zobrazení názvu souboru uživateli. V opačném případě metoda volá [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) , aby získala název souboru (včetně přípony souboru) podkladového souboru. To znamená, že Přípona souboru není vždy obsažena v řetězci vráceného názvu souboru. Další informace najdete v tématu [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea) a [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) v Windows SDK.

Chcete-li vrátit celou cestu k souboru, včetně názvu, volejte metodu [GetFilePath](#getfilepath). Chcete-li vrátit pouze název souboru, zavolejte metodu [getsouboru](#getfilename).

### <a name="example"></a>Příklad

Podívejte se na příklad [](#getfilename)pro getsouboru.

##  <a name="getlength"></a>CFile –:: GetLength

Získá aktuální logickou délku souboru v bajtech.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka souboru

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>CFile –:: GetPosition

Získá aktuální hodnotu ukazatele na soubor, který lze použít v pozdějších voláních `Seek`.

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na soubor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>CFile –:: GetStatus

Tato metoda načte informace o stavu související s danou `CFile` instancí objektu nebo danou cestou k souboru.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*rStatus*<br/>
Odkaz na strukturu zadanou `CFileStatus` uživatelem, která bude přijímat informace o stavu. `CFileStatus` Struktura obsahuje následující pole:

- `CTime m_ctime`Datum a čas vytvoření souboru.

- `CTime m_mtime`Datum a čas poslední změny souboru.

- `CTime m_atime`Datum a čas posledního otevření souboru pro čtení.

- `ULONGLONG m_size`Logická velikost souboru v bajtech, jak je uvedeno v příkazu DIR.

- `BYTE m_attribute`Bajt atributu souboru

- `char m_szFullName[_MAX_PATH]`Absolutní název souboru ve znakové sadě Windows

*lpszFileName*<br/>
Řetězec ve znakové sadě systému Windows, který je cestou k požadovanému souboru. Cesta může být relativní nebo absolutní nebo může obsahovat název síťové cesty.

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se informace o stavu zadaného souboru úspěšně získávají; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Nestatická verze `GetStatus` načte informace o stavu otevřeného souboru přidruženého k danému `CFile` objektu.  Statická verze `GetStatus` Získá stav souboru z dané cesty k souboru, aniž by soubor skutečně otevřel. Tato verze je užitečná pro testování existence a přístupových práv k souboru.

`m_attribute` Člen`CFileStatus` struktury odkazuje na sadu atributů souboru. Třída poskytuje typ výčtu atributu, takže atributy souboru lze zadat symbolické:  `CFile`

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

##  <a name="hfilenull"></a>CFile –:: hFileNull

Určuje přítomnost platné obslužné rutiny souboru pro daný `CFile` objekt.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Poznámky

Tato konstanta se používá k určení, `CFile` zda má objekt platnou obslužnou rutinu souboru.

Následující příklad demonstruje tuto operaci:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>CFile –:: LockRange

Zamkne rozsah bajtů v otevřeném souboru a vyvolává výjimku, pokud je soubor již uzamčen.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Posun bajtů začátku rozsahu bajtů, který se má zamknout.

*dwCount*<br/>
Počet bajtů v rozsahu, který se má zamknout.

### <a name="remarks"></a>Poznámky

Uzamykání bajtů v souboru brání v přístupu k těmto bajtům jiným procesům. Můžete uzamknout více než jednu oblast souboru, ale nejsou povoleny žádné překrývající se oblasti.

Při odemčení oblasti pomocí `UnlockRange` členské funkce musí rozsah bajtů přesně odpovídat oblasti, která byla dříve uzamčena. `LockRange` Funkce nesloučí sousední oblasti. Pokud se dvě uzamčené oblasti sousedí, je nutné každou oblast odemknout samostatně.

> [!NOTE]
>  Tato funkce není k dispozici `CMemFile`pro třídu odvozenou od třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>CFile –:: m_hFile

Obsahuje popisovač souborů operačního systému pro otevřený soubor.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Poznámky

`m_hFile`je veřejná proměnná typu UINT. Obsahuje `CFile::hFileNull`indikátor prázdného souboru nezávisle na operačním systému, pokud nebyl popisovač přiřazen.

`m_hFile` Použití není doporučeno, protože význam člena závisí na odvozené třídě. `m_hFile`je vytvořen veřejný člen pro usnadnění v podpoře nepolymorfního použití třídy.

##  <a name="m_ptm"></a>CFile –:: m_pTM

Ukazatel na `CAtlTransactionManager` objekt.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

##  <a name="open"></a>CFile –:: Open

Přetíženo. `Open`je určen pro použití s výchozím `CFile` konstruktorem.

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
Řetězec, který obsahuje cestu k požadovanému souboru. Cesta může být relativní, absolutní nebo název sítě (UNC).

*nOpenFlags*<br/>
UINT, který definuje režim sdílení a přístupu souboru. Určuje akci, která se má provést při otevírání souboru. Možnosti lze kombinovat pomocí operátoru bitového operátoru OR **&#124;** (). Vyžaduje se jedno oprávnění k přístupu a jedna možnost sdílení. režimy `modeCreate` a`modeNoInherit` jsou volitelné. Seznam možností režimu naleznete v konstruktoru [CFile –](#cfile) .

*pError*<br/>
Ukazatel na existující objekt s výjimkou souboru, který obdrží stav operace, která selhala.

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo otevření úspěšné; v opačném případě 0. Parametr *pError* má smysl pouze v případě, že je vrácena hodnota 0.

### <a name="remarks"></a>Poznámky

Tyto dvě `Open` funkce jsou "bezpečné" metody pro otevření souboru, kde selhání je normální, očekávaná podmínka.

I když `Open` konstruktor vyvolá výjimku v chybovém stavu, vrátí hodnotu false pro chybové podmínky. `CFile` `Open`může stále inicializovat objekt [CFileException](../../mfc/reference/cfileexception-class.md) , aby popsal chybu, ale. Pokud parametr *pError* nezadáte, nebo Pokud předáte hodnotu null pro *pError*, `Open` `CFileException`vrátí hodnotu false a nevyvolá. Pokud předáte ukazatel na existující `CFileException`a `Open` dojde k chybě, funkce ji vyplní informacemi, které popisují tuto chybu. `Open`v obou případech nevyvolá výjimku.

V následující tabulce jsou popsány možné `Open`výsledky.

|`pError`|Došlo k chybě|Návratová hodnota|CFileException obsah|
|--------------|------------------------|------------------|----------------------------|
|NULL|Ne|PODMÍNKA|není k dispozici|
|PTR na`CFileException`|Ne|PODMÍNKA|oproti|
|NULL|Ano|CHYBNÉ|není k dispozici|
|PTR na`CFileException`|Ano|CHYBNÉ|inicializováno k popisu chyby|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>CFile –:: operator – popisovač

Pomocí tohoto `CFile` operátoru můžete předat popisovač objektu funkcím, jako jsou například [ReadFileEx](/windows/desktop/api/fileapi/nf-fileapi-readfileex) a [funkce GetFileTime](/windows/desktop/api/fileapi/nf-fileapi-getfiletime) , které očekávají `HANDLE`.

```
operator HANDLE() const;
```

##  <a name="read"></a>CFile –:: Read

Načte data do vyrovnávací paměti ze souboru přidruženého `CFile` k objektu.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na vyrovnávací paměť zadanou uživatelem, která bude přijímat data načtená ze souboru.

*nCount*<br/>
Maximální počet bajtů, které mají být ze souboru načteny. Pro soubory v textovém režimu se páry návratového řádku započítávají jako jednotlivé znaky.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů přenesených do vyrovnávací paměti. Pro všechny `CFile` třídy může být návratová hodnota menší než *nCount* , pokud bylo dosaženo konce souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Další příklad naleznete v tématu [CFile –:: Open](#open).

##  <a name="remove"></a>CFile –:: Remove

Tato statická funkce odstraní soubor určený cestou.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Řetězec, který představuje cestu k požadovanému souboru. Cesta může být relativní nebo absolutní a může obsahovat název sítě.

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

`Remove`neodebere adresář.

`Remove` Členská funkce vyvolá výjimku, pokud je připojený soubor otevřen nebo pokud soubor nelze odebrat. Tato funkce je ekvivalentní příkazu DEL.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>CFile –:: rename

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

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

Adresáře nelze přejmenovat. Tato funkce je ekvivalentní příkazu REN.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>CFile –:: Seek

Přemístí ukazatel na soubor v otevřeném souboru.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOff*<br/>
Počet bajtů, které mají přesunout ukazatel na soubor. Kladné hodnoty posunou ukazatel souboru směrem ke konci souboru; záporné hodnoty přesunou ukazatel souboru směrem k začátku souboru.

*Nze*<br/>
Pozice pro hledání. Možné hodnoty jsou uvedeny v části poznámky.

### <a name="return-value"></a>Návratová hodnota

Pozice ukazatele souboru, pokud byla metoda úspěšná; v opačném případě není návratová hodnota definována a je vyvolána ukazatel `CFileException` na výjimku.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny možné hodnoty parametru *Nze* .

|Value|Popis|
|-----------|-----------------|
|`CFile::begin`|Hledání od začátku souboru.|
|`CFile::current`|Vyhledejte z aktuálního umístění ukazatele souboru.|
|`CFile::end`|Vyhledejte z konce souboru.|

Když je otevřen soubor, ukazatel na soubor je umístěný na 0, začátek souboru.

Ukazatel na soubor můžete nastavit na pozici za koncem souboru. Pokud tak učiníte, velikost souboru se nezvýší, dokud nebudete zapisovat do souboru.

Obslužná rutina výjimky pro tuto metodu musí po zpracování výjimky odstranit objekt výjimky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>CFile –:: SeekToBegin

Nastaví hodnotu ukazatele souboru na začátek souboru.

```
void SeekToBegin();
```

### <a name="remarks"></a>Poznámky

`SeekToBegin()`je ekvivalentem `Seek( 0L, CFile::begin )`k.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>CFile –:: SeekToEnd

Nastaví hodnotu ukazatele souboru na logický konec souboru.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>Návratová hodnota

Délka souboru v bajtech

### <a name="remarks"></a>Poznámky

`SeekToEnd()`je ekvivalentem `CFile::Seek( 0L, CFile::end )`k.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>CFile –:: SetFilePath

Voláním této funkce určíte cestu k souboru. Například pokud cesta k souboru není k dispozici, když je vytvořen objekt [CFile –](../../mfc/reference/cfile-class.md) , zavolejte `SetFilePath` k jeho poskytnutí.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Ukazatel na řetězec určující novou cestu.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> `SetFilePath`neotevře soubor nebo soubor nevytvoří. jednoduše přidružuje `CFile` objekt k názvu cesty, který lze použít.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>CFile –:: SetLength

Voláním této funkce změníte délku souboru.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen*<br/>
Požadovaná délka souboru v bajtech Tato hodnota může být větší nebo menší než aktuální délka souboru. Soubor bude v případě potřeby rozšířen nebo zkrácen.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  S `CMemFile`nástrojem by tato funkce mohla `CMemoryException` vyvolat objekt.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>CFile –:: SetStatus

Nastaví stav souboru přidruženého k tomuto umístění souboru.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Řetězec, který představuje cestu k požadovanému souboru. Cesta může být relativní nebo absolutní a může obsahovat název sítě.

*status*<br/>
Vyrovnávací paměť obsahující nové informace o stavu. Zavolejte členskou funkci pro vyplnění struktury aktuálními hodnotami a proveďte změny podle potřeby. `CFileStatus` `GetStatus` Pokud je hodnota 0, odpovídající stavová položka nebude aktualizována. Popis`CFileStatus` struktury [](#getstatus) naleznete v tématu členské funkce GetStatus.

*pTM*<br/>
Ukazatel na objekt CAtlTransactionManager

### <a name="remarks"></a>Poznámky

Chcete-li nastavit čas, upravte `m_mtime` pole *stav*.

Když zavoláte `SetStatus` do v pokusu o změnu pouze atributů souboru `m_mtime` a člen struktury stavu souboru je nenulová, může být ovlivněn i atributů (změna časového razítka může mít vedlejší účinky na atributy). Chcete-li změnit pouze atributy souboru, nejprve nastavte `m_mtime` člena struktury stav souboru na hodnotu nula a poté proveďte `SetStatus`volání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>CFile –:: UnlockRange

Odemkne rozsah bajtů v otevřeném souboru.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Posun bajtů začátku rozsahu bajtů, který se má odemknout

*dwCount*<br/>
Počet bajtů v rozsahu, který se má odemknout

### <a name="remarks"></a>Poznámky

Podrobnosti najdete v popisu členské funkce [LockRange](#lockrange) .

> [!NOTE]
>  Tato funkce není k dispozici pro `CMemFile`třídu odvozenou od třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>CFile –:: Write

Zapisuje data z vyrovnávací paměti do souboru přidruženého `CFile` k objektu.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na vyrovnávací paměť zadanou uživatelem, která obsahuje data, která mají být zapsána do souboru.

*nCount*<br/>
Počet bajtů, které mají být přeneseny z vyrovnávací paměti. Pro soubory v textovém režimu se páry návratového řádku započítávají jako jednotlivé znaky.

### <a name="remarks"></a>Poznámky

`Write`vyvolá výjimku v reakci na několik podmínek, včetně podmínky úplného disku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Podívejte se také na příklady pro [CFile –:: CFile –](#cfile) a [CFile –:: Open](#open).

## <a name="see-also"></a>Viz také:

[DRAWCLI Sample MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile – třída](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile – třída](../../mfc/reference/cmemfile-class.md)
