---
title: COleStreamFile – třída
ms.date: 11/04/2016
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
ms.openlocfilehash: 1f53d3bd55fbff45257c06af2ab11f066d421a54
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376102"
---
# <a name="colestreamfile-class"></a>COleStreamFile – třída

Představuje datový proud`IStream`( ) ve složeném souboru jako součást strukturovaného úložiště OLE.

## <a name="syntax"></a>Syntaxe

```
class COleStreamFile : public CFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleStreamFile::COleStreamFile](#colestreamfile)|Vytvoří `COleStreamFile` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleStreamFile::Připojit](#attach)|Přidruží datový proud k objektu.|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Vytvoří datový proud z globální paměti a přidruží jej k objektu.|
|[COleStreamFile::CreateStream](#createstream)|Vytvoří datový proud a přidruží jej k objektu.|
|[COleStreamFile::Detach](#detach)|Odpojí datový proud od objektu.|
|[COleStreamFile::GetStream](#getstream)|Vrátí aktuální datový proud.|
|[COleStreamFile::OpenStream](#openstream)|Bezpečně otevře datový proud a přidruží jej k objektu.|

## <a name="remarks"></a>Poznámky

Objekt `IStorage` musí existovat před otevřením nebo vytvořením datového proudu, pokud se nejedná o datový proud paměti.

`COleStreamFile`s objekty se manipuluje přesně jako s objekty [CFile.](../../mfc/reference/cfile-class.md)

Další informace o manipulaci s datovými proudy a úložišti naleznete v článku [Kontejnery: Složené soubory](../../mfc/containers-compound-files.md)..

Další informace najdete v tématu [IStream](/windows/win32/api/objidl/nn-objidl-istream) a [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) v sadě Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[Soubor C](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="colestreamfileattach"></a><a name="attach"></a>COleStreamFile::Připojit

Přidruží k `COleStreamFile` objektu zadaný datový proud OLE.

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Parametry

*lpStream*<br/>
Odkazuje na datový`IStream`proud OLE ( ) a které mají být přidruženy k objektu. Nemůže být null.

### <a name="remarks"></a>Poznámky

Objekt již nesmí být přidružen k datovému proudu OLE.

Další informace naleznete v [tématu IStream](/windows/win32/api/objidl/nn-objidl-istream) v sadě Windows SDK.

## <a name="colestreamfilecolestreamfile"></a><a name="colestreamfile"></a>COleStreamFile::COleStreamFile

Vytvoří `COleStreamFile` objekt.

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Parametry

*lpStream*<br/>
Ukazatel na datový proud OLE, který má být přidružen k objektu.

### <a name="remarks"></a>Poznámky

Pokud *lpStream* je NULL, objekt není spojen s datovým proudem OLE, jinak objekt je přidružen k zadanému datovému proudu OLE.

Další informace naleznete v [tématu IStream](/windows/win32/api/objidl/nn-objidl-istream) v sadě Windows SDK.

## <a name="colestreamfilecreatememorystream"></a><a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream

Bezpečně vytvoří nový datový proud z globální sdílené paměti, kde selhání je normální, očekávaný stav.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*chyba*<br/>
Odkazuje na objekt [CFileException](../../mfc/reference/cfileexception-class.md) nebo NULL, který označuje stav dokončení operace vytvoření. Zadejme tento parametr, pokud chcete sledovat možné výjimky generované pokusem o vytvoření datového proudu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je datový proud úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Paměť je přidělena subsystémem OLE.

Další informace naleznete v tématu [CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) v sadě Windows SDK.

## <a name="colestreamfilecreatestream"></a><a name="createstream"></a>COleStreamFile::CreateStream

Bezpečně vytvoří nový datový proud v zadaném objektu úložiště, kde selhání je normální, očekávaný stav.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpStorage*<br/>
Odkazuje na objekt úložiště OLE, který obsahuje datový proud, který má být vytvořen. Nemůže být null.

*lpszStreamName*<br/>
Název datového proudu, který má být vytvořen. Nemůže být null.

*nOpenFlags*<br/>
Přístup ový režim, který se má použít při otevírání datového proudu. Ve výchozím nastavení se používají výhradní režimy pro čtení a zápis a vytváření. Úplný seznam dostupných režimů naleznete v tématu [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*chyba*<br/>
Odkazuje na objekt [CFileException](../../mfc/reference/cfileexception-class.md) nebo NULL. Zadejme tento parametr, pokud chcete sledovat možné výjimky generované pokusem o vytvoření datového proudu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je datový proud úspěšně vytvořen; jinak 0.

### <a name="remarks"></a>Poznámky

Výjimka souboru bude vyvolána, pokud se open nezdaří a *chyba pError* není null.

Další informace naleznete v [tématu IStorage::CreateStream](/windows/win32/api/objidl/nf-objidl-istorage-createstream) v sadě Windows SDK.

## <a name="colestreamfiledetach"></a><a name="detach"></a>COleStreamFile::Detach

Odpojí datový proud od objektu bez zavření datového proudu.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na datový`IStream`proud ( ), který byl přidružen k objektu.

### <a name="remarks"></a>Poznámky

Datový proud musí být před ukončením programu uzavřen jiným způsobem.

Další informace naleznete v [tématu IStream](/windows/win32/api/objidl/nn-objidl-istream) v sadě Windows SDK.

## <a name="colestreamfilegetstream"></a><a name="getstream"></a>COleStreamFile::GetStream

Volání této funkce vrátit ukazatel na aktuální datový proud.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální rozhraní datového proudu ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)).

## <a name="colestreamfileopenstream"></a><a name="openstream"></a>COleStreamFile::OpenStream

Otevře existující datový proud.

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpStorage*<br/>
Odkazuje na objekt úložiště OLE, který obsahuje datový proud, který má být otevřen. Nemůže být null.

*lpszStreamName*<br/>
Název datového proudu, který má být otevřen. Nemůže být null.

*nOpenFlags*<br/>
Přístup ový režim, který se má použít při otevírání datového proudu. Ve výchozím nastavení se používají exkluzivní režimy a režimy čtení a zápisu. Úplný seznam dostupných režimů naleznete v tématu [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).

*chyba*<br/>
Odkazuje na objekt [CFileException](../../mfc/reference/cfileexception-class.md) nebo NULL. Zadejme tento parametr, pokud chcete sledovat možné výjimky generované pokusem o otevření datového proudu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je datový proud úspěšně otevřen; jinak 0.

### <a name="remarks"></a>Poznámky

Výjimka souboru bude vyvolána, pokud se open nezdaří a *chyba pError* není null.

Další informace naleznete v [tématu IStorage::OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
