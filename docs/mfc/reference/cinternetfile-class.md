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
ms.openlocfilehash: 68a0a0f35d1a1f4519401080f9f207bf76c87079
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890776"
---
# <a name="cinternetfile-class"></a>CInternetFile – třída

Umožňuje přístup k souborům ve vzdálených systémech, které používají protokoly sítě Internet.

## <a name="syntax"></a>Syntaxe

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>Členové

### <a name="protected-constructors"></a>Chráněné konstruktory

|Název|Popis|
|----------|-----------------|
|[CInternetFile::CInternetFile](#cinternetfile)|Vytvoří objekt `CInternetFile`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CInternetFile:: Abort](#abort)|Zavře soubor a ignoruje všechna upozornění a chyby.|
|[CInternetFile:: Close](#close)|Zavře `CInternetFile` a uvolní jeho prostředky.|
|[CInternetFile:: flush](#flush)|Vyprázdní obsah vyrovnávací paměti pro zápis a zajistí, že jsou data v paměti zapsána do cílového počítače.|
|[CInternetFile:: GetLength](#getlength)|Vrátí velikost souboru.|
|[CInternetFile:: Read](#read)|Přečte počet zadaných bajtů.|
|[CInternetFile::ReadString](#readstring)|Přečte datový proud znaků.|
|[CInternetFile:: Seek](#seek)|Přemístí ukazatel v otevřeném souboru.|
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Nastaví velikost vyrovnávací paměti, do které se budou číst data.|
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Nastaví velikost vyrovnávací paměti, kam budou zapsána data.|
|[CInternetFile:: Write](#write)|Zapíše počet zadaných bajtů.|
|[CInternetFile::WriteString](#writestring)|Zapíše řetězec zakončený hodnotou null do souboru.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CInternetFile:: operator HINTERNET](#operator_hinternet)|Operátor přetypování pro internetový popisovač.|

### <a name="protected-data-members"></a>Chránění členové dat

|Název|Popis|
|----------|-----------------|
|[CInternetFile:: m_hFile](#m_hfile)|Popisovač souboru.|

## <a name="remarks"></a>Poznámky

Poskytuje základní třídu pro třídy souborů [CHttpFile](../../mfc/reference/chttpfile-class.md) a [CGopherFile –](../../mfc/reference/cgopherfile-class.md) . Nikdy nevytvoříte objekt `CInternetFile` přímo. Místo toho vytvořte objekt jedné z jeho odvozených tříd voláním [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) nebo [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Můžete také vytvořit objekt `CInternetFile` voláním [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

Pro `Duplicate` nejsou implementované členské funkce `CInternetFile` `Open`, `LockRange`, `UnlockRange`a `CInternetFile`. Pokud tyto funkce zavoláte na objekt `CInternetFile`, dostanete se [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).

Další informace o tom, jak `CInternetFile` pracuje s dalšími internetovými třídami knihovny MFC, najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFile –](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

##  <a name="abort"></a>CInternetFile:: Abort

Zavře soubor přidružený k tomuto objektu a nastaví soubor jako nedostupný pro čtení nebo zápis.

```
virtual void Abort();
```

### <a name="remarks"></a>Poznámky

Pokud jste soubor nezavřeli před zničením objektu, destruktor ho uzavře za vás.

Při zpracování výjimek se `Abort` liší od [zavření](#close) dvěma důležitými způsoby. Nejprve funkce `Abort` nevyvolává výjimku při selhání, protože ignoruje chyby. Druhý `Abort` **neuplatňuje** , pokud soubor nebyl otevřen nebo byl dříve uzavřen.

##  <a name="cinternetfile"></a>CInternetFile::CInternetFile

Tato členská funkce se volá, když se vytvoří objekt `CInternetFile`.

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

*hFile*<br/>
Popisovač internetového souboru.

*pstrFileName*<br/>
Ukazatel na řetězec obsahující název souboru.

*pConnection*<br/>
Ukazatel na objekt [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) .

*bReadMode*<br/>
Určuje, zda je soubor určen jen pro čtení.

*hSession*<br/>
Popisovač internetové relace.

*pstrServer*<br/>
Ukazatel na řetězec, který obsahuje název serveru.

*dwContext*<br/>
Identifikátor kontextu pro objekt `CInternetFile`. Další informace o identifikátoru kontextu najdete v tématu [Základy WinInet](../../mfc/wininet-basics.md) .

### <a name="remarks"></a>Poznámky

Nikdy nevytvoříte objekt `CInternetFile` přímo. Místo toho vytvořte objekt jedné z jeho odvozených tříd voláním [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) nebo [CHttpConnection:: OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Můžete také vytvořit objekt `CInternetFile` voláním [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).

##  <a name="close"></a>CInternetFile:: Close

Zavře `CInternetFile` a uvolní všechny jeho prostředky.

```
virtual void Close();
```

### <a name="remarks"></a>Poznámky

Pokud byl soubor otevřen pro zápis, existuje implicitní volání metody [flush](#flush) , které zajistí, že všechna data uložená do vyrovnávací paměti budou zapsána do hostitele. Po dokončení používání souboru byste měli volat `Close`.

##  <a name="flush"></a>CInternetFile:: flush

Chcete-li vyprázdnit obsah vyrovnávací paměti pro zápis, zavolejte tuto členskou funkci.

```
virtual void Flush();
```

### <a name="remarks"></a>Poznámky

Pomocí `Flush` zajistěte, aby byla veškerá data v paměti skutečně zapsána do cílového počítače a aby se zajistila vaše transakce v hostitelském počítači. `Flush` platí pouze pro objekty `CInternetFile` otevřené pro zápis.

##  <a name="getlength"></a>CInternetFile:: GetLength

Vrátí velikost souboru.

```
virtual ULONGLONG GetLength() const;
```

##  <a name="m_hfile"></a>CInternetFile:: m_hFile

Popisovač souboru přidruženého k tomuto objektu.

```
HINTERNET m_hFile;
```

##  <a name="operator_hinternet"></a>CInternetFile:: operator HINTERNET

Tento operátor použijte k získání popisovače Windows pro aktuální internetovou relaci.

```
operator HINTERNET() const;
```

##  <a name="read"></a>CInternetFile:: Read

Volejte tuto členskou funkci pro čtení do dané paměti, počínaje od *lpvBuf*, zadaného počtu bajtů, *nCount*.

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>Parametry

*lpBuf*<br/>
Ukazatel na adresu paměti, na kterou jsou čtena data souborů.

*nCount*<br/>
Počet bajtů, které mají být zapsány.

### <a name="return-value"></a>Návratová hodnota

Počet bajtů přenesených do vyrovnávací paměti. Návratová hodnota může být menší než *nCount* , pokud bylo dosaženo konce souboru.

### <a name="remarks"></a>Poznámky

Funkce vrátí počet aktuálně přečtených bajtů – číslo, které může být menší než *nCount* , pokud soubor skončí. Pokud při čtení souboru dojde k chybě, funkce vyvolá objekt [CInternetException](../../mfc/reference/cinternetexception-class.md) , který popisuje chybu. Všimněte si, že čtení za koncem souboru není považováno za chybu a nebude vyvolána žádná výjimka.

Aby bylo zajištěno, že budou načtena všechna data, musí aplikace nadále volat metodu `CInternetFile::Read`, dokud metoda nevrátí hodnotu nula.

##  <a name="readstring"></a>CInternetFile::ReadString

Zavolejte tuto členskou funkci pro čtení datového proudu znaků, dokud nenajde znak nového řádku.

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Ukazatel na řetězec, který získá čtený řádek.

*Nmaximum*<br/>
Maximální počet znaků, které mají být čteny.

*rString*<br/>
Odkaz na objekt [CString](../../atl-mfc-shared/reference/cstringt-class.md) , který obdrží načtený řádek.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vyrovnávací paměť obsahující prostá data načtená z objektu [CInternetFile](../../mfc/reference/cinternetfile-class.md) . Bez ohledu na datový typ vyrovnávací paměti předané touto metodou neprovede žádná manipulace s daty (například převod na kódování Unicode), takže je nutné namapovat vrácená data do struktury, kterou očekáváte, jako kdyby byl vrácen typ **void** <strong>\*</strong> .

Hodnota NULL, pokud bylo dosaženo konce souboru bez čtení dat; nebo, pokud logická hodnota, FALSE, pokud bylo dosaženo konce souboru, bez čtení jakýchkoli dat.

### <a name="remarks"></a>Poznámky

Funkce umístí výsledný řádek do paměti, na kterou odkazuje parametr *PSTR* . Zastaví čtení znaků, když dosáhne maximálního počtu znaků zadaného parametrem *nmaximum*. Vyrovnávací paměť vždy obdrží ukončující znak null.

Pokud zavoláte `ReadString` bez prvního volání [SetReadBufferSize](#setreadbuffersize), dostanete vyrovnávací paměť 4096 bajtů.

##  <a name="seek"></a>CInternetFile:: Seek

Chcete-li změnit umístění ukazatele v dříve otevřeném souboru, zavolejte tuto členskou funkci.

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>Parametry

*lOffset*<br/>
Posun v bajtech, aby se v souboru přesunul ukazatel pro čtení a zápis.

*Nze*<br/>
Relativní odkaz pro posun. Toto musí být jedna z následujících hodnot:

- `CFile::begin` přesunete ukazatel souboru *lOff* bajty vpřed od začátku souboru.

- `CFile::current` přesunete ukazatel souboru *lOff* bajtů z aktuální pozice v souboru.

- `CFile::end` přesune ukazatel na soubor *lOff* bajtů z konce souboru. *lOff* musí být pro hledání v existujícím souboru negativní. kladné hodnoty budou hledat za koncem souboru.

### <a name="return-value"></a>Návratová hodnota

Nový posun bajtů od začátku souboru, pokud je požadovaná pozice platná; v opačném případě není hodnota definována a je vyvolána výjimka objektu [CInternetException](../../mfc/reference/cinternetexception-class.md) .

### <a name="remarks"></a>Poznámky

Funkce `Seek` umožňuje náhodný přístup k obsahu souboru přesunutím ukazatele na zadanou hodnotu, která je absolutní nebo relativně. Během hledání nejsou ve skutečnosti čtena žádná data.

V tuto chvíli se volání této členské funkce podporuje jenom pro data přidružená k objektům `CHttpFile`. Nepodporuje se u požadavků FTP a Gopher. Pokud zavoláte `Seek` pro jednu z těchto nepodporovaných služeb, vrátí vás zpět do kódu chyby Win32 ERROR_INTERNET_INVALID_OPERATION.

Po otevření souboru je ukazatel souboru na posunu 0, začátek souboru.

> [!NOTE]
>  Použití `Seek` může způsobit [vyprázdnit](#flush)implicitní volání.

### <a name="example"></a>Příklad

  Podívejte se na příklad implementace základní třídy ( [CFile –:: Seek](../../mfc/reference/cfile-class.md#seek)).

##  <a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize

Zavolejte tuto členskou funkci pro nastavení velikosti dočasné vyrovnávací paměti pro čtení, kterou používá objekt odvozený `CInternetFile`.

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>Parametry

*nReadSize*<br/>
Požadovaná velikost vyrovnávací paměti v bajtech.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

Základní rozhraní WinInet API neprovádí ukládání do vyrovnávací paměti, takže vyberte velikost vyrovnávací paměti, která umožňuje vaší aplikaci efektivně číst data bez ohledu na množství dat, která se mají přečíst. Pokud každé volání [čtení](#read) obvykle zahrnuje velké aount dat (například čtyři nebo více kilobajtů), neměli byste vyrovnávací paměť potřebovat. Pokud však zavoláte `Read` pro získání malých objemů dat nebo pokud používáte [ReadString](#readstring) ke čtení jednotlivých řádků najednou, vyrovnávací paměť čtení zvyšuje výkon aplikace.

Ve výchozím nastavení objekt `CInternetFile` neposkytuje žádné ukládání do vyrovnávací paměti pro čtení. Pokud voláte tuto členskou funkci, musíte zajistit, aby byl soubor otevřen pro přístup pro čtení.

Velikost vyrovnávací paměti můžete zvětšit kdykoli, ale zmenšení vyrovnávací paměti nebude mít žádný vliv. Pokud zavoláte [ReadString](#readstring) bez prvního volání `SetReadBufferSize`, dostanete vyrovnávací paměť 4096 bajtů.

##  <a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize

Zavolejte tuto členskou funkci pro nastavení velikosti dočasné vyrovnávací paměti pro zápis, kterou používá objekt odvozený `CInternetFile`.

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>Parametry

*nWriteSize*<br/>
Velikost vyrovnávací paměti v bajtech.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0. Pokud se volání nezdařilo, může být volána funkce Win32 Function [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) , aby bylo možné zjistit příčinu chyby.

### <a name="remarks"></a>Poznámky

Základní rozhraní WinInet API neprovádí ukládání do vyrovnávací paměti, takže vyberte velikost vyrovnávací paměti, která umožňuje vaší aplikaci efektivně zapisovat data bez ohledu na množství dat, která mají být zapsána. Pokud každé volání [zápisu](#write) obvykle zahrnuje velké množství dat (například čtyři nebo více kilobajtů najednou), neměli byste potřebovat vyrovnávací paměť. Nicméně pokud zavoláte metodu [Write](#write) pro zápis malých bloků dat, vyrovnávací paměť pro zápis vylepšuje výkon vaší aplikace.

Ve výchozím nastavení objekt `CInternetFile` neposkytuje žádné ukládání do vyrovnávací paměti pro zápis. Pokud voláte tuto členskou funkci, je nutné zajistit, aby byl soubor otevřen pro zápis. Velikost vyrovnávací paměti pro zápis můžete kdykoli změnit, ale to způsobí, že se implicitní volání [vyprázdní](#flush).

##  <a name="write"></a>CInternetFile:: Write

Zavolejte tuto členskou funkci pro zápis do dané paměti, *lpvBuf*, zadaného počtu bajtů, *nCount*.

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

Pokud při zápisu dat dojde k nějaké chybě, funkce vyvolá objekt [CInternetException](../../mfc/reference/cinternetexception-class.md) popisující chybu.

##  <a name="writestring"></a>CInternetFile::WriteString

Tato funkce zapíše řetězec zakončený hodnotou null do přidruženého souboru.

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>Parametry

*pstr*<br/>
Ukazatel na řetězec obsahující obsah, který se má zapsat.

### <a name="remarks"></a>Poznámky

Pokud při zápisu dat dojde k nějaké chybě, funkce vyvolá objekt [CInternetException](../../mfc/reference/cinternetexception-class.md) popisující chybu.

## <a name="see-also"></a>Viz také

[CStdioFile – třída](../../mfc/reference/cstdiofile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)
