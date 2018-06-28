---
title: Třída CMemFile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemFile
- AFX/CMemFile
- AFX/CMemFile::CMemFile
- AFX/CMemFile::Attach
- AFX/CMemFile::Detach
- AFX/CMemFile::Alloc
- AFX/CMemFile::Free
- AFX/CMemFile::GrowFile
- AFX/CMemFile::Memcpy
- AFX/CMemFile::Realloc
dev_langs:
- C++
helpviewer_keywords:
- CMemFile [MFC], CMemFile
- CMemFile [MFC], Attach
- CMemFile [MFC], Detach
- CMemFile [MFC], Alloc
- CMemFile [MFC], Free
- CMemFile [MFC], GrowFile
- CMemFile [MFC], Memcpy
- CMemFile [MFC], Realloc
ms.assetid: 20e86515-e465-4f73-b2ea-e49789d63165
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e13c3b609a53e8c885e04530995a11218bf2704d
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37040061"
---
# <a name="cmemfile-class"></a>CMemFile – třída
[Cfile –](../../mfc/reference/cfile-class.md)– odvozené třídy, která podporuje soubory paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMemFile : public CFile  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMemFile::CMemFile](#cmemfile)|Vytvoří objekt souboru paměti.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMemFile::Attach](#attach)|Blok paměti, která se připojí `CMemFile`.|  
|[CMemFile::Detach](#detach)|Umožňuje odpojit bloku paměti z `CMemFile` a vrátí ukazatel na oblast paměti odpojit.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMemFile::Alloc](#alloc)|Přepsání nastavení za účelem změny chování při přidělování paměti.|  
|[CMemFile::Free](#free)|Přepsání nastavení za účelem změny chování při zrušení přidělení paměti.|  
|[CMemFile::GrowFile](#growfile)|Přepsání změnit chování při rostoucí soubor.|  
|[CMemFile::Memcpy](#memcpy)|Přepsání nastavení za účelem změny chování při kopírování paměti při čtení a zápis souborů.|  
|[CMemFile::Realloc](#realloc)|Přepsání nastavení za účelem změny chování při opakované přidělení paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto soubory paměti chovat jako soubory disku s tím rozdílem, že je soubor uložený v paměti RAM místo na disku. Soubor paměti je užitečná pro rychlé dočasné úložiště nebo přenos nezpracovaná bajtů nebo serializovat objekty mezi nezávislé procesy.  
  
 `CMemFile` objekty lze automaticky přidělit vlastní paměti nebo můžete připojit vlastní blok paměti k `CMemFile` objekt voláním [Attach](#attach). V obou případech se přidělí paměť pro rostoucí soubor paměti automaticky v `nGrowBytes`– velikost se zvýší, pokud `nGrowBytes` není nula.  
  
 Bloku paměti bude automaticky odstraněna po zničení `CMemFile` objektu, pokud je paměť byla původně přidělena `CMemFile` objektu; jinak, je zodpovědná za rušení přidělení paměti připojen k objektu.  
  
 Mají přístup k paměti bloku pomocí ukazatele zadaný při odpojení od `CMemFile` objekt voláním [odpojení](#detach).  
  
 Nejběžnější použití `CMemFile` je vytvoření `CMemFile` objektu a použít ho voláním [cfile –](../../mfc/reference/cfile-class.md) členské funkce. Všimněte si, že vytváření `CMemFile` ho automaticky otevře: Nevolejte [CFile::Open](../../mfc/reference/cfile-class.md#open), který se používá pouze pro soubory disku. Protože `CMemFile` nepoužívá soubor na disku, datový člen `CFile::m_hFile` nepoužívá.  
  
 `CFile` Členské funkce [duplicitní](../../mfc/reference/cfile-class.md#duplicate), [LockRange](../../mfc/reference/cfile-class.md#lockrange), a [UnlockRange](../../mfc/reference/cfile-class.md#unlockrange) nejsou implementované pro `CMemFile`. Když zavoláte na tyto funkce `CMemFile` objektů, zobrazí se [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 `CMemFile` využívá funkce běhové knihovny [malloc –](../../c-runtime-library/reference/malloc.md), [realloc –](../../c-runtime-library/reference/realloc.md), a [volné](../../c-runtime-library/reference/free.md) přidělit, znovu přidělte a zrušit přidělení paměti; a vnitřní [memcpy –](../../c-runtime-library/reference/memcpy-wmemcpy.md) blokování kopírování paměti při čtení a zápisu. Pokud chcete změnit toto chování nebo chování při `CMemFile` zvětšování soubor odvodit vlastní třídu z `CMemFile` a přepsat příslušné funkce.  
  
 Další informace o `CMemFile`, najdete v článcích [soubory v prostředí MFC](../../mfc/files-in-mfc.md) a [správy paměti (MFC)](../../mfc/memory-management.md) a zobrazit [zpracování souborů](../../c-runtime-library/file-handling.md) v *Run-Time Referenční příručka knihovny*.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile –](../../mfc/reference/cfile-class.md)  
  
 `CMemFile`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afx.h  
  
##  <a name="alloc"></a>  CMemFile::Alloc  
 Tato funkce je volána `CMemFile` členské funkce.  
  
```  
virtual BYTE* Alloc(SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 *nBytes*  
 Počet bajtů paměti, která bude přidělena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatele na blok paměti, který byl přidělen, nebo **NULL** Pokud přidělení se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto funkci implementovat vlastní paměti přidělení. Pokud přepíšete tuto funkci, budete pravděpodobně chtít přepsat [volné](#free) a [realloc –](#realloc) také.  
  
 Výchozí implementace používá funkce běhové knihovny [malloc](../../c-runtime-library/reference/malloc.md) přidělit paměť.  
  
##  <a name="attach"></a>  CMemFile::Attach  
 Volání této funkce připojit blok paměti, která se `CMemFile`.  
  
```  
void Attach(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpBuffer.*  
 Ukazatel na vyrovnávací paměti, připojí se k `CMemFile`.  
  
 *nBufferSize*  
 Celé číslo, které určuje velikost vyrovnávací paměti v bajtech.  
  
 *nGrowBytes*  
 Přírůstek přidělení paměti v bajtech.  
  
### <a name="remarks"></a>Poznámky  
 To způsobí, že `CMemFile` používat bloku paměti jako soubor paměti.  
  
 Pokud *nGrowBytes* 0, `CMemFile` nastaví délku souboru *nBufferSize*. To znamená, že data v bloku paměti předtím, než se připojil k `CMemFile` se použije jako soubor. Paměť soubory vytvořené tímto způsobem nelze zvětšil.  
  
 Vzhledem k tomu, že soubor nemůže být vyvinuta, dejte pozor, abyste způsobit `CMemFile` se pokusit o zvětšení souboru. Například nemůžete volat `CMemFile` přepsání [CFile:Write](../../mfc/reference/cfile-class.md#write) k zápisu za konec nebo Nevolat [CFile:SetLength](../../mfc/reference/cfile-class.md#setlength) s délkou maximálně *nBufferSize*.  
  
 Pokud *nGrowBytes* je větší než 0, `CMemFile` bude ignorovat obsah bloku paměti, který jste připojili. Budete mít k zápisu obsahu souboru paměti od začátku pomocí `CMemFile` přepsat z `CFile::Write`. Pokud se pokusíte zapsat za koncem souboru nebo zvětšení souboru voláním `CMemFile` přepsat z `CFile::SetLength`, `CMemFile` se zvýší přidělení paměti v přírůstcích po *nGrowBytes*. Přidělení paměti se rozšiřující se nezdaří, pokud blok paměti, můžete předat `Attach` nebyla přidělena pomocí metody kompatibilní s [alokační](#alloc). Aby byl kompatibilní s výchozí implementaci `Alloc`, musíte přidělit paměť pomocí funkce běhové knihovny [malloc –](../../c-runtime-library/reference/malloc.md) nebo [calloc –](../../c-runtime-library/reference/calloc.md).  
  
##  <a name="cmemfile"></a>  CMemFile::CMemFile  
 První přetížení otevře soubor prázdný paměti.  
  
```  
CMemFile(UINT nGrowBytes = 1024);

 
CMemFile(
    BYTE* lpBuffer,  
    UINT nBufferSize,  
    UINT nGrowBytes = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *nGrowBytes*  
 Přírůstek přidělení paměti v bajtech.  
  
 *lpBuffe*r  
 Ukazatel na vyrovnávací paměť, která přijímá informace o velikosti *nBufferSize*.  
  
 *nBufferSize*  
 Celé číslo, které určuje velikost vyrovnávací paměti souboru v bajtech.  
  
### <a name="remarks"></a>Poznámky  
 Poznámka: otevření souboru konstruktorem a neměli volat [CFile::Open](../../mfc/reference/cfile-class.md#open).  
  
 Druhý přetížení chová, stejně jako použít první konstruktor a okamžitě volat [Attach](#attach) se stejnými parametry. V tématu `Attach` podrobnosti.  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCFiles#36](../../atl-mfc-shared/reference/codesnippet/cpp/cmemfile-class_1.cpp)]  
  
##  <a name="detach"></a>  CMemFile::Detach  
 Volání této funkce získání ukazatele na blok paměti používá `CMemFile`.  
  
```  
BYTE* Detach();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na blok paměti, který obsahuje obsah souboru paměti.  
  
### <a name="remarks"></a>Poznámky  
 Volání této funkce také zavře `CMemFile`. Můžete znovu připojte blok paměti k `CMemFile` voláním [Attach](#attach). Pokud chcete používat data při ji a připojte soubor, by měly volat [CFile::GetLength](../../mfc/reference/cfile-class.md#getlength) získat délku souboru před voláním `Detach`. Všimněte si, že pokud připojíte bloku paměti, aby `CMemFile` tak, aby jeho data můžete použít ( `nGrowBytes` == 0), pak nebude možné pro zvětšení souboru paměti.  
  
##  <a name="free"></a>  CMemFile::Free  
 Tato funkce je volána `CMemFile` členské funkce.  
  
```  
virtual void Free(BYTE* lpMem);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMem*  
 Ukazatel na paměť k zrušení přiřazení.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci implementovat zrušení přidělení paměti vlastní přepište. Pokud přepíšete tuto funkci, budete pravděpodobně chtít přepsat [alokační](#alloc) a [realloc –](#realloc) také.  
  
##  <a name="growfile"></a>  CMemFile::GrowFile  
 Tato funkce je volána řadou `CMemFile` členské funkce.  
  
```  
virtual void GrowFile(SIZE_T dwNewLen);
```  
  
### <a name="parameters"></a>Parametry  
 *dwNewLen*  
 Novou velikost souboru paměti.  
  
### <a name="remarks"></a>Poznámky  
 Je možné přepsat, pokud chcete změnit jak `CMemFile` zvětšování jeho souboru. Výchozí implementace volá [realloc –](#realloc) růst existující blok (nebo [alokační](#alloc) vytvořit blok paměti), přidělování paměti v násobcích `nGrowBytes` hodnotu zadaným v konstruktoru nebo [Attach](#attach) volání.  
  
##  <a name="memcpy"></a>  CMemFile::Memcpy  
 Tato funkce je volána `CMemFile` přepsání [CFile::Read](../../mfc/reference/cfile-class.md#read) a [CFile::Write](../../mfc/reference/cfile-class.md#write) k přenosu dat do a ze souboru paměti.  
  
```  
virtual BYTE* Memcpy(
    BYTE* lpMemTarget,  
    const BYTE* lpMemSource,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMemTarget*  
 Ukazatel na bloku paměti, do kterého se zkopírují paměti zdroje.  
  
 *lpMemSource*  
 Ukazatel na oblast paměti zdroje.  
  
 *nBytes*  
 Počet bajtů, které mají být zkopírovány.  
  
### <a name="return-value"></a>Návratová hodnota  
 Kopie *lpMemTarget*.  
  
### <a name="remarks"></a>Poznámky  
 Funkci přepsat, pokud chcete změnit způsob, `CMemFile` nemá tyto kopie paměti.  
  
##  <a name="realloc"></a>  CMemFile::Realloc  
 Tato funkce je volána `CMemFile` členské funkce.  
  
```  
virtual BYTE* Realloc(
    BYTE* lpMem,  
    SIZE_T nBytes);
```  
  
### <a name="parameters"></a>Parametry  
 *lpMem*  
 Ukazatel na blok paměti, který má být opětovnému přidělení.  
  
 *nBytes*  
 Nová velikost bloku paměti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatele na blok paměti, která byla znovu přidělit, (a případně přesunout), nebo **NULL** Pokud přerozdělení se nezdařilo.  
  
### <a name="remarks"></a>Poznámky  
 Tuto funkci implementovat vlastní paměti přerozdělení přepište. Pokud přepíšete tuto funkci, budete pravděpodobně chtít přepsat [alokační](#alloc) a [volné](#free) také.  
  
## <a name="see-also"></a>Viz také  
 [Cfile – třída](../../mfc/reference/cfile-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



