---
title: "Třída CAtlTemporaryFile | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::CAtlTemporaryFile
- ATLFILE/ATL::CAtlTemporaryFile::Close
- ATLFILE/ATL::CAtlTemporaryFile::Create
- ATLFILE/ATL::CAtlTemporaryFile::Flush
- ATLFILE/ATL::CAtlTemporaryFile::GetPosition
- ATLFILE/ATL::CAtlTemporaryFile::GetSize
- ATLFILE/ATL::CAtlTemporaryFile::HandsOff
- ATLFILE/ATL::CAtlTemporaryFile::HandsOn
- ATLFILE/ATL::CAtlTemporaryFile::LockRange
- ATLFILE/ATL::CAtlTemporaryFile::Read
- ATLFILE/ATL::CAtlTemporaryFile::Seek
- ATLFILE/ATL::CAtlTemporaryFile::SetSize
- ATLFILE/ATL::CAtlTemporaryFile::TempFileName
- ATLFILE/ATL::CAtlTemporaryFile::UnlockRange
- ATLFILE/ATL::CAtlTemporaryFile::Write
dev_langs:
- C++
helpviewer_keywords:
- CAtlTemporaryFile class
ms.assetid: 05f0f2a5-94f6-4594-8dae-b114292ff5f9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5911de856d13d9d66e8c950d446083a36811f535
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="catltemporaryfile-class"></a>CAtlTemporaryFile – třída
Tato třída poskytuje metody pro vytváření a používání dočasný soubor.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CAtlTemporaryFile
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile)|Konstruktor|  
|[CAtlTemporaryFile:: ~ CAtlTemporaryFile](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlTemporaryFile::Close](#close)|Voláním této metody lze dočasný soubor zavřete, a buď odstranit její obsah, nebo je uložit pod názvem zadaného souboru.|  
|[CAtlTemporaryFile::Create](#create)|Voláním této metody lze vytvořit dočasný soubor.|  
|[CAtlTemporaryFile::Flush](#flush)|Voláním této metody lze vynutit veškerá data ve vyrovnávací paměti souboru má být zapsán do dočasného souboru.|  
|[CAtlTemporaryFile::GetPosition](#getposition)|Volejte tuto metodu za účelem získání aktuálního umístění ukazatele souboru.|  
|[CAtlTemporaryFile::GetSize](#getsize)|Volejte tuto metodu za účelem získání velikost v bajtech dočasný soubor.|  
|[CAtlTemporaryFile::HandsOff](#handsoff)|Volat tuto metodu za účelem zrušte přidružení souboru `CAtlTemporaryFile` objektu.|  
|[CAtlTemporaryFile::HandsOn](#handson)|Volejte tuto metodu za účelem otevře existující soubor dočasné a umístěte ukazatel na konec souboru.|  
|[CAtlTemporaryFile::LockRange](#lockrange)|Volejte tuto metodu za účelem uzamčení oblasti, v souboru s jinými procesy zabránit v přístupu k jeho.|  
|[CAtlTemporaryFile::Read](#read)|Volejte tuto metodu za účelem čtení dat z dočasný soubor začínající na pozici ukazatele souboru.|  
|[CAtlTemporaryFile::Seek](#seek)|Voláním této metody lze přesunout soubor ukazatel dočasný soubor.|  
|[CAtlTemporaryFile::SetSize](#setsize)|Volejte tuto metodu a nastavit velikost dočasný soubor.|  
|[CAtlTemporaryFile::TempFileName](#tempfilename)|Volejte tuto metodu vrátit název dočasného souboru.|  
|[CAtlTemporaryFile::UnlockRange](#unlockrange)|Volejte tuto metodu k odemknutí oblasti dočasný soubor.|  
|[CAtlTemporaryFile::Write](#write)|Volejte tuto metodu za účelem zápisu dat do dočasného souboru začínající na pozici ukazatele souboru.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlTemporaryFile::operator POPISOVAČ](#operator_handle)|Vrátí popisovač do dočasného souboru.|  
  
## <a name="remarks"></a>Poznámky  
 `CAtlTemporaryFile`umožňuje snadno vytvořit a použít dočasný soubor. Soubor je automaticky s názvem, otevřít, uzavřený a odstranit. Pokud obsah souboru zavření souboru, mohou být uloženy do nového souboru se zadaným názvem.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlfile.h  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="catltemporaryfile"></a>CAtlTemporaryFile::CAtlTemporaryFile  
 Konstruktor  
  
```
CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Soubor není otevřený ve skutečnosti, dokud je volána k [CAtlTemporaryFile::Create](#create).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_ATL_Utilities#73](../../atl/codesnippet/cpp/catltemporaryfile-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlTemporaryFile:: ~ CAtlTemporaryFile  
 Destruktor.  
  
```
~CAtlTemporaryFile() throw();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání destruktoru [CAtlTemporaryFile::Close](#close).  
  
##  <a name="close"></a>CAtlTemporaryFile::Close  
 Voláním této metody lze dočasný soubor zavřete, a buď odstranit její obsah, nebo je uložit pod názvem zadaného souboru.  
  
```
HRESULT Close(LPCTSTR szNewName = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *szNewName*  
 Název pro nový soubor pro uložení obsahu dočasný soubor v. Pokud tento argument je NULL, se odstraní obsah dočasný soubor.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="create"></a>CAtlTemporaryFile::Create  
 Voláním této metody lze vytvořit dočasný soubor.  
  
```
HRESULT Create(LPCTSTR pszDir = NULL, DWORD dwDesiredAccess = GENERIC_WRITE) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszDir`  
 Cesta pro dočasný soubor. Pokud je hodnota NULL, [GetTempPath](http://msdn.microsoft.com/library/windows/desktop/aa364992) bude volána k přiřazení cesty.  
  
 `dwDesiredAccess`  
 Požadovaný přístup. V tématu `dwDesiredAccess` v [CreateFile](http://msdn.microsoft.com/library/windows/desktop/aa363858) ve Windows SDK.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="flush"></a>CAtlTemporaryFile::Flush  
 Voláním této metody lze vynutit veškerá data ve vyrovnávací paměti souboru má být zapsán do dočasného souboru.  
  
```
HRESULT Flush() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Podobně jako [CAtlTemporaryFile::HandsOff](#handsoff)kromě toho, že soubor není uzavřený.  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="getposition"></a>CAtlTemporaryFile::GetPosition  
 Volejte tuto metodu za účelem získání aktuálního umístění ukazatele souboru.  
  
```
HRESULT GetPosition(ULONGLONG& nPos) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Pozice v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Můžete změnit umístění souboru ukazatele [CAtlTemporaryFile::Seek](#seek).  
  
##  <a name="getsize"></a>CAtlTemporaryFile::GetSize  
 Volejte tuto metodu za účelem získání velikost v bajtech dočasný soubor.  
  
```
HRESULT GetSize(ULONGLONG& nLen) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nLen`  
 Počet bajtů v souboru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
##  <a name="handsoff"></a>CAtlTemporaryFile::HandsOff  
 Volat tuto metodu za účelem zrušte přidružení souboru `CAtlTemporaryFile` objektu.  
  
```
HRESULT HandsOff() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 `HandsOff`a [CAtlTemporaryFile::HandsOn](#handson) se používají k zrušte přidružení souboru z objektu a připojte ho v případě potřeby. `HandsOff`bude vynutit veškerá data ve vyrovnávací paměti souboru má být zapsán do dočasného souboru a poté zavřete soubor. Pokud chcete zavřít a trvale odstranit soubor, nebo pokud chcete zavřít a zachovat obsah souboru se zadaným názvem, použijte [CAtlTemporaryFile::Close](#close).  
  
##  <a name="handson"></a>CAtlTemporaryFile::HandsOn  
 Volejte tuto metodu za účelem otevře existující soubor dočasné a umístěte ukazatel na konec souboru.  
  
```
HRESULT HandsOn() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 [CAtlTemporaryFile::HandsOff](#handsoff) a `HandsOn` se používají k zrušte přidružení souboru z objektu a připojte ho v případě potřeby.  
  
##  <a name="lockrange"></a>CAtlTemporaryFile::LockRange  
 Volejte tuto metodu za účelem uzamčení oblasti, v dočasný soubor na jiné procesy zabránit v přístupu k jeho.  
  
```
HRESULT LockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Pozice v souboru, kde by měl začínat zámek.  
  
 `nCount`  
 Délka rozsah bajtů, které se uzamkne.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Zamykací bajty v souboru brání přístupu k těchto bajtů s jinými procesy. Zamknete více než jedné oblasti souboru, ale žádné překrývající se oblasti jsou povoleny. Chcete-li úspěšně odemknout oblasti, použijte [CAtlTemporaryFile::UnlockRange](#unlockrange), zajištění rozsah bajtů přesně odpovídá oblasti, která byla dříve uzamčena. `LockRange`nesloučí přiléhající oblasti; Pokud jsou dva uzamčení oblasti vedle sebe, je třeba každý odemknout samostatně.  
  
##  <a name="operator_handle"></a>CAtlTemporaryFile::operator POPISOVAČ  
 Vrátí popisovač do dočasného souboru.  
  
```  
operator HANDLE() throw();
```  
  
##  <a name="read"></a>CAtlTemporaryFile::Read  
 Volejte tuto metodu za účelem čtení dat z dočasný soubor začínající na pozici ukazatele souboru.  
  
```
HRESULT Read(
    LPVOID pBuffer,
    DWORD nBufSize,
    DWORD& nBytesRead) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pBuffer`  
 Ukazatel do vyrovnávací paměti, která bude přijímat data načtená ze souboru.  
  
 `nBufSize`  
 Velikost vyrovnávací paměti v bajtech.  
  
 `nBytesRead`  
 Počet přečtených bajtů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CAtlFile::Read](../../atl/reference/catlfile-class.md#read). Chcete-li změnit umístění ukazatele souboru, volejte [CAtlTemporaryFile::Seek](#seek).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="seek"></a>CAtlTemporaryFile::Seek  
 Voláním této metody lze přesunout soubor ukazatel dočasný soubor.  
  
```
HRESULT Seek(LONGLONG nOffset, DWORD dwFrom = FILE_CURRENT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nOffset`  
 Posun v bajtech od počátečního bodu poskytují *dwFrom.*  
  
 `dwFrom`  
 Výchozí bod (FILE_BEGIN, FILE_CURRENT nebo FILE_END).  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CAtlFile::Seek](../../atl/reference/catlfile-class.md#seek). Chcete-li získat aktuální umístění ukazatele souboru, volejte [CAtlTemporaryFile::GetPosition](#getposition).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
##  <a name="setsize"></a>CAtlTemporaryFile::SetSize  
 Volejte tuto metodu a nastavit velikost dočasný soubor.  
  
```
HRESULT SetSize(ULONGLONG nNewLen) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nNewLen`  
 Nové délka souboru v bajtech.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CAtlFile::SetSize](../../atl/reference/catlfile-class.md#setsize). Při návratu ukazatele souboru je nastavený na konci souboru.  
  
##  <a name="tempfilename"></a>CAtlTemporaryFile::TempFileName  
 Volejte tuto metodu vrátit název dočasného souboru.  
  
```
LPCTSTR TempFileName() throw();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `LPCTSTR` odkazující na název souboru.  
  
### <a name="remarks"></a>Poznámky  
 Název souboru je vytvořen v [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile) pomocí volání [GetTempFile](http://msdn.microsoft.com/library/windows/desktop/aa364991)funkce Windows SDK. Přípona souboru bude vždy "TFR" pro dočasný soubor.  
  
##  <a name="unlockrange"></a>CAtlTemporaryFile::UnlockRange  
 Volejte tuto metodu k odemknutí oblasti dočasný soubor.  
  
```
HRESULT UnlockRange(ULONGLONG nPos, ULONGLONG nCount) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nPos`  
 Pozice v souboru, kde by měl začínat odemčení.  
  
 `nCount`  
 Délka rozsahu bajtů k odemknutí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CAtlFile::UnlockRange](../../atl/reference/catlfile-class.md#unlockrange).  
  
##  <a name="write"></a>CAtlTemporaryFile::Write  
 Volejte tuto metodu za účelem zápisu dat do dočasného souboru začínající na pozici ukazatele souboru.  
  
```
HRESULT Write(  
    LPCVOID pBuffer,
    DWORD nBufSize,
    DWORD* pnBytesWritten = NULL) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pBuffer`  
 Vyrovnávací paměť obsahující data, která má být zapsán do souboru.  
  
 `nBufSize`  
 Počet bajtů, které se mají přenést z vyrovnávací paměti.  
  
 `pnBytesWritten`  
 Počet zapsaných bajtů.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí `S_OK` na úspěch nebo Chyba `HRESULT` při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Volání [CAtlFile::Write](../../atl/reference/catlfile-class.md#write).  
  
### <a name="example"></a>Příklad  
 Podívejte se na příklad pro [CAtlTemporaryFile::CAtlTemporaryFile](#catltemporaryfile).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [CAtlFile – třída](../../atl/reference/catlfile-class.md)
