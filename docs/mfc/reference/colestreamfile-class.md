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
ms.openlocfilehash: 96e8fee71f02ea750fd8b33f41fd2fd517e9081e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503691"
---
# <a name="colestreamfile-class"></a>COleStreamFile – třída

Představuje datový proud dat (`IStream`) ve složeném souboru jako součást strukturovaného úložiště OLE.

## <a name="syntax"></a>Syntaxe

```
class COleStreamFile : public CFile
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleStreamFile::COleStreamFile](#colestreamfile)|`COleStreamFile` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleStreamFile::Attach](#attach)|Přidruží datový proud k objektu.|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Vytvoří datový proud z globální paměti a přidruží ho k objektu.|
|[COleStreamFile::CreateStream](#createstream)|Vytvoří datový proud a přidruží ho k objektu.|
|[COleStreamFile::Detach](#detach)|Zruší přidružení datového proudu k objektu.|
|[COleStreamFile::GetStream](#getstream)|Vrátí aktuální datový proud.|
|[COleStreamFile::OpenStream](#openstream)|Bezpečně otevře datový proud a přidruží ho k objektu.|

## <a name="remarks"></a>Poznámky

Aby bylo možné datový proud otevřít nebo vytvořit, musí existovat objekt,pokudsenejednáoproudpaměti.`IStorage`

`COleStreamFile`objekty jsou manipulovány přesně jako objekty [CFile –](../../mfc/reference/cfile-class.md) .

Další informace o manipulaci s datovými proudy a úložišti najdete v kontejnerech článků [: Složené soubory](../../mfc/containers-compound-files.md)...

Další informace najdete v tématu [IStream](/windows/win32/api/objidl/nn-objidl-istream) a [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) v Windows SDK.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CFile –](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AFXOLE. h

##  <a name="attach"></a>COleStreamFile:: Attach

Přidruží zadaný datový proud OLE k `COleStreamFile` objektu.

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>Parametry

*lpStream*<br/>
Odkazuje na datový proud OLE (`IStream`), který má být přidružen k objektu. Nemůže mít hodnotu NULL.

### <a name="remarks"></a>Poznámky

Objekt již nesmí být přidružen ke streamu OLE.

Další informace najdete v tématu [IStream](/windows/win32/api/objidl/nn-objidl-istream) v Windows SDK.

##  <a name="colestreamfile"></a>COleStreamFile::COleStreamFile

`COleStreamFile` Vytvoří objekt.

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>Parametry

*lpStream*<br/>
Ukazatel na datový proud OLE, který má být přidružen k objektu.

### <a name="remarks"></a>Poznámky

Pokud má *LPSTREAM* hodnotu null, objekt není přidružen ke streamu OLE, v opačném případě je objekt přidružen k dodanému streamu OLE.

Další informace najdete v tématu [IStream](/windows/win32/api/objidl/nn-objidl-istream) v Windows SDK.

##  <a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream

Bezpečně vytvoří nový Stream z globální sdílené paměti, kde selhání je normální, očekávaná podmínka.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*pError*<br/>
Odkazuje na objekt [CFileException](../../mfc/reference/cfileexception-class.md) nebo hodnotu null, která označuje stav dokončení operace vytvoření. Zadejte tento parametr, pokud chcete monitorovat možné výjimky vygenerované při pokusu o vytvoření datového proudu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je datový proud úspěšně vytvořen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Paměť přiděluje Podsystém OLE.

Další informace najdete v tématu [CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) v Windows SDK.

##  <a name="createstream"></a>COleStreamFile:: CreateStream –

Bezpečně vytvoří nový datový proud v zadaném objektu úložiště, ve kterém je selhání normální, očekávaná podmínka.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parametry

*lpStorage*<br/>
Odkazuje na objekt úložiště OLE, který obsahuje datový proud, který má být vytvořen. Nemůže mít hodnotu NULL.

*lpszStreamName*<br/>
Název streamu, který se má vytvořit Nemůže mít hodnotu NULL.

*nOpenFlags*<br/>
Režim přístupu, který se má použít při otevírání streamu. Ve výchozím nastavení se používají exkluzivní režimy pro čtení a zápis a vytváření. Úplný seznam dostupných režimů najdete v tématu [CFile –:: CFile –](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Odkazuje na objekt [CFileException](../../mfc/reference/cfileexception-class.md) nebo na hodnotu null. Zadejte tento parametr, pokud chcete monitorovat možné výjimky vygenerované při pokusu o vytvoření datového proudu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je datový proud úspěšně vytvořen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud se otevření nezdaří a *pError* nemá hodnotu null, bude vyvolána výjimka souboru.

Další informace naleznete v tématu [IStorage:: CreateStream –](/windows/win32/api/objidl/nf-objidl-istorage-createstream) v Windows SDK.

##  <a name="detach"></a>COleStreamFile::D etach

Zruší přidružení datového proudu k objektu bez zavření datového proudu.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na datový proud (`IStream`), který byl přidružen k objektu.

### <a name="remarks"></a>Poznámky

Před ukončením programu musí být datový proud uzavřen jiným způsobem.

Další informace najdete v tématu [IStream](/windows/win32/api/objidl/nn-objidl-istream) v Windows SDK.

##  <a name="getstream"></a>COleStreamFile:: GetStream

Voláním této funkce vrátíte ukazatel na aktuální datový proud.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální rozhraní datového proudu ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)).

##  <a name="openstream"></a>COleStreamFile::OpenStream

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
Odkazuje na objekt úložiště OLE, který obsahuje datový proud, který má být otevřen. Nemůže mít hodnotu NULL.

*lpszStreamName*<br/>
Název datového proudu, který se má otevřít Nemůže mít hodnotu NULL.

*nOpenFlags*<br/>
Režim přístupu, který se má použít při otevírání streamu. Ve výchozím nastavení se používají výhradně režimy čtení a zápis. Úplný seznam dostupných režimů naleznete v tématu [CFile –:: CFile –](../../mfc/reference/cfile-class.md#cfile).

*pError*<br/>
Odkazuje na objekt [CFileException](../../mfc/reference/cfileexception-class.md) nebo na hodnotu null. Zadejte tento parametr, pokud chcete monitorovat možné výjimky vygenerované při pokusu o otevření streamu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud se datový proud úspěšně otevřel; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pokud se otevření nezdaří a *pError* nemá hodnotu null, bude vyvolána výjimka souboru.

Další informace naleznete v tématu [IStorage:: OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) v Windows SDK.

## <a name="see-also"></a>Viz také:

[CFile – třída](../../mfc/reference/cfile-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
