---
title: Cinternetfile – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e16aa9377676e415f416dc4f7dae9cb9f2a40dab
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336563"
---
# <a name="cinternetfile-class"></a>Cinternetfile – třída
Umožňuje přístup k souborům ve vzdálených systémech, které používají protokoly sítě Internet.  
  
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
|[CInternetFile::Abort](#abort)|Zavře soubor, ignoruje se všechna upozornění a chyby.|  
|[CInternetFile::Close](#close)|Zavře `CInternetFile` a uvolní její prostředky.|  
|[CInternetFile::Flush](#flush)|Vyprázdní obsah vyrovnávací paměti pro zápis a je zajištěno, že data v paměti je zapsána do cílového počítače.|  
|[CInternetFile::GetLength](#getlength)|Vrátí velikost souboru.|  
|[CInternetFile::Read](#read)|Načte počet zadaných bajtů.|  
|[CInternetFile::ReadString](#readstring)|Načte posloupnost znaků.|  
|[CInternetFile::Seek](#seek)|Přemístí ukazatel v otevření souboru.|  
|[CInternetFile::SetReadBufferSize](#setreadbuffersize)|Nastaví velikost vyrovnávací paměti, které se budou číst data.|  
|[CInternetFile::SetWriteBufferSize](#setwritebuffersize)|Nastaví velikost vyrovnávací paměti, kde se budou zapisovat data.|  
|[CInternetFile::Write](#write)|Zapíše počet zadaných bajtů.|  
|[CInternetFile::WriteString](#writestring)|Zapíše řetězec zakončený hodnotou null do souboru.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInternetFile::operator HINTERNET](#operator_hinternet)|Operátor přetypování pro internetového popisovače.|  
  
### <a name="protected-data-members"></a>Chránění členové dat  
  
|Název|Popis|  
|----------|-----------------|  
|[CInternetFile::m_hFile](#m_hfile)|Popisovač souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Poskytuje základní třídu pro [chttpfile –](../../mfc/reference/chttpfile-class.md) a [cgopherfile –](../../mfc/reference/cgopherfile-class.md) třídy souborů. Nikdy nevytvářejte `CInternetFile` objektu přímo. Místo toho vytvořte objekt jednoho z jeho odvozených tříd voláním [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) nebo [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Můžete také vytvořit `CInternetFile` objektu voláním [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
 `CInternetFile` Členské funkce `Open`, `LockRange`, `UnlockRange`, a `Duplicate` nejsou implementovány pro `CInternetFile`. Při volání těchto funkcí na `CInternetFile` objektu, zobrazí se [cnotsupportedexception –](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Další informace o tom, `CInternetFile` funguje s jinými třídami MFC Internetu najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 [Cstdiofile –](../../mfc/reference/cstdiofile-class.md)  
  
 `CInternetFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="abort"></a>  CInternetFile::Abort  
 Soubor přidružený k tomuto objektu se zavře a znepřístupní soubor pro čtení nebo zápis.  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud soubor ještě zavřen před zničení objektu, destruktor zavře za vás.  
  
 Při zpracování výjimek, `Abort` se liší od [Zavřít](#close) dvěma důležitými způsoby. Nejprve je potřeba `Abort` funkce nevyvolá výjimky na chyby, protože ignoruje chyby. Druhý, `Abort` nemá **ASSERT** Pokud soubor nebyl otevřen nebo bylo již ukončeno.  
  
##  <a name="cinternetfile"></a>  CInternetFile::CInternetFile  
 Tato členská funkce je volána, když `CInternetFile` je vytvořen objekt.  
  
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
 *hfile –*  
 Popisovač souboru k Internetu.  
  
 *pstrFileName*  
 Ukazatel na řetězec obsahující název souboru.  
  
 *pConnection*  
 Ukazatel [cinternetconnection –](../../mfc/reference/cinternetconnection-class.md) objektu.  
  
 *bReadMode*  
 Označuje, zda je soubor jen pro čtení.  
  
 *hSession*  
 Popisovač pro relaci Internet.  
  
 *pstrServer*  
 Ukazatel na řetězec obsahující název serveru.  
  
 *dwContext*  
 Identifikátor kontextu `CInternetFile` objektu. Zobrazit [Wininet – Základy](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.  
  
### <a name="remarks"></a>Poznámky  
 Nikdy nevytvářejte `CInternetFile` objektu přímo. Místo toho vytvořte objekt jednoho z jeho odvozených tříd voláním [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) nebo [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest). Můžete také vytvořit `CInternetFile` objektu voláním [CFtpConnection::OpenFile](../../mfc/reference/cftpconnection-class.md#openfile).  
  
##  <a name="close"></a>  CInternetFile::Close  
 Zavře `CInternetFile` a uvolní všechny její prostředky.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud soubor byl otevřen pro zápis, je implicitním voláním [vyprázdnění](#flush) , aby zajistil, že všechny ukládány do vyrovnávací paměti data jsou zapsána do hostitele. Měli byste zavolat `Close` až budete hotovi, pomocí souboru.  
  
##  <a name="flush"></a>  CInternetFile::Flush  
 Voláním této členské funkce Vyprázdnit obsah vyrovnávací paměti pro zápis.  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>Poznámky  
 Použití `Flush` , aby zajistil, že všechna data v paměti ve skutečnosti byl zapsán do cílového počítače a proto, aby zajistil vaše transakce se hostitelský počítač byla dokončena. `Flush` nabídka platí jenom v `CInternetFile` objekty otevřena pro zápis.  
  
##  <a name="getlength"></a>  CInternetFile::GetLength  
 Vrátí velikost souboru.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
##  <a name="m_hfile"></a>  CInternetFile::m_hFile  
 Popisovač souboru spojené s tímto objektem.  
  
```  
HINTERNET m_hFile;  
```  
  
##  <a name="operator_hinternet"></a>  CInternetFile::operator HINTERNET  
 Tento operátor se získat popisovač Windows pro aktuální relaci Internet.  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="read"></a>  CInternetFile::Read  
 Voláním této členské funkce pro načtení do daného paměti, počínaje *lpvBuf*, zadaný počet bajtů, *nCount*.  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuf*  
 Ukazatel na adresu paměti na soubor, který je číst data.  
  
 *nCount*  
 Počet bajtů, které mají být zapsána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů přenesených do vyrovnávací paměti. Návratová hodnota může být kratší než *nCount* Pokud bylo dosaženo konce souboru.  
  
### <a name="remarks"></a>Poznámky  
 Funkce vrátí počet bajtů ve skutečnosti čtení – číslo, které mohou být menší než *nCount* Pokud skončí souboru. Pokud dojde k chybě při čtení souboru, funkce vyvolá [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objekt popisující chybu. Všimněte si, že čtení za koncem souboru není považováno za chybu a bude vyvolána žádná výjimka.  
  
 Aby se všechna data načítají, musí aplikace nadále volají `CInternetFile::Read` metodu, dokud se metoda vrátí hodnotu 0.  
  
##  <a name="readstring"></a>  CInternetFile::ReadString  
 Zavolejte tuto členskou funkci na čtení datového proudu znaků, dokud nenajde znak nového řádku.  
  
```  
virtual BOOL ReadString(CString& rString);

 
virtual LPTSTR ReadString(
    LPTSTR pstr,  
    UINT nMax);
```  
  
### <a name="parameters"></a>Parametry  
 *pstr*  
 Ukazatel na řetězec, který se zobrazí na řádku, který je čten.  
  
 *Nmaximum*  
 Maximální počet znaků pro čtení.  
  
 *rString*  
 Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) objekt, který přijme čtení řádku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel do vyrovnávací paměti obsahující prostý dat načtených z [cinternetfile –](../../mfc/reference/cinternetfile-class.md) objektu. Bez ohledu na datový typ vyrovnávací paměť předaná této metodě neprovádí žádné manipulace s daty (například převod na kódování Unicode), takže vrácená data musí být namapovaný na strukturu, který jste očekávali, jako kdyby **void\***  typ byly vráceny.  
  
 Hodnota NULL, pokud bylo dosaženo souboru bez přečtení všech dat; nebo, pokud je logická, FALSE, pokud ukončení souboru bylo dosaženo bez přečtení žádná data.  
  
### <a name="remarks"></a>Poznámky  
 Funkce umístí výsledný řádek do paměť odkazovanou *pstr* parametru. Zastaví čtení znaků při dosažení maximální počet znaků, určené *Nmaximum*. Vyrovnávací paměť vždy obdrží ukončujícího znaku null.  
  
 Při volání `ReadString` bez první volání [SetReadBufferSize](#setreadbuffersize), zobrazí se vyrovnávací paměť 4096 bajtů.  
  
##  <a name="seek"></a>  CInternetFile::Seek  
 Voláním této členské funkce, aby přemístil ukazatel v dříve otevřený soubor.  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOffset,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>Parametry  
 *lOffset*  
 Posun v bajtech přesunout ukazatel čtení/zápisu v souboru.  
  
 *Nze*  
 Relativní odkaz na posunu. Musí být jedna z následujících hodnot:  
  
- `CFile::begin` Přesuňte ukazatel na soubor *lOff* vpřed bajtů od začátku souboru.  
  
- `CFile::current` Přesuňte ukazatel na soubor *lOff* bajtů z aktuální pozice v souboru.  
  
- `CFile::end` Přesuňte ukazatel na soubor *lOff* bajtů z konce souboru. *lOff* musí být záporné vystavit do existujících souborů; kladné hodnoty pozice za koncem souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nové bajtů posun od začátku souboru, pokud je na požadovanou pozici platný; v opačném případě hodnota není definována a [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objektu je vyvolána výjimka.  
  
### <a name="remarks"></a>Poznámky  
 `Seek` Funkce umožňuje náhodný přístup k obsahu souboru přesunutím ukazatele zadanou velikost, relativně nebo vůbec. Během hledání ve skutečnosti nenačtou žádná data.  
  
 V tomto okamžiku volání tato členská funkce je podporována pouze pro data související s `CHttpFile` objekty. Není podporováno pro protokol FTP nebo gopher požadavky. Při volání `Seek` pro jednu z těchto nepodporovaných služeb se předá zpět můžete kód chyby Win32 ERROR_INTERNET_INVALID_OPERATION.  
  
 Když je soubor otevřen, je ukazatel na soubor na posunu 0, na začátek souboru.  
  
> [!NOTE]
>  Pomocí `Seek` může způsobit, že implicitním voláním [vyprázdnění](#flush).  
  
### <a name="example"></a>Příklad  
  Podívejte se na příklad pro implementaci základní třídy ( [CFile::Seek](../../mfc/reference/cfile-class.md#seek)).  
  
##  <a name="setreadbuffersize"></a>  CInternetFile::SetReadBufferSize  
 Voláním této členské funkce pro nastavení velikosti dočasné vyrovnávací paměti čtení používané `CInternetFile`-odvozenému objektu.  
  
```  
BOOL SetReadBufferSize(UINT nReadSize);
```  
  
### <a name="parameters"></a>Parametry  
 *nReadSize*  
 Velikost požadované vyrovnávací paměti v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.  
  
### <a name="remarks"></a>Poznámky  
 Základní rozhraní API rozhraní WinInet není provádět ukládání do vyrovnávací paměti, proto zvolte velikost vyrovnávací paměti, který umožňuje aplikaci číst data efektivně, bez ohledu na množství dat pro čtení. Pokud se každé volání [čtení](#read) obvykle zahrnuje velké aount dat (například čtyři nebo více kilobajtů), neměli byste potřebovat vyrovnávací paměti. Ale při volání `Read` získat menší bloky dat, nebo pokud používáte [ReadString](#readstring) číst jednotlivých řádků najednou, pak vyrovnávací paměti pro čtení vylepšuje výkon aplikace.  
  
 Ve výchozím nastavení `CInternetFile` objekt neposkytuje žádné ukládání do vyrovnávací paměti pro čtení. Pokud jste zavolat tuto členskou funkci, musíte být jisti, že soubor byl otevřen pro čtení.  
  
 Kdykoli můžete zvýšit velikost vyrovnávací paměti, ale zmenšení vyrovnávací paměti nebude mít žádný efekt. Při volání [ReadString](#readstring) bez první volání `SetReadBufferSize`, zobrazí se vyrovnávací paměť 4096 bajtů.  
  
##  <a name="setwritebuffersize"></a>  CInternetFile::SetWriteBufferSize  
 Voláním této členské funkce nastavit velikost vyrovnávací paměti pro zápis dočasné používané `CInternetFile`-odvozenému objektu.  
  
```  
BOOL SetWriteBufferSize(UINT nWriteSize);
```  
  
### <a name="parameters"></a>Parametry  
 *nWriteSize*  
 Velikost vyrovnávací paměti v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.  
  
### <a name="remarks"></a>Poznámky  
 Základní rozhraní API rozhraní WinInet neprovádí se ukládání do vyrovnávací paměti, takže zvolte velikost vyrovnávací paměti, která umožňuje vaší aplikaci k zápisu dat efektivně bez ohledu na množství dat, která má být proveden zápis. Pokud se každé volání [zápisu](#write) obvykle zahrnuje velké množství dat (například čtyři nebo více kilobajtů najednou), neměli byste potřebovat vyrovnávací paměti. Ale při volání [zápisu](#write) pro zápis menší bloky dat, vyrovnávací paměti pro zápis zlepšuje výkon vaší aplikace.  
  
 Ve výchozím nastavení `CInternetFile` objekt neposkytuje žádné ukládání do vyrovnávací paměti pro zápis. Pokud jste zavolat tuto členskou funkci, musíte být jisti, že soubor byl otevřen pro zápis. Kdykoli můžete změnit velikost vyrovnávací paměti pro zápis, ale to způsobilo, že implicitním voláním [vyprázdnění](#flush).  
  
##  <a name="write"></a>  CInternetFile::Write  
 Voláním této členské funkce k zápisu do daného paměti *lpvBuf*, zadaný počet bajtů, *nCount*.  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuf*  
 Ukazatel na první bajt má být proveden zápis.  
  
 *nCount*  
 Určuje počet bajtů, které mají být zapsána.  
  
### <a name="remarks"></a>Poznámky  
 Pokud dojde k chybě při zápisu dat, funkce vyvolá [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objekt popisující chybu.  
  
##  <a name="writestring"></a>  CInternetFile::WriteString  
 Tato funkce zapíše do přidruženého souboru řetězec zakončený hodnotou null.  
  
```  
virtual void WriteString(LPCTSTR pstr);
```  
  
### <a name="parameters"></a>Parametry  
 *pstr*  
 Ukazatel na řetězec obsahující obsah má být proveden zápis.  
  
### <a name="remarks"></a>Poznámky  
 Pokud dojde k chybě při zápisu dat, funkce vyvolá [cinternetexception –](../../mfc/reference/cinternetexception-class.md) objekt popisující chybu.  
  
## <a name="see-also"></a>Viz také  
 [Cstdiofile – třída](../../mfc/reference/cstdiofile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)
