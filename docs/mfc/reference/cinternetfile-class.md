---
title: CInternetFile – třída
ms.date: 11/04/2016
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
helpviewer_keywords:
- CInternetFile [MFC], CInternetFile
- CInternetFile [MFC], Abort
- CInternetFile [MFC], Close
- CInternetFile [MFC], Flush
- CInternetFile [MFC], GetLength
- CInternetFile [MFC], Read
- CInternetFile [MFC], ReadString
- CInternetFile [MFC], Seek
- CInternetFile [MFC], SetReadBufferSize
- CInternetFile [MFC], SetWriteBufferSize
- CInternetFile [MFC], Write
- CInternetFile [MFC], WriteString
- CInternetFile [MFC], m_hFile
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
ms.openlocfilehash: e3f1a7167f5464423754951764c4441513197841
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372392"
---
# <a name="cinternetfile-class"></a>CInternetFile – třída

Umožňuje přístup k souborům ve vzdálených systémech, které používají internetové protokoly.

## <a name="syntax"></a>Syntaxe

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetFile::CInternetFile](#cinternetfile)|Vytvoří `CInternetFile` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetFile::Přerušit](#abort)|Zavře soubor a ignoruje všechna upozornění a chyby.|
|[CInternetFile::Zavřít](#close)|Zavře `CInternetFile` a uvolní své prostředky.|
|[CInternetFile::Vyprázdnění](#flush)|Vyprázdní obsah vyrovnávací paměti pro zápis a zajistí, že data v paměti jsou zapsána do cílového počítače.|
|[CInternetFile::GetLength](#getlength)|Vrátí velikost souboru.|
|[CInternetFile::Číst](#read)|Přečte počet určených bajtů.|
|[CInternetFile::Řetězec čtení](#readstring)|Přečte proud znaků.|
|[CInternetFile::Hledat](#seek)|Přemístí ukazatel do otevřeného souboru.|
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Nastaví velikost vyrovnávací paměti, kde budou data číst.|
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Nastaví velikost vyrovnávací paměti, kde budou zapsána data.|
|[CInternetFile::Zápis](#write)|Zapíše počet určených bajtů.|
|[CInternetFile::Řetězec zápisu](#writestring)|Zapíše do souboru řetězec s ukončeným hodnotou null.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetFile::operátor HINTERNET](#operator_hinternet)|Operátor odlitku pro popisovač internetu.|

### <a name="protected-data-members"></a>Členové chráněných dat

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetFile::m_hFile](#m_hfile)|Popisovač souboru.|

## <a name="remarks"></a>Poznámky

Poskytuje základní třídu pro třídy souborů [CHttpFile](../../mfc/reference/chttpfile-class.md) a [CGopherFile.](../../mfc/reference/cgopherfile-class.md) Nikdy nevytváříte `CInternetFile` objekt přímo. Místo toho vytvořte objekt jedné z jeho odvozených tříd voláním [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) nebo [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Objekt můžete také `CInternetFile` vytvořit voláním [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

Členské `CInternetFile` funkce `Open` `LockRange`, `UnlockRange`, `Duplicate` a nejsou `CInternetFile`implementovány pro . Pokud voláte tyto `CInternetFile` funkce na objekt, získáte [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Další informace o `CInternetFile` práci s ostatními třídami MFC Internet naleznete v článku [Internetové programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

[Soubor CStdio](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cinternetfileabort"></a><a name="abort"></a>CInternetFile::Přerušit

Zavře soubor přidružený k tomuto objektu a znepřístupní soubor pro čtení nebo zápis.

```
virtual void Abort();
```

### <a name="remarks"></a>Poznámky

Pokud jste soubor nezavřeli před zničením objektu, destruktor jej zavře za vás.

Při zpracování výjimek `Abort` se liší od [Close](#close) dvěma důležitými způsoby. Za prvé, `Abort` funkce nevyvolá výjimku na selhání, protože ignoruje selhání. Za `Abort` druhé, není **ASSERT,** pokud soubor nebyl otevřen nebo byl uzavřen dříve.

## <a name="cinternetfilecinternetfile"></a><a name="cinternetfile"></a>CInternetFile::CInternetFile

Tato členská funkce `CInternetFile` je volána při vytvoření objektu.

```
CInternetFile(
    HINTERNET hFile,
    LPCTSTR pstrFileName,
    CInternetConnection* pConnection,
    BOOL bReadMode);

CInternetFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrFileName,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext,
    BOOL bReadMode);
```

### <a name="parameters"></a>Parametry

*hSoubor*<br/>
Popisovač k souboru internetu.

*název souboru pstrFile*<br/>
Ukazatel na řetězec obsahující název souboru.

*pPřipojení*<br/>
Ukazatel na objekt [CInternetConnection.](../../mfc/reference/cinternetconnection-class.md)

*bReadMode*<br/>
Označuje, zda je soubor jen pro čtení.

*hRelace*<br/>
Popisovač relace Internetu.

*server pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru.

*dwKontext*<br/>
Identifikátor kontextu pro `CInternetFile` objekt. Další informace o identifikátoru kontextu naleznete v tématu [Základy wininet.](../../mfc/wininet-basics.md)

### <a name="remarks"></a>Poznámky

Nikdy nevytváříte `CInternetFile` objekt přímo. Místo toho vytvořte objekt jedné z jeho odvozených tříd voláním [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) nebo [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Objekt můžete také `CInternetFile` vytvořit voláním [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

## <a name="cinternetfileclose"></a><a name="close"></a>CInternetFile::Zavřít

Zavře `CInternetFile` a uvolní všechny své prostředky.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Pokud byl soubor otevřen pro zápis, je implicitní volání [Flush](#flush) zajistit, že všechna data ve vyrovnávací paměti je zapsána do hostitele. Měli byste `Close` zavolat po dokončení používání souboru.

## <a name="cinternetfileflush"></a><a name="flush"></a>CInternetFile::Vyprázdnění

Volání této členské funkce vyprázdnění obsahu vyrovnávací paměti pro zápis.

```
virtual void Flush();
```

### <a name="remarks"></a>Poznámky

Slouží `Flush` k zajištění, že všechna data v paměti byla skutečně zapsána do cílového počítače a zajistit, aby vaše transakce s hostitelským počítačem byla dokončena. `Flush`je účinný `CInternetFile` pouze u objektů otevřených pro psaní.

## <a name="cinternetfilegetlength"></a><a name="getlength"></a>CInternetFile::GetLength

Vrátí velikost souboru.

```
virtual ULONGLONG GetLength() const;
```

## <a name="cinternetfilem_hfile"></a><a name="m_hfile"></a>CInternetFile::m_hFile

Popisovač souboru přidruženého k tomuto objektu.

```
HINTERNET m_hFile;
```

## <a name="cinternetfileoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetFile::operátor HINTERNET

Pomocí tohoto operátoru získáte popisovač systému Windows pro aktuální relaci Internetu.

```
operator HINTERNET() const;
```

## <a name="cinternetfileread"></a><a name="read"></a>CInternetFile::Číst

Volání této členské funkce číst do dané paměti, počínaje *lpvBuf*, zadaný počet bajtů, *nCount*.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na adresu paměti, na kterou se čtou data souboru.

*nCount*<br/>
Počet bajtů, které mají být zapsány.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů přenesených do vyrovnávací paměti. Vrácená hodnota může být menší než *nCount,* pokud bylo dosaženo konce souboru.

### <a name="remarks"></a>Poznámky

Funkce vrátí počet bajtů skutečně číst – číslo, které může být menší než *nCount,* pokud soubor končí. Pokud dojde k chybě při čtení souboru, funkce vyvolá [CInternetException](../../mfc/reference/cinternetexception-class.md) objekt, který popisuje chybu. Všimněte si, že čtení za koncem souboru není považováno za chybu a nebude vyvolána žádná výjimka.

Chcete-li zajistit všechna data jsou načteny, `CInternetFile::Read` aplikace musí pokračovat v volání metody, dokud metoda vrátí nulu.

## <a name="cinternetfilereadstring"></a><a name="readstring"></a>CInternetFile::Řetězec čtení

Volání této členské funkce číst proud znaků, dokud nenajde znak nového řádku.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>Parametry

*str.*<br/>
Ukazatel na řetězec, který obdrží řádek, který se čte.

*nMax*<br/>
Maximální počet znaků, které mají být přečteny.

*rString*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který přijímá řádek pro čtení.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyrovnávací paměť obsahující prostá data načtená z objektu [CInternetFile.](../../mfc/reference/cinternetfile-class.md) Bez ohledu na datový typ vyrovnávací paměti předané této metodě neprovádí žádné manipulace s daty (například převod na Unicode), takže je nutné namapovat vrácená data na strukturu, kterou očekáváte, jako by byl vrácen typ **void.** <strong>\*</strong>

NULL, pokud bylo dosaženo konce souboru bez čtení dat; nebo, pokud je logická hodnota NEPRAVDA, pokud bylo dosaženo konce souboru bez čtení dat.

### <a name="remarks"></a>Poznámky

Funkce umístí výsledný řádek do paměti odkazuje *pstr* parametr. Zastaví čtení znaků, když dosáhne maximálního počtu znaků, *určeného nMax*. Vyrovnávací paměť vždy obdrží ukončující znak null.

Pokud voláte `ReadString` bez předchozího volání [SetReadBufferSize](#setreadbuffersize), získáte vyrovnávací paměť 4096 bajtů.

## <a name="cinternetfileseek"></a><a name="seek"></a>CInternetFile::Hledat

Volání této členské funkce pro přemístění ukazatele v dříve otevřeném souboru.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOffset*<br/>
Posun v bajtů přesunout ukazatel pro čtení a zápis v souboru.

*nFrom*<br/>
Relativní odkaz pro posun. Toto musí být jedna z následujících hodnot:

- `CFile::begin`Přesuňte ukazatel souboru *lOff* bajty dopředu od začátku souboru.

- `CFile::current`Přesuňte ukazatel souboru *lOff* bajtů z aktuální pozice v souboru.

- `CFile::end`Přesuňte ukazatel souboru *lOff* bajtů z konce souboru. *lOff* musí být negativní hledat do existujícího souboru; kladné hodnoty budou usilovat o konec souboru.

### <a name="return-value"></a>Návratová hodnota

Nový posun bajtů od začátku souboru, pokud je požadovaná pozice legální; v opačném případě hodnota není definována a je vyvolán objekt [CInternetException.](../../mfc/reference/cinternetexception-class.md)

### <a name="remarks"></a>Poznámky

Funkce `Seek` umožňuje náhodný přístup k obsahu souboru přesunutím ukazatele o zadanou částku, absolutně nebo relativně. Během hledání se ve skutečnosti nečtou žádná data.

V současné době volání této členské funkce je podporována pouze pro data spojená s `CHttpFile` objekty. Není podporována pro požadavky FTP nebo gopher. Pokud zavoláte `Seek` pro jednu z těchto nepodporovaných služeb, předá vám zpět do kódu chyby Win32 ERROR_INTERNET_INVALID_OPERATION.

Při otevření souboru je ukazatel souboru v posunu 0, začátek souboru.

> [!NOTE]
> Použití `Seek` může způsobit implicitní volání [Flush](#flush).

### <a name="example"></a>Příklad

  Viz příklad pro implementaci základní třídy ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).

## <a name="cinternetfilesetreadbuffersize"></a><a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize

Volání této členské funkce nastavit velikost dočasné vyrovnávací `CInternetFile`paměti pro čtení používá -derived objektu.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>Parametry

*nReadSize*<br/>
Požadovaná velikost vyrovnávací paměti v bajtů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Základní rozhraní API WinInet neprovádějí ukládání do vyrovnávací paměti, proto zvolte velikost vyrovnávací paměti, která umožňuje aplikaci efektivně číst data, bez ohledu na množství dat, která mají být přečtena. Pokud každé volání [Read](#read) obvykle zahrnuje velké aount dat (například čtyři nebo více kilobajtů), neměli byste potřebovat vyrovnávací paměť. Pokud však `Read` voláte získat malé bloky dat nebo pokud používáte [ReadString](#readstring) ke čtení jednotlivých řádků najednou, pak vyrovnávací paměť pro čtení zlepšuje výkon aplikace.

Ve výchozím `CInternetFile` nastavení objekt neposkytuje žádné ukládání do vyrovnávací paměti pro čtení. Pokud voláte tuto členovou funkci, musíte se ujistit, že soubor byl otevřen pro přístup pro čtení.

Velikost vyrovnávací paměti můžete kdykoli zvětšit, ale zmenšení vyrovnávací paměti nebude mít žádný vliv. Pokud zavoláte [ReadString](#readstring) `SetReadBufferSize`bez předchozího volání , získáte vyrovnávací paměť 4096 bajtů.

## <a name="cinternetfilesetwritebuffersize"></a><a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize

Volání této členské funkce nastavit velikost dočasného zápisu vyrovnávací paměti používané `CInternetFile`-derived objektu.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>Parametry

*nWriteSize*<br/>
Velikost vyrovnávací paměti v bajtů.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

### <a name="remarks"></a>Poznámky

Základní rozhraní API WinInet neprovádějí ukládání do vyrovnávací paměti, proto zvolte velikost vyrovnávací paměti, která umožňuje aplikaci efektivně zapisovat data bez ohledu na množství dat, která mají být zapsána. Pokud každé volání [Write](#write) obvykle zahrnuje velké množství dat (například čtyři nebo více kilobajtů najednou), neměli byste potřebovat vyrovnávací paměť. Pokud však zavoláte [Write](#write) zapisovat malé bloky dat, vyrovnávací paměť pro zápis zlepšuje výkon vaší aplikace.

Ve výchozím `CInternetFile` nastavení objekt neposkytuje žádné ukládání do vyrovnávací paměti pro zápis. Pokud voláte tuto členovou funkci, musíte se ujistit, že soubor byl otevřen pro přístup pro zápis. Velikost vyrovnávací paměti pro zápis můžete kdykoli změnit, ale to způsobí, že implicitní volání [flush](#flush).

## <a name="cinternetfilewrite"></a><a name="write"></a>CInternetFile::Zápis

Volání této členské funkce pro zápis do dané paměti, *lpvBuf*, zadaný počet bajtů, *nCount*.

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na první bajt, který má být zapsán.

*nCount*<br/>
Určuje počet bajtů, které mají být zapsány.

### <a name="remarks"></a>Poznámky

Pokud dojde k nějaké chybě při zápisu dat, funkce vyvolá [CInternetException](../../mfc/reference/cinternetexception-class.md) objekt popisující chybu.

## <a name="cinternetfilewritestring"></a><a name="writestring"></a>CInternetFile::Řetězec zápisu

Tato funkce zapíše řetězec s nulovým ukončením do přidruženého souboru.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>Parametry

*str.*<br/>
Ukazatel na řetězec obsahující obsah, který má být zapsán.

### <a name="remarks"></a>Poznámky

Pokud dojde k nějaké chybě při zápisu dat, funkce vyvolá [CInternetException](../../mfc/reference/cinternetexception-class.md) objekt popisující chybu.

## <a name="see-also"></a>Viz také

[CStdioFile – třída](../../mfc/reference/cstdiofile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CInternetConnection](../../mfc/reference/cinternetconnection-class.md)
