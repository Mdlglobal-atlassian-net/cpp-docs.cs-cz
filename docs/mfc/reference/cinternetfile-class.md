---
title: "Třída CInternetFile | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1e4b05e2aceb8fb4c8a4abed0dd6038fff6cfee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cinternetfile-class"></a>CInternetFile – třída
Umožňuje přístup k souborům na vzdálené systémy, které používají internetové protokoly.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CInternetFile : public CStdioFile  
```  
  
## <a name="members"></a>Členové  
  
### <a name="protected-constructors"></a>Chráněné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInternetFile::CInternetFile](#cinternetfile)|Vytvoří `CInternetFile` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CInternetFile::Abort](#abort)|Zavře soubor, bez ohledu na všechna upozornění a chyby.|  
|[CInternetFile::Close](#close)|Zavře `CInternetFile` a uvolní jeho prostředky.|  
|[CInternetFile::Flush](#flush)|Vyprázdnění obsahu vyrovnávací paměť pro zápis a zajišťuje, že data v paměti se zapisují do cílového počítače.|  
|[CInternetFile::GetLength](#getlength)|Vrátí velikost souboru.|  
|[CInternetFile::Read](#read)|Přečte počet zadaný bajtů.|  
|[CInternetFile::ReadString](#readstring)|Přečte znaků.|  
|[CInternetFile::Seek](#seek)|Přemístí ukazatele v otevření souboru.|  
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Nastaví velikost vyrovnávací paměti, kde bude číst data.|  
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Nastaví velikost vyrovnávací paměti, kde budou data zapsána.|  
|[CInternetFile::Write](#write)|Zapíše počet zadaný bajtů.|  
|[CInternetFile::WriteString](#writestring)|Řetězce ukončené hodnotou null se zapíše do souboru.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInternetFile::operator HINTERNET](#operator_hinternet)|Operátor přetypování internetového popisovače.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CInternetFile::m_hFile](#m_hfile)|Obslužná rutina do souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Poskytuje základní třídu pro [CHttpFile](../../mfc/reference/chttpfile-class.md) a [CGopherFile](../../mfc/reference/cgopherfile-class.md) třídy souborů. Nikdy vytvoříte `CInternetFile` objektu přímo. Místo toho vytvořte objekt jednoho z jeho odvozené třídy voláním [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) nebo [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Také můžete vytvořit `CInternetFile` objekt voláním [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
 `CInternetFile` Členské funkce **otevřete**, `LockRange`, `UnlockRange`, a `Duplicate` nejsou implementované pro `CInternetFile`. Když zavoláte na tyto funkce `CInternetFile` objektů, zobrazí se [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Další informace o tom, `CInternetFile` funguje s ostatní třídy MFC Internetu najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="abort"></a>CInternetFile::Abort  
 Zavře soubor přidružené k tomuto objektu a soubor, nebude možné čtení nebo zápis.  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud jste ještě zavřeli soubor před zničení objektu, destruktoru se automaticky zavře.  
  
 Při zpracování výjimek, **Abort** se liší od [Zavřít](#close) důležité dvěma způsoby. Nejdřív **Abort** funkce nevyvolá výjimku o selhání, protože ignoruje selhání. Druhý, **Abort** nemá **ASSERT** Pokud je soubor nebyl otevřen nebo dříve bylo ukončeno.  
  
##  <a name="cinternetfile"></a>CInternetFile::CInternetFile  
 Tento člen funkce je volána, když `CInternetFile` je vytvořen objekt.  
  
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
 `hFile`  
 Popisovač pro soubor Internetu.  
  
 `pstrFileName`  
 Ukazatel na řetězec, který obsahuje název souboru.  
  
 `pConnection`  
 Ukazatel [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) objektu.  
  
 *bReadMode*  
 Určuje, zda soubor je jen pro čtení.  
  
 `hSession`  
 Popisovač pro relaci Internet.  
  
 `pstrServer`  
 Ukazatel na řetězec, který obsahuje název serveru.  
  
 `dwContext`  
 Identifikátor kontext pro `CInternetFile` objektu. V tématu [WinInet – Základy](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
### <a name="remarks"></a>Poznámky  
 Nikdy vytvoříte `CInternetFile` objektu přímo. Místo toho vytvořte objekt jednoho z jeho odvozené třídy voláním [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) nebo [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Také můžete vytvořit `CInternetFile` objekt voláním [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
##  <a name="close"></a>CInternetFile::Close  
 Zavře `CInternetFile` a uvolní všechny jeho prostředky.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud soubor byla otevřena pro zápis, je implicitní volání [vyprázdnění](#flush) , aby zajistil, že všechny do vyrovnávací paměti data se zapisují do hostitele. By měly volat **Zavřít** po dokončení pomocí souboru.  
  
##  <a name="flush"></a>CInternetFile::Flush  
 Volání této funkce člen vyprázdnění obsah vyrovnávací paměť pro zápis.  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>Poznámky  
 Použití `Flush` , aby zajistil, že všechna data v paměti ve skutečnosti byla zapsána na cílovém počítači a chcete-li zajistit vaší transakce s hostitelský počítač byla dokončena. `Flush`platí pouze na `CInternetFile` objekty otevřena pro zápis.  
  
##  <a name="getlength"></a>CInternetFile::GetLength  
 Vrátí velikost souboru.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
##  <a name="m_hfile"></a>CInternetFile::m_hFile  
 Popisovač pro soubor přidružené k tomuto objektu.  
  
```  
HINTERNET m_hFile;  
```  
  
##  <a name="operator_hinternet"></a>CInternetFile::operator HINTERNET  
 Tento operátor. použijte k získání popisovačů systému Windows pro aktuální relaci Internet.  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="read"></a>CInternetFile::Read  
 Volání této funkce člen k načtení do dané paměti, počínaje `lpvBuf`, zadaný počet bajtů, `nCount`.  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Ukazatel na adresu paměti pro soubor, který je číst data.  
  
 `nCount`  
 Počet bajtů, které mají být zapsána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů přenesených do vyrovnávací paměti. Vrácená hodnota může být menší než `nCount` Pokud bylo dosaženo konce souboru.  
  
### <a name="remarks"></a>Poznámky  
 Funkce vrátí počet bajtů přečtených ve skutečnosti – číslo, které může být menší než `nCount` Pokud skončí soubor. Pokud dojde k chybě při čtení souboru, funkce vyvolá [CInternetException](../../mfc/reference/cinternetexception-class.md) objektu, která popisuje danou chybu. Všimněte si, že čtení za koncem souboru není považují za chybu a bude vyvolána žádná výjimka.  
  
 Aby se načítají všechna data, musí aplikace nadále volání **CInternetFile::Read** metoda dokud vrátí tato metoda hodnotu nula.  
  
##  <a name="readstring"></a>CInternetFile::ReadString  
 Volání této funkce členů ke čtení znaků, dokud nenajde znak nového řádku.  
  
```  
virtual BOOL ReadString(CString& rString);

 
virtual LPTSTR ReadString(
    LPTSTR pstr,  
    UINT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 `pstr`  
 Ukazatel na řetězec, který se zobrazí na řádku, který je čten.  
  
 `nMax`  
 Maximální počet znaků ke čtení.  
  
 `rString`  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který přijme čtení řádku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na obsahující nešifrovaná data načtená z vyrovnávací paměti [CInternetFile](../../mfc/reference/cinternetfile-class.md) objektu. Bez ohledu na datový typ vyrovnávací paměti předaná této metodě, neprovede žádné manipulace na data (například u převodu na kódování Unicode), takže vrácená data je nutné mapovat do struktury očekáváte, jako kdyby **void\***  typu byly vráceny.  
  
 **NULL** Pokud end souboru bylo dosaženo bez přečtení všech dat, nebo pokud je to logická hodnota, **FALSE** Pokud end souboru bylo dosaženo bez přečtení žádná data.  
  
### <a name="remarks"></a>Poznámky  
 Funkce umístí výsledný řádek do paměti odkazuje `pstr` parametr. Zastaví načítání znaků až dorazí do maximální počet znaků, určeného `nMax`. Vyrovnávací paměť vždy obdrží ukončující znak hodnoty null.  
  
 Když zavoláte `ReadString` bez první volání [SetReadBufferSize](#setreadbuffersize), zobrazí se vyrovnávací paměť 4096 bajtů.  
  
##  <a name="seek"></a>CInternetFile::Seek  
 Volání této funkce člen, aby přemístil ukazatel v dříve otevřený soubor.  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOffset,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>Parametry  
 `lOffset`  
 Posun v bajtech přesunout ukazatel pro čtení a zápis v souboru.  
  
 `nFrom`  
 Relativní odkaz posunu. Musí být jedna z následujících hodnot:  
  
- **CFile::begin** přesunout ukazatel souboru `lOff` bajtů předávání od začátku souboru.  
  
- **CFile::current** přesunout ukazatel souboru `lOff` bajtů z aktuální pozice v souboru.  
  
- **CFile::end** přesunout ukazatel souboru `lOff` bajtů od konce souboru. `lOff`musí být záporné k vyhledání do existující soubor; kladné hodnoty bude hledat za koncem souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Posun od začátku souboru, pokud je požadovaný pozice právní; bajtů, nové jinak hodnota je definovaný a [CInternetException](../../mfc/reference/cinternetexception-class.md) objektu je vyvolána výjimka.  
  
### <a name="remarks"></a>Poznámky  
 `Seek` Funkce umožňuje náhodný přístup k obsahu souboru přesunutím ukazatele po zadanou dobu absolutně nebo relativně. Během hledání ve skutečnosti nenačtou žádná data.  
  
 V tomto okamžiku volání této funkce člen je podporován pouze pro data související s `CHttpFile` objekty. Není podporováno pro protokol FTP nebo gopher požadavky. Když zavoláte `Seek` pro jednu z těchto nepodporované služeb se předá zpět je kód chyby Win32 **ERROR_INTERNET_INVALID_OPERATION**.  
  
 Po otevření souboru ukazatele souboru je na posunu 0, na začátek souboru.  
  
> [!NOTE]
>  Pomocí `Seek` může způsobit, že implicitní volání [vyprázdnění](#flush).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro implementaci třídy base ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).  
  
##  <a name="setreadbuffersize"></a>CInternetFile::SetReadBufferSize  
 Volání této funkce člen nastavit velikost dočasné čtení vyrovnávací paměti používané `CInternetFile`-odvozené objektu.  
  
```  
BOOL SetReadBufferSize(UINT nReadSize);
```  
  
### <a name="parameters"></a>Parametry  
 *nReadSize*  
 Vyrovnávací paměť požadovanou velikost v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 Základní rozhraní API WinInet není provést ukládání do vyrovnávací paměti, takže zvolte velikost vyrovnávací paměti, který umožňuje aplikaci číst data efektivně, bez ohledu na množství dat ke čtení. Pokud každé volání do [čtení](#read) obvykle zahrnuje velké aount dat (například minimálně 4 kB), neměli byste potřebovat vyrovnávací paměti. Ale při volání **čtení** získat malé bloky dat, nebo pokud používáte [ReadString](#readstring) číst jednotlivé řádky současně, pak vyrovnávací paměti pro čtení vylepšuje výkon aplikace.  
  
 Ve výchozím nastavení `CInternetFile` objekt neposkytuje žádné ukládání do vyrovnávací paměti pro čtení. Když zavoláte tuto – členská funkce, musí být jisti, že byla otevřena soubor přístup pro čtení.  
  
 Velikost vyrovnávací paměti můžete zvýšit kdykoli, ale zmenšit velikost vyrovnávací paměti nebude mít žádný vliv. Když zavoláte [ReadString](#readstring) bez první volání `SetReadBufferSize`, zobrazí se vyrovnávací paměť 4096 bajtů.  
  
##  <a name="setwritebuffersize"></a>CInternetFile::SetWriteBufferSize  
 Volání této funkce člen nastavit velikost vyrovnávací paměti pro dočasné zápis používané `CInternetFile`-odvozené objektu.  
  
```  
BOOL SetWriteBufferSize(UINT nWriteSize);
```  
  
### <a name="parameters"></a>Parametry  
 *nWriteSize*  
 Velikost vyrovnávací paměti v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0. Pokud volání selže, funkce Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu této chyby.  
  
### <a name="remarks"></a>Poznámky  
 Základní rozhraní API WinInet neprovádí se ukládání do vyrovnávací paměti, takže zvolte velikost vyrovnávací paměti, která umožňuje aplikacím při zápisu dat efektivně bez ohledu na množství dat, která má být proveden zápis. Pokud každé volání do [zápisu](#write) obvykle zahrnuje velké množství dat (například čtyři nebo více kilobajtů najednou), neměli byste potřebovat vyrovnávací paměti. Ale když zavoláte [zápisu](#write) zápis malé bloky dat, vyrovnávací paměť pro zápis vylepšuje výkon vaší aplikace.  
  
 Ve výchozím nastavení `CInternetFile` objekt neposkytuje žádné ukládání do vyrovnávací paměti pro zápis. Když zavoláte tuto – členská funkce, musí být jisti, že soubor byla otevřena pro zápis. Velikost vyrovnávací paměti pro zápis můžete změnit kdykoli, ale to způsobí tak, že implicitní volání [vyprázdnění](#flush).  
  
##  <a name="write"></a>CInternetFile::Write  
 Volání této funkce členů k zápisu do daného paměti `lpvBuf`, zadaný počet bajtů, `nCount`.  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Ukazatel na prvním bajtem k zapsání.  
  
 `nCount`  
 Určuje počet bajtů, které mají být zapsána.  
  
### <a name="remarks"></a>Poznámky  
 Pokud dojde k chybě při zápisu dat, funkce vyvolá [CInternetException](../../mfc/reference/cinternetexception-class.md) objekt popisující chybu.  
  
##  <a name="writestring"></a>CInternetFile::WriteString  
 Tato funkce zapíše související soubor řetězce ukončené hodnotou null.  
  
```  
virtual void WriteString(LPCTSTR pstr);
```  
  
### <a name="parameters"></a>Parametry  
 `pstr`  
 Ukazatel na řetězec obsahující obsah má být proveden zápis.  
  
### <a name="remarks"></a>Poznámky  
 Pokud dojde k chybě při zápisu dat, funkce vyvolá [CInternetException](../../mfc/reference/cinternetexception-class.md) objekt popisující chybu.  
  
## <a name="see-also"></a>Viz také  
 [CStdioFile – třída](../../mfc/reference/cstdiofile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)
