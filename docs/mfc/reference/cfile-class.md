---
title: "Cfile – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1f7a2b0e1dd95b460d6b6007e79378bc69f1b4ce
ms.sourcegitcommit: 2aeb507a426fc7881ea59115b1d5139c0a30ba91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2018
---
# <a name="cfile-class"></a>Cfile – třída
Základní třída pro třídy Microsoft Foundation Class souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CFile : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFile::CFile](#cfile)|Vytvoří `CFile` objektu ze souboru nebo cesty popisovače.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CFile::Abort](#abort)|Zavře souboru ignoruje všechny chyby a varování.|  
|[CFile::Close](#close)|Soubor se zavře a odstraní objekt.|  
|[CFile::Duplicate](#duplicate)|Vytvoří objekt duplicitní podle tohoto souboru.|  
|[CFile::Flush](#flush)|Počet vyprázdnění žádná data ještě k zapsání.|  
|[CFile::GetFileName](#getfilename)|Načte název souboru vybraného souboru.|  
|[CFile::GetFilePath](#getfilepath)|Načte je úplná cesta vybraného souboru.|  
|[CFile::GetFileTitle](#getfiletitle)|Načte název vybraného souboru.|  
|[CFile::GetLength](#getlength)|Načte délku souboru.|  
|[CFile::GetPosition](#getposition)|Načte aktuální ukazatele souboru.|  
|[CFile::GetStatus](#getstatus)|Načte stav otevření souboru, nebo v statické verze, načte stav zadaný soubor (statické, virtuální funkce).|  
|[CFile::LockRange](#lockrange)|Zamkne rozsah bajtů v souboru.|  
|[CFile::Open](#open)|Bezpečně otevře soubor s možností testování chyby.|  
|[CFile::Read](#read)|Čtení ze souboru na aktuální pozici souboru (bez vyrovnávací paměti) data.|  
|[CFile::Remove](#remove)|Odstraní zadaný soubor (statické funkce).|  
|[CFile::Rename](#rename)|Přejmenuje zadaný soubor (statické funkce).|  
|[CFile::Seek](#seek)|Umisťuje aktuální ukazatele souboru.|  
|[CFile::SeekToBegin](#seektobegin)|Aktuální ukazatele souboru se umístí na začátku souboru.|  
|[CFile::SeekToEnd](#seektoend)|Umisťuje aktuální ukazatele souboru na konci souboru.|  
|[CFile::SetFilePath](#setfilepath)|Nastaví cestu k souboru úplné vybraného souboru.|  
|[CFile::SetLength](#setlength)|Změní délku souboru.|  
|[CFile::SetStatus](#setstatus)|Nastaví stav zadaného souboru (statické, virtuální funkce).|  
|[CFile::UnlockRange](#unlockrange)|Odemkne rozsah bajtů v souboru.|  
|[CFile::Write](#write)|Zápisy (bez vyrovnávací paměti) data do souboru na aktuální pozici souboru.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CFile::operator POPISOVAČ](#operator_handle)|Popisovač pro `CFile` objektu.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CFile::hFileNull](#hfilenull)|Určuje, zda `CFile` objekt má neplatný popisovač.|  
|[CFile::m_hFile](#m_hfile)|Obvykle obsahuje popisovač souboru operačního systému.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CFile::m_pTM](#m_ptm)|Ukazatel na `CAtlTransactionManager` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 Přímo poskytuje služby vstupu/výstupu disku bez vyrovnávací paměti, binární a nepřímo podporuje textové soubory a soubory paměti pomocí jejich odvozené třídy. `CFile`funguje ve spojení s `CArchive` třídy pro podporu serializace objektů Microsoft Foundation Class.  
  
 Hierarchický vztah mezi této třídy a jejich odvozené třídy umožňuje vaším programem fungovat pro všechny objekty souboru prostřednictvím polymorfní `CFile` rozhraní. Soubor paměti, například chová jako soubor na disku.  
  
 Použití `CFile` a odvozených tříd pro obecné účely disku vstupně-výstupní operace. Použití `ofstream` nebo jiných Microsoft iostream – třídy pro formátovaný text odeslaný do souboru na disku.  
  
 Za normálních okolností automaticky na Otevřít soubor na disku `CFile` vytváření a odstraňování uzavřené na. Statické členské funkce umožňují zjistěte stav souboru bez otevření souboru.  
  
 Další informace o používání `CFile`, najdete v článcích [soubory v prostředí MFC](../../mfc/files-in-mfc.md) a [zpracování souborů](../../c-runtime-library/file-handling.md) v *referenční dokumentace běhové knihovny*.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="abort"></a>CFile::Abort  
 Zavře soubor přidružené k tomuto objektu a soubor, nebude možné čtení nebo zápis.  
  
```  
virtual void Abort();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud jste ještě zavřeli soubor před zničení objektu, destruktoru se automaticky zavře.  
  
 Při zpracování výjimek, `CFile::Abort` se liší od `CFile::Close` důležité dvěma způsoby. Nejdřív **Abort** funkce nebude vyvolat výjimku o selhání, protože selhání ignorují podle **Abort**. Druhý, **Abort** nikoli **ASSERT** Pokud je soubor nebyl otevřen nebo dříve bylo ukončeno.  
  
 Pokud jste použili **nové** přidělit `CFile` objektu v haldě, pak je nutné odstranit po zavření souboru. **Abort –** nastaví `m_hFile` k `CFile::hFileNull`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]  
  
##  <a name="cfile"></a>CFile::CFile  
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
 `hFile`  
 Popisovač souboru pro připojení k `CFile` objektu.  
  
 `lpszFileName`  
 Úplná nebo relativní cestu k souboru pro připojení k `CFile` objektu.  
  
 `nOpenFlags`  
 Bitová kombinace (nebo) možnosti přístupu k souboru pro zadaný soubor. Dostupné možnosti v části poznámky.  
  
 `pTM`  
 Ukazatel na objekt CAtlTransactionManager  
  
### <a name="remarks"></a>Poznámky  
 Následujících pět tabulkách jsou uvedeny dostupné možnosti `nOpenFlags` parametr.  
  
 Zvolte pouze jeden z následujících možností režimu přístup k souboru. Výchozí režim přístupu k souboru je `CFile::modeRead`, která je jen pro čtení.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CFile::modeRead`|Žádosti o přístup jen pro čtení.|  
|`CFile::modeWrite`|Požadavky pouze k zápisu.|  
|`CFile::modeReadWrite`|Žádosti o čtení a zápis.|  
  
 Vyberte jednu z následujících možností režimu znak.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CFile::typeBinary`|Nastaví binárního režimu (používá se v odvozených třídách pouze).|  
|`CFile::typeText`|Nastaví režim textové s speciální zpracování pro dvojice znaků CR vrátit-konce řádku (používá se v odvozených třídách pouze).|  
|`CFile::typeUnicode`|Nastaví režim Unicode (používá se v odvozených třídách pouze). Pokud aplikace je součástí konfigurace kódování Unicode, je text psán do souboru ve formátu Unicode. Žádné BOM je zapsán do souboru.|  
  
 Zvolte pouze jeden z následujících možností režimu sdílené složky souborů. Je výchozí režim sdílené složky souboru `CFile::shareExclusive`, což je výhradní.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CFile::shareDenyNone`|Bez omezení sdílení.|  
|`CFile::shareDenyRead`|Odepře přístup pro čtení pro všechny ostatní.|  
|`CFile::shareDenyWrite`|Odepře přístup pro zápis pro všechny ostatní.|  
|`CFile::shareExclusive`|Odmítne oprávnění ke čtení a zápisu pro všechny ostatní.|  
  
 Zvolte první, nebo obě z následujících možností režimu vytvoření souboru. Je výchozí režim vytváření `CFile::modeNoTruncate`, což je otevřít existující.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CFile::modeCreate`|Vytvoří nový soubor, pokud neexistuje žádný soubor.; Pokud soubor již existuje, [CFileException](../../mfc/reference/cfileexception-class.md) je vyvolána.|  
|`CFile::modeNoTruncate`|Vytvoří nový soubor, pokud neexistuje žádný soubor; jinak, pokud soubor již existuje, je připojen k `CFile` objektu.|  
  
 Vyberte následující soubor, ukládání do mezipaměti možnosti, jak je popsáno. Ve výchozím nastavení používá systém obecné účely ukládání do mezipaměti schématu, která není k dispozici možnost.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CFile::osNoBuffer`|Systém nepoužívá zprostředkující mezipaměti pro soubor. Tato možnost zruší následující 2 možnosti.|  
|`CFile::osRandomAccess`|Mezipaměť souborů je optimalizovaná pro náhodný přístup. Nepoužívejte tuto možnost a možnost sekvenční kontroly.|  
|`CFile::osSequentialScan`|Mezipaměť souborů je optimalizovaná pro sekvenční přístup. Nepoužívejte tuto možnost a možnost náhodný přístup.|  
|`CFile::osWriteThrough`|Zapsat operací bez zpoždění.|  
  
 Vyberte následující možnost zabezpečení zabránit dědí popisovač souboru. Ve výchozím nastavení můžete použít všechny nové podřízené procesy popisovač souboru.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CFile::modeNoInherit`|Všechny podřízené procesy bránit v použití popisovač souboru.|  
  
 Výchozí konstruktor inicializuje členy ale nepřipojí soubor, který chcete `CFile` objektu. Po použití tohoto konstruktoru, použijte [CFile::Open](#open) metodu pro otevření souboru a připojte ji k `CFile` objektu.  
  
 Konstruktor s jeden parametr inicializuje členy a připojí k existující soubor `CFile` objektu.  
  
 Konstruktor s dva parametry inicializuje členy a pokusí otevřít zadaný soubor. Pokud se tento konstruktor úspěšně otevře zadaného souboru, soubor je připojen k `CFile` objektu; jinak, vyvolá tento konstruktor ukazatel na `CInvalidArgException` objektu. Další informace o tom, jak zpracování výjimek najdete v tématu [výjimky](../../mfc/exception-handling-in-mfc.md).  
  
 Pokud `CFile` objekt úspěšně otevře zadaný soubor, zavře se tento soubor automaticky při `CFile` zničena objektu; jinak, je třeba výslovně zavřít soubor po je již připojen k `CFile` objektu.  
  
### <a name="example"></a>Příklad  
 Následující kód ukazuje, jak používat `CFile`.  
  
 [!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]  
  
##  <a name="close"></a>CFile::Close  
 Zavře soubor přidružené k tomuto objektu a soubor, nebude možné čtení nebo zápis.  
  
```  
virtual void Close();
```  
  
### <a name="remarks"></a>Poznámky  
 Pokud jste ještě zavřeli soubor před zničení objektu, destruktoru se automaticky zavře.  
  
 Pokud jste použili **nové** přidělit `CFile` objektu v haldě, pak je nutné odstranit po zavření souboru. **Zavřít** nastaví `m_hFile` k `CFile::hFileNull`.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFile::CFile](#cfile).  
  
##  <a name="duplicate"></a>CFile::Duplicate  
 Vytvoří duplicitní `CFile` objekt pro daný soubor.  
  
```  
virtual CFile* Duplicate() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na duplicitní `CFile` objektu.  
  
### <a name="remarks"></a>Poznámky  
 Jde o ekvivalent spuštění funkce C `_dup`.  
  
##  <a name="flush"></a>CFile::Flush  
 Vynutí veškerá data ve vyrovnávací paměti souboru pro zápis do souboru.  
  
```  
virtual void Flush();
```  
  
### <a name="remarks"></a>Poznámky  
 Použití `Flush` není zaručeno, abyste vyprázdnili z `CArchive` vyrovnávací paměti. Pokud používáte archiv, zavolejte [CArchive::Flush](../../mfc/reference/carchive-class.md#flush) první.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CFile::SetFilePath](#setfilepath).  
  
##  <a name="getfilename"></a>CFile::GetFileName  
 Volání této funkce člen načíst název zadaného souboru.  
  
```  
virtual CString GetFileName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název souboru.  
  
### <a name="remarks"></a>Poznámky  
 Například při volání `GetFileName` vygenerovat zprávu pro uživatele o souboru `c:\windows\write\myfile.wri`, název souboru, `myfile.wri`, je vrácena.  
  
 Chcete-li vrátit celou cestu k souboru, včetně názvu, volejte [GetFilePath](#getfilepath). Vrátit název souboru ( `myfile`), volání [GetFileTitle](#getfiletitle).  
  
### <a name="example"></a>Příklad  
 Tento fragment kódu otevře systému. Soubor INI v adresáři systému WINDOWS. Pokud se najde, v příkladu bude vytiskněte název a cesta a název, jak je znázorněno v rámci výstupu:  
  
 [!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]  
  
##  <a name="getfilepath"></a>CFile::GetFilePath  
 Volání této funkce člen načíst úplnou cestu zadaný soubor.  
  
```  
virtual CString GetFilePath() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Úplná cesta zadaného souboru.  
  
### <a name="remarks"></a>Poznámky  
 Například při volání `GetFilePath` vygenerovat zprávu pro uživatele o souboru `c:\windows\write\myfile.wri`, cesta k souboru `c:\windows\write\myfile.wri`, je vrácena.  
  
 Vrátit jen název souboru ( `myfile.wri`), volání [GetFileName](#getfilename). Vrátit název souboru ( `myfile`), volání [GetFileTitle](#getfiletitle).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetFileName](#getfilename).  
  
##  <a name="getfiletitle"></a>CFile::GetFileTitle  
 Volání této funkce člen načíst (zobrazovaný název) název souboru pro soubor.  
  
```  
virtual CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název základního souboru.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda volá [GetFileTitle](http://msdn.microsoft.com/library/windows/desktop/ms646924) načíst název souboru. Pokud bylo úspěšné, metoda vrátí řetězec, který by systému použít k zobrazení názvu souboru pro uživatele. Jinak, volá metodu [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589) pro získání názvu souboru podkladový soubor (včetně přípony souboru). V názvu řetězce vrácené souborů proto nebudou vždy zahrnuty přípona souboru. Další informace najdete v tématu [GetFileTitle](http://msdn.microsoft.com/library/windows/desktop/ms646924) a [PathFindFileName](http://msdn.microsoft.com/library/windows/desktop/bb773589) ve Windows SDK.  
  
 Chcete-li vrátit celou cestu k souboru, včetně názvu, volejte [GetFilePath](#getfilepath). Chcete-li vrátit jen název souboru, volejte [GetFileName](#getfilename).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [GetFileName](#getfilename).  
  
##  <a name="getlength"></a>CFile::GetLength  
 Získá aktuální délka logického souboru v bajtech.  
  
```  
virtual ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka souboru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]  
  
##  <a name="getposition"></a>CFile::GetPosition  
 Získá aktuální hodnota ukazatele souboru, který může být použit v následné volání `Seek`.  
  
```  
virtual ULONGLONG GetPosition() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatele souboru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]  
  
##  <a name="getstatus"></a>CFile::GetStatus  
 Tato metoda načítá informace o stavu týkající se dané `CFile` instance objektu nebo cestu, kterou daný soubor.  
  
```  
BOOL GetStatus(CFileStatus& rStatus) const;  
  
static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,  
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `rStatus`  
 Odkaz na uživatelem zadané **CFileStatus** struktura, která bude přijímat informace o stavu. **CFileStatus** struktura má následující pole:  
  
- **CTime – m_ctime** datum a čas vytvoření souboru.  
  
- **CTime – m_mtime** datum a čas poslední změny souboru.  
  
- **CTime – m_atime** datum a čas posledního přístupu k souboru pro čtení.  
  
- **ULONGLONG m_size** logické velikosti souboru v bajtech, vykazované příkaz DIR.  
  
- **BYTE m_attribute** bajtů atribut souboru.  
  
- **Char – m_szFullName [_max_path –]** absolutní název souboru ve znakové sadě Windows.  
  
 `lpszFileName`  
 Řetězec v systému Windows znak nastavení tedy cesty požadovaný soubor. Cesta může být relativní nebo absolutní, nebo může obsahovat název cesty sítě.  
  
 `pTM`  
 Ukazatel na objekt CAtlTransactionManager  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud informace o stavu pro zadaný soubor je úspěšně získaných, jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Nestatické verzi **getStatus –** načte informace o stavu otevřete přidružené k souboru danou `CFile` objektu.  Statické verzi **GetStatus** získá stav souboru z daného souboru cesty bez ve skutečnosti otevření souboru. To je užitečné pro testování existence a přístupová práva souboru.  
  
 **M_attribute** členem **CFileStatus** struktura odkazuje na sadu atributů souboru. `CFile` Třída poskytuje **atribut** typ výčtu, atributy souboru může být zadáno symbolicky:  
  
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
  
##  <a name="hfilenull"></a>CFile::hFileNull  
 Určuje přítomnost popisovač platný soubor pro `CFile` objektu.  
  
```  
static AFX_DATA const HANDLE hFileNull;  
```  
  
### <a name="remarks"></a>Poznámky  
 Tato konstanta slouží k určení, zda `CFile` objekt má popisovač platný soubor.  
  
 Následující příklad ukazuje, tato operace:  
  
 [!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]  
  
##  <a name="lockrange"></a>CFile::LockRange  
 Zamkne rozsah bajtů v otevření souboru, pokud už je zamčená souboru došlo k výjimce.  
  
```  
virtual void LockRange(
    ULONGLONG dwPos,  
    ULONGLONG dwCount);
```  
  
### <a name="parameters"></a>Parametry  
 `dwPos`  
 Posun bajtů spuštění rozsah bajtů k uzamčení.  
  
 `dwCount`  
 Počet bajtů v rozsahu k uzamčení.  
  
### <a name="remarks"></a>Poznámky  
 Zamykací bajty v souboru brání přístupu k těchto bajtů s jinými procesy. Zamknete více než jedné oblasti souboru, ale žádné překrývající se oblasti jsou povoleny.  
  
 Při odemknutí oblasti pomocí `UnlockRange` – členská funkce rozsah bajtů musí přesně odpovídat oblasti, která byla dříve uzamčena. `LockRange` Funkce nesloučí přiléhající oblasti; pokud jsou dva uzamčení oblasti vedle sebe, je třeba samostatně odemknout každou oblast.  
  
> [!NOTE]
>  Tato funkce není k dispozici pro `CMemFile`-odvozené třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]  
  
##  <a name="m_hfile"></a>CFile::m_hFile  
 Obsahuje popisovač souboru operačního systému pro otevření souboru.  
  
```  
HANDLE m_hFile;  
```  
  
### <a name="remarks"></a>Poznámky  
 `m_hFile`je veřejné proměnné typu **Celé_číslo**. Obsahuje `CFile::hFileNull` (prázdný soubor operačního systému nezávislé na indikátor) Pokud popisovač nebyla přiřazena.  
  
 Použití `m_hFile` se nedoporučuje, protože člen význam závisí na odvozené třídy. `m_hFile`je členem veřejné ke zvýšení pohodlí při podpoře nonpolymorphic pomocí třídy.  
  
##  <a name="m_ptm"></a>CFile::m_pTM  
 Ukazatel na `CAtlTransactionManager` objektu.  
  
```  
CAtlTransactionManager* m_pTM;  
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="open"></a>CFile::Open  
 Přetíženo. **Otevřete** je určen k použití s výchozím `CFile` konstruktor.  
  
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
 `lpszFileName`  
 Řetězec, který je cesta k souboru požadovaného. Cesta může být relativní, absolutní nebo název sítě (UNC).  
  
 `nOpenFlags`  
 A **Celé_číslo** režimu sdílení a přístup k souboru, který definuje. Určuje akci, která se má provést při otevření souboru. Možnosti můžete kombinovat pomocí bitové operace OR ( **&#124;** ) operátor. Jeden přístupová oprávnění a možnost jednu sdílenou složku jsou povinné; **modeCreate** a **modeNoInherit** režimy jsou volitelné. Najdete v článku [cfile –](#cfile) konstruktor seznam možností režimu.  
  
 `pError`  
 Ukazatel na existující objekt výjimky souborů, který se zobrazí stav neúspěšnou operaci.  
  
 `pTM`  
 Ukazatel na objekt CAtlTransactionManager  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud open byla úspěšná. jinak 0. `pError` Parametr má smysl pouze v případě, že se vrátí 0.  
  
### <a name="remarks"></a>Poznámky  
 Dvě funkce představují "bezpečnou" metodu pro otevření souboru, kde selhání je normální, očekávané podmínku.  
  
 Když `CFile` konstruktor vyvolá výjimku v chybový stav, **otevřete** vrátí **FALSE** pro chybové podmínky. **Otevřete** můžete stále inicializovat [CFileException](../../mfc/reference/cfileexception-class.md) objekt, který má v chybě, ale popisují. Pokud nezadáte `pError` parametr, nebo Pokud předáte **NULL** pro `pError`, **otevřete** vrátí **FALSE** a nevyvolá výjimku `CFileException`. Pokud předáte ukazatel na stávající `CFileException`, a **otevřete** komunikaci se chyba, funkce bude vyplňte informace, které popisují chybu. V ani případu bude **otevřete** výjimku.  
  
 Následující tabulka popisuje možné výsledky **otevřete**.  
  
|`pError`|Došlo k chybě|Návratová hodnota|CFileException obsahu|  
|--------------|------------------------|------------------|----------------------------|  
|**HODNOTU NULL**|Ne|**HODNOTA TRUE**|není k dispozici|  
|PTR na`CFileException`|Ne|**HODNOTA TRUE**|Beze změny|  
|**HODNOTU NULL**|Ano|**FALSE**|není k dispozici|  
|PTR na`CFileException`|Ano|**FALSE**|inicializovat popis chyby|  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]  
  
 [!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]  
  
##  <a name="operator_handle"></a>CFile::operator POPISOVAČ  
 Použití tohoto operátoru popisovač pro předávání `CFile` objektu na funkce, jako [readfileex spuštěná](http://msdn.microsoft.com/library/windows/desktop/aa365468) a [funkce GetFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724320) který očekávat `HANDLE`.  
  
```  
operator HANDLE() const;  
```  
  
##  <a name="read"></a>CFile::Read  
 Čte data do vyrovnávací paměti ze souboru přidružené `CFile` objektu.  
  
```  
virtual UINT Read(
    void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Ukazatel do vyrovnávací paměti zadanou uživatelem, který je pro příjem dat ze souboru přečíst.  
  
 `nCount`  
 Maximální počet bajtů ke čtení ze souboru. Pro režim textové soubory znaků CR vrátit-konce řádku páry se počítají jako jeden znaků.  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet bajtů přenesených do vyrovnávací paměti. Všimněte si, že se pro všechny `CFile` třídy, může být návratovou hodnotu menší než `nCount` Pokud bylo dosaženo konce souboru.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]  
  
 Další příklad najdete v části [CFile::Open](#open).  
  
##  <a name="remove"></a>CFile::Remove  
 Tato statická funkce odstraní soubor určený touto cestu.  
  
```  
static void PASCAL Remove(
    LPCTSTR lpszFileName, 
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Řetězec, který je cesta k souboru požadovaného. Cesta může být relativní nebo absolutní a může obsahovat název sítě.  
  
 `pTM`  
 Ukazatel na objekt CAtlTransactionManager  
  
### <a name="remarks"></a>Poznámky  
 Adresář se nebude odebrat.  
  
 **Odebrat** – členská funkce vyvolá výjimku, pokud je připojený soubor otevřít, nebo pokud soubor nelze odebrat. Jde o ekvivalent k příkazu DEL.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]  
  
##  <a name="rename"></a>CFile::Rename  
 Tato statická funkce Přejmenuje zadaný soubor.  
  
```  
static void PASCAL Rename(
    LPCTSTR lpszOldName,  
    LPCTSTR lpszNewName,  
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszOldName`  
 Staré cestě.  
  
 `lpszNewName`  
 Novou cestu.  
  
 `pTM`  
 Ukazatel na objekt CAtlTransactionManager  
  
### <a name="remarks"></a>Poznámky  
 Adresáře nelze přejmenovat. Jde o ekvivalent k příkazu REN.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]  
  
##  <a name="seek"></a>CFile::Seek  
 Přemístí ukazatele souboru v otevření souboru.  
  
```  
virtual ULONGLONG Seek(
LONGLONG lOff,  
UINT nFrom);
```  
  
### <a name="parameters"></a>Parametry  
 `lOff`  
 Počet bajtů, které mají přesunout ukazatele souboru. Kladné hodnoty přesunout ukazatel souboru na konci souboru. záporné hodnoty přesunout na začátek souboru ukazatele souboru.  
  
 `nFrom`  
 Pozice k vyhledání z. Možné hodnoty v části poznámky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pozice souboru ukazatele, pokud metoda byla úspěšná. jinak, není definován návratovou hodnotu a odkazy `CFileException` je vyvolána výjimka.  
  
### <a name="remarks"></a>Poznámky  
 Následující tabulka uvádí možné hodnoty pro `nFrom` parametr.  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`CFile::begin`|Hledání od začátku souboru.|  
|`CFile::current`|Hledat z aktuálního umístění ukazatele souboru.|  
|`CFile::end`|Hledat od konce souboru.|  
  
 Po otevření souboru ukazatele souboru je nastavený na 0, spuštění souboru.  
  
 Ukazatele souboru můžete nastavit na pozici přesahuje za konec souboru. Pokud to uděláte, velikost souboru se nezvyšuje, dokud zapisovat do souboru.  
  
 Obslužná rutina výjimky pro tuto metodu, musíte odstranit objekt výjimky, po zpracování výjimky.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]  
  
##  <a name="seektobegin"></a>CFile::SeekToBegin  
 Nastaví hodnotu ukazatele souboru na začátek souboru.  
  
```  
void SeekToBegin();
```  
  
### <a name="remarks"></a>Poznámky  
 `SeekToBegin()`je ekvivalentní `Seek( 0L, CFile::begin )`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]  
  
##  <a name="seektoend"></a>CFile::SeekToEnd  
 Nastaví hodnotu ukazatele souboru na konec logického souboru.  
  
```  
ULONGLONG SeekToEnd();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Délka souboru v bajtech.  
  
### <a name="remarks"></a>Poznámky  
 `SeekToEnd()`je ekvivalentní `CFile::Seek( 0L, CFile::end )`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]  
  
##  <a name="setfilepath"></a>CFile::SetFilePath  
 Volání této funkce můžete zadat cestu k souboru; například, pokud cesta k souboru není k dispozici při [cfile –](../../mfc/reference/cfile-class.md) vytvoření objektu, volejte `SetFilePath` ho poskytnout.  
  
```  
virtual void SetFilePath(LPCTSTR lpszNewName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszNewName`  
 Ukazatel na řetězec určující novou cestu.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> `SetFilePath`Otevřete soubor nebo vytvoření souboru. jednoduše přidruží `CFile` objekt s názvem cesty, která je pak možné použít.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]  
  
##  <a name="setlength"></a>CFile::SetLength  
 Volání této funkce změnit délku souboru.  
  
```  
virtual void SetLength(ULONGLONG dwNewLen);
```  
  
### <a name="parameters"></a>Parametry  
 `dwNewLen`  
 Požadovaná délka souboru v bajtech. Tato hodnota může být větší nebo menší než aktuální délka souboru. Soubor se rozšířené nebo zkrácen podle potřeby.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  S `CMemFile`, tato funkce může throw `CMemoryException` objektu.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]  
  
##  <a name="setstatus"></a>CFile::SetStatus  
 Nastaví stav soubor přidružený k této umístění souboru.  
  
```  
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,  
    const CFileStatus& status,  
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszFileName`  
 Řetězec, který je cesta k souboru požadovaného. Cesta může být relativní nebo absolutní a může obsahovat název sítě.  
  
 *Stav*  
 Vyrovnávací paměť, která obsahuje nové informace o stavu. Volání **GetStatus** členské funkce k prefill **CFileStatus** struktury pomocí aktuálních hodnot, a potom provést změny podle potřeby. Pokud je hodnota 0, není aktualizován odpovídající položka stavu. Najdete v článku [GetStatus](#getstatus) – členská funkce Popis **CFileStatus** struktura.  
  
 `pTM`  
 Ukazatel na objekt CAtlTransactionManager  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li nastavit dobu, změňte **m_mtime** pole z *stav*.  
  
 Pamatujte, že pokud provedete volání `SetStatus` při pokusu o změnu atributů souboru a **m_mtime** členem strukturu stav souboru je nenulové hodnoty, atributy může mít vliv i (Změna časové razítko může mít vedlejší účinky na atributy). Pokud chcete změnit pouze atributy souboru, nastavte nejprve **m_mtime** členem strukturu stav souboru nula a pak proveďte volání `SetStatus`.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]  
  
##  <a name="unlockrange"></a>CFile::UnlockRange  
 Odemkne rozsah bajtů v otevření souboru.  
  
```  
virtual void UnlockRange(
    ULONGLONG dwPos,  
    ULONGLONG dwCount);
```  
  
### <a name="parameters"></a>Parametry  
 `dwPos`  
 Posun bajtů spuštění rozsah bajtů k odemčení.  
  
 `dwCount`  
 Počet bajtů v rozsahu odemknout.  
  
### <a name="remarks"></a>Poznámky  
 Viz popis [LockRange](#lockrange) – členská funkce podrobnosti.  
  
> [!NOTE]
>  Tato funkce není k dispozici pro `CMemFile`-odvozené třídy.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]  
  
##  <a name="write"></a>CFile::Write  
 Zapisuje data z vyrovnávací paměti do souboru přidružené `CFile` objektu.  
  
```  
virtual void Write(
    const void* lpBuf,  
    UINT nCount);
```  
  
### <a name="parameters"></a>Parametry  
 `lpBuf`  
 Ukazatel do vyrovnávací paměti zadanou uživatelem, který obsahuje data, která má být zapsán do souboru.  
  
 `nCount`  
 Počet bajtů, které se mají přenést z vyrovnávací paměti. Pro režim textové soubory znaků CR vrátit-konce řádku páry se počítají jako jeden znaků.  
  
### <a name="remarks"></a>Poznámky  
 **Zápis** vyvolá výjimku, v reakci na několika podmínek, včetně disku úplné podmínku.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]  
  
 Kromě toho, podívejte se na příklady pro [CFile::CFile](#cfile) a [CFile::Open](#open).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MFC DRAWCLI](../../visual-cpp-samples.md)   
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CStdioFile – třída](../../mfc/reference/cstdiofile-class.md)   
 [CMemFile – třída](../../mfc/reference/cmemfile-class.md)
