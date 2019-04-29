---
title: Cfile – třída
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
ms.openlocfilehash: db499ffa5f1d82b6e3622287f86132930a929102
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385307"
---
# <a name="cfile-class"></a>Cfile – třída

Základní třída pro třídy souborů Microsoft Foundation Class.

## <a name="syntax"></a>Syntaxe

```
class CFile : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CFile::CFile](#cfile)|Vytvoří `CFile` objekt z cesty nebo souboru popisovače.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CFile::Abort](#abort)|Zavře soubor bez ohledu na všechna upozornění a chyby.|
|[CFile::Close](#close)|Soubor se zavře a odstraní objekt.|
|[CFile::Duplicate](#duplicate)|Vytvoří objekt duplicitní na základě tohoto souboru.|
|[CFile::Flush](#flush)|Vyprázdní žádná data ještě má být proveden zápis.|
|[CFile::GetFileName](#getfilename)|Načte název souboru vybraného souboru.|
|[CFile::GetFilePath](#getfilepath)|Získá úplnou cestou k souboru vybraného souboru.|
|[CFile::GetFileTitle](#getfiletitle)|Načte název vybraného souboru.|
|[CFile::GetLength](#getlength)|Načte délku souboru.|
|[CFile::GetPosition](#getposition)|Načte aktuální ukazatel na soubor.|
|[CFile::GetStatus](#getstatus)|Načte stav otevřít soubor, nebo statické verze, načítá stav zadaného souboru (statické, virtuální funkce).|
|[CFile::LockRange](#lockrange)|Zamkne rozsah bajtů v souboru.|
|[CFile::Open](#open)|Bezpečně otevře soubor s možností testování chyby.|
|[CFile::Read](#read)|Operace čtení (bez vyrovnávací paměti) data ze souboru na aktuální pozici souboru.|
|[CFile::Remove](#remove)|Odstraní zadaný soubor (statická funkce).|
|[CFile::Rename](#rename)|Přejmenuje zadaný soubor (statická funkce).|
|[CFile::Seek](#seek)|Umístí ukazatel na aktuální soubor.|
|[CFile::SeekToBegin](#seektobegin)|Ukazatel na aktuální soubor se umístí na začátku souboru.|
|[CFile::SeekToEnd](#seektoend)|Umístí ukazatel na aktuální soubor na konci souboru.|
|[CFile::SetFilePath](#setfilepath)|Nastaví úplnou cestou k souboru vybraného souboru.|
|[CFile::SetLength](#setlength)|Délka souboru se změní.|
|[CFile::SetStatus](#setstatus)|Nastaví stav zadaného souboru (statické, virtuální funkce).|
|[CFile::UnlockRange](#unlockrange)|Odemkne celou řadu bajtů v souboru.|
|[CFile::Write](#write)|Zápisy (bez vyrovnávací paměti) data do souboru na aktuální pozici souboru.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CFile::operator POPISOVAČ](#operator_handle)|Popisovač `CFile` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|Určuje, zda `CFile` objekt má platný popisovač.|
|[CFile::m_hFile](#m_hfile)|Obvykle obsahuje popisovač souboru operačního systému.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objektu.|

## <a name="remarks"></a>Poznámky

Přímo obsahuje vstupní a výstupní služby bez vyrovnávací paměti, binární disku a podporuje nepřímo textové soubory a soubory z paměti prostřednictvím odvozené třídy. `CFile` funguje ve spojení s `CArchive` třídy pro podporu serializaci objektů Microsoft Foundation Class.

Hierarchický vztah mezi tato třída a odvozené třídy umožňuje programu použít pro všechny objekty souboru prostřednictvím polymorfní `CFile` rozhraní. Soubor paměti, například chová jako soubor na disku.

Použití `CFile` a odvozené třídy pro obecné účely diskové vstupně-výstupních operací. Použití `ofstream` nebo jiné třídy iostream – Microsoft pro formátovaný text odeslaný do souboru na disku.

Za normálních okolností automaticky při otevření souboru na disku `CFile` konstrukcí a destrukcí na Uzavřeno. Statické členské funkce umožňují dotazování stav bez otevření souboru.

Další informace o používání `CFile`, najdete v článcích [soubory v prostředí MFC](../../mfc/files-in-mfc.md) a [zpracování souborů](../../c-runtime-library/file-handling.md) v *Run-Time Library Reference*.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afx.h

##  <a name="abort"></a>  CFile::Abort

Soubor přidružený k tomuto objektu se zavře a znepřístupní soubor pro čtení nebo zápis.

```
virtual void Abort();
```

### <a name="remarks"></a>Poznámky

Pokud soubor ještě zavřen před zničení objektu, destruktor zavře za vás.

Při zpracování výjimek, `CFile::Abort` se liší od `CFile::Close` dvěma důležitými způsoby. Nejprve je potřeba `Abort` funkce nebude na selhání vyvolat výjimku, protože selhání jsou ignorovány ve `Abort`. Druhý, `Abort` nebudou **ASSERT** Pokud soubor nebyl otevřen nebo bylo již ukončeno.

Pokud jste použili **nové** přidělení `CFile` objektů na haldě, pak je nutné odstranit až po zavření souboru. `Abort` Nastaví `m_hFile` k `CFile::hFileNull`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>  CFile::CFile

Vytvoří a inicializuje `CFile` objektu.

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
Popisovač souboru pro připojení k `CFile` objektu.

*lpszFileName*<br/>
Úplná nebo relativní cestu k souboru se připojit k `CFile` objektu.

*nOpenFlags*<br/>
Bitová kombinace (nebo) možnosti přístupu k souboru pro určený soubor. Možnosti v části poznámky.

*pTM*<br/>
Ukazatel na catltransactionmanager – objekt

### <a name="remarks"></a>Poznámky

Následující tabulky obsahují pět seznam možností *nOpenFlags* parametru.

Zvolte pouze jeden z následujících možností režim přístupu k souboru. Je výchozí režim přístupu k souboru `CFile::modeRead`, která je jen pro čtení.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::modeRead`|Požadavky na přístup jen pro čtení.|
|`CFile::modeWrite`|Požadavky pouze oprávnění k zápisu.|
|`CFile::modeReadWrite`|Požadavky na čtení a zápis.|

Zvolte jednu z následujících možností režimu znak.

|Value|Popis|
|-----------|-----------------|
|`CFile::typeBinary`|Nastaví binárním režimu (používané pouze odvozené třídy).|
|`CFile::typeText`|Nastaví režim text s speciální zpracování pro návrat na začátek řádku dvojice návratový znak odřádkování (používané pouze odvozené třídy).|
|`CFile::typeUnicode`|Nastaví režim kódování Unicode (používané pouze odvozené třídy). Text je zapsán do souboru ve formátu Unicode, když je aplikace sestavená v konfiguraci ve formátu Unicode. Žádný BOM je zapsána do souboru.|

Zvolte pouze jeden z následujících možností režimu sdílené složky souboru. Je výchozí režim sdílené složky souboru `CFile::shareExclusive`, což je exkluzivní.

|Value|Popis|
|-----------|-----------------|
|`CFile::shareDenyNone`|Žádná omezení sdílení.|
|`CFile::shareDenyRead`|Odepřít přístup pro čtení pro všechny ostatní.|
|`CFile::shareDenyWrite`|Odepřít přístup pro zápis pro všechny ostatní.|
|`CFile::shareExclusive`|Zakazuje čtení a zápis pro všechny ostatní.|

Zvolte první, nebo obě z následujících možností vytvoření režim souboru. Je výchozí režim vytváření `CFile::modeNoTruncate`, což je otevřít existující.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::modeCreate`|Vytvoří nový soubor, pokud neexistuje žádný soubor. Pokud soubor již existuje, je přepsán a zpočátku nastaven nulovou délku.|
|`CFile::modeNoTruncate`|Vytvoří nový soubor, pokud neexistuje žádný soubor; jinak, pokud soubor již existuje, je připojen k `CFile` objektu.|

Vyberte následující soubor ukládání do mezipaměti možnosti, jak je popsáno. Ve výchozím nastavení používá systém obecné schéma, které není k dispozici možnost ukládání do mezipaměti.

|Value|Popis|
|-----------|-----------------|
|`CFile::osNoBuffer`|Systém nepoužívá zprostředkující mezipaměti souboru. Tato volba zruší následující 2 možnosti.|
|`CFile::osRandomAccess`|Soubor mezipaměti je optimalizované pro náhodný přístup. Nepoužívejte tuto možnost a možnost kontroly sekvenční.|
|`CFile::osSequentialScan`|Soubor mezipaměti je optimalizovaná pro sekvenční přístup. Nepoužívejte tuto možnost a možnosti náhodného přístupu.|
|`CFile::osWriteThrough`|Zápisu operace jsou prováděny bez zpoždění.|

Vyberte následující možnost zabezpečení zabránit děděny popisovač souboru. Ve výchozím nastavení můžete použít všechny nové podřízené procesy popisovač souboru.

|Value|Popis|
|-----------|-----------------|
|`CFile::modeNoInherit`|Všechny podřízené procesy bránit v použití popisovače souboru.|

Výchozí konstruktor inicializuje členy, ale nepřipojí soubor, který chcete `CFile` objektu. Po použití tohoto konstruktoru, použijte [CFile::Open](#open) metodu pro otevření souboru a připojte ji k `CFile` objektu.

Konstruktor s jedním parametrem inicializuje členy a připojí k existující soubor `CFile` objektu.

Konstruktor se dvěma parametry inicializuje členy a pokusí otevřít zadaný soubor. Pokud se tento konstruktor úspěšně otevře zadaný soubor, soubor je připojen k `CFile` objektu; v opačném případě vyvolá ukazatel na tento konstruktor `CInvalidArgException` objektu. Další informace o tom, jak zpracování výjimek naleznete v tématu [výjimky](../../mfc/exception-handling-in-mfc.md).

Pokud `CFile` objekt úspěšně otevře zadaný soubor, dojde k uzavření tento soubor automaticky při `CFile` zničení objektu; v opačném případě musíte explicitně zavřít soubor po je již připojen k `CFile` objektu.

### <a name="example"></a>Příklad

Následující kód ukazuje, jak používat `CFile`.

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>  CFile::Close

Soubor přidružený k tomuto objektu se zavře a znepřístupní soubor pro čtení nebo zápis.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Pokud soubor ještě zavřen před zničení objektu, destruktor zavře za vás.

Pokud jste použili **nové** přidělení `CFile` objektů na haldě, pak je nutné odstranit až po zavření souboru. `Close` Nastaví `m_hFile` k `CFile::hFileNull`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFile::CFile](#cfile).

##  <a name="duplicate"></a>  CFile::Duplicate

Vytvoří duplicitní `CFile` objekt pro daný soubor.

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na duplicitní `CFile` objektu.

### <a name="remarks"></a>Poznámky

Jedná se o ekvivalent k funkci run-time C `_dup`.

##  <a name="flush"></a>  CFile::Flush

Vynutí žádná data zbývajících ve vyrovnávací paměti souboru má být zapsán do souboru.

```
virtual void Flush();
```

### <a name="remarks"></a>Poznámky

Použití `Flush` nezaručuje vyprazdňování `CArchive` vyrovnávací paměti. Pokud používáte archiv, zavolejte [CArchive::Flush](../../mfc/reference/carchive-class.md#flush) první.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [CFile::SetFilePath](#setfilepath).

##  <a name="getfilename"></a>  CFile::GetFileName

Voláním této členské funkce, aby se načetl název zadaného souboru.

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název souboru.

### <a name="remarks"></a>Poznámky

Například při volání `GetFileName` se vygenerovat zprávu pro uživatele o souboru `c:\windows\write\myfile.wri`, název souboru, `myfile.wri`, je vrácena.

Chcete-li vrátit celou cestu k souboru, včetně názvu, zavolejte [GetFilePath](#getfilepath). Vrátit název souboru ( `myfile`), volání [GetFileTitle](#getfiletitle).

### <a name="example"></a>Příklad

Tento fragment kódu se otevře v systému. Soubor INI v adresáři systému WINDOWS. Pokud najde, příklad vytiskne název a cestu a název, jak je znázorněno v rámci výstupu:

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>  CFile::GetFilePath

Voláním této členské funkce k načtení úplná cesta zadaného souboru.

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>Návratová hodnota

Úplná cesta zadaného souboru.

### <a name="remarks"></a>Poznámky

Například při volání `GetFilePath` se vygenerovat zprávu pro uživatele o souboru `c:\windows\write\myfile.wri`, cesta k souboru, `c:\windows\write\myfile.wri`, je vrácena.

Vrátit pouze název souboru (`myfile.wri`), volání [GetFileName](#getfilename). Vrátit název souboru (`myfile`), volání [GetFileTitle](#getfiletitle).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetFileName](#getfilename).

##  <a name="getfiletitle"></a>  CFile::GetFileTitle

Voláním této členské funkce k načtení názvu souboru (zobrazovaný název) pro soubor.

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>Návratová hodnota

Název základního souboru.

### <a name="remarks"></a>Poznámky

Tato metoda volá [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea) k načtení názvu souboru. V případě úspěchu, metoda vrátí řetězec, který systém použít k zobrazovaný název souboru pro uživatele. V opačném případě metoda volá [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) načíst název souboru základního souboru (včetně přípony souboru). V nadpisu vráceného souboru proto nebudou vždy zahrnuty příponu souboru. Další informace najdete v tématu [GetFileTitle](/windows/desktop/api/commdlg/nf-commdlg-getfiletitlea) a [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea) v sadě Windows SDK.

Chcete-li vrátit celou cestu k souboru, včetně názvu, zavolejte [GetFilePath](#getfilepath). Chcete-li vrátit pouze název souboru, zavolejte [GetFileName](#getfilename).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [GetFileName](#getfilename).

##  <a name="getlength"></a>  CFile::GetLength

Získá aktuální délka logického souboru v bajtech.

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>Návratová hodnota

Délka souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>  CFile::GetPosition

Získá aktuální hodnotu ukazatel na soubor, který můžete použít v následných voláních `Seek`.

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na soubor.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>  CFile::GetStatus

Tato metoda načte informace o stavu, které souvisí dané `CFile` instance objektu nebo zadaná cesta k souboru.

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*rStatus*<br/>
Odkaz na uživatelem zadané `CFileStatus` struktura, která se zobrazí informace o stavu. `CFileStatus` Struktura obsahuje následující pole:

- `CTime m_ctime` Datum a čas vytvoření souboru.

- `CTime m_mtime` Datum a čas poslední změny souboru.

- `CTime m_atime` Datum a čas posledního přístupu k souboru pro čtení.

- `ULONGLONG m_size` Logická velikost souboru v bajtech, jak je hlásí příkazu DIR.

- `BYTE m_attribute` Byte atribut souboru.

- `char m_szFullName[_MAX_PATH]` Absolutní název souboru ve znakové sadě Windows.

*lpszFileName*<br/>
Řetězec znaků Windows nastavte, který je cestu do požadovaného souboru. Cesta může být relativní nebo absolutní, nebo může obsahovat název síťové cesty.

*pTM*<br/>
Ukazatel na catltransactionmanager – objekt

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud informace o stavu pro zadaný soubor se úspěšně získá; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Nestatická verzi `GetStatus` načte informace o stavu otevřít souboru přidruženého daný `CFile` objektu.  Statické verze `GetStatus` získá stav souboru z cesty daný soubor bez skutečně otevření souboru. To je užitečné pro testování existence a přístupová práva souboru.

`m_attribute` Člena `CFileStatus` struktura odkazuje na sadu atributů souboru. `CFile` Třída poskytuje **atribut** typ výčtu, takže atributy souborů lze symbolicky:

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

##  <a name="hfilenull"></a>  CFile::hFileNull

Určuje existenci platného popisovače souboru pro `CFile` objektu.

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Poznámky

Tato konstanta se používá k určení, zda `CFile` objekt nemá platného popisovače souboru.

Následující příklad ukazuje tuto operaci:

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>  CFile::LockRange

Zamkne rozsah bajtů v otevření souboru došlo k výjimce, pokud soubor už je uzamknuté.

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Posun bajtů počáteční rozsah bajtů k uzamčení.

*dwCount*<br/>
Počet bajtů v rozsahu, který chcete zamknout.

### <a name="remarks"></a>Poznámky

Zamykací bajty v souboru brání v přístupu k těmto bajtů s jinými procesy. Můžeš více než jedné oblasti souboru, ale žádné překrývající se oblasti jsou povoleny.

Po odemknutí oblast pomocí `UnlockRange` členskou funkci, rozsah bajtů musí přesně odpovídat oblasti, která dříve byla uzamčena. `LockRange` Funkce nesloučí sousední oblasti; pokud jsou dvě oblasti uzamčené vedle sebe, musí každá oblast odemknout samostatně.

> [!NOTE]
>  Tato funkce není k dispozici pro `CMemFile`-odvozené třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>  CFile::m_hFile

Obsahuje popisovač souboru operačního systému pro otevření souboru.

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Poznámky

`m_hFile` je veřejná proměnná typu UINT. Obsahuje `CFile::hFileNull` (prázdný soubor operačního systému – nezávislé na ukazatel) Pokud je popisovač nebyl přiřazen.

Použití `m_hFile` se nedoporučuje, protože člen význam závisí na odvozenou třídu. `m_hFile` provedení veřejného člena pro usnadnění práce při podpoře nepolymorfních použít třídy.

##  <a name="m_ptm"></a>  CFile::m_pTM

Ukazatel `CAtlTransactionManager` objektu.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Poznámky

##  <a name="open"></a>  CFile::Open

Přetíženo. `Open` je určený pro použití s výchozím `CFile` konstruktoru.

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
Řetězec, který určuje cestu k souboru požadovaného. Cesta může být relativní nebo absolutní, název sítě (UNC).

*nOpenFlags*<br/>
UINT, který definuje režim sdílení a přístup k souboru. Určuje akci, která má provést při otevírání souboru. Možnosti lze kombinovat pomocí bitového operátoru OR ( **&#124;** ) – operátor. Jsou vyžadovány; jeden přístupová oprávnění a možnost jedna sdílená složka `modeCreate` a `modeNoInherit` režimy jsou volitelné. Zobrazit [cfile –](#cfile) konstruktor pro seznam možností režimu.

*pError*<br/>
Ukazatel na existující objekt výjimky souborů, který se zobrazí stav operace, která selhala.

*pTM*<br/>
Ukazatel na catltransactionmanager – objekt

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud otevřít byla úspěšná. jinak 0. *PError* parametr má smysl pouze v případě, že se vrátí 0.

### <a name="remarks"></a>Poznámky

Tyto dvě funkce tvoří "bezpečné" metodu pro otevření souboru, kde je normální, očekávaný stav selhání.

Zatímco `CFile` konstruktor vyvolá výjimku v chybový stav, `Open` vrátí hodnotu FALSE pro chybové podmínky. `Open` stále můžete inicializovat [cfileexception –](../../mfc/reference/cfileexception-class.md) objekt popisující chybu, ale. Pokud nezadáte *pError* parametr, nebo Pokud předáte hodnotu NULL *pError*, `Open` vrátí hodnotu FALSE a nevyvolají výjimku `CFileException`. Pokud předáte ukazatel do existujícího `CFileException`, a `Open` zjistí chybu, funkce se vyplní jej s informace popisující chybu. V ani případu se `Open` vyvolat výjimku.

Následující tabulka popisuje možné důsledků `Open`.

|`pError`|Došlo k chybě|Návratová hodnota|Cfileexception – obsah|
|--------------|------------------------|------------------|----------------------------|
|NULL|Ne|HODNOTA TRUE|není k dispozici|
|PTR – k `CFileException`|Ne|HODNOTA TRUE|beze změny|
|NULL|Ano|FALSE|není k dispozici|
|PTR – k `CFileException`|Ano|FALSE|inicializovat k popisu chyby|

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>  CFile::operator POPISOVAČ

Operátor pro předání popisovač `CFile` objekt funkce, jako [readfileex spuštěná](/windows/desktop/api/fileapi/nf-fileapi-readfileex) a [funkce GetFileTime](/windows/desktop/api/fileapi/nf-fileapi-getfiletime) , které očekávají `HANDLE`.

```
operator HANDLE() const;
```

##  <a name="read"></a>  CFile::Read

Načte data do vyrovnávací paměti ze souboru spojené s `CFile` objektu.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel uživatelem zadané vyrovnávací paměti, která má obdržet data načtená ze souboru.

*nCount*<br/>
Maximální počet bajtů ke čtení ze souboru. Pro režim textové soubory návratový znak odřádkování páry znaků CR se počítají jako jednotlivé znaky.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů přenesených do vyrovnávací paměti. Všimněte si, že pro všechny `CFile` třídy, návratová hodnota může být kratší než *nCount* Pokud bylo dosaženo konce souboru.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

Další příklad naleznete v tématu [CFile::Open](#open).

##  <a name="remove"></a>  CFile::Remove

Tato statická funkce odstraní soubor určený parametrem cestu.

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Řetězec, který určuje cestu k souboru požadovaného. Cesta může být relativní nebo absolutní a může obsahovat název sítě.

*pTM*<br/>
Ukazatel na catltransactionmanager – objekt

### <a name="remarks"></a>Poznámky

Neodebere adresáře.

`Remove` Členská funkce vyvolá výjimku, pokud je připojený soubor otevřen nebo pokud soubor nelze odebrat. Jde o ekvivalent k příkazu DELETE.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>  CFile::Rename

Tato statická funkce přejmenuje zadaného souboru.

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszOldName*<br/>
Staré cestě.

*lpszNewName*<br/>
Novou cestu.

*pTM*<br/>
Ukazatel na catltransactionmanager – objekt

### <a name="remarks"></a>Poznámky

Adresáře nejde přejmenovat. Jde o ekvivalent příkazu REN.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>  CFile::Seek

Přemístí ukazatel na soubor v otevření souboru.

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOff*<br/>
Počet bajtů, které mají ukazatel souboru. Kladné hodnoty přesuňte ukazatel na soubor na konci souboru. záporné hodnoty přesuňte ukazatel na soubor směrem k začátku souboru.

*nFrom*<br/>
Pozice k vyhledání z. Možné hodnoty v části poznámky.

### <a name="return-value"></a>Návratová hodnota

Pozice ukazatel souboru, pokud metoda byla úspěšná. v opačném případě není definováno návratovou hodnotu a ukazatel `CFileException` je vyvolána výjimka.

### <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny možné hodnoty pro *Nze* parametru.

|Hodnota|Popis|
|-----------|-----------------|
|`CFile::begin`|Hledat od začátku souboru.|
|`CFile::current`|Vyhledávání z aktuálního umístění ukazatel na soubor.|
|`CFile::end`|Hledání od konce souboru.|

Když je soubor otevřen, ukazatel na soubor je umístěn na 0, začátek souboru.

Nastavení ukazatele souboru na pozici za koncem souboru. Pokud to uděláte, velikost souboru se nezvyšuje, dokud se zapisovat do souboru.

Obslužná rutina výjimky této metody musíte odstranit objekt výjimky po zpracování výjimky.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>  CFile::SeekToBegin

Nastaví hodnotu ukazatel na soubor na začátek souboru.

```
void SeekToBegin();
```

### <a name="remarks"></a>Poznámky

`SeekToBegin()` je ekvivalentní `Seek( 0L, CFile::begin )`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>  CFile::SeekToEnd

Nastaví hodnotu ukazatele souboru logické konec souboru.

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>Návratová hodnota

Délka souboru v bajtech.

### <a name="remarks"></a>Poznámky

`SeekToEnd()` je ekvivalentní `CFile::Seek( 0L, CFile::end )`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>  CFile::SetFilePath

Voláním této funkce zadejte cestu k souboru. například, pokud cesta k souboru není k dispozici při [cfile –](../../mfc/reference/cfile-class.md) objekt je vytvořen, zavolejte `SetFilePath` ho poskytnout.

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>Parametry

*lpszNewName*<br/>
Ukazatel na řetězec určující novou cestu.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> `SetFilePath` Otevřete soubor nebo vytvoření souboru. jednoduše přiřadí `CFile` objektu pomocí cesty, který je pak možné použít.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>  CFile::SetLength

Voláním této funkce, chcete-li změnit délku souboru.

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>Parametry

*dwNewLen*<br/>
Požadovaná délka souboru v bajtech. Tato hodnota může být větší nebo menší než aktuální délka souboru. Soubor se rozšířené nebo je oříznutá. podle potřeby.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  S `CMemFile`, tato funkce může vyvolat `CMemoryException` objektu.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>  CFile::SetStatus

Nastaví stav souboru přidružené k danému umístění souboru.

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parametry

*lpszFileName*<br/>
Řetězec, který určuje cestu k souboru požadovaného. Cesta může být relativní nebo absolutní a může obsahovat název sítě.

*status*<br/>
Vyrovnávací paměť obsahující nové informace o stavu. Volání `GetStatus` členskou funkci k předběžnému vyplnění `CFileStatus` struktury pomocí aktuální hodnoty a pak proveďte požadované změny. Pokud je hodnota 0, není aktualizován odpovídající položky stavu. Najdete v článku [GetStatus](#getstatus) členskou funkci Popis `CFileStatus` struktury.

*pTM*<br/>
Ukazatel na catltransactionmanager – objekt

### <a name="remarks"></a>Poznámky

Chcete-li nastavit čas, upravte `m_mtime` pole *stav*.

Upozorňujeme, že pokud provedete volání `SetStatus` ve snaze změnit pouze atributy souboru a `m_mtime` členu struktury stav souboru je nenulová, atributů může mít vliv i na (Změna času razítko může mít vedlejší účinky na atributy). Pokud chcete změnit pouze atributy souboru, nejprve nastavte `m_mtime` členu struktury stav souboru na hodnotu nula a pak proveďte volání `SetStatus`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>  CFile::UnlockRange

Odemkne celou řadu bajtů v otevření souboru.

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>Parametry

*dwPos*<br/>
Posun bajtů počáteční rozsah bajtů k odemknutí.

*dwCount*<br/>
Počet bajtů v rozsahu, který chcete odemknout.

### <a name="remarks"></a>Poznámky

Viz popis [LockRange](#lockrange) členskou funkci podrobnosti.

> [!NOTE]
>  Tato funkce není k dispozici pro `CMemFile`-odvozené třídy.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>  CFile::Write

Zapisuje data ze vyrovnávací paměť do souboru spojené s `CFile` objektu.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel uživatelem zadané vyrovnávací paměti, která obsahuje data, která mají být zapsána do souboru.

*nCount*<br/>
Počet bajtů, které mají být přeneseny z vyrovnávací paměti. Pro režim textové soubory návratový znak odřádkování páry znaků CR se počítají jako jednotlivé znaky.

### <a name="remarks"></a>Poznámky

`Write` vyvolá výjimku v reakci na několika podmínek, včetně stavu zaplnění disku.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

Kromě toho, podívejte se na příklady pro [CFile::CFile](#cfile) a [CFile::Open](#open).

## <a name="see-also"></a>Viz také:

[Ukázky knihovny MFC DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile – třída](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile – třída](../../mfc/reference/cmemfile-class.md)
